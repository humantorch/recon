# Assess

Evaluate a job posting for fit. Produces a structured assessment and a go/no-go recommendation.

## Variables

input: $ARGUMENTS (URL, pasted JD text, or a path to a local file containing the JD — plain text or PDF)

---

## Instructions

### Phase 1: Load Context

Read:
- `context/profile.md`
- `context/search-criteria.md`
- `resumes/index.md`
- `context/assessed-rejections.md`

### Phase 2: Duplicate Check

Before fetching or assessing anything, scan `context/assessed-rejections.md` for a matching URL or Company + Title combination.

If a match is found: stop immediately and inform the user — "This role was already assessed on [date] and received a No-Go: [reason]." Do not proceed with a full assessment unless the user explicitly asks to re-assess.

### Phase 3: Get the JD

If `$ARGUMENTS` starts with http/https, fetch the URL. This is the canonical URL — carry it forward to Phase 4 regardless of what happens next.

If the fetch fails, or returns something that isn't a usable JD (a JS-rendered shell, a login wall, garbled text — Ashby-hosted postings in particular tend to fail this way even though the link works fine in a browser), don't give up on the URL. Tell the user the fetch didn't work and ask them to paste the JD text directly, or save it to a local file and pass the path instead. The URL they originally gave you is still canonical — keep it for Phase 4, don't treat this as a URL-less paste.

If `$ARGUMENTS` is a path to a local file, read the file (plain text or PDF) and use its contents as the JD text.

If `$ARGUMENTS` is pasted text, use it directly.

If `$ARGUMENTS` is empty, ask the user to paste or provide the JD, a URL if there is one.

**Canonical URL check:** whenever the JD arrives as pasted text or a local file (not a directly-fetched URL), scan the text itself for a posting URL (a "view job" / "apply here" link, a Greenhouse/Lever/Workday/etc. link, or similar, often present at the top or bottom of a copied posting). If one is found, that's the canonical URL, use it.

If no URL is found in the text, ask the user for it before archiving: "Do you have the link to this posting? I'd like to keep it with the record." Some postings genuinely have no URL to give, a recruiter forwarding a JD as a PDF or Word doc with no public listing is a normal, common case, not just an edge case. If the user confirms there's no URL (no public posting, a screenshot transcription, a posting that's already gone), proceed without one rather than blocking the assessment — set `url` to `"none"` in Phase 4 and note the source (e.g. "PDF from recruiter") in the role file's Notes section instead.

### Phase 4: Archive the JD

Once the JD content is in hand, save it to `jd-archive/` before proceeding. This preserves the posting even if it's taken down later.

Set `url` to the canonical URL found or provided in Phase 3. Only use `"none"` if the user confirmed no URL exists (e.g. a recruiter-sent PDF with no public posting).

- Derive a slug from the company name and role title (kebab-case, e.g. `grafana-labs-em-app-platform`)
- Write to `jd-archive/[slug].md` with this format:

```
---
company: [Company Name]
title: [Role Title]
url: [source URL or "none"]
captured: [YYYY-MM-DD]
---

[Full JD text as fetched or provided]
```

### Phase 5: Assess

Produce a structured assessment covering:

**Role basics**
- Company, title, location, salary (if listed), employment type
- Remote policy — does it support the user's location?

**Fit summary**
- Overall rating: Strong / Good / Marginal / Poor — with one sentence rationale

**Strengths**
- Where the user's background directly maps to what they're asking for
- Be specific, not generic

**Gaps**
- Honest assessment of where the fit breaks down
- Distinguish between hard gaps (likely disqualifying) and soft gaps (addressable in interview)

**Resume recommendation**
- Which version to use (per `resumes/index.md`)
- Specific adjustments needed, if any

**Application strategy**
- Cover letter needed? Reference the user's default stance from `context/profile.md`
- Key talking points to emphasize
- Any application form questions to anticipate

**Compensation check**
- Does the posted range meet the user's floor from `context/search-criteria.md`?
- Flag immediately if it doesn't — no point proceeding

**Go / No-Go recommendation**
- Clear recommendation with reasoning
- If No-Go, say why plainly

### Phase 6: Offer Next Steps

If Go: offer to create a role file in `roles/flagged/` using the template. Populate the **URL** field with the same value used in Phase 4 (the canonical URL, or "none" if confirmed there isn't one) — the role file and the JD archive should always agree on the source URL.

If No-Go:
- Close the assessment — don't soft-pedal it into a maybe
- Append a row to `context/assessed-rejections.md` with: Company, Title, URL, one-line No-Go reason, today's date
