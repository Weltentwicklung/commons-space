# Persons

**Version:** 0.1 (Temporary manual tracking)  
**Note:** This will be migrated to SQL table when database is operational.  
**Future location:** `/src/database/` tables

---

## Person List

| person_id | name | contact_email | joined |
|-----------|------|---------------|--------|
| 1 | Stefan Hubschmid | info@visionaere-bewegung.org | 2024-12-24 |

---

## Notes

- **One person = One contributor_id:** Each real person can only have ONE contributor ID
- **Privacy balance:** Names stored for transparency, but not displayed in most contexts
- **Contact:** Primary email for reaching this person
- **Address:** Optional field (not shown here, can be added when needed)

**For contributor mapping:** See [contributors_v0.1.md](contributors_v0.1.md)  
**For session participation:** See [sessions_v0.1.md](sessions_v0.1.md)

---

## Future Database Structure

```sql
persons (
  person_id INT PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  contact_email VARCHAR(255),
  address TEXT,
  joined DATE NOT NULL
)
```

**One-to-One Relationship:**
- One person → One contributor_id
- This ensures clarity: same contributor_id = same person
- Prevents confusion through multiple identities
- Note: Reputation building is not possible on this platform by design (no ranking, no status system)
