# OPS Compliance Validator
## Tool Specification — OPS v1.0

**Status:** Draft  
**Scope:** Defines how to automatically validate whether a Prompt Component is OPS v1.0 compliant.  
**Inputs:** OPS Component (JSON/YAML) + OPS Canonical Schema + OPS Compliance Checklist  
**Outputs:** Deterministic validation report (JSON)

---

## 1. Purpose

The OPS Compliance Validator is a tool that:

1. Validates structural compliance against the OPS canonical schema (`spec/ops-1.0.json|yaml`)
2. Applies rule-based checks aligned with `compliance/checklist.md`
3. Produces a deterministic report that is:
   - machine-readable
   - audit-friendly
   - suitable for CI/CD and certification

---

## 2. Non-Goals

The validator does NOT:
- guarantee correctness of model outputs
- evaluate semantic “quality” of prompts
- run or execute the prompt
- enforce style preferences beyond explicit rules

---

## 3. Validator Inputs

A compliant validator implementation MUST accept:

### 3.1 Component Document
- JSON or YAML OPS component definition

### 3.2 OPS Version Target
- default: `"1.0"`
- MUST fail if component `ops_version` mismatches target

### 3.3 Optional Configuration
Validator MAY accept configuration flags (see Section 8).

---

## 4. Validation Phases

A validator MUST run the following phases in order:

### Phase A — Parse
- Parse JSON/YAML
- Fail on invalid syntax

### Phase B — Schema Validation
- Validate against `spec/ops-1.0.json` (canonical)
- Fail on missing required fields
- Fail on unexpected additional properties (as defined by schema)

### Phase C — Checklist Rules (Static)
Applies additional checks not strictly expressed in JSON Schema, including:

- Separation of concerns heuristics
- Required variables consistency
- Output format/schema consistency
- Model-independence checks

### Phase D — Classification
Assign compliance level:
- `OPS_COMPLIANT`
- `OPS_COMPATIBLE`
- `NOT_OPS_COMPLIANT`

---

## 5. Deterministic Output Report (Required)

A validator MUST output a JSON report with the following schema:

```json
{
  "validator": {
    "name": "string",
    "version": "string",
    "ops_target_version": "1.0"
  },
  "component": {
    "name": "string",
    "version": "string",
    "ops_version": "string"
  },
  "result": {
    "status": "OPS_COMPLIANT | OPS_COMPATIBLE | NOT_OPS_COMPLIANT",
    "score": 0,
    "errors": [],
    "warnings": [],
    "checks": []
  }
}
