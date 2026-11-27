# n8n Automation Projects

Documentation of two workflows I designed in [n8n](https://n8n.io). Both follow a **human-in-the-loop** approach: automation prepares and checks the work, and a person stays in control of anything that is sent or published.

These are personal projects, not client work. The repository describes the design; it does not include credentials, account identifiers or workflow exports.

## Project 1: Outreach queue and weekly report

**Daily queue** (weekdays, 09:30, Asia/Dhaka)

1. Read up to 10 prospects marked `to_connect`, oldest first
2. Build the first-message text for each
3. Mark them `queued_today`
4. A person sends the messages, because the platform does not allow automated sending

**Weekly report** (Mondays, 10:00)

1. Count the funnel: to_connect, requested, connected, replied, call_booked, client
2. Count posts published in the last 7 days
3. Save plain-language advice to a report table

## Project 2: Approval-gated post publisher

Runs on weekdays at 10:00 and publishes only rows whose status is `approved` and whose scheduled date is today. It never publishes late and never twice.

1. Get approved posts and previously published posts
2. A code node selects today's post and checks for duplicates and the length limit
3. The row is locked as `publishing` before the API call, so a re-run cannot double-post
4. On success, save the publication ID; on failure, record the error with no automatic retry

**Status:** built and ready, not switched on yet, because the platform connection (OAuth) still needs the account owner's authorisation.

## Skills shown

n8n, schedule triggers, webhooks and REST APIs, JavaScript code nodes, data tables, status-based workflows, human-in-the-loop design.

## More

Diagrams and write-ups: [sites.google.com/view/faridur-rahman-research/automation-projects](https://sites.google.com/view/faridur-rahman-research/automation-projects)
