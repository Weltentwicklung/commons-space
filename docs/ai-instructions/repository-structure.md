# commons-space Repository Structure

**Repository:** https://github.com/Weltentwicklung/commons-space

**Last Updated:** 2025-01-03

---

## Quick Navigation

**Core Documents:**
- Philosophical Foundation: `/docs/foundation/philosophical-foundation/`
- Constitution: `/docs/foundation/constitution/`
- License: `/docs/license/` (pending)
- Contributors Guide: `/docs/guides/contributions_v0.2.md`

**AI Instructions:** `/docs/ai-instructions/`

**Latest Session:** `/development-logs/session-3/session-3-protocol.md`

**Database Files:** `/database/` (temporary tracking, will migrate to SQL)

---

## Full Structure

```
commons-space/
│
├── README.md (pending)
├── LICENSE.md (pending)
├── TODO.md (pending)
│
├── /database/                          # Temporary tracking (manual .md files)
│   ├── contributors_v0.1.md           # Contributor tracking table
│   ├── persons_v0.1.md                # Person details (one person = one contributor)
│   ├── entities_v0.1.md               # Entity details (AI, bots only)
│   ├── sessions_v0.1.md               # Session tracking table
│   └── /archive/                      # Old versions when updated
│
├── /docs/
│   ├── /foundation/                   # Core philosophical & legal documents
│   │   ├── /philosophical-foundation/ # Folder: Philosophical background (human-readable)
│   │   ├── /constitution/             # Folder: Platform governance framework
│   │   └── /archive/                  # Previous versions
│   │
│   ├── /ai-instructions/              # Instructions for AI assistants
│   │   ├── /general-instructions/     # Folder: How to work with project
│   │   ├── /philosophical-instructions/ # Folder: Philosophy condensed for AI
│   │   ├── /session-documentation-guide/ # Folder: How to create session files
│   │   ├── /repository-structure/     # Folder: Navigation guide (contains this file)
│   │   └── /archive/                  # Previous versions
│   │
│   ├── /license/
│   │   └── (pending weltentwicklung-license)
│   │
│   ├── /guides/                       # Documentation & handbooks
│   │   ├── /contributions/            # Folder: Contributor system philosophy
│   │   └── /archive/
│   │
│   └── /technical/                    # Future: ER diagrams, API specs
│
├── /development-logs/                 # Session documentation
│   ├── README.md                      # Explains documentation system
│   │
│   ├── /session-1/                    # Foundation session
│   │   ├── session-1-raw.txt         # Complete transcript
│   │   ├── session-1-metadata.yaml   # Machine-readable data
│   │   └── session-1-protocol.md     # Human summary (2 pages max)
│   │
│   └── /session-2/                    # GitHub setup & organization
│       ├── session-2-raw.txt
│       ├── session-2-metadata.yaml
│       └── session-2-protocol.md
│
└── /src/                              # Future: source code

```

---

## File Naming Rules

**Current files:** Always have version number in filename
- Example: `constitution_v0.1.md`, `contributors_v0.1.md`

**When updated:**
1. Create new version: `constitution_v0.2.md`
2. Move old to archive: `mv constitution_v0.1.md archive/`
3. No renaming needed

**Result:** Main folders always contain latest version only

---

## Important Notes

**Session Protocols:**
- Never updated after creation (historical record)
- Always found in `/development-logs/session-[id]/`

**Database Files:**
- Temporary manual tracking (.md files)
- Will migrate to SQL database in Phase 2

**Archive Pattern:**
- Each folder with versions contains `/archive/` subfolder
- Old versions moved there when superseded
- Main folders stay clean

---

## Finding Latest Version

**Pattern:** Check main folder for file with highest version number
- `/docs/constitution/constitution_v0.X.md` ← Latest in main folder
- `/docs/constitution/archive/` ← Previous versions

**Tools:** Use `web_fetch` to read any specific file from repository

---

*Version: 1.0 - Created 2025-01-03*  
*Update this file when major structural changes occur*
