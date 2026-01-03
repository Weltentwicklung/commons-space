# Sessions

**Version:** 0.1 (Temporary manual tracking)  
**Note:** This will be migrated to SQL table when database is operational.  
**Future location:** `/src/database/` tables

---

## Session List

| session_id | session_start | session_end | topics | contributors |
|------------|---------------|-------------|--------|--------------|
| 1 | 2024-12-24 | 2024-12-29 | Constitutional Framework, License Creation, Anarchism Philosophy, Documentation System | 1, 2 |
| 2 | 2024-12-25 | ongoing | GitHub Structure, Database Design, Documentation | 1, 2 |

---

## Topics Index

**Session 1:**
- Constitutional Framework
- Philosophical Foundation  
- License Creation (Weltentwicklung License)
- Project Naming (commons-space)
- Documentation System Design
- Anarchism as Edge State
- GKW as Fallback Mechanism
- Anti-Institutionalization Design
- GitHub Structure
- Contributor ID System

**Session 2:**
- GitHub Structure finalization
- Database normalization
- Documentation refinement
- Session tracking system
- Contributor system design

---

## Documents Created by Session

**Session 1:**
- `docs/constitution/constitution-v0.1.md`
- `docs/constitution/constitution-v0.2.md`
- `docs/license/weltentwicklung-license-v0.1.md`
- `development-logs/session-001/SESSION-1-RAW.txt`

**Session 2:**
- `README.md` (updated)
- `development-logs/README.md`
- `sessions_v0.1.md` (this file)
- `contributors_v0.1.md`
- `CONTRIBUTORS.md` (revised)

---

## Future Database Structure

This file will be replaced by SQL tables. Planned structure:

```sql
-- Core session table
CREATE TABLE sessions (
    session_id INT AUTO_INCREMENT PRIMARY KEY,
    session_start DATE NOT NULL,
    session_end DATE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Session topics (normalized, many-to-many)
CREATE TABLE topics (
    topic_id INT AUTO_INCREMENT PRIMARY KEY,
    topic_name VARCHAR(200) UNIQUE NOT NULL
);

CREATE TABLE session_topics (
    session_id INT NOT NULL,
    topic_id INT NOT NULL,
    PRIMARY KEY (session_id, topic_id),
    FOREIGN KEY (session_id) REFERENCES sessions(session_id),
    FOREIGN KEY (topic_id) REFERENCES topics(topic_id)
);

-- Session contributors (normalized, many-to-many)
CREATE TABLE session_contributors (
    session_id INT NOT NULL,
    contributor_id INT NOT NULL,
    PRIMARY KEY (session_id, contributor_id),
    FOREIGN KEY (session_id) REFERENCES sessions(session_id),
    FOREIGN KEY (contributor_id) REFERENCES contributors(contributor_id)
);

-- Session documents created
CREATE TABLE session_documents (
    document_id INT AUTO_INCREMENT PRIMARY KEY,
    session_id INT NOT NULL,
    file_path VARCHAR(500) NOT NULL,
    document_type ENUM('constitution', 'license', 'code', 'documentation', 'other'),
    FOREIGN KEY (session_id) REFERENCES sessions(session_id)
);
```

---

## Notes

- **session_id:** Simple auto-increment integer (1, 2, 3, ...)
- **session_start/end:** Dates only (no duration calculated here)
- **topics:** Free text for now, will become normalized topic_id references
- **contributors:** Comma-separated IDs for now, will become separate table rows

**Duration calculation:** Not stored, calculated as `session_end - session_start` when needed

---

**For detailed session information:** See `development-logs/session-*/` folders

**For contributor details:** See `contributors_v0.1.md`