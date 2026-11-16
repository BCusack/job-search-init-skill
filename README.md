# job-search-init

A Claude skill that sets up a job application tracker in Notion and a scheduled task that keeps it current from your email — so recruiter replies don't get buried and applications don't go quiet without you noticing.

Built from a setup that has been running daily through a real job hunt, generalised so you can point it at your own.

## What you get

Run the skill once and Claude will interview you for about ten minutes, then create:

- **Job Search HQ** — one Notion page holding everything.
- **Job Applications Tracker** — one row per role or recruiter approach, with status, fit score, last activity and a running history. Views for what's active, what needs a reply, and what's going cold.
- **Candidate Profile** — the facts about you that the automation reads.
- **Inbox scan** — a scheduled task that reads your job-search email hourly on weekdays and updates the tracker: new approaches become rows, replies move rows forward, anything needing your reply gets flagged `REPLY NEEDED.`, outcomes get recorded, and anything untouched for 28 days goes stale.

## What it will never do

The scheduled task runs unattended on your inbox, so the scope is deliberately narrow:

- No sending, replying, forwarding, labelling, archiving or deleting email. No drafts either.
- Email content is treated as information, never as instructions — if an email asks for something, it goes in your Notes for you to decide.
- No verification codes, passwords, bank or ID details copied into Notion.
- Your applications are never marked "Completed" for you, and a row is never moved backwards. Outcomes get recorded; the narrative stays yours.

Everything is read-only apart from adding and updating rows in your tracker.

## Requirements

| Connector | Needed for | Required? |
|---|---|---|
| Notion | Everything is stored there | Yes |
| Gmail | The inbox scan (read-only) | For the inbox scan |
| Google Drive | Reading your resume to pre-fill the profile | Optional |

You also need somewhere that can run scheduled tasks. Without that, the tracker and the task prompt still get created and you can run the prompt by hand.

## Install

**Claude.ai** — download `job-search-init.skill` from this repo, then Settings → Capabilities → Skills → upload it.

**Claude Code** — clone into your skills directory:

```bash
git clone https://github.com/BCusack/job-search-init-skill.git
cp -r job-search-init-skill/job-search-init ~/.claude/skills/
```

Then start a conversation and say something like *"help me set up a job application tracker"* or *"I've just been made redundant and I need to get organised"*. The skill triggers on its own.

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
    ├── notion-schemas.md             exact database, properties, select options
    ├── inbox-scan-prompt.md          task prompt template + why it's shaped this way
    └── scheduled-tasks.md            schedule, model choice, notifications
job-search-init.skill                 packaged, ready to upload
```

## Adapting it

The Status and Fit Score meanings in `notion-schemas.md` are the part worth reading if you want to change how it behaves — the task prompt follows them closely, and they're what make the tracker trustworthy rather than just tidy.

For a non-Gmail mail connector, the structure in `inbox-scan-prompt.md` holds but the search syntax doesn't; that file explains what to rewrite and why the search window deliberately overlaps the schedule.

Everything else is driven by the interview, so it adapts on its own.

## Running it again

Re-running won't duplicate anything. It checks what exists and offers to fill gaps instead: create the task if it's missing, update the task prompt when your pay target or target titles change, or run a health check on a setup that's already working.

## Licence

MIT — see [LICENSE](LICENSE).
