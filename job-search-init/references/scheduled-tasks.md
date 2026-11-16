# Creating the scheduled task

One task, created with whatever scheduling tool the session has. Check what is available before promising anything — if there is no scheduling tool, the tracker and the prompt are still worth creating, and the person can run the prompt by hand or set the task up from a surface that supports them.

## Inbox scan

- **Schedule:** weekdays, hourly, within waking hours. `0 7-18 * * 1-5` in their time zone covers 7am–6pm.
- **Why not overnight or weekends:** recruitment email does not arrive at 3am, and an hourly task that runs 24/7 costs four times as much for nothing. The Monday 3-day window in the prompt is what covers the weekend gap.
- **Model:** a cheap, fast model is right here. The work is reading email and updating table cells against clear rules — not reasoning. This task runs around 55 times a week, so the model choice is the main cost lever in the whole system.
- **Time zone:** always set it explicitly in the cron expression. A task that silently runs on UTC will scan at 6pm their time and report "no new email" every evening.

If hourly feels like too much for them, twice a day works and costs a tenth as much — the trade is that a recruiter's email might sit unlogged for a few hours. Either way, widen the search window in the prompt to overlap the gap.

## Notifications

The task can notify when a run finishes with something to report:

- **Push** to their phone — sensible, since the useful runs are the ones that found something needing a reply.
- **Email** — only if the person asks for it. Do not turn it on by choice: the whole point of this system is to make their inbox quieter.

Set notifications when creating the task. Some surfaces cannot change the notification setting on an existing task afterwards without recreating it, which resets its run history — so ask at creation time rather than assuming it can be fixed later.

## Approvals

The task runs unattended, so a run that stops to ask a question achieves nothing. The prompt says "nobody is watching this run, so do not ask questions" for that reason.

Where the scheduling tool exposes an approval mode, the task needs to be able to write to Notion without a prompt. Tell the person which mode it got, and that they can change it in the task's own settings. Do not describe the task as fully automatic unless you have confirmed it is.

What makes this safe to run unattended is not the approval setting — it is the scope. The task is read-only everywhere except adding and updating rows in one database. Nothing is sent, nothing is deleted, nothing leaves their account.

## After creating it

Fire the task once by hand if the tool allows it, and read what it reports. A first run catches the two things that otherwise go unnoticed for a day: a wrong data source ID, and a Status or Source select option whose name does not match what the prompt expects.

Then tell the person:

- The task name and when it runs.
- That they can pause, edit or delete it themselves.
- That editing the prompt keeps its history, so updating the pay target or target titles later is cheap.

## Keeping the task in step with the profile

Job hunts change. Six weeks in, the pay target has moved and the target titles have narrowed. The task does not notice.

Suggest a standing habit: when something in the Candidate Profile changes, update the task prompt. It takes a minute, and it is the difference between Fit Scores that still mean something in month two and a column nobody trusts.
