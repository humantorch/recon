# GitHub Project Board

<!--
Optional. If you want a visual Kanban view of your pipeline alongside the
markdown files, set this up via /setup (GitHub Project Board section) or fill
it in by hand after creating the project yourself.

Leave the fields below blank to skip this feature entirely — every command
checks whether Owner is set before attempting any sync, and does nothing
(no errors, no prompts) if it's blank.
-->

**Owner:** 
<!-- Your GitHub username, e.g. "humantorch" -->

**Project number:** 
<!-- The number in the project URL: github.com/users/<owner>/projects/<number> -->

**Pipeline Status field name:** Pipeline Status
<!-- The single-select field on the project that mirrors role status. Default
name is "Pipeline Status" — change only if you named it something else. -->

---

## Status Mapping

Role file `Status` → Project `Pipeline Status` option. Both sides should use
these exact option names:

| Role file Status | Project Pipeline Status |
|------------------|--------------------------|
| flagged          | Flagged                  |
| applied          | Applied                  |
| screen           | Screen                   |
| interviewing     | Interviewing             |
| offer            | Offer                    |
| rejected         | Rejected                 |
| withdrawn        | Withdrawn                |

---

## Sync Rule

Whenever a role file's **Status** field changes, for any reason, through
`/apply`, `/assess`, or just editing the file directly in conversation, also
update the matching project item's Pipeline Status field to keep the board in
sync. Match project items by title (`[Company] — [Role Title]`, same as the
role file's own title). If no matching item exists yet, create one as a draft
issue rather than skipping the sync.

This file being blank is the signal to skip all of this — don't ask about it
per-command, just check once at the top of the relevant phase.

---

## How to Sync (commands)

Assumes `gh` is authenticated and Owner/Project number above are filled in.
Substitute `$OWNER` and `$NUMBER` from this file.

**Create a new item** (used by `/assess` when flagging a Go):
```sh
gh project item-create $NUMBER --owner "$OWNER" --title "[Company] — [Role Title]"
```
This prints the new item's id — you'll need it for the status update below.

**Look up an existing item** by title (used whenever you need to update
status and don't already have the item id):
```sh
gh project item-list $NUMBER --owner "$OWNER" --format json --limit 200
```
Match on `content.title`. If nothing matches, create it first (above).

**Get the field id and option ids** (once per session is enough, they don't change):
```sh
gh project field-list $NUMBER --owner "$OWNER" --format json
```
Find the field named "Pipeline Status" (or whatever's configured above) and
note its `id` and each option's `id`.

**Get the project's node id** (needed for the edit command below):
```sh
gh project view $NUMBER --owner "$OWNER" --format json
```
The `id` field in the response, looks like `PVT_...`.

**Update an item's status:**
```sh
gh project item-edit --id [item-id] --project-id [project-node-id] --field-id [field-id] --single-select-option-id [option-id]
```

If any of these commands fail (auth expired, project renamed, field deleted),
tell the user the sync didn't go through and continue with the local
markdown update regardless — the files are the source of truth, the board is
a convenience layer on top.
