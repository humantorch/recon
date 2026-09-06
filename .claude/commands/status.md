# Status

Pipeline overview. Shows all active applications, current status, last activity, and next action.

---

## Instructions

### Phase 1: Load Context

Read:
- `context/applications.md`
- All files in `roles/applied/`
- All files in `roles/flagged/`

### Phase 2: Produce Status Report

Output a clean pipeline summary:

**Active Applications**
For each role in `roles/applied/` with status applied/screen/interviewing/offer:
- Company, role, status, days since last activity
- Next action (follow up? wait? prep for interview?)
- Flag if silent for more than 2 weeks with role still listed — may warrant a follow-up or write-off

**Flagged (Not Yet Applied)**
For each role in `roles/flagged/`:
- Company, role, fit rating
- Why it hasn't been applied to yet
- Prompt if it's been sitting there too long without action

**Closed**
Brief summary count only — no detail needed unless asked

If `context/github-project.md` has an Owner configured, mention the board URL once at the end of the summary as a reference (`github.com/users/[owner]/projects/[number]`) — don't fetch or re-render it, the markdown files above are already the full picture.

### Phase 3: Recommendations

After the status summary:

1. **Highest priority action** — one specific thing to do today
2. **Pipeline health check** — is the pipeline thin? Should more roles be added?
3. **Any roles to write off** — if something has been silent for 3+ weeks with no signal, call it

Be direct. If the pipeline is thin, say so. If a role is almost certainly dead, say so.
