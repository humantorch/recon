# Apply

Full application assistance for a role. Helps with resume selection, application questions, cover letters, and creates a tracking file when submitted.

## Variables

role: $ARGUMENTS (company name, role title, or exact filename — whatever identifies the role)

---

## Instructions

### Phase 1: Load Context

Read:
- `context/profile.md`
- `context/search-criteria.md`
- `resumes/index.md`

Match `$ARGUMENTS` against files in `roles/flagged/` and `roles/applied/` — by filename, company, or role title, doesn't need to be exact. If exactly one file matches, read it and proceed. If several could match, list them and ask which one. If nothing matches, ask the user to describe the role or run `/assess` first.

### Phase 2: Resume

Confirm which resume version to use based on the role (per `resumes/index.md`).
Note any specific adjustments needed — exact language, not vague suggestions.

### Phase 3: Application Questions

For each question on the application form:
- Draft a specific, honest answer grounded in real experience from `context/profile.md`
- Keep answers concise — respect character/word limits if specified
- Do not manufacture enthusiasm. If the connection is real, show it. If it isn't, find what is real.
- "Why this company" answers must be specific to this company, not generic boilerplate

**For standing questions, reference `context/profile.md`:**
- Team size and management scope → use the user's actual background
- Salary expectations → use the anchor from `context/search-criteria.md`; do not volunteer the floor
- Start date → use the user's standing answer if defined in profile
- Location and work authorization → use the user's details from profile

### Phase 4: Cover Letter

Reference the user's cover letter stance from `context/profile.md`.

Only draft if:
- The role explicitly asks for one, OR
- There is a domain gap large enough that a human needs to read past the resume

If drafting: lead with something specific and real — a genuine connection to the company, domain, or problem. No generic openers.

Target 300-400 words unless a specific limit is given.

### Phase 5: Create / Update Role File

If the application is being submitted:
1. Move or create file in `roles/applied/[company-role-slug].md`
2. Update `context/applications.md` with current status
3. Set status to `applied` and record the date

Offer to create the file if it doesn't exist yet.

If `context/github-project.md` has an Owner set, also update the matching project item's Pipeline Status to `Applied` (see that file for the exact commands). If no matching item exists yet, create one rather than skipping the sync. Skip silently if Owner is blank.
