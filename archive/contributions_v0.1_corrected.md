# Contributors

**Note:** This is a temporary manual list for transparency during the foundation phase. Once the database is operational, contributor data will be managed via SQL table and this file will link to the platform's contributor page.

For technical contributor table schema, see: `/src/database/schema.sql` (when created)
<!-- Better something like: The SQL table will be located in ...-->
---

## Current Contributors

| ID | Name | Role | Contact | Joined | Sessions | Active |
|----|------|------|---------|--------|----------|--------|
| 1 | Stefan Hubschmid | Initiator, Primary Vision | info@visionaere-bewegung.org | 2024-12-24 | 001, 002 | Yes |
| 2 | Claude.ai (Anthropic) | Technical Advisor, Documentation | N/A (AI) | 2024-12-24 | 001, 002 | Yes |
<!-- I don't know best practice but i guess sql is always small for titles? also: 
ID: if id is ok like that (because inside of contributor table) we can leave it as it is, if "contributor_id" would be better (example for later references) the we may better change it. 
Name:
Isn't it better to have something like surname and family name? maybe (because of you) even better would be surname | familiyname | institution all with the possibility of null. so you will have null | null | Claue.ai (Anthropic) and i will have stefan | hubschmid | null
also one person maybe a contributor, a creator of a group, a voter ... simultaniously -> reuse of the id
role: Wouldn't a good nomalized table have a separate table and here only add a role_id? that way we can better work with the roles. 
Contact: could be splitted in email | street | "PLZ" (-> in engl.) | country | phone

Sessions: First it would need to be 1, 2 .... (as session_id is autoincrement). Secound about having multiple infos in one cell, wouldn't a normalized table need one row per session?

Active: Better : last_contribution (or because of github, last_push?)

-> but better normalized would be to have contributor_id 1 | id (person_id (or a better name for the indivitual) or company_id (or entity_id for AI???))

So
| id (or contributor_id) | person_id | session_start | session_end (no duration needed -> short sessions like hourly, as well as long sessions over multiple days can be calculated from this 2 infos, so no further infor needed) |

also that's enought to generate a view, if we have a person.md (or better name) with:
| surname | familyname | country | city | street | nr | email | phone

and a company.md and/or ai.md ....

but maybe its a bit to much to have contributor table normalized and the persons just there by id

-->

---

## About Contributor IDs

**Why IDs instead of prominent names?**

This project follows an **anti-personality-cult principle**. We believe:

- Ideas matter more than individuals
- Collective effort creates value
- Focus on people creates hierarchies
- Everyone contributes equally
<!-- Not bad but better would be something like:
- Personality-cult in the society leads to the worship and idealization of people
- This supports hierarchic structure, unequal evaluation of peoples and fame
- It reduces the ability to concentrate on content
- supports the focus on people instead of content
- reduces the ability of selfreflection and openness to criticism
- reduces accountability because of the goodwill towards famous peoples
-->
**Therefore:**
- Contributors receive sequential numeric IDs
- IDs are used in all session documentation
- Full details available in this table for transparency
- No "founder" status or special recognition <!-- you litteraly added "initiator" to my name which is equal to founder xD as i say we should normalize toppics and just make a toppic for creation of fundamental strucures (that also other can have if they contribute :) -->
<!-- we could add

***The appreciation of people is an important part in the humans live, but it should be done on a personal matter but be excluded in society - level projects.***
To appreciate peoples on a direct level helps them to feel the appreciation without overwelmning them and it helps for motivation and inspration.

-->
-->

**Balance:** Complete transparency (full table) without hero-worship (ID-based references)

<!--
- Complets transparence....
- Appreciation included on the right level (personal) but excluded on the wrong level (society)
-->

---

## How to Become a Contributor

**Current Phase:** Foundation design by core team 
<!-- above we stated: no core team, here "core team", without explanation ;) better something like:
Building a good fundament after the core principles stated in the constitution. To contribute contact:info@visionaere-bewegung.org, subject: Contribution to common-space
-->

**Future Phases:**

Once the platform is operational, becoming a contributor will be simple:

1. **Register:** Use the self-service contributor registration form
2. **Receive ID:** System automatically assigns next available ID
3. **Contribute:** Participate in discussions, code, documentation, etc.
4. **Recorded:** All contributions automatically tracked 
<!-- 
well that difficult to say like that, we have to say that there will be contributor_guidelines. There we should write how the adaptation of the system works. We have to refine that, because for now it's just clear, that strucural changes is a matter of the society, not of a single person. so they can push (github) but the merging will be done after evaluation and voting (in later phases). We maybe need 3 phases depending on the amout of participants 
1. creation phase (now) -> Contact me
2. growing phase (or something that makes clear -> it's about to grow)
and 
3. Integration phase (common-space is integrated in the first local communities or countries or used widely in society (eventually measured by a cutof of participants) -> because the view may be different in different localities, we have to think about it deeper)

For now i suggest: 
**Future Phases:**
Will be clearified later (or something like that)
-->

**Principle:** Anyone can contribute. No gatekeeping. No application process. Just start helping. 
<!-- again above you write: register, here: no application, is that ok like that in english or is a registration not a kind of applicaiton?
We can also write just
"After phase 1 (Creation Phase) The contribution will be open to everyone under the conditions stated in the contributer_guidelines (will be created)"-->

---

## Contribution Types

Contributors can help with:

- **Design:** Architecture, UI/UX, system design
- **Development:** Backend, frontend, database
- **Documentation:** Writing, editing, translating
- **Testing:** Bug reports, feature testing, user feedback
- **Philosophy:** Constitutional refinement, principle clarification
- **Community:** Helping others, answering questions, onboarding

**All equally valuable.** Platform tracks what you do, not who you are. <!--this sentence and **All equally valuable.** is unnecessary here -->

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
<!-- There shouldn't be contributor roles. If you have a contributor id and you make contribution in a table will be saved, to which toppincs you contributed. nothing more is needed. no contributor roles are needed. They actaually would be bad as they, even if written otherwise, can produce subconsious evaluations. So we can delete this hole section or write, that no contributor roles exists but rather a contributer can have one or more contribution toppics -> for clearification if "contributor roles" is often used in other projects -->

---

## Future: Database Migration

**When platform operational, this structure will become:**
<!-- this hole section depends on the normalization we will choose -->
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
- ✅ Credit collective effort <!-- no we don't credit collective effort as this would credit something. its clear a contribution gets nothing in return and is a free givt to humanity -->

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
<!-- i would leave this seciton for now and maybe just write: a system for easy contribution will be created -->
---

## Volunteer Principles

All contributors agree to:

1. **Volunteer Work:** No payment for platform development
2. **Collective Ownership:** Work belongs to the commons
3. **Transparency:** All work visible and documented
4. **No Status Building:** Don't use platform for reputation/career
5. **Anti-Institutionalization:** Resist permanent roles
6. **Ideas Over Identity:** Focus on what, not who
<!-- very good :) -->
**Why these principles?**

They prevent the platform from becoming a vehicle for personal advancement, which would create conflicting interests (incentive to maintain unnecessary structures).

---

## Questions?

**About contributing:** See [README.md](README.md)   <!-- Later contributor_guidelines -->
**About sessions:** See [development-logs/README.md](development-logs/README.md)  
**General inquiries:** info@visionaere-bewegung.org

---

**Remember:** This list shows who contributed, not who "owns" the project. The platform belongs to all humanity, present and future.

*"Names don't matter, the people who fill things with life do!"*