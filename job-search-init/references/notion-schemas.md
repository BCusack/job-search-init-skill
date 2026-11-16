# Notion structure

Create these in order: the HQ page, then the tracker inside it, then the tracker's two views, then the Candidate Profile page. Record the page URL and data source ID as you create the tracker — the scheduled task prompt needs them, and they are tedious to find afterwards.

## Job Search HQ (page)

A plain page that holds everything else, so the person has one bookmark rather than three. If they already have an old job-hunt page, offer to reuse it instead of adding a second one.

Body: a short contents list linking to the tracker and the profile, and one line saying the inbox scan is running and when. That line is the thing people look for in three weeks when they have forgotten what is automated.

## Job Applications Tracker (database)

One row per role or recruiter approach. This is the system of record: if it is not in here, it is not happening.

Give the data source a description naming what it tracks and where the roles come from, e.g. *"Tracking job applications, recruiter activity and interview progress for <name>'s job search (<the boards they use>)."* It is the fastest way for them to remember what the table is for.

| Property | Type | Options / notes |
|---|---|---|
| Role/Company | Title | Written as `Role title @ Company` so the row is readable in a narrow view |
| Company | Text | For an agency, the end client if named, otherwise `(end client not yet known)` |
| Recruiter/Contact | Text | Name, and a work email only if the person wants it stored |
| Email Link | URL | The Gmail thread URL, so a row is one click from its conversation |
| Date Applied | Date | Empty for inbound approaches they have not acted on |
| Last Activity | Date | Driven by the inbox scan; the stale check reads this |
| Source | Select | `Seek` (blue), `LinkedIn` (purple), `Direct` (grey), `Other` (default) — adjust to the boards they actually use |
| Status | **Status** | Grouped, see below. Default option `Not started` |
| Fit Score | Select | `Strong` (green), `Possible` (yellow), `Poor` (red) |
| Notes | Text | A running history, newest sentence appended |

**Status must be a Status property, not a Select.** The board view groups by its built-in groups, and a Select cannot do that. Set the groups up like this:

| Group | Options |
|---|---|
| To-do | `Not started` |
| In progress | `In progress`, `Engaged`, `Interviewing` |
| Complete | `Completed`, `Stale` |

Put a description on **Fit Score** saying what it is and who owns it — something like *"Quick automated estimate of how well the role matches what I'm looking for. Not reviewed unless I change it."* This matters more than it looks: the column is machine-written, and a person glancing at a red `Poor` three weeks later should know it was a guess they are free to overrule.

### What the Status values mean

The automation can only be trusted if these mean one thing. Worth stating in the database description:

- **Not started** — an inbound approach the person has not answered.
- **In progress** — they applied and have only had automated acknowledgements.
- **Engaged** — real two-way contact with a human: a recruiter replying to something they wrote, or an email referring to a phone call.
- **Interviewing** — an interview with the hiring company is booked or has happened.
- **Completed** — the process ended (offer, rejection, withdrawal). **Only the person sets this.** The automation records the outcome in Notes prefixed `OUTCOME:` and leaves the status alone, because an agent declaring someone's application dead on their behalf is both presumptuous and sometimes wrong.
- **Stale** — no activity for 28 days. Set automatically; cleared automatically when something arrives.

Two conventions that make the tracker much more usable, and which the task prompt relies on:

- `REPLY NEEDED.` at the start of Notes means the person owes someone a reply.
- `PARKED` at the start of Notes means hands off: no status changes, no stale marking. For roles they have consciously put aside but do not want deleted.

## Views

Two views, and the second is the one they will actually live in.

### Default view (table)

Every property, no filter, no sort. This is the full record — useful when something looks wrong and they need to see everything, and it is where rows that the board filters out are still visible.

### Board

A kanban board grouped by Status, so an application is dragged from column to column as it moves. Configure it exactly like this:

- **Type:** board, grouped by **Status**, grouping by option, sorted ascending, empty groups shown.
- **Filter:** Status is not `Stale`, **and** Fit Score is `Strong` or `Possible`.
- **Sort:** Last Activity, descending.
- **Card properties:** Role/Company, Fit Score, Company, Recruiter/Contact, Last Activity, Source.

The filter is the whole point, so it is worth understanding before changing it. A job hunt accumulates dead weight fast — roles that were never a fit, applications that went nowhere a month ago. Hiding `Poor` fits and `Stale` rows leaves a board showing only live, plausible opportunities, which is what makes it usable as a daily view rather than an archive. Nothing is deleted; it is all still in the table view.

Showing empty groups matters too, in a small way: an empty `Interviewing` column is informative. A column that vanishes when it empties hides the thing the person most wants to see fill up.

Sorting by Last Activity descending puts whatever moved most recently at the top of each column, which is nearly always what they want to act on.

### Optional extras

Not part of the standard setup, but worth offering if they want them:

- **Needs reply** — a table filtered to Notes containing `REPLY NEEDED`. Useful for anyone who gets a lot of inbound.
- **Going cold** — `Not started` or `In progress` with Last Activity more than 14 days ago. Catches things before the stale check does.

## Candidate Profile (page)

The prose profile from `profile-from-resume.md`. Lives here so the person can edit it, and so you can read it next time to refresh the scheduled task when something changes.

## If they already have a tracker

Do not replace it. Read its schema, map these concepts onto the columns it has, and adapt the task prompt to those column names. Missing a Fit Score column is not worth a migration; the task can skip that field. A tracker someone already trusts and uses is worth more than a tidier one they abandon.

If theirs has a Select called Status rather than a Status property, the board cannot group by it. Say so and offer the conversion, but do not do it unasked — changing a property's type touches every existing row.
