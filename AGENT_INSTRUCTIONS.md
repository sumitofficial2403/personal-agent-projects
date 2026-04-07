# Agent Behavioral Instructions

These rules apply to every project in this reference system. Read and follow them without exception.

---

## Core Rules

### 1. Ask — Never Assume
If you are uncertain about **anything** — a requirement, a file path, a business rule, a user intent — **stop and ask**.

Do not guess. Do not fill in blanks with what "seems right". Ask a specific, targeted question and wait for the answer before proceeding.

**Wrong behavior:**
> "I'll assume the API base URL is `/api/v1` since that's common."

**Right behavior:**
> "What is the API base URL? I need this before I can proceed."

---

### 2. Never Hallucinate
Do not invent:
- File names or paths that you haven't verified exist
- Library APIs, function signatures, or config keys you haven't confirmed
- Business logic, data models, or requirements not explicitly stated
- "Standard" behavior that you haven't confirmed applies here

If you don't know something, say so. Look it up using available tools. Ask the user.

---

### 3. Confirm Before Destructive Actions
Before deleting files, dropping data, overwriting code, or any irreversible action — **state what you're about to do and ask for confirmation**.

---

### 4. Clarify Scope Before Starting
Before beginning any non-trivial task:
- Restate your understanding of the task in 2–3 bullet points
- List any open questions
- Ask for confirmation before writing code

---

### 5. Read Before You Write
Before modifying any file, read its current state. Never overwrite code you haven't read.

---

### 6. Stay In Scope
Only change what is asked. Do not refactor, rename, or "improve" adjacent code. Do not add features that weren't requested.

---

### 7. Follow the Spec-Driven Reading Order
Each project is a **package**. Before starting any work on a package, read its docs in this order:

1. `SUMMARY.md` — current state, in-progress work, open questions (fast orientation)
2. `SPEC.md` — the source of truth; functional and non-functional requirements
3. `PLANNING.md` — architecture and design decisions derived from the spec
4. `IMPLEMENTATION.md` — task list and completion status

**The chain of authority is: SPEC → PLANNING → IMPLEMENTATION.**  
If these files conflict with each other or with what the user says, **stop and ask**. Never silently resolve conflicts by picking one side.

---

### 8. Update Docs As You Work
When you complete a step, update `IMPLEMENTATION.md` to reflect the new status. When a decision is made, log it in `SUMMARY.md`.

---

## How To Use This Reference System

The agent should be passed either:
- The root path of this folder (to access `agent-config.json` and all projects), or
- A specific project subfolder path (e.g., `./projects/coinbazar/`) to scope to one project

The `agent-config.json` at the root contains the path to the actual code (`solution_root`). Use it to resolve where the real source files live.
