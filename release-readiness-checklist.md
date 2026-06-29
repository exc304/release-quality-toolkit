# Release Readiness Checklist

Use this checklist at two gates:

- **Pre-candidate gate:** before the release candidate is created
- **Release gate:** before the candidate moves to user acceptance testing or production

The goal is not to prove that nothing can go wrong. The goal is to make the release decision explicit, evidence-based, and honest about remaining risk.

## Pre-Candidate Gate

These checks confirm that scope is clear and dependencies are visible before candidate testing begins.

### Scope and Planning

- [ ] In-scope features, fixes, and known exclusions are documented.
- [ ] Out-of-scope work is explicitly named.
- [ ] Dependencies between work items are identified and sequenced.
- [ ] Feature flag questions are answered or assigned owners.
- [ ] Release notes outline is drafted, even if incomplete.
- [ ] Deferred work has a reason, not just a vague "later."

### Test Automation

- [ ] Test scenarios exist for in-scope changes or gaps are documented.
- [ ] Workflow coverage is identified.
- [ ] Test suites are updated with new or changed scenarios.
- [ ] Data dependencies are documented.
- [ ] Environment variables, fixtures, or seed data are accounted for.
- [ ] No feature-flagged tests are hidden in configuration without documentation.

### Documentation

- [ ] User-facing docs are updated or tracked as deferred.
- [ ] Internal runbooks reflect current behavior.
- [ ] Known limitations are documented.
- [ ] Architecture or process decisions are captured where the team can find them.

### Infrastructure and Tools

- [ ] CI/CD pipeline changes are configured and tested.
- [ ] Required test runners, agents, or environments are available.
- [ ] Observability, logs, and alerts are ready for the release.
- [ ] Operations or support teams know about infrastructure changes.

## Release Gate

These checks confirm that the release candidate is stable enough for the next environment or audience.

### Test Execution and Readiness

- [ ] Core workflow tests are passing.
- [ ] Dependent workflows are tested relative to core workflow stability.
- [ ] Coverage inventory is current: the team knows what was tested and what was not.
- [ ] Test data is present, current, and verified.
- [ ] Test environment was stable during execution.
- [ ] Any reruns, retries, or skipped tests are explained.

### Signal Quality

- [ ] Passing tests include substantive assertions.
- [ ] No tests are marked passing with zero meaningful execution.
- [ ] Failures have known causes or explicit risk acceptance.
- [ ] Flaky behavior is tracked and does not mask release risk.
- [ ] Edge cases and error paths are considered, not only happy paths.

### Documentation and Communication

- [ ] Release notes are finalized and reviewed.
- [ ] Known limitations are listed with business impact.
- [ ] Stakeholders are briefed on scope changes.
- [ ] Support or customer-facing teams are briefed on workflow changes.
- [ ] Rollback or disablement instructions are available.

### Risk Assessment

- [ ] Data model or schema changes are tested in the candidate environment.
- [ ] Feature flag behavior is verified.
- [ ] Backward compatibility is assessed.
- [ ] Monitoring plan is ready for launch.
- [ ] The team has named the top remaining risks.

### Sign-Off

- [ ] Product or business owner sign-off.
- [ ] Quality sign-off on coverage and signal quality.
- [ ] Operations sign-off on environment stability.
- [ ] Release manager decision: **GO / NO-GO / GO WITH CONDITIONS**.

## Failure Modes to Catch

These issues should trigger additional review before the release proceeds:

- **Coverage illusion:** tests pass but do not prove meaningful behavior.
- **Hidden scope:** work merged without clear release scoping.
- **Unstable candidate:** tests pass inconsistently or the environment is unreliable.
- **Undocumented data dependencies:** tests require specific data that is not captured.
- **Untested workflows:** a workflow is considered in scope but was not exercised.
- **Ambiguous deferrals:** nobody knows whether a feature is shipping or waiting.
- **Infrastructure surprises:** behavior differs between candidate and production environments.

## Notes

- User acceptance testing is usually a scoped confidence check, not a substitute for regression coverage.
- Feature flags are useful only when status, ownership, and disablement paths are clear.
- Fewer meaningful tests are better than many shallow checks that create false confidence.

