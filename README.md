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
│   ├── railguard-input-validation.mdc               # Global behavior (RAILGUARD-based)
│   ├── fastapi-secure-railguard-available.mdc       # FastAPI project conventions
│   ├── ... etc
```
---

## 🛠️ How to Build a New CursorRule (Contributor Guide)

When contributing a new `.mdc` rule, follow this trusted process:

1. **Pick a Category You Know**  
   Choose a domain, tech, or tool you’re comfortable and experienced with.

2. **Start With Official Documentation**  
   Before writing anything, collect and study the official docs of the framework, tool, or language.

3. **List All Security Rules by Hand**  
   Write down all the security rules you know and find (from docs and experience).  
   🔒 _**No LLMs used at this step — this is very important.**_

4. **Draft the Rule Manually**  
   Write the first version of the `.mdc` file based on your list. It doesn’t have to be perfect — focus on clarity and completeness.

5. **Test with 3 LLMs**  
   Choose 3 major models (e.g., ChatGPT, Gemini, LLaMA 3). Paste in your security rule and test:
   - ✅ Normal prompts (how it behaves)
   - ⚠️ Tricky prompts (how it fails)
   - 🔁 Iterate to improve how the rule defends and reasons

6. **Complete the Rule Collaboratively with the LLMs**  
   Use the models to challenge and refine your draft. Ask for corner cases, generate sample code, improve clarity.

7. **Build 2 files for one Rule:**
   - Build a **standalone rule**, embed the full [RAILGUARD] framework inside (R, A, I, L, G, U, A, R+D).
   - Build a **domain-specific rule**, focus on syntax, context, and patterns. Reference `.cursor/rules/input-validation.mdc` inside it (instead of rewriting RAILGUARD logic).

8. **Test in Cursor or IDE**  
   Apply the rule in a real project. Verify behavior and output. Refine wording or globs if necessary.

---

## License
This project is licensed under the MIT License - see the LICENSE file for details.

