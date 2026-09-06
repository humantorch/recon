# Prep

Interview preparation for a specific role. Loads role context, identifies likely interview themes, and prepares talking points and questions to ask.

## Variables

role: $ARGUMENTS (company name, role title, or exact filename — whatever identifies the role)

---

## Instructions

### Phase 1: Load Context

Read:
- `context/profile.md`
- `context/search-criteria.md`

Match `$ARGUMENTS` against files in `roles/applied/` and `roles/flagged/` — by filename, company, or role title, doesn't need to be exact. If exactly one file matches, read it and proceed. If several could match, list them and ask which one. If nothing matches, ask the user to describe the role.

Fetch the company's recent news if not already in the role file — understanding what's happening at the company right now sharpens preparation.

### Phase 2: Interview Landscape

Based on the role and company, identify:

**Likely interview stages:**
- Recruiter screen
- Hiring manager conversation
- Technical or domain-specific interview
- Leadership / values / culture
- Panel or final round

**Likely themes per stage** — be specific to this role and company, not generic.

### Phase 3: Preparation Materials

**Talking points**
Draw from the user's background in `context/profile.md`. For each relevant story:
- The situation
- What they did specifically
- The outcome with numbers where possible

Map these to the role's stated requirements. Don't generate generic talking points — connect the user's actual experience to what this specific company is asking for.

**Domain or skill gaps (if applicable)**
If the role requires something the user has adjacent but not direct experience with, prepare an honest framing that acknowledges the gap without underselling real depth.

**Questions to ask**
5-7 genuine questions tailored to this company and role. They should signal real research and real opinions — not a generic list.

### Phase 4: Offer Next Steps

- Offer to run a mock interview question
- Offer to update the role file with prep notes
