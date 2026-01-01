# Entities

**Version:** 0.1 (Temporary manual tracking)  
**Note:** This will be migrated to SQL table when database is operational.  
**Future location:** `/src/database/` tables

---

## Entity List

| entity_id | name | type | contact_info | joined |
|-----------|------|------|--------------|--------|
| 2 | Claude.ai (Anthropic) | AI | N/A | 2024-12-24 |

---

## Entity Types

- **AI:** Artificial intelligence systems (e.g., Claude, GPT, etc.)
- **Bot:** Automated systems

**Note:** Organizations or groups may apply as individual contributors. See contribution_v0.1.md for details.

---

## Notes

- **Multiple contributors per entity:** Entities (AI/Bots) CAN have multiple contributor IDs
  - Example: AI used by different persons → different contributor IDs per person using it
- **Why multiple IDs?** Same AI used by different people in different contexts needs separate tracking

**For contributor mapping:** See [contributors_v0.1.md](contributors_v0.1.md)  
**For session participation:** See [sessions_v0.1.md](sessions_v0.1.md)

---

## Future Database Structure

```sql
entities (
  entity_id INT PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  type ENUM('AI', 'Bot') NOT NULL,
  contact_info TEXT,
  joined DATE NOT NULL
)

-- Example:
-- Entity 2 (Claude.ai) → Contributor 2 (used by Person 1)
-- Entity 2 (Claude.ai) → Contributor 5 (used by Person 3)
```

**One-to-Many Relationship:**
- One AI/Bot entity → Multiple contributor_ids (when used by different persons)
- Each contributor_id still maps to exactly ONE entity or person
