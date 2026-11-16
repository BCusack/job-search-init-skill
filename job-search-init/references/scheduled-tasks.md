# Creating the scheduled tasks

Two tasks, created with whatever scheduling tool the session has. Check what is available before promising anything — if there is no scheduling tool, the databases and prompts are still worth creating, and the person can run the prompts by hand or set the tasks up from a surface that supports them.

## Inbox scan

- **Schedule:** weekdays, hourly, within waking hours. `0 7-18 * * 1-5` in their time zone covers 7am–6pm.
- **Why not overnight or weekends:** recruitment email does not arrive at 3am, and an hourly task that runs 24/7 costs four times as much for nothing. The Monday 3-day window in the prompt is what covers the weekend gap.
- **Model:** a cheap, fast model is right here. The work is reading email and updating table cells against clear rules — not reasoning. This task runs around 55 times a week, so the model choice is the main cost lever in the whole system.
- **Time zone:** always set it explicitly in the cron expression. A task that silently runs on UTC will scan at 6pm their time and report "no new email" every evening.

## Daily lead search

- **Schedule:** once each weekday morning, before they start. Something like `41 6 * * 1-5`.
- **Avoid round numbers.** A task set for exactly 7:00 competes with every other task on the hour. A few minutes either side gets it run on time.
- **Model:** a stronger model earns its keep here — it is reading unstructured listings, judging fit, and deciding what not to add. A cheap model on this task produces either noise or nothing.
- **Weekdays only.** Few roles are posted on weekends, and a Saturday run mostly re-reads Friday's.

## Notifications

Both tasks can notify when a run finishes with something to report:

- **Push** to their phone — sensible on both. The lead search in particular is worth a morning push.
- **Email** — only if the person asks for it. Do not turn it on by choice: the whole point of this system is to make their inbox quieter.

Set notifications when creating the task. Some surfaces cannot change the notification setting on an existing task afterwards without recreating it, which resets its run history — so ask at creation time rather than assuming it can be fixed later.

## Approvals

These tasks run unattended, so a run that stops to ask a question achieves nothing. Both prompts say "nobody is watching this run, so do not ask questions" for that reason.

Where the scheduling tool exposes an approval mode, the tasks need to be able to write to Notion without a prompt. Tell the person which mode each task got, and that they can change it in the task's own settings. Do not describe a task as fully automatic unless you have confirmed it is.

What makes this safe to run unattended is not the approval setting — it is the scope. Both tasks are read-only everywhere except adding or updating rows in two databases. Nothing is sent, nothing is deleted, nothing leaves their account.

## After creating them

Fire the inbox scan once by hand if the tool allows it, and read what it reports. A first run catches the two things that otherwise go unnoticed for a day: a wrong data source ID, and a Status or Source select option whose name does not match what the prompt expects.

Then tell the person:

- Both task names and when each runs.
- That they can pause, edit or delete either one themselves.
- That editing a task's prompt keeps its history, so updating the pay target or target titles later is cheap.

## Keeping the tasks in step with the profile

Job hunts change. Six weeks in, the pay target has moved, two agencies have been added, and the target titles have narrowed. The tasks do not notice.

Suggest a standing habit: when something in the Candidate Profile changes, update both task prompts. It takes a minute and it is the difference between a lead search that still works in month two and one that quietly stopped being relevant.
