# Post-Release Review Template

Run this review one to two weeks after a release reaches production, after the first wave of stabilization and support feedback.

The goal is to capture what the release taught the team while the details are still fresh.

## Release Overview

| Field | Notes |
|---|---|
| Release version | |
| Release date | |
| Planned scope | |
| Actual scope shipped | |
| Candidate testing duration | |
| Critical issues after launch | |
| Hotfixes required | |

## What Went Well

### Signal Quality and Testing

- Which tests caught real issues?
- Which workflows were most stable?
- Which test data or assertions gave the team useful confidence?
- Were there moments when a test signal made the release decision easier?

### Process and Tools

- Which checklists or templates helped?
- Which automation saved time or reduced risk?
- Which communication pattern reduced confusion?
- What should the team repeat next time?

### Collaboration and Communication

- Were stakeholders informed at the right time?
- Did support teams have what they needed?
- Were ownership boundaries clear?
- Did the team make good decisions with incomplete information?

## What Needs Improvement

### Signal Quality Gaps

- Were any tests marked passing without proving meaningful behavior?
- Did a workflow feel under-tested despite passing status?
- Did any production issue escape candidate testing?
- Which signals were noisy, misleading, or missing?

### Data and Environment Gaps

- Was test data current and realistic?
- Did environment differences create surprises?
- Were configuration values documented?
- Did any test fail because setup knowledge lived only in someone's head?

### Scope and Feature Flag Gaps

- Did unscoped work enter the release?
- Were feature flags documented before launch?
- Did any flag state cause confusion during support or troubleshooting?
- Did anything ship enabled or disabled unexpectedly?

### Documentation and Support Gaps

- Were release notes accurate?
- Were user-facing docs ready?
- Did support teams receive clear workflow changes?
- Did customers report confusion that documentation could have prevented?

## Specific Issues and Root Causes

| Issue | Root Cause | Impact | Owner | Fix for Next Release |
|---|---|---|---|---|
| | | | | |
| | | | | |
| | | | | |

## Release Quality Scorecard

| Metric | Target | Actual | Status |
|---|---|---|---|
| Critical production bugs | 0 | | |
| In-scope workflows tested | 100% | | |
| Feature flags documented | 100% | | |
| Support briefing complete | Yes | | |
| Candidate-to-launch duration | | | |
| Hotfix required | No | | |

## Coverage by Workflow

| Workflow | Scenario Count | Pass Rate | Confidence | Notes |
|---|---:|---:|---|---|
| Core workflow | | | | |
| Secondary workflow | | | | |
| Admin workflow | | | | |
| Integration workflow | | | | |

## Learnings for Next Release

### Process Improvements

1. 
2. 
3. 

### Test Automation Improvements

1. 
2. 
3. 

### Documentation Improvements

1. 
2. 
3. 

## Action Items

| Action | Owner | Due Before Next Gate |
|---|---|---|
| | | |
| | | |
| | | |

## Final Notes

### Keep Doing

- 

### Change

- 

### Open Questions

- 

