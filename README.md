# PFL Fitness Directive Builder

A single-page, no-backend tool for USAF Physical Fitness Leaders (PFLs), Unit
Fitness Program Managers (UFPMs), and Master Fitness Leaders (MFLs) to generate
exemption-aware training directives and track a roster's fitness-program
administrative status.

Grounded in **AFMAN36-2905 (24 March 2026)** and the **Warfighter's Fitness
Playbook 2.0 (February 2026)** — component scoring, PFRA Hold / Adaptive Fitness
Program logic, Exercise Modality vs. Component Exemption status, and exercise
prescriptions all trace back to those two documents rather than being invented.

## Live site

Once GitHub Pages is enabled for this repo (Settings → Pages → Deploy from branch →
`main` / root), it will be available at:

`https://<your-github-username>.github.io/<repo-name>/`

## What it does

The tool has three tabs:

### Directive Builder
Enter a member profile — gender, age, height/weight, ability level, objective,
per-component exemption status (Cardio / Strength / Core, each: not restricted /
Exercise Modality Exemption / Component Exemption), pregnancy, lower-body/joint
restriction, no-standing/static-hold restriction, and available equipment — and
generate a phased training directive (cardio, strength, core, and mobility work
per day, with exercises, sets x reps, and recommended load).

- **303-exercise library**, filtered live by documented restrictions and available
  equipment, with automatic fallback to broader options if a category would
  otherwise show fewer than 3 exercises.
- **Ability-level rep scaling** (Level 1/2/3) per the Playbook's own progression.
- **⟳ Swap** — substitute any single exercise for another from the same filtered
  pool without regenerating the whole directive.
- **PFRA Hold / Adaptive Fitness Program banner**, Reconditioning Period due-date
  calculation (from an optional AF Form 469 expiration date), and a full
  Component Status Matrix (EXEMPT / MODALITY / TESTED) per component.
- **Print / Save as PDF**, with interactive controls (swap buttons, etc.) hidden
  automatically in the printed output.
- **Roster Preview (Demo)** — generate a randomized 6-member synthetic roster,
  or send the current form's exact profile to the roster with "Add This Profile
  to Roster" (no randomization). Optional First/Last Name fields are demo labels
  only, clearly marked as such — never enter a real member's name.

### Administrative
Reads live from whatever's currently in the roster.

- **Roster tracker** — status (HOLD/READY), Next PFRA Due, and an AMRO Board
  referral flag (para 4.3's 1-year-on-hold threshold), color-coded.
- **Per-member action checklist** — auto-built from that member's exemption
  status, each item citing the specific AFMAN paragraph behind it.
- **View Directive / Remove** per roster member.
- **CSV export** and **print** of the roster summary.
- **Environmental & Safety** and **Role** quick-reference sections — deliberately
  limited to what's actually been verified against the source documents (e.g. no
  invented WBGT/heat-category thresholds, no fabricated role-responsibility text
  beyond what's been confirmed).

### Acronym Glossary
47 terms used throughout the tool's own output, each tagged with its source
(AFMAN36-2905, Playbook 2.0, general fitness/AF usage, or internal to this tool).

## What this is / isn't

- **Is:** a training-programming and light administrative-tracking aid. Everything
  runs client-side in the browser — no data is stored, transmitted, or logged
  anywhere, including the roster (it lives only in memory for the current tab).
- **Isn't:** an official myFitness tool. It does not calculate PFRA scores, and it
  does not replace guidance from a medical provider, HAWC, UFPM, or a properly
  constituted AMRO Board. The exemption/component logic is this tool's own
  interpretation and should be verified by someone with current UFPM-level
  knowledge before relying on it for a real member.

## Usage

Open `index.html` in any browser — no build step, no dependencies, no server
required.

## Privacy note

Do not enter real names or other identifying information anywhere in this tool.
The First/Last Name fields, if used, are for demo labeling only. Nothing is
persisted between sessions — closing the tab clears everything, including any
roster built up during that session.

## Status

This is a personal prototype, not an approved or officially hosted DAF tool.
Before any real-member use: a Privacy Impact Assessment, a UFPM/subject-matter
review of the exemption logic, and hosting on DAF-approved infrastructure (not
personal GitHub Pages) would all be required.
