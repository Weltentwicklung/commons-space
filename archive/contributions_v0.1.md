# Contributors

**Note:** This is a temporary manual list for transparency during the foundation phase. Once the database is operational, contributor data will be managed via SQL table and this file will link to the platform's contributor page.

For technical contributor table schema, see: `/src/database/schema.sql` (when created)

---

## Current Contributors

| ID | Name | Role | Contact | Joined | Sessions | Active |
|----|------|------|---------|--------|----------|--------|
| 1 | Stefan Hubschmid | Initiator, Primary Vision | info@visionaere-bewegung.org | 2024-12-24 | 001, 002 | Yes |
| 2 | Claude.ai (Anthropic) | Technical Advisor, Documentation | N/A (AI) | 2024-12-24 | 001, 002 | Yes |

---

## About Contributor IDs

**Why IDs instead of prominent names?**

This project follows an **anti-personality-cult principle**. We believe:

- Ideas matter more than individuals
- Collective effort creates value
- Focus on people creates hierarchies
- Everyone contributes equally

**Therefore:**
- Contributors receive sequential numeric IDs
- IDs are used in all session documentation
- Full details available in this table for transparency
- No "founder" status or special recognition

**Balance:** Complete transparency (full table) without hero-worship (ID-based references)

---

## How to Become a Contributor

**Current Phase:** Foundation design by core team

**Future Phases:**

Once the platform is operational, becoming a contributor will be simple:

1. **Register:** Use the self-service contributor registration form
2. **Receive ID:** System automatically assigns next available ID
3. **Contribute:** Participate in discussions, code, documentation, etc.
4. **Recorded:** All contributions automatically tracked

**Principle:** Anyone can contribute. No gatekeeping. No application process. Just start helping.

---

## Contribution Types

Contributors can help with:

- **Design:** Architecture, UI/UX, system design
- **Development:** Backend, frontend, database
- **Documentation:** Writing, editing, translating
- **Testing:** Bug reports, feature testing, user feedback
- **Philosophy:** Constitutional refinement, principle clarification
- **Community:** Helping others, answering questions, onboarding

**All equally valuable.** Platform tracks what you do, not who you are.

---

## Contributor Roles

**Note:** Roles are descriptive, not hierarchical. Everyone has equal decision rights.

**Common Roles:**
- **Initiator:** Started the project
- **Core Contributor:** Regular active participation
- **Technical Advisor:** Provides technical guidance
- **Translator:** Translates documentation
- **Designer:** Creates visual/UX elements
- **Tester:** Tests features and reports issues

**Roles can change** as contributors' focus shifts. Multiple roles common.

---

## Future: Database Migration

**When platform operational, this structure will become:**

```sql
CREATE TABLE contributors (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255),
    location VARCHAR(255),
    contact_info TEXT,
    joined_date DATE NOT NULL,
    active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE contributor_sessions (
    contributor_id INT NOT NULL,
    session_id INT NOT NULL,
    role VARCHAR(100),
    PRIMARY KEY (contributor_id, session_id),
    FOREIGN KEY (contributor_id) REFERENCES contributors(id),
    FOREIGN KEY (session_id) REFERENCES sessions(id)
);

CREATE TABLE contributions (
    id INT AUTO_INCREMENT PRIMARY KEY,
    contributor_id INT NOT NULL,
    type ENUM('code', 'documentation', 'design', 'testing', 'other'),
    description TEXT,
    session_id INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (contributor_id) REFERENCES contributors(id),
    FOREIGN KEY (session_id) REFERENCES sessions(id)
);
```

**This file will then become:**

```markdown
# Contributors

See current contributors on the platform:
https://commons-space.org/contributors

For database schema, see: `/src/database/schema.sql`
```

**No redundancy.** Single source of truth in database.

---

## Contributor Statistics

**Session 001:**
- Total contributors: 2
- New contributors: 2
- Sessions completed: 1
- Documents created: 3 (Constitution v0.1, v0.2, License v0.1)

**All-time:**
- Total contributors: 2
- Total sessions: 1 (+ 1 in progress)
- Total documents: 3
- Lines of documentation: ~15,000
- Lines of code: 0 (pre-development phase)

*Updated: December 25, 2024*

---

## Recognition Without Hierarchy

We recognize contributions without creating hierarchies:

**What we do:**
- ✅ Track all contributions in database
- ✅ Show who participated in what
- ✅ Make information searchable
- ✅ Credit collective effort

**What we don't do:**
- ❌ Create "core team" vs "contributors" distinction
- ❌ Award badges, karma, or reputation points
- ❌ Rank contributors by "importance"
- ❌ Give special status to early contributors
- ❌ Use contributions as social currency

**Why:** Prevents institutionalization and status hierarchies that would undermine platform values.

---

## Adding Yourself (Future)

When self-service registration is available:

1. Visit commons-space.org/contribute
2. Fill in registration form:
   - Name (required)
   - Email (optional but recommended)
   - Location (optional)
   - Contact info (optional)
   - Areas of interest
3. Agree to volunteer principles
4. Receive your contributor ID
5. Start contributing!

**No approval needed.** System is open by default.

---

## Volunteer Principles

All contributors agree to:

1. **Volunteer Work:** No payment for platform development
2. **Collective Ownership:** Work belongs to the commons
3. **Transparency:** All work visible and documented
4. **No Status Building:** Don't use platform for reputation/career
5. **Anti-Institutionalization:** Resist permanent roles
6. **Ideas Over Identity:** Focus on what, not who

**Why these principles?**

They prevent the platform from becoming a vehicle for personal advancement, which would create conflicting interests (incentive to maintain unnecessary structures).

---

## Questions?

**About contributing:** See [README.md](README.md)  
**About sessions:** See [development-logs/README.md](development-logs/README.md)  
**General inquiries:** info@visionaere-bewegung.org

---

**Remember:** This list shows who contributed, not who "owns" the project. The platform belongs to all humanity, present and future.

*"Names don't matter, the people who fill things with life do!"*