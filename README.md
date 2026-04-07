# PersonalAgents

A spec-driven, multi-package reference system for AI agents.  
Each package is an independent project with its own spec, plan, and task list.

---

## Folder Structure

```
CoinBazar/                              ← this repo (agent reference system)
├── agent-config.json                   ← set solution_root + list active packages
├── AGENT_INSTRUCTIONS.md               ← behavioral rules enforced on every agent
├── README.md                           ← this file
│
├── projects/
│   ├── coinbazar/                      ← package: coinbazar
│   │   ├── SUMMARY.md                  ← read first: current state & open questions
│   │   ├── SPEC.md                     ← source of truth: requirements
│   │   ├── PLANNING.md                 ← architecture & design (derived from spec)
│   │   └── IMPLEMENTATION.md           ← task list & status (derived from planning)
│   │
│   └── catcygame/                      ← package: catcygame
│       ├── SUMMARY.md
│       ├── SPEC.md
│       ├── PLANNING.md
│       └── IMPLEMENTATION.md
│
└── templates/                          ← copy these when adding a new package
    ├── SPEC_TEMPLATE.md
    ├── PLANNING_TEMPLATE.md
    ├── IMPLEMENTATION_TEMPLATE.md
    └── SUMMARY_TEMPLATE.md
```

---

## Spec-Driven Flow

```
User provides requirements
        ↓
   Fill SPEC.md          ← source of truth
        ↓
   Fill PLANNING.md      ← derived from spec (architecture, data models, API)
        ↓
Fill IMPLEMENTATION.md   ← derived from planning (phased task list)
        ↓
  Update SUMMARY.md      ← updated each session (current state)
```

**The authority chain:** `SPEC → PLANNING → IMPLEMENTATION`  
Never update a downstream doc in a way that contradicts an upstream one without updating the upstream first.

---

## Setup

1. Open [agent-config.json](agent-config.json)
2. Set `solution_root` to the folder where your actual code projects live
3. `active_projects` lists the currently active package names

---

## Adding a New Package

1. Create `projects/<package-name>/`
2. Copy all 4 files from `templates/` into it (rename `SPEC_TEMPLATE.md` → `SPEC.md`, etc.)
3. Fill in `SPEC.md` first — do not write planning or implementation until the spec is confirmed
4. Add the package name to `active_projects` in `agent-config.json`

---

## Passing Reference to an Agent

**All packages:**
```
/path/to/CoinBazar/
```

**Single package:**
```
/path/to/CoinBazar/projects/coinbazar/
```

The agent reads docs in this order: `SUMMARY.md` → `SPEC.md` → `PLANNING.md` → `IMPLEMENTATION.md`

---

## Core Agent Rule

The agent must **ask** at any point of doubt.  
It must never assume, guess, or hallucinate.  
All spec questions must be raised before planning begins.  
All planning questions must be raised before implementation begins.  
See [AGENT_INSTRUCTIONS.md](AGENT_INSTRUCTIONS.md) for the full rule set.
