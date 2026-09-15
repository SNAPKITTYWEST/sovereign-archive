<!--
  SPDX-License-Identifier: GPL-3.0-or-later
  Copyright (c) 2026 SnapKittyWest
  Ahmad Ali Parr / Bel Esprit D'Accord Irrevocable Trust
  CLONE GATE: Any clone, fork, or derivative MUST be released under GPL-3.0-or-later
-->

# Sovereign Archive

**SANDBOX → ARCHIVE OPS → VERIFICATION → AUDIT SEAL → LEDGER**

A zero-stub, fully executable Go pipeline for deterministic archive operations with tamper-detection, policy enforcement, and full audit trail.

## Pipeline

```
SANDBOX (path validation)
    → ARCHIVE OPS (execute)
    → VERIFICATION (integrity check)
    → AUDIT SEAL (record)
    → LEDGER (persist)
```

All code executable. Zero stubs. Full audit trail with tamper detection.

## Packages

| Package | File | LOC | Purpose |
|---------|------|-----|---------|
| `archive` | `archive-tools.go` | 1,136 | Archive operations |
| `control` | `control-policy.go` | 441 | Policy engine |
| `control` | `control-dag.go` | 693 | DAG scheduler |
| `sandbox` | `sandbox-boundary.go` | 288 | Path safety |
| `audit` | `audit-verify.go` | 196 | Verification engine |
| `audit` | `audit-seal.go` | 387 | Decision seals & ledger |
| `main` | `main-app.go` | 370 | CLI application |
| `main` | `acceptance-tests.go` | 305 | Test suite |
| `main` | `acceptance_test.go` | 654 | Integration tests |
| `archive` | `archive-extract-verify.go` | 286 | Extract/verify ops |
| `audit` | `audit-module.go` | 345 | Audit module |
| `sandbox` | `sandbox-module.go` | 148 | Sandbox module |
| `main` | `cmd/gui-main.go` | 293 | Fyne GUI |

**Total: 5,542 lines**

## Build

```bash
# CLI
go build -o sovereign-archive .

# GUI
go build -o sovereign-archive-gui ./cmd/

# Tests
go test ./...
```

## License

GPL-3.0-or-later. CLONE GATE: any fork must be open-source under GPL-3.0+.
Copyright (c) 2026 SnapKittyWest. Ahmad Ali Parr / Bel Esprit D'Accord Irrevocable Trust.
