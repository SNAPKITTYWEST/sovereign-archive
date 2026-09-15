<!--
  SPDX-License-Identifier: GPL-3.0-or-later
  Copyright (c) 2026 SnapKittyWest
  Ahmad Ali Parr / Bel Esprit D'Accord Irrevocable Trust
  CLONE GATE: Any clone, fork, or derivative MUST be released under GPL-3.0-or-later
-->

# Sovereign Archive

A deterministic, auditable Go pipeline for secure archive operations. Every operation passes through a sandbox boundary, gets policy-checked by a DAG scheduler, produces a tamper-evident audit seal, and is persisted to an immutable ledger.

```
SANDBOX       →  ARCHIVE OPS  →  VERIFICATION  →  AUDIT SEAL  →  LEDGER
(path safety)    (execute)        (integrity)       (record)       (persist)
```

Zero stubs. All code executable. Full audit trail with tamper detection.

---

## Repository Layout

```
sovereign-archive/
│
├── main-app.go            CLI entry point
│
├── archive/               Archive operations
│   ├── archive-tools.go       Core archive create/extract/list/verify
│   └── archive-extract-verify.go  Extract with integrity verification
│
├── control/               Policy engine + DAG scheduler
│   ├── control-policy.go      Policy rules and enforcement
│   └── control-dag.go         DAG-based operation scheduling
│
├── sandbox/               Path safety and boundary enforcement
│   ├── sandbox-boundary.go    Path validation and confinement
│   └── sandbox-module.go      Sandbox module interface
│
├── audit/                 Audit trail and tamper detection
│   ├── audit-verify.go        Integrity verification engine
│   ├── audit-seal.go          Decision seals and ledger persistence
│   └── audit-module.go        Audit module interface
│
├── cmd/
│   └── gui-main.go            Fyne desktop GUI (optional)
│
└── tests/
    ├── acceptance-tests.go    Acceptance test suite
    └── acceptance_test.go     Integration tests
```

---

## Pipeline

Each archive operation runs through five stages in order:

| Stage | Package | What It Does |
|-------|---------|-------------|
| **SANDBOX** | `sandbox/` | Validates all paths are within permitted boundaries before any I/O |
| **ARCHIVE OPS** | `archive/` | Executes create/extract/list/verify against the validated paths |
| **VERIFICATION** | `audit/audit-verify.go` | Checks checksums, signatures, and structural integrity of the result |
| **AUDIT SEAL** | `audit/audit-seal.go` | Records a tamper-evident seal (hash + timestamp) of the decision |
| **LEDGER** | `audit/audit-module.go` | Persists the sealed record to the immutable audit ledger |

---

## Build

```bash
# Build CLI
go build -o sovereign-archive .

# Build GUI
go build -o sovereign-archive-gui ./cmd/

# Run tests
go test ./...
```

---

## License

GPL-3.0-or-later. CLONE GATE: any fork must be open-source under GPL-3.0+.  
Copyright (c) 2026 SnapKittyWest. Ahmad Ali Parr / Bel Esprit D'Accord Irrevocable Trust.
