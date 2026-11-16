# Deriving the profile

Do not interview the person. Almost everything the inbox scan needs is in their resume or already in their inbox. Read both, show what you worked out, and ask one question.

## Step A — Read the resume

Search Google Drive for `resume`, `CV`, or their name, and read the most recent-looking file. Extract:

| What | Used for |
|---|---|
| Full name and any variants | Recognising mail addressed to them |
| Email addresses and phone | Telling mail *to them* from mail *about* them |
| LinkedIn, GitHub, portfolio URLs | Recognising profile-view notifications instead of discarding them as noise |
| City and country | Scoring location fit; also gives the time zone for the task schedule |
| Employers and job titles | The difference between "a recruiter mentions where I used to work" and "this is a new role" — without it the scan misreads history as opportunity |
| Years of experience and seniority | Scoring Fit Score. A graduate role scores `Poor` on its own once you know this |
| Skills and keywords | Sharpening Fit Score beyond a bare list of target titles |

If no resume turns up, ask for one or ask them to paste it. If they have neither, fall back to the short question list at the end.

## Step B — Read the inbox once

Which job boards they use and what they have already applied to are both sitting in their email. Searching is better than asking: people forget half of it, and the inbox is current.

Search Gmail across about 30 days for application receipts, recruiter mail, and job alert digests. From that, work out:

- **The `Source` options** — the boards actually sending them mail.
- **The alert senders to ignore** — the digests that will otherwise flood every run. This is the single biggest source of noise in a job-hunting inbox.
- **Roles already in flight** — candidate first rows for the tracker, which the stale check needs in order to be useful from day one.

This is the one point in setup that touches a lot of email at once. It is read-only, but show the list and get a yes before creating rows. Importing a month of someone's history silently is not a good first impression, and they may want half of it left out.

## Step C — Confirm, and ask about pay

Show one short screen of what you worked out: name and addresses, location and time zone, current seniority and domain, the boards found, and how many in-flight applications you can seed. Ask them to correct anything wrong — correcting a list is far quicker than answering questions.

Then ask the one thing neither the resume nor the inbox can tell you:

> "What pay are you looking for? Give me the number you want and the number you'd accept for a role you liked — a range is fine."

Ask it directly and wait for an answer. It is worth the one question because Fit Score drives the Board filter: the board hides `Poor` rows, so a vague Fit Score means the board hides the wrong things and stops being trustworthy. The resume tells you they are senior; it cannot tell you whether $180k is insulting or acceptable, and most inbound recruiter mail sits near that line.

If they decline, say the board will be blunter than it could be, score on seniority alone, and move on. Do not ask twice.

While you are there, two things worth a single line each if the resume left them unclear:

- **Which email addresses are theirs.** The resume often lists a personal address that differs from the Gmail account being scanned.
- **Remote, hybrid or onsite**, and which city — the resume rarely says, and it affects scoring.

## If there is no resume at all

Ask only this, in one message:

- Name, city and country.
- Current or most recent title, and roughly how many years.
- The titles they want next, in the words they would expect in a job ad.
- Pay: target and the figure they would accept.
- Remote, hybrid or onsite.

Nothing else. Everything further can be inferred or corrected later.

## Write the profile to Notion

Save the result as the **Candidate Profile** page inside Job Search HQ, in plain prose under short headings. The scheduled task embeds its own copy of the relevant facts, so this page is mainly for the person — but it is also what you read next time to refresh the task when something changes.

```
## Basics
Name, email addresses, location, time zone.

## What I'm looking for
Target titles, pay target and acceptable floor, remote preference.

## Background in one paragraph
Most recent role and what they are known for — written so it could be
pasted into a recruiter reply.

## Skills
A plain list.

## Profiles
LinkedIn and anything else hirers find them through.

## Where I'm applying
The boards found in the inbox pass.

## Live as of <date>
Applications seeded from the inbox pass.
```
