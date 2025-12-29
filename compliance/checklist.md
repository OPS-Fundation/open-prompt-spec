# OPS v1.0 — Compliance Checklist

This checklist defines the **minimum requirements** for a Prompt Component to be considered
**compliant with the Open Prompt Specification (OPS) v1.0**.

A compliant component is:
- structurally valid
- auditable
- reusable
- suitable for automated validation

---

## 1. General Structure

- [ ] The component is a valid JSON or YAML document
- [ ] `ops_version` is present and equals `"1.0"`
- [ ] All required top-level fields are present:
  - [ ] `meta`
  - [ ] `roles`
  - [ ] `variables`
  - [ ] `rules`
  - [ ] `outputs`
- [ ] No unexpected top-level fields are present

---

## 2. Metadata (`meta`)

### Required Fields

- [ ] `meta.name` exists and is a string
- [ ] `meta.version` exists and follows semantic versioning
- [ ] `meta.description` exists and clearly describes the component purpose

### Optional Fields (if present)

- [ ] Optional metadata fields do not contain execution logic
- [ ] Optional fields are descriptive only (author, license, tags, domain)

---

## 3. Roles Separation

### System Prompt (`roles.system`)

- [ ] `roles.system.template` exists and is a string
- [ ] Defines the role and intent of the model
- [ ] Defines behavioral constraints
- [ ] **Does NOT include user-provided data**
- [ ] **Does NOT reference raw input directly**

---

### User Prompt (`roles.user`)

- [ ] `roles.user.template` exists and is a string
- [ ] Contains only user input or placeholders
- [ ] **Does NOT contain instructions or behavioral guidance**

---

## 4. Variables

### Variable Schema

- [ ] `variables.schema` exists and is an object
- [ ] All variables have explicitly defined types
- [ ] Variable names are consistent across the component

### Required Variables (if defined)

- [ ] `variables.required` is an array of strings
- [ ] All required variables exist in `variables.schema`

---

## 5. Rules Engine

### Behavioral Rules

- [ ] `rules.behavioral_rules` exists and is an array
- [ ] Rules constrain reasoning behavior
- [ ] Rules prohibit unsupported assumptions

---

### Validation Rules

- [ ] `rules.validation_rules` exists and is an array
- [ ] Rules define invalid execution conditions
- [ ] Missing or invalid inputs are explicitly handled

---

### Output Rules

- [ ] `rules.output_rules` exists and is an array
- [ ] Rules define output structure or style
- [ ] Rules are compatible with the declared output format

---

## 6. Output Contract

- [ ] `outputs.format` exists and is valid
- [ ] Output format matches one of the supported types:
  - text
  - markdown
  - json
  - structured

### Structured Output (if applicable)

- [ ] `outputs.schema` exists
- [ ] Output schema defines all expected fields
- [ ] No implicit or undocumented output fields exist

---

## 7. Composability

- [ ] The component can be executed independently
- [ ] The component exposes a clear variable interface
- [ ] The output contract can be consumed by other components

---

## 8. Model Independence

- [ ] The component does not reference specific model names
- [ ] The component does not depend on vendor-specific features
- [ ] The component is portable across compatible models

---

## 9. Inspectability

- [ ] The component can be read and understood without proprietary tooling
- [ ] All behaviors and constraints are explicitly declared
- [ ] No hidden or implicit logic is present

---

## 10. Compliance Result

Based on this checklist, a Prompt Component may be classified as:

- ✅ **OPS v1.0 Compliant**
- ⚠️ **OPS v1.0 Compatible (partial compliance)**
- ❌ **Not OPS v1.0 Compliant**

The compliance result MUST be justifiable using the checks above.

---

## Final Note

This checklist is intended to be:
- human-readable
- machine-verifiable
- extensible in future OPS versions

Automated validators SHOULD follow this checklist as their source of truth.
