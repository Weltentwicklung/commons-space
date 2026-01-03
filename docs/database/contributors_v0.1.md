# Contributors

**Version:** 0.1 (Temporary manual tracking)  
**Note:** This will be migrated to SQL table when database is operational.  
**Future location:** `/src/database/` tables

---

## Contributor List

| contributor_id | person_id | entity_id | joined |
|----------------|-----------|-----------|--------|
| 1 | 1 | NULL | 2024-12-24 |
| 2 | NULL | 2 | 2024-12-24 |

---

## Notes

- **person_id OR entity_id:** Each contributor is either a person OR an entity, never both
- **One person = One contributor_id:** Real persons can only have ONE contributor ID
- **Multiple contributors per entity:** Entities CAN have multiple contributor IDs (different contexts/working groups)
- **No sessions field:** Would be redundant - see [sessions_v0.1.md](sessions_v0.1.md) for session participation
- **Joined:** Date of first contribution

**Important:** All contributors map to either a person or entity for full transparency. Contact information, addresses, and names are stored in the persons/entities tables, not here.

**For person information:** See [persons_v0.1.md](persons_v0.1.md)  
**For entity information:** See [entities_v0.1.md](entities_v0.1.md)  
**For session participation:** See [sessions_v0.1.md](sessions_v0.1.md)  
**For system explanation:** See [contribution_v0.1.md](contribution_v0.1.md)

---

## Future Normalization

**When database is operational:**

```sql
-- Contributors table (lightweight, references persons OR entities)
contributors (
  contributor_id INT PRIMARY KEY,
  person_id INT REFERENCES persons(person_id),
  entity_id INT REFERENCES entities(entity_id),
  joined DATE,
  CONSTRAINT one_source CHECK (
    (person_id IS NOT NULL AND entity_id IS NULL) OR
    (person_id IS NULL AND entity_id IS NOT NULL)
  )
)
```

This separation allows:
- Clean contributor tracking without redundant contact data
- Single source of truth for person/entity information
- Easy updates to contact info without touching contributor records
- Support for multiple contributors from same entity
- Support for different roles with one login (contributions, voting, group creation, etc.)
