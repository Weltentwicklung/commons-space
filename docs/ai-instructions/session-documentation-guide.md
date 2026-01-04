# Session Documentation Guide

## Overview

Each session produces 3 files to serve different purposes:
1. **Raw transcript** - Complete conversation (transparency)
2. **Metadata** - Machine-readable data (automation)
3. **Protocol** - Human-readable summary (understanding)

---

## File 1: Raw Transcript

**Filename:** `session-[id]-raw.txt`  
**Format:** Plain text  
**Purpose:** Complete transparency, full conversation preserved

### Structure:

```
================================================================================
RAW CONVERSATION TRANSCRIPT - SESSION [ID]
================================================================================

Session ID: [number]
Topic: [Brief description]
Date: [Start date] - [End date]

Contributors:
- [contributor_id]
- [contributor_id]

Related Documents Created During This Session:
- [list of files]

================================================================================
CONVERSATION BEGIN - [Start date]
================================================================================

Contributor-[id]:
[First message]

---

Contributor-[id]:
[Response]

---

[Continue conversation format...]

================================================================================
END OF RAW TRANSCRIPT - SESSION [ID]
================================================================================

Session Complete: [Dates]
Major Outcomes: [Brief list]
Next Session Topics: [Brief list]

================================================================================
```

### Guidelines:
- Minimal formatting (just readability)
- Word-for-word conversation
- Use contributor IDs (1, 2, 3...) not names
- Include all messages, including errors and corrections
- Preserve authenticity (typos, informal language, etc.)

---

## File 2: Metadata

**Filename:** `session-[id]-metadata.yaml`  
**Format:** YAML  
**Purpose:** Machine-readable for automation, database import, search

### Required Fields:

```yaml
session_id: [number]
title: "[Brief descriptive title]"

# Session Information
date_start: YYYY-MM-DD
date_end: YYYY-MM-DD
duration: null  # or HH:MM for timed sessions
location: "Remote" # or city/venue
media_type: "text" # or audio, video, mixed
language: "en" # ISO code

# Participants
contributors:
  - [id]  # Just numbers
  - [id]

# Topics Covered
topics:
  - "[Topic 1]"
  - "[Topic 2]"
  - "[etc]"

# Documents Created
documents_created:
  - path: "[relative path]"
    description: "[What it is]"
    status: "created" # or uploaded, pending, etc

# Documents Updated
documents_updated:
  - path: "[relative path]"
    changes: "[What changed]"

# Key Decisions Made
key_decisions:
  - decision: "[What was decided]"
    rationale: "[Why]"

# Major Insights
insights:
  - "[Insight 1]"
  - "[Insight 2]"

# Technical Decisions
technical:
  - "[Technical decision or implementation detail]"

# Open Questions
open_questions:
  - "[Question for future sessions]"

# Next Session Topics
next_session:
  - "[Topic 1]"
  - "[Topic 2]"

# Session Statistics
word_count: ~[number]
conversation_turns: ~[number]
documents_created_count: [number]

# Links
github_repo: "https://github.com/Weltentwicklung/commons-space"
session_folder: "[URL to session folder]"
```

### Guidelines:
- Use YAML format (machine-readable)
- Be comprehensive (this is for automation)
- Include all relevant metadata
- Use lists for multiple items
- Keep descriptions brief but clear

---

## File 3: Protocol

**Filename:** `session-[id]-protocol.md`  
**Format:** Markdown  
**Purpose:** Human-readable summary for quick understanding  
**Length:** Maximum 2 A4 pages

### Structure:

```markdown
# Session [ID] Protocol: [Title]

**Session ID:** [number]  
**Date:** [Start] - [End]  
**Contributors:** [ids]

---

## Executive Summary

[2-3 sentences summarizing entire session]

---

## 1. [Topic Name]

[2-5 sentence summary of what happened]

**Actions:**
- [Bullet point of main action]
- [Bullet point of main action]
- [etc]

**Conclusion:** [If important decision or insight]

---

## 2. [Topic Name]

[Continue same format...]

---

## Varias

**[Minor topics]:**
- [One-liner for troubleshooting or minor items]

---

## Key Decisions

| Decision | Rationale |
|----------|-----------|
| [Decision] | [Why] |

---

## Next Session Topics

1. [Topic]
2. [Topic]

---

## Links

- **Repository:** [URL]
- **[Other relevant links]**

---

*Protocol v1.0 - Created [Date]*
```

### Guidelines:

**DO:**
- Keep concise (max 2 A4 pages)
- Use 2-5 sentence summaries per topic
- Bullet points for main steps only
- Combine related topics
- Use "Varias" for minor items
- Include key decisions table
- Focus on high-level overview

**DON'T:**
- Repeat data from metadata file
- Go into excessive detail
- Include full code/commands (just reference)
- Add `status: complete` (always implied)
- Make longer than 2 A4 pages

**Topics should be:**
- High-level (combine related work)
- Action-focused (what was done)
- Conclusion when important decision made

---

## Creation Workflow

### During Session:
1. Have conversation naturally
2. Take mental notes of major topics

### After Session Complete:

**Step 1: Create Raw Transcript**
- Copy entire conversation
- Add header and footer
- Format with contributor IDs
- Save as `session-[id]-raw.txt`

**Step 2: Create Metadata**
- Extract key information
- Fill YAML template
- Include all relevant data
- Save as `session-[id]-metadata.yaml`

**Step 3: Create Protocol**
- Write executive summary
- Organize into 5-7 main topics
- Keep each topic to 2-5 sentences + bullets
- Add key decisions table
- Ensure under 2 A4 pages
- Save as `session-[id]-protocol.md`

**Step 4: Upload to GitHub**
```
development-logs/session-[id]/
  session-[id]-raw.txt
  session-[id]-metadata.yaml
  session-[id]-protocol.md
```

---

## Quality Checklist

### Raw Transcript:
- [ ] Complete conversation included
- [ ] Contributor IDs used (not names)
- [ ] Header and footer present
- [ ] Related documents listed

### Metadata:
- [ ] All required fields filled
- [ ] Valid YAML format
- [ ] Lists properly formatted
- [ ] GitHub links included

### Protocol:
- [ ] Under 2 A4 pages
- [ ] Executive summary present
- [ ] 5-7 main topics
- [ ] Each topic 2-5 sentences + bullets
- [ ] Key decisions table included
- [ ] No redundant data from metadata
- [ ] Links section present

---

## Examples

See completed sessions for reference:
- `development-logs/session-1/` - Foundation session
- `development-logs/session-2/` - GitHub setup session

---

*Version: 1.0 - Created 2025-01-03*
