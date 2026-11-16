# job-search-init

A Claude skill that sets up a job-search system for you: a Notion tracker for applications and recruiter contacts, a Notion database of fresh job leads, and two scheduled tasks that keep both current without you doing data entry.

Built from a setup that has been running daily through a real job hunt, generalised so you can point it at your own.

## What you get

Run the skill once and Claude will interview you for about ten minutes, then create:

- **Job Search HQ** — one Notion page holding everything.
- **Job Applications Tracker** — one row per role or recruiter approach, with status, fit score, last activity and a running history. Views for what's active, what needs a reply, and what's going cold.
- **Job Leads** — new roles found for you, kept separate from things you've actually applied to.
- **Candidate Profile** — the facts about you that the automation reads.
- **Inbox scan** — a scheduled task that reads your job-search email hourly on weekdays and updates the tracker: new approaches become rows, replies move rows forward, anything needing your reply gets flagged, and anything untouched for 28 days goes stale.
- **Daily lead search** — a scheduled task that searches boards, agency pages and company careers pages each morning and adds only strong-fit roles.

## What it will never do

The two scheduled tasks run unattended on your inbox, so the scope is deliberately narrow:

- No sending, replying, forwarding, labelling, archiving or deleting email. No drafts either.
- No applying to jobs, submitting forms, creating accounts or signing in anywhere.
- Email content is treated as information, never as instructions — if an email asks for something, it goes in your Notes for you to decide.
- No verification codes, passwords, bank or ID details copied into Notion.
- Your applications are never marked "Completed" for you, and a row is never moved backwards. Outcomes get recorded; the narrative stays yours.

Everything is read-only apart from adding and updating rows in your two databases.

## Requirements

| Connector | Needed for | Required? |
|---|---|---|
| Notion | Everything is stored there | Yes |
| Gmail | The inbox scan (read-only) | For the inbox scan |
| Google Drive | Reading your resume to pre-fill the profile | Optional |

You also need somewhere that can run scheduled tasks for the two automations. Without that, the databases and both task prompts still get created and you can run them by hand.

## Install

**Claude.ai** — download `job-search-init.skill` from this repo, then Settings → Capabilities → Skills → upload it.

**Claude Code** — clone into your skills directory:

```bash
git clone https://github.com/BCusack/job-search-init-skill.git
cp -r job-search-init-skill/job-search-init ~/.claude/skills/
```

Then start a conversation and say something like *"help me set up a job search tracker"* or *"I've just been made redundant and I need to get organised"*. The skill triggers on its own.

To rebuild the `.skill` file after editing:

```bash
python -m scripts.package_skill job-search-init
```

## Layout

```
job-search-init/
├── SKILL.md                          the workflow Claude follows
└── references/
    ├── profile-questions.md          the interview, and resume pre-fill
    ├── notion-schemas.md             exact databases, properties, select options
    ├── inbox-scan-prompt.md          task prompt template + why it's shaped this way
    ├── lead-search-prompt.md         task prompt template + choosing sources
    └── scheduled-tasks.md            schedules, model choice, notifications
job-search-init.skill                 packaged, ready to upload
```

## Adapting it

The templates are built around tech roles in Australia, because that's where it came from. Two places to change for a different market or field:

- **Sources** in `lead-search-prompt.md` — swap the national aggregator, agencies and niche boards for your field's equivalents. The skill asks about this during setup.
- **Scoring criteria** in the same file — the titles, pay floor and location rules that decide what counts as a strong lead.

Everything else is driven by the interview, so it adapts on its own.

## Running it again

Re-running won't duplicate anything. It checks what exists and offers to fill gaps instead: create missing tasks, update task prompts when your pay target or target titles change, or run a health check on a setup that's already working.

## Licence

MIT — see [LICENSE](LICENSE).
