# Open Prompt Specification (OPS)

**An open standard for structured, data-driven prompt engineering.**

The Open Prompt Specification (OPS) defines a vendor-neutral, model-agnostic way to design prompts as reusable, inspectable, and composable system components.

OPS exists to move prompt engineering from ad-hoc text to **engineering-grade architectures**.

---

## Why OPS?

As AI systems move into production, prompts have become critical infrastructure.  
However, most prompts today are:

- Informal and unstructured
- Tightly coupled to specific models
- Difficult to reuse or audit
- Fragile under scale and change

OPS addresses this gap by defining **how prompts should be designed**, not how models work.

---

## What OPS Defines

OPS specifies a standard architecture for prompts, including:

- Clear separation between system instructions and user data
- Explicit variable schemas
- Behavioral and validation rules
- Contractual output definitions
- Composable prompt components

OPS-compliant prompts behave like **software components**, not static messages.

---

## What OPS Does NOT Define

OPS intentionally does NOT define:

- Model internals
- Agent orchestration
- Execution runtimes
- UI or UX patterns

OPS focuses exclusively on **prompt architecture and structure**.

---

## Core Concepts

An OPS Prompt Component consists of:

1. **System Prompt Template**  
   Defines role, intent, and constraints.

2. **User Prompt Template**  
   Supplies real input data only.

3. **Variable Schema**  
   Structured representation of extracted data.

4. **Rules Engine**  
   Behavioral, validation, and output rules.

5. **Output Contract**  
   Explicit format and schema for results.

---

## Specification

- 📄 Technical Specification: [`spec/ops-1.0.md`](spec/ops-1.0.md)
- 📦 Canonical Schemas: `spec/ops-1.0.json`, `spec/ops-1.0.yaml`
- ✅ Compliance Checklist: [`compliance/checklist.md`](compliance/checklist.md)
- 🧩 Minimal Example: [`examples/minimal`](examples/minimal)

---

## Reference Implementation

[Nova](https://example.com) is a reference implementation of OPS.

Nova provides tooling to:
- Validate OPS compliance
- Generate and compose prompt components
- Connect OPS components to execution platforms

Implementing OPS does **not** require using Nova.

---

## License

The Open Prompt Specification (OPS) is licensed under the **Apache License, Version 2.0**.

This license allows both open-source and proprietary implementations of the specification.

See the [LICENSE](LICENSE) file for details.

---

## Governance and Contributions

OPS is vendor-neutral and designed to evolve through community collaboration.

- Contribution guidelines: [`CONTRIBUTING.md`](CONTRIBUTING.md)
- Governance model: [`GOVERNANCE.md`](GOVERNANCE.md)

By contributing, you agree that your contributions will be licensed under Apache License 2.0.

---

## Status

- **Current version:** OPS 1.0 (Draft)
- **Stability:** Suitable for experimentation and early adoption
- **Roadmap:** See [`docs/roadmap.md`](docs/roadmap.md)

---

## Getting Started

If you are new to OPS:

1. Read the minimal example in `/examples/minimal`
2. Review the compliance checklist
3. Explore or build an OPS-compliant implementation

OPS is designed to be simple to adopt and powerful to scale.

---

## Final Note

Prompts are no longer experiments.  
They are infrastructure.

OPS provides the foundation to build prompt systems that are reliable, auditable, and reusable.

---

**OPS is the standard. Nova is the platform.**
