---
name: context-handoff
description: Use when the user wants to hand off, transfer or brief another agent or fresh session on a chosen part of the current context.
---

# Context handoff

Write a brief that lets an agent with zero access to this conversation continue one slice of the work.

## 1. Pin down the slice

You need two things:
- **Scope:** which part of the context to carry over.
- **Next task:** what the receiving agent should do with it. This decides what is relevant.

Take both from the request or the conversation. Ask one short question only if a wrong guess would change what goes in. Also note whether the receiver can access the same files and repo. If unknown, assume it can't read this chat but can read the repo, and say so.

## 2. Gather

Pull everything in scope, plus anything outside it that the task depends on (an earlier decision, a constraint, a correction). Leave the rest out.

- Keep the user's requirements and corrections in their own words. Paraphrasing loses constraints.
- Record what was tried and failed, and why, so it isn't repeated.
- Separate what was verified (ran it, read it) from what was assumed or only proposed. A suggestion the user never accepted is not a decision.
- Point to things the receiver can open (paths, branch, commit, URLs, commands). Paste content only if the receiver can't get it, or exact wording matters, such as error messages.
- If files or git state are available, check them instead of relying on memory of the conversation.
- Never include keys, tokens or passwords. Name the environment variable instead.

## 3. Output

Return one copyable block, fenced with four backticks so inner code blocks survive. Drop any empty section. Write to a file only if asked.

````markdown
# Handoff: <short title>

## Task
<What to do next>
**Done when:** <checkable condition>

## Background
<Only what's needed to understand the task>

## Current state
- Verified: ...
- Unverified / assumed: ...

## Decisions and constraints
- <decision> (why)
- User said: "..."

## Tried and failed
- <approach>: <why it failed>

## Pointers
- <path / command / URL>: <what's there>

## Open questions
- ...

## Start here
Check the current state against the files, restate the task in two lines, then <first action>. Ask if anything conflicts.
````

## 4. Check

Reread the brief as an agent that has only this text. Fix undefined names, "the bug" or "as discussed" references, and missing first steps. Keep it as short as it can be while passing that test, usually under 500 words.

After the block, add one line listing notable things you left out, so the user can ask for them back.