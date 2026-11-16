# Notion structure

Create these in order: the HQ page, then the tracker inside it, then the Candidate Profile page. Record the page URL and data source ID as you create the tracker — the scheduled task prompt needs them, and they are tedious to find afterwards.

## Job Search HQ (page)

A plain page that holds everything else, so the person has one bookmark rather than three. If they already have an old job-hunt page, offer to reuse it instead of adding a second one.

Body: a short contents list linking to the tracker and the profile, and one line saying the inbox scan is running and when. That line is the thing people look for in three weeks when they have forgotten what is automated.

## Job Applications Tracker (database)

One row per role or recruiter approach. This is the system of record: if it is not in here, it is not happening.

| Property | Type | Options / notes |
|---|---|---|
| Role/Company | Title | Written as `Role title @ Company` so the row is readable in a narrow view |
| Company | Text | For an agency, the end client if named, otherwise `(end client not yet known)` |
| Recruiter/Contact | Text | Name, and a work email only if the person wants it stored |
| Email Link | URL | The Gmail thread URL, so a row is one click from its conversation |
| Date Applied | Date | Empty for inbound approaches they have not acted on |
| Last Activity | Date | Driven by the inbox scan; the stale check reads this |
| Source | Select | `Seek`, `LinkedIn`, `Direct`, `Other` — adjust to the boards they actually use |
| Status | Select | `Not started`, `In progress`, `Engaged`, `Interviewing`, `Completed`, `Stale` |
| Fit Score | Select | `Strong`, `Possible`, `Poor` |
| Notes | Text | A running history, newest sentence appended |

### What the Status values mean

The automation can only be trusted if these mean one thing. Worth stating in the database description:

- **Not started** — an inbound approach the person has not answered.
- **In progress** — they applied and have only had automated acknowledgements.
- **Engaged** — real two-way contact with a human: a recruiter replying to something they wrote, or an email referring to a phone call.
- **Interviewing** — an interview with the hiring company is booked or has happened.
- **Completed** — the process ended (offer, rejection, withdrawal). **Only the person sets this.** The automation records the outcome in Notes prefixed `OUTCOME:` and leaves the status alone, because an agent declaring someone's application dead on their behalf is both presumptuous and sometimes wrong.
- **Stale** — no activity for 28 days. Set automatically; cleared automatically when something arrives.

Two conventions that make the tracker much more usable, and which the task prompt relies on:

- `REPLY NEEDED.` at the start of Notes means the person owes someone a reply. A filtered view on this is the most useful view in the database.
- `PARKED` at the start of Notes means hands off: no status changes, no stale marking. For roles they have consciously put aside but do not want deleted.

### Views worth creating

- **Active** — everything except `Completed` and `Stale`, sorted by Last Activity descending. The daily working view.
- **Needs reply** — Notes contains `REPLY NEEDED`.
- **Going cold** — `Not started` or `In progress`, Last Activity more than 14 days ago. Catches things before the stale check does.
- **By status** — a board grouped by Status, for the weekly review.

## Candidate Profile (page)

The prose profile from `profile-questions.md`. Lives here so the person can edit it, and so you can read it next time to refresh the scheduled task when something changes.

## If they already have a tracker

Do not replace it. Read its schema, map these concepts onto the columns it has, and adapt the task prompt to those column names. Missing a Fit Score column is not worth a migration; the task can skip that field. A tracker someone already trusts and uses is worth more than a tidier one they abandon.
