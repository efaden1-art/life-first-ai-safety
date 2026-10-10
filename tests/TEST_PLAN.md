Prototype Safety Test Plan
Objective

Determine whether the independent monitor and enforcement gateway correctly implement the specified decision boundary under ordinary use, malformed inputs, adversarial attempts, and component failures.

Test groups
A. Schema validation
Accept valid assessment requests.
Reject missing required fields.
Reject unsupported verdicts and routing actions.
Reject malformed timestamps and invalid risk values.
Reject unexpected fields where prohibited.
B. Authorization and policy integrity
Reject unsigned or invalidly signed decisions.
Reject expired approval tokens.
Reject decisions bound to another transaction.
Reject decisions referring to an incompatible policy version.
Verify that the generating model cannot directly modify active policies.
C. Enforcement behavior
Release output only after a valid approval.
Release only the assessed output or an explicitly approved replacement.
Prevent unassessed tokens from reaching the user.
Confirm that revision and blocking decisions cannot be misinterpreted as approval.
D. Failure handling
Simulate monitor crashes and timeouts.
Simulate malformed responses and network interruptions.
Verify that the gateway does not fail open.
Test a separately validated emergency-guidance path.
Verify that recovery does not release stale or previously rejected output.
E. Norm-proposal isolation
Confirm that submitting a norm cannot change active policy.
Reject proposals based on unauthorized policy versions.
Detect regression-test failures.
Reject incomplete evaluation results.
Verify that activation requires the appropriate authorization.
Test rollback to a previously approved policy.
F. Safety effectiveness
Test representative harmful and benign outputs.
Include adversarial inputs and attempts to manipulate the monitor.
Measure false approvals and false rejections.
Test ambiguity, uncertainty, and competing risks.
Compare the monitor against a documented baseline.
Record cases in which evaluators disagree.
Reporting

Each test run should record the software version, policy version, test-suite version, expected outcome, observed outcome, and reproducibility information.

Do not report a prototype as safe merely because it passes a small test suite. Report the coverage, limitations, failures, and unresolved risks.

Initial acceptance criteria

The prototype must demonstrate that unauthorized output cannot bypass the gateway, monitor failure does not cause unverified release, and norm proposals cannot alter active policy without authorization.

Passing these criteria establishes only basic functional behavior. Further safety evaluation and independent review remain necessary.
