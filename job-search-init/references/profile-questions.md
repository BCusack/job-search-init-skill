# Building the candidate profile

The profile is what the inbox scan reads to score a role as a strong, possible or poor fit. Ten minutes spent here saves a tracker full of mis-scored rows.

## Try the resume first

Before asking anything, offer to read their resume from Google Drive:

> "Do you have a resume in Drive? If so I'll read it and fill in most of this myself, then you just correct me."

Search Drive for `resume`, `CV`, or their name, read the most recent-looking file, and draft the profile from it. Then present it for correction. People find it much easier to say "no, I want lead roles not architect roles" than to answer an open question about their target titles.

What the resume gives you reliably: years of experience, recent titles, employers, skills, location. What it will *not* give you: pay target, work rights, remote preference, or what they actually want next — which is often different from what they did last. Always ask those four.

## The questions

Ask these in three batches and let them answer in prose. Do not walk through them one at a time; it reads like an intake form and people disengage.

### Batch 1 — Who they are and what they can accept

- Name, as they want it to appear.
- City and country, and their time zone.
- Work rights: can they work in that country without sponsorship? Do they need a visa anywhere they are targeting?
- Remote preference: fully remote, mostly remote, hybrid (how many days, which city), or onsite.

### Batch 2 — What they want next

- Target titles — the actual words they want in the job ad. Push for specifics. "Something senior in AI" scores badly; "lead, principal or staff AI engineer, or AI engineering lead" scores well.
- Field or domain, if it matters to them.
- Pay target: the number they want, and the number they would accept for a role they liked. Both matter — a single figure makes the scoring brittle. If they contract, get a day rate too.
- Permanent, contract, or either.
- Anything that is a hard no: relocation, on-call, specific industries.

If they are reluctant on pay — common, and fair — explain why it is being asked: without it the scan cannot tell a strong approach from a time-waster, and they will end up re-reading every row by hand. A range is enough.

### Batch 3 — What their email looks like

This batch exists to tune the scan, so keep it brief:

- Which job boards they applied through. This sets the `Source` select options, and it tells the scan which job alert digests to ignore — the digests are the main source of noise in a job-hunting inbox.
- Roles they have already applied to, and any live recruiter conversations. These become the first rows in the tracker, and the stale check needs them to be useful.
- Their LinkedIn and any profile hirers can find them through, so profile-view notifications get recognised rather than ignored.

## What to do with reluctance or vagueness

Some of this is uncomfortable to answer, particularly straight after a redundancy. Two things help:

- **Let them skip and come back.** Build with what you have, note the gap, and say which part will be weaker until they fill it. A working tracker with a vague pay target beats an interrogation.
- **Offer a default they can react to.** "I'll treat lead and principal AI engineering roles at or above $X as strong fits — adjust that and I'll use whatever you say." Reacting is easier than specifying.

## Write the profile to Notion

Save the result as the **Candidate Profile** page inside Job Search HQ, in plain prose under short headings. The scheduled task embeds its own copy of the relevant facts, so this page is primarily for the person — but it is also what you read next time to update the task when something changes, so keep it current rather than decorative.

Structure it as:

```
## Basics
Name, location, time zone, work rights.

## What I'm looking for
Target titles, permanent or contract, pay target and acceptable floor,
remote preference, hard nos.

## Background in one paragraph
What they did most recently and what they are known for — written so it
could be pasted into a recruiter reply.

## Skills
A plain list.

## Where I'm applying
The boards they use, and profile links.

## Live as of <date>
Applications in flight and recruiter conversations, so the tracker's
first rows match reality.
```
