# OPS Compliance Validator

The OPS Compliance Validator is a tool designed to automatically evaluate whether a Prompt Component
is compliant with the **Open Prompt Specification (OPS) v1.0**.

This directory defines the **specification, scope, and expected behavior** of the validator.
Actual implementations may vary, but MUST follow this specification to be considered OPS-compliant.

---

## Purpose

The validator exists to:

- Ensure structural correctness of OPS components
- Enforce separation of concerns
- Enable automated compliance checks
- Support CI/CD, marketplaces, and certification workflows

The validator evaluates **prompt architecture**, not model execution or output quality.

---

## What the Validator Does

An OPS-compliant validator:

1. Parses an OPS component (JSON or YAML)
2. Validates it against the canonical OPS schema
3. Applies rule-based checks from the OPS compliance checklist
4. Produces a deterministic validation report

---

## What the Validator Does NOT Do

The validator does NOT:

- Execute prompts
- Call language models
- Judge creativity or usefulness
- Guarantee correctness of AI outputs

---

## Specification

The formal behavior of the validator is defined in:

- 📄 **Validator Specification:** `ops-validator-spec.md`
- 📋 **Compliance Checklist:** `/compliance/checklist.md`
- 📐 **Canonical Schema:** `/spec/ops-1.0.json`

Any implementation MUST follow these documents.

---

## Expected Input

- A single OPS Prompt Component
- Format: JSON or YAML
- Target OPS version: `1.0`

---

## Expected Output

A compliant validator MUST produce a **machine-readable JSON report** including:

- Validator identity and version
- Component metadata
- Compliance status
- Compliance score
- Detailed check results

See the validator specification for the exact report schema.

---

## Compliance Levels

The validator classifies components as:

- ✅ **OPS_COMPLIANT**
- ⚠️ **OPS_COMPATIBLE** (partial compliance)
- ❌ **NOT_OPS_COMPLIANT**

Classification rules are fully defined in the validator specification.

---

## Intended Usage

The OPS Compliance Validator is designed to be used in:

- Developer workflows
- Continuous Integration (CI)
- Prompt marketplaces
- Certification programs
- Enterprise governance pipelines

---

## Reference Implementation

Nova is intended to provide a reference implementation of the OPS Compliance Validator.

However, OPS does not require the use of Nova.
Any implementation following the validator specification is considered valid.

---

## Status

- Validator specification: **Draft**
- Reference implementation: **Planned**
- OPS target version: **1.0**

---

## Contributing

Contributions to the validator specification should follow the repository contribution guidelines.

Validator implementations may be open-source or proprietary.

---

## Final Note

The OPS Compliance Validator enables trust at scale.

By making prompt architectures inspectable and verifiable, OPS moves prompt engineering
from informal practice to professional discipline.
