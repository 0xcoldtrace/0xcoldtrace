# audit-reports

Security audit findings and vulnerability disclosures by **0xcoldtrace**.

---

## structure

```
audit-reports/
├── solo/                    # independent audits
│   └── YYYY-MM-protocol/
│       ├── report.md
│       ├── findings/
│       │   ├── H-01.md
│       │   ├── M-01.md
│       │   └── L-01.md
│       └── poc/
│           └── Exploit.t.sol
├── contests/                # competitive audit contests
│   └── YYYY-MM-platform-protocol/
│       ├── findings.md
│       └── poc/
└── bug-bounty/              # responsible disclosures (redacted)
    └── YYYY-MM-protocol/
        └── disclosure.md
```

## finding template

Each finding follows this format:

```markdown
# [H/M/L-XX] Title

## Summary
One-line description of the vulnerability.

## Vulnerability Detail
Technical breakdown — what the bug is, where it lives, why it exists.

## Impact
What an attacker can achieve. Quantify when possible (TVL at risk, max extractable value).

## Code Reference
Link to the vulnerable code with line numbers.

## Proof of Concept
Foundry test or script demonstrating the exploit.

## Recommendation
Suggested fix with code diff.
```

## severity classification

| Severity | Definition |
|----------|-----------|
| Critical | Direct loss of funds, >$1M TVL at risk, no user interaction required |
| High | Direct loss of funds with conditions, protocol insolvency risk |
| Medium | Loss of funds with significant constraints, griefing, DoS |
| Low | Best practice violations, informational, gas optimizations |

---

*findings are added as audits are completed. redacted entries indicate responsible disclosure in progress.*
