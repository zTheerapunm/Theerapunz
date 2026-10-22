name: powerapps-development-agent-skill
description: "Production-grade Power Apps development skill powered by Jev orchestration. Builds Canvas Apps (Power Fx), Model-Driven Apps (Dataverse), and Power Apps Code Apps (React/Vite) with Fluent UI and ALM pipelines."
version: "1.0.0"
author: "Gemini Notebook Agent Workbench"
---

# Power Apps Multi-Skill Development Framework

## 1. OVERVIEW & TARGET PLATFORMS

This skill equips AI coding agents to build, refactor, and audit Microsoft Power Apps applications across three distinct creation paths:

1. **Canvas Apps (Low-Code/Power Fx)**: Focuses on custom pixel-perfect mobile/web interfaces using Power Fx declarative logic, delegable Dataverse queries, and offline collection caching.
2. **Model-Driven Apps (Data-First/Dataverse)**: Focuses on enterprise business apps built on Dataverse metadata, custom client scripts (JavaScript/TypeScript Web Resources), and Power Apps Component Framework (PCF) controls.
3. **Power Apps Code Apps (Pro-Code Web Apps)**: Focuses on custom React/TypeScript/Vite web apps running natively inside Power Apps using standard web stacks, Fluent UI v9, and Power Platform connectors via the `@microsoft/power-apps` SDK.

---

## 2. CORE ARCHITECTURE & DEPENDENCIES

* **Core Decision Engine**:
  * [**Jev Skills**](https://github.com/wuyoscar/jev-skill) (`wuyoscar/jev-skill`): Uses `jev-triage` to classify app types, `jev-act` to select Power Platform CLI (`pac`) or Power Fx actions, and `jev-eval` for ALM quality gates.
* **Power Apps Pro-Code & Technical Guidance**:
  * [**Power Apps Code Apps**](https://github.com/microsoft/PowerAppsCodeApps) (`microsoft/PowerAppsCodeApps`): Official templates (`npx degit microsoft/PowerAppsCodeApps/templates/starter my-app`), Dataverse CRUD samples, and SDK integration guidelines.
  * [**Microsoft Power Apps Documentation**](https://github.com/MicrosoftDocs/powerapps-docs) (`MicrosoftDocs/powerapps-docs`): Official technical reference for Power Fx coding guidelines, Dataverse metadata, and Client Scripting.
  * [**Building AI Agents From Zero to Production**](https://github.com/microsoft/Building-AI-Agents-From-Zero-To-Production) (`microsoft/Building-AI-Agents-From-Zero-To-Production`): Microsoft Agent Framework (MAF), Microsoft Foundry hosted agents, and MCP toolboxes.
* **UI/UX & Design Systems**:
  * [**UI/UX Pro Max**](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) (`nextlevelbuilder/ui-ux-pro-max-skill`): Design intelligence supporting Fluent UI 2, React, Tailwind CSS, and Microsoft platform guidelines.
  * [**Awesome DESIGN.md**](https://github.com/VoltAgent/awesome-design-md) (`VoltAgent/awesome-design-md`): Brand design system definitions in plain-text markdown.
* **Software Engineering Discipline**:
  * [**Agent Skills**](https://github.com/addyosmani/agent-skills) (`addyosmani/agent-skills`): Spec-driven development, TDD, code review, and git versioning.
  * [**Ponytail**](https://github.com/DietrichGebert/ponytail) (`DietrichGebert/ponytail`): Minimalist code generation (YAGNI) for Power Fx expressions and TypeScript client scripts.

---

## 3. WORKFLOW PROCESS

```
┌────────────────────────────────────────────────────────────────────────┐
│ PHASE 1: APP TYPE TRIAGE (`jev-triage`)                                │
│ - Classify request: Canvas App | Model-Driven App | Code App           │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│ PHASE 2: ARCHITECTURE & SPECIFICATION (`agent-skills` /spec & /plan)    │
│ - Define Dataverse entities, Power Fx state, or React/Vite hierarchy  │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│ PHASE 3: IMPLEMENTATION (`jev-act` + Domain Skills)                     │
│ ├── Canvas App: Power Fx formulas + Delegable Filter/Search            │
│ ├── Model-Driven: Dataverse Forms/Views + Client Scripting/PCF         │
│ └── Code App: `PowerAppsCodeApps` template + Fluent UI v9 + SDK        │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│ PHASE 4: AUDIT, ALM & SOLUTION PACKAGING (`jev-eval` + ISO 29110)      │
│ - Delegation check | Accessibility (WCAG) | Solution export via `pac` │
└────────────────────────────────────────────────────────────────────────┘
```

### Phase 1: App Type Triage (`jev-triage`)
1. Analyze the user request using `jev-triage`:
   * **Canvas App**: Select when visual freedom, mobile responsiveness, or multi-connector canvas UI is required.
   * **Model-Driven App**: Select for complex relational data workflows, process flows, or standard back-office interfaces.
   * **Code App**: Select when complex React components, custom chart visualizations, or custom web libraries are needed within Power Apps.

### Phase 2: Architecture & Data Modeling
1. **Dataverse Schema**: Define tables, choices, columns, and relationships (1:N, N:N).
2. **Design System Setup**: Extract brand tokens into `DESIGN.md` or apply Fluent UI v9 theme providers.
3. **Spec-Driven Plan**: Execute `/spec` and `/plan` from `agent-skills` to establish component boundaries and acceptance criteria.

### Phase 3: Implementation Guidelines

#### A. Canvas App (Power Fx) Standards
* **Delegation Rule**: Always use delegable functions (`Filter`, `LookUp`, `Search`) to avoid the 500/2000 record limit.
* **Performance & State**: Use `Concurrent()` for parallel data loading; minimize global variables (`Set()`) in favor of context variables (`UpdateContext()`) or component parameters.
* **Layout**: Utilize Responsive Containers (`HorizontalLayoutContainer`, `VerticalLayoutContainer`) rather than absolute X/Y positioning.

#### B. Model-Driven App Standards
* **Client Scripting**: Write TypeScript for form event handlers (`OnLoad`, `OnChange`, `OnSave`); compile to ES6 JavaScript Web Resources.
* **PCF Controls**: Build custom controls with Power Apps Component Framework using React + Fluent UI v9 when native controls are insufficient.

#### C. Power Apps Code Apps Standards
* **Scaffolding**: Initialize using official template: `npx degit microsoft/PowerAppsCodeApps/templates/starter my-code-app`.
* **Data Integration**: Use `@microsoft/power-apps` SDK and TanStack Query for caching and asynchronous connector calls.
* **UI Framework**: Import `@fluentui/react-components` (Fluent UI v9) to ensure seamless visual parity with Microsoft 365 / Power Apps shell.

### Phase 4: Quality Gates & Solution ALM
1. **Power Fx / Code Simplification**: Apply `ponytail` YAGNI rules—remove redundant Power Fx variables or unnecessary React hooks.
2. **Accessibility Audit**: Validate contrast, keyboard navigation, and screen reader labels using `Checklist-Design/skills` and WCAG 2.1 AA rules.
3. **Solution Lifecycle (ALM)**: Package assets into Dataverse Solutions using Power Platform CLI (`pac solution init`, `pac solution pack`) for pipeline deployment.

---

## 4. SKILL ROUTING & REFERENCE MATRIX

| Development Target | Recommended Skill / Repository | Key Deliverable / Command | Reference Link |
| :--- | :--- | :--- | :--- |
| **App Type Classification** | `jev-triage` | App architecture selection report | [wuyoscar/jev-skill](https://github.com/wuyoscar/jev-skill) |
| **Power Apps Code Apps (React)** | `PowerAppsCodeApps` templates & SDK | Custom React web app running in Power Apps | [microsoft/PowerAppsCodeApps](https://github.com/microsoft/PowerAppsCodeApps) |
| **Power Apps Documentation & Fx** | `powerapps-docs` | Delegable Power Fx formulas & TS Web Resources | [MicrosoftDocs/powerapps-docs](https://github.com/MicrosoftDocs/powerapps-docs) |
| **Hosted AI Agents & MCP** | `Building-AI-Agents-From-Zero-To-Production` | Microsoft Agent Framework & Foundry deployments | [microsoft/Building-AI-Agents-From-Zero-To-Production](https://github.com/microsoft/Building-AI-Agents-From-Zero-To-Production) |
| **Fluent UI & Design System** | `ui-ux-pro-max-skill` + `awesome-design-md` | Fluent UI v9 design tokens & layout rules | [nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) |
| **Engineering & TDD Workflow** | `agent-skills` (`/spec`, `/plan`, `/test`) | PRD specs, task breakdown, unit tests | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) |
| **Code & Formula Minimization** | `ponytail` | Concise Power Fx / TS code without bloat | [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) |

---

## 5. RED FLAGS & ANTI-RATIONALIZATION

* ❌ **Non-Delegable Queries in Canvas Apps**: Never use `ClearCollect()` to fetch entire Dataverse tables into client memory to bypass delegation limits.
* ❌ **Hardcoded Connection GUIDs**: Never hardcode Environment IDs or Connection GUIDs in Power Fx or React code; use Environment Variables in Solutions.
* ❌ **Unmanaged Direct Editing**: Never edit canvas apps or web resources directly in Production; changes must be deployed via Dataverse Unmanaged/Managed Solutions.
* ❌ **Ignoring Access Control**: Never rely solely on UI button hiding for security; enforce Dataverse Table Permissions and Column-Level Security at the backend.

---

## 6. VERIFICATION & EXIT CRITERIA

1. **Delegation Verified**: All Dataverse and SQL calls in Canvas Apps pass the Power Apps App Checker with zero delegation warnings.
2. **Code App Build Passing**: Code Apps compile cleanly via `npm run build` and pass Playwright E2E tests.
3. **Accessibility Verified**: Form controls have ARIA labels, semantic roles, and pass WCAG 2.1 AA audits.
4. **Solution Packaged**: Assets are exported as a valid Dataverse Solution zip via `pac solution pack` ready for CI/CD pipelines.
