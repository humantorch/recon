# Setup

First-run onboarding for Recon. Walks through filling in your profile and search criteria so every other command works correctly.

---

## Instructions

Greet the user and explain what you're doing:

> "Welcome to Recon. Before we can assess roles or track applications, I need to know who you are and what you're looking for. I'll ask you a series of questions and build your profile and search criteria from your answers. This takes about 10 minutes and you only do it once."

Work through each section below sequentially. Ask the questions conversationally — don't dump the whole list at once. Wait for each answer before moving on. After each section, confirm what you captured before proceeding.

---

## Section 1: Who You Are

Ask:
1. What's your name, location, and time zone?
2. What's your current role and company (if employed)?
3. What's your background — how long have you been in your field, and what's the arc of your career?
4. What are your strongest skills and the work you're most proud of?
5. Do you have a GitHub, LinkedIn, personal site, or portfolio? Any public projects worth mentioning?

---

## Section 2: What You're Looking For

Ask:
1. What types of roles are you targeting? (Title, seniority, individual contributor vs. management, etc.)
2. Where can you work? Remote, hybrid, in-person? Any geographic constraints?
3. What's your compensation floor — the number below which you won't seriously engage?
4. Are you open to contract/freelance arrangements, or FTE only?
5. Are there visa or work authorization constraints to be aware of?

---

## Section 3: Strong Preferences and Hard Nos

Ask:
1. What does a great opportunity look like for you beyond the basics? (Team size, domain, company stage, culture, etc.)
2. What are your hard nos — things that would make you decline regardless of everything else?
3. Are there domains or industries you're specifically interested in, or specifically avoiding?

---

## Section 4: Application Defaults

Ask:
1. What's your default position on cover letters? (Always, never, only when required, etc.)
2. What salary anchor do you use when asked — what number do you lead with?
3. Are there standing answers you'd like to pre-load? (Start date, visa status, preferred work style, etc.)

---

## Section 5: Resume Versions

Ask:
1. Do you have multiple versions of your resume for different types of roles?
2. If yes, briefly describe each version and when you'd use it.

---

## After All Sections

Write the following files based on the conversation:

1. `context/profile.md` — full professional profile using the template structure
2. `context/search-criteria.md` — criteria, preferences, and hard nos
3. `resumes/index.md` — resume version index (even if it's just one version)

Show the user each file after writing it and ask: "Does this look right? Anything to add or correct?"

Then confirm:

> "You're set up. Here's what you can do now:
> - `/assess [url or JD text]` — evaluate a role for fit
> - `/status` — see your pipeline at a glance
> - `/apply [company or role]` — get help applying to a specific role
>
> Bring me a job posting whenever you're ready."
