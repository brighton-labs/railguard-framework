# The R.A.I.L.G.U.A.R.D Framework
## Robust AI-Instructional Layer Guiding Uniform Agent Reasoning & Development

To define a multi-layered security and reasoning system for LLMs using Cursor, Windsurf or whatever GenAI coding tool, with the following goals:
- Enforce secure coding behavior
- Promote explainable, reflective AI outputs
- Separate global reasoning from language-specific syntax
- Reduce code injection, data leakage, and insecure assumptions

## 🧠 Core Principle: RAILGUARD
All foundational security and behavior rules follow the RAILGUARD Framework, composed of:
- **R**: Risk First
- **A**: Attached Constraints
- **I**: Interpretative Framing
- **L**: Local Defaults
- **G**: Generative Path Checks
- **U**: Uncertainty Disclosure
- **A**: Auditability
- **R+D**: Revision + Dialogue

## 🗂️ Rule Structure Overview

### 1. `railguard-input-validation.mdc` *(Global RAILGUARD Logic)*
```yaml
description: Secure reasoning and input validation behavior for all code
alwaysApply: true
globs: ["**/*"]
```
- Applies project-wide across languages
- Embeds the full RAILGUARD scaffolding
- Teaches the LLM how to reason securely before generating code
- Avoids specifying syntax (e.g. no `pydantic`, no `zod` — that’s left to language-specific rules)

This file acts as the **behavioral anchor** for:
- Input validation
- Risk detection
- Secure reasoning
- Inference time AI decisions

---

### 2. Domain-Specific Rules *(Refer to railguard-input-validation.mdc)*
These rules enforce conventions and practices within specific tech stacks, deferring behavioral logic to `railguard-input-validation.mdc`.
The Cursor Rules are visible [here](https://github.com/brighton-labs/railguard-cursor-coding).

Examples:

#### `fastapi-secure-railguard-available.mdc`
```yaml
# Describes route structure, Pydantic models, auth checks, logging
# Assumes `.cursor/rules/input-validation.mdc` is always loaded
```

## Recommended Directory Layout
```
.cursor/
├── rules/
│   ├── input-validation.mdc                         # Global behavior (RAILGUARD-based)
│   ├── fastapi-secure-railguard-available.mdc       # FastAPI project conventions
│   ├── ... etc
```

