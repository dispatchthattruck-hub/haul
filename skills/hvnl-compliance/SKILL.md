---
name: hvnl-compliance
description: "Build and update HVNL-compliant driver screens and audit trails for the dispatchthattruck haul app. Use when creating or modifying fit-for-duty, pre-start, run sheet, or any flow that must hard-block on statutory duties, embed exact HVNL sections, and generate a defensible record."
type: workflow
lifecycle: active
---

# HVNL Compliance — Pre-empt the Ass-Fucking

Build driver flows that turn the Heavy Vehicle National Law into your defence. Every screen hard-blocks on the relevant duty and creates timestamped, section-cited evidence so an inspector can't pin you for what you "should have known".

Repo: `dispatchthattruck-hub/haul` on GitHub, deployed to Vercel as static HTML (or Vite+React when ready).

## Core Workflow

1. Identify the duty and exact HVNL section (see references/duties.md).
2. Design the screen so the driver cannot proceed without a real declaration or check.
3. Embed the section citation and the consequence of a false/skipped declaration on the page itself.
4. Generate the HTML (or React component) with inputs, hard-block button, and audit fields (driver, date, vehicle, timestamp).
5. Push to `main` on the haul repo. Vercel auto-deploys.
6. Confirm the live URL serves only the intended file (no leftover index.html).

## Fit-for-Duty Screen (first gate)

- 10 checkboxes covering fatigue, medical/impairment, vehicle readiness, CoR awareness.
- New statutory duty on driver not to drive if unfit; operator not to cause or permit it.
- Hard-block submit until every box ticked.
- Warning: false declaration is an offence for driver and operator.
- Fields: driver name, shift date, vehicle, timestamp.
- Executive due diligence (s26D) note if operator scales beyond owner-driver.

## Pre-empt Pattern

For any scenario ("driver went out with low hours", "mass not verified"):
- State the exact evidence the app must have captured.
- Cite the section that protects you if the evidence exists.
- Output the checklist item or gate that forces the evidence.

## Resources

- See `references/duties.md` for the key sections and who they bite.
- See `assets/fit-for-duty-template.html` for the starting screen.

## Common Issues

| Problem | Fix |
|---|---|
| Old index.html still serving | Delete it from repo root and push. Rename target file to index.html. |
| Vercel not deploying | Confirm Git connection is to dispatchthattruck-hub/haul. Fresh push triggers build. |
| Missing citation | Pull exact section from references/duties.md before writing the screen. |
