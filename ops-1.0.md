# Open Prompt Specification (OPS)
## Version 1.0

**Status:** Draft  
**License:** Apache License 2.0  
**Last updated:** 2025  
**Scope:** Prompt architecture and prompt lifecycle definition

---

## 1. Purpose

The Open Prompt Specification (OPS) defines a **vendor-neutral, model-agnostic standard** for designing prompts as structured, reusable, and inspectable system components.

OPS exists to enable prompt systems that are:
- reproducible
- composable
- auditable
- scalable beyond ad-hoc usage

OPS does not define execution runtimes, model internals, or user interfaces.

---

## 2. Terminology

The key words **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** in this document are to be interpreted as described in RFC 2119.

---

## 3. Core Concepts

### 3.1 Prompt Component

A **Prompt Component** is the fundamental unit defined by OPS.

A Prompt Component MUST include:
- a System Prompt Template
- a User Prompt Template
- a Variable Schema
- a Rules Engine
- an Output Contract

A Prompt Component MUST be representable in a structured format such as JSON or YAML.

---

## 4. Architectural Principles

### 4.1 Separation of Concerns

OPS mandates strict separation between the following elements:

| Element | Responsibility |
|------|---------------|
| System Prompt | Defines behavior, intent, and constraints |
| User Prompt | Supplies input data only |
| Variables | Structured representation of extracted data |
| Rules | Behavioral, validation, and output constraints |
| Output | Contractual result definition |

A compliant Prompt Component MUST NOT mix instructions and user data in the same template.

---

## 5. Prompt Component Structure

An OPS Prompt Component MUST define the following top-level fields:

```json
{
  "ops_version": "1.0",
  "meta": {},
  "roles": {},
  "variables": {},
  "rules": {},
  "outputs": {}
}
