# Release Decision Flowchart

Use this flowchart to decide whether a work item should **ship**, **defer**, or **ship behind a feature flag**.

## Start Here

```text
Is this work item committed to the current release?

YES -> Continue to Scope Assessment
NO  -> DEFER
```

## Scope Assessment

```text
Is the work complete?

YES -> Continue to Quality Gate
NO  -> Is it likely to be complete before the release gate?
       YES -> Continue, but mark as schedule risk
       NO  -> DEFER
```

Ask:

- What is incomplete?
- Who owns the remaining work?
- What decision date prevents last-minute scope drift?

## Quality Gate

```text
Do test scenarios exist for this work?

YES -> Continue to Test Readiness
NO  -> Is this a critical production fix?
       YES -> FLAG AND SHIP if risk can be isolated
       NO  -> DEFER
```

If work ships without complete tests, document the reason, expected impact, and follow-up coverage.

## Test Readiness

```text
Are relevant tests passing in the release candidate environment?

YES -> Continue to Workflow Scope
NO  -> Is the root cause known and fixable before the gate?
       YES -> Continue, but mark as timeline risk
       NO  -> DEFER or FLAG AND SHIP with explicit limitation
```

Ask:

- Is the failure caused by product behavior, test data, environment configuration, or automation instability?
- Does the failure affect a core workflow?
- Is the risk isolated enough to disable?

## Workflow Scope

```text
Which workflows does this work affect?

One workflow       -> Check that workflow's readiness
Multiple workflows -> Check each workflow independently
Unknown            -> DEFER until scope is clear
```

For each workflow:

- Is the workflow in scope for this release?
- Are tests passing?
- Are known gaps documented?
- Can this workflow ship independently?
- Can incomplete behavior be disabled safely?

## Feature Flag Decision

```text
Is the work high-risk, incomplete, customer-specific, or workflow-specific?

YES -> FLAG AND SHIP if the disabled path is safe
NO  -> SHIP if all gates pass
```

Feature flag review should answer:

- What flag controls this behavior?
- What is the default state?
- Who owns enabling or disabling it?
- How is the flag verified?
- What happens when the flag is off?
- How quickly can the team disable it in production?

## Final Decision

```text
All required workflows ready and quality gates pass
-> SHIP

Some workflows ready and incomplete behavior can be isolated
-> FLAG AND SHIP

Critical workflows blocked or scope unclear
-> DEFER
```

## Decision Matrix

| Scenario | Code Ready? | Tests Pass? | Scope Clear? | Decision |
|---|---:|---:|---:|---|
| Complete work, tests passing, scope clear | Yes | Yes | Yes | SHIP |
| Complete work, one optional workflow blocked | Yes | Partial | Yes | FLAG AND SHIP |
| Work ready but tests failing for unknown reason | Yes | No | Partial | DEFER |
| Critical fix with limited test coverage | Yes | Partial | Yes | FLAG AND SHIP |
| Work nearly done but not stable before gate | Partial | No | Yes | DEFER |
| Work complete but workflow impact unknown | Yes | Unknown | No | DEFER |

## Tips

- Defer unclear scope early.
- Use flags to reduce risk, not to avoid making a decision.
- Document assumptions while they are fresh.
- Treat "unknown" as a release risk, not a neutral status.
- If the team cannot explain what evidence supports shipping, the release decision is not ready.

