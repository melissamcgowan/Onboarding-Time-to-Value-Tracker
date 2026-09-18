# Onboarding Time-to-Value Tracker

An interactive dashboard that tracks new customers through onboarding milestones and flags accounts falling behind benchmark pace, before a slow start becomes a renewal risk.

**[View the live demo](#)** *(replace with your GitHub Pages link once published)*

## The problem

Onboarding is where churn risk gets seeded, often months before a renewal conversation happens. A CSM juggling 30+ new accounts can't manually track where every one of them sits against expected pace, and by the time a stalled onboarding shows up in a QBR, the damage is already done. This tool gives CS leadership a single view of every active onboarding, sorted by risk, with enough detail to know exactly where and why an account is falling behind.

## Approach

**Segment-aware milestones.** Enterprise and SMB onboardings don't follow the same path; Enterprise moves through a longer sequence (technical integration, admin training, data migration, end-user training) with milestones benchmarked in weeks, while SMB is a fast, five-step path benchmarked in days. Each tier has its own expected-day benchmarks per milestone.

**A weighted health score, not just a days-late count.** Days-late alone misses accounts that are hitting milestones on schedule but quietly disengaging. The score blends two signals:
- **Pace (60%)** — how many days overdue the account is on its current milestone
- **Engagement (40%)** — login frequency against a tier-specific target, blended with feature adoption percentage

An account can be on pace but still show yellow if logins have gone quiet, which is often the earlier warning sign.

**Portfolio view with drill-down.** The main view is a sorted list of every active onboarding, worst pace first, rendered as a milestone "track" so you can see at a glance how far along each account is and where its marker sits relative to risk. Clicking an account expands a full milestone timeline (on-time vs. late, in days) and the score breakdown behind the number.

## Tech

Single-file HTML/CSS/JS, no build step or dependencies. Synthetic data for 16 accounts across both tiers, covering a realistic spread from graduated accounts to stalled, at-risk ones.

## Notes on the scoring model

The pace and engagement weights (60/40) and the login-frequency targets (3/week Enterprise, 5/week SMB) are illustrative assumptions, documented here rather than buried in code, so they can be swapped for a real team's actual benchmarks. In a production version, the milestone completions and login/adoption data would come from a CSP (Gainsight, Totango) or product analytics feed in place of the synthetic dataset — the scoring logic itself wouldn't need to change.
