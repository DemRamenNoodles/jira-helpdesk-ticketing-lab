# Jira Helpdesk: Account Lockout After Password Expiration

| | |
|---|---|
| **Incident** | User unable to log in after password expiration (KAN-4) |
| **Severity** | High. Blocked from critical work |
| **Root Cause** | Password expired + AD account locked after failed attempts |
| **Status** | Resolved. Same-day fix |
| **Environment** | Corporate IT environment, March 2026 |

---

## Overview

Marcus couldn't log in to his workstation Monday morning. The system locked him out after the weekend, and he had critical work waiting. The fix itself was simple: reset the password, unlock the account. But the process around that fix is what this case study is about. Scope check, root cause, verification, and a prevention note so it doesn't happen again.

---

## The Incident

Monday morning, Marcus reported he couldn't log in to his workstation. The system locked him out, and he had immediate work to do. I opened the ticket in Jira, classified it as an Incident, set it High priority, and got to work.

**Supporting screenshots:**

![Jira ticket opened: KAN-4 logged as Incident, High priority](screenshots/Step01A.png)

![Full ticket details: summary, description, and priority confirmed](screenshots/Step01B.png)

---

## Diagnosis Process

First thing I needed to rule out: was this just Marcus, or was the whole domain having problems?

**Scope Check**

I verified that other users could log in fine and that Marcus's workstation was on the network with an active account. That ruled out a system outage or a general network problem. The issue was specific to Marcus.

![Scope check confirmed: other domain users authenticating successfully (9:04 AM)](screenshots/Step02A.png)

**Root Cause**

I pulled up Active Directory and checked the password policy. The answer was clear: Marcus's password had expired Friday, and the account locked after too many failed login attempts Monday morning. Standard AD behavior, nothing malicious.

![Active Directory account view: password expired + account locked (9:11 AM)](screenshots/Step03A.png)

---

## Resolution & Closure

With the root cause confirmed, the fix was straightforward. I reset the password in Active Directory and unlocked the account. Then I had Marcus test the login immediately.

Marcus confirmed he was back in a few minutes later:

> "Hey, that worked! I'm back in and got through the password reset fine. Thanks for the help, I can actually get started on my morning now."

**What made this close smoothly:** verification. I didn't just fix it and move on. I waited for Marcus to confirm access was restored before closing the ticket. That extra step is the difference between resolved and reopened.

**Prevention:** I documented a recommendation to enable password expiry notification emails so users get warned before the deadline, not locked out after. Without that note, this same call comes back in three months. That's the difference between closing a ticket and actually solving the problem.

**Resolution screenshots (9:18 AM to 9:26 AM):**

![Password reset confirmed in Active Directory](screenshots/Step04A.png)

![Ticket closure confirmed with resolution notes](screenshots/Step05A.png)

![KAN-4 marked Resolved on the Kanban board](screenshots/Step05B.png)

---

## What This Taught Me

Ten minutes of actual work. Password reset, account unlock, done. But the way I got there is the whole point.

**Documentation is the job.** Scope check, root cause, fix, verification. Every step logged as it happened. If someone else had to pick this up mid-way through, or if it came back in a review six months later, the activity log tells the whole story.

**Don't just close it, solve it.** The ticket is done when the user is back online. The job is done when you've documented why it happened and what stops it from happening again.

---

## Lab Context: The Jira Board Setup

I built this case study inside a broader IT Helpdesk lab. The foundation is a Kanban board I set up with four columns (To Do, In Progress, Waiting for Customer, Resolved) and three ticket types:

- **Incidents**: Break-fix issues that need to move now
- **Service Requests**: Planned work like installs, new setups, or access requests
- **Tasks**: Internal IT items like audits or documentation

KAN-4 (the ticket walked through above) is one of the Incidents that ran through this board.

---

## Tools & Technologies Used

| Tool | Purpose |
|---|---|
| **Jira** | Organizing and tracking incidents from report to resolution |
| **Active Directory** | Managing user accounts, security groups, and password policies |
| **Kanban board** | Visualizing ticket lifecycle and queue prioritization |
| **ITSM methodology** | Structuring incident response (Intake → Scope → Root Cause → Resolution → Closure) |

---

*Case Study, Lab Simulation, March 2026*
