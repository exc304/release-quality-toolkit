# Feature Flag Inventory Template

Use this template to track feature flag status during planning, release candidate testing, launch, and rollback readiness.

Feature flags reduce release risk only when they are visible, owned, and tested. Hidden flags create hidden scope.

## Flag Summary

| Flag Name | Default | Current State | In Scope? | Owner | Test Coverage | Notes |
|---|---|---|---|---|---|---|
| `example-new-workflow` | Off | Off | Yes | Product | Workflow smoke + regression | Enable after approval |
| `example-beta-ui` | Off | On in staging | No | Engineering | Visual regression only | Not production-ready |
| `example-risky-integration` | Off | Unknown | TBD | TBD | None | Must resolve before release gate |

## Per-Environment Status

| Environment | Flag Name | State | Verified By | Verification Date | Notes |
|---|---|---|---|---|---|
| Development | `example-new-workflow` | On | | | |
| Staging | `example-new-workflow` | On | | | |
| Release Candidate | `example-new-workflow` | Off | | | |
| Production | `example-new-workflow` | Off | | | |

## Scope Checklist

- [ ] Every in-scope flag has an owner.
- [ ] Every in-scope flag has a default state.
- [ ] Unknown flag states are resolved before release.
- [ ] Test coverage is mapped to each enabled flag.
- [ ] Dependencies between flags are documented.
- [ ] Customer-specific or environment-specific behavior is explicit.
- [ ] Release notes include user-facing flag impacts.
- [ ] Support teams know which features are enabled or disabled.

## Disablement Plan

For each production-facing flag, document:

- What tool or configuration controls the flag?
- Who has permission to disable it?
- How quickly does the change take effect?
- Does the app require restart, redeploy, cache clear, or session refresh?
- How will the team verify the feature is disabled?
- Who needs to be notified?

## Rollback Notes

```text
Flag:
Owner:
Disable procedure:
Expected user impact:
Verification steps:
Monitoring links:
Comms channel:
Post-disable follow-up:
```

## Why This Matters

Feature flags help teams:

- Ship incomplete or risky work in a disabled state.
- Reduce pressure to hold a whole release for one feature.
- Enable functionality gradually.
- Disable problem behavior without an emergency code rollback.

But flags also create risk when nobody knows what is on, what is off, or what "off" actually means. Treat flag inventory as part of release readiness.

