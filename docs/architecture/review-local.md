# Local review: drive-bays (branch diff main...HEAD)

- Date: 2026-11-04
- Commit: b3bfce9
- Scope: branch diff main...HEAD (docs only: README, PROJECT_LOG, ADR-0001)
- Checks run: adversarial (Opus, 2 rounds), secrets scan. Design, docs, tests, security and correctness audits skipped: no code in the diff.
- Verdict: ship as-is. Must 0, Should 1, Nice 3

## Adversarial review (#236)
- Round 1 on `ff45d57`: Must 2, Should 3, Nice 4, unverified 2, Push gate: closed
- Round 2 on `b3bfce9`: 9 fixed, 0 not fixed, 0 regressed, new Must 0, **Push gate: open**
- Hosted reviewers (filled at the pre-merge run): Copilot pending, Codex not requested

## Pre-merge gate
`--push` mode: no `justfile`, no code.

| Step | Result |
|---|---|
| 0 CI mirror | n/a, no `.github/workflows` |
| 1 Tests | n/a, no code |
| 2 Coverage | deferred to the pre-merge run, no code |
| 3 SonarQube | deferred to the pre-merge run |
| 4 Secrets | gitleaks clean on `main..b3bfce9`, no tracked .env, diff read: nothing sensitive |
| 5 E2E/smoke | skipped with `--push` |
- Gate: **pre-push green**, steps 2, 3 and 5 deferred (never GREEN)

## Must Have
_None._

## Should Have
- `docs/architecture/decisions/0001-build-two-modules-from-one-five-bay-pcb.md:28-29` [adversarial] Seven matrix cells (Scalability A and B, Cabling A, B, C) have no one-line reason. Add one per cell.

## Nice to Have
- `ADR-0001:36` [adversarial] State that the 70 % threshold scales the other weights proportionally (exact 69.4).
- `README.md:23-24` [adversarial] Say which simulator is the default (ngspice, PSpice only with a Windows host).
- `PROJECT_LOG.md:6` [adversarial] Log the ngspice / Windows-host decision in the toolchain entry.

## Disagree / Intentional
_None._

## Per-dimension summary
- Adversarial: 9 round-1 findings fixed, none regressed. Design, docs, tests, security, correctness: not run (no code).
