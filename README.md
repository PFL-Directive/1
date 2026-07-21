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

The tool has three tabs, in this order: **Administrative**, **Directive Builder**,
**Acronym Glossary**.

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
- **Objective/status consistency check** — flags a contradiction (e.g. "Preparing
  for Reassessment" set on a member who's on PFRA Hold and not authorized to test).
- **Print / Save as PDF**, with interactive controls (swap buttons, etc.) hidden
  automatically in the printed output.
- **Roster Preview (Demo)** — generate a randomized 6-member synthetic roster, or
  send the current form's exact profile to the roster with "Add This Profile to
  Roster" (no randomization). Remove any member individually, or clear the whole
  roster. Optional First/Last Name fields are demo labels only, clearly marked as
  such — never enter a real member's name.
- **Save/Load Roster to a file** — exports the current roster as a JSON file you
  keep, and re-imports it later. This is the only way a roster survives between
  sessions; the tool itself never stores anything automatically. Malformed or
  hand-edited import files are validated field-by-field rather than trusted
  outright, so a bad file can't corrupt the tool or crash the page.

### Administrative
Reads live from whatever's currently in the roster.

- **Roster tracker** — status (HOLD/READY), Next PFRA Due, and an AMRO Board
  referral flag (para 4.3's 1-year-on-hold threshold), color-coded. Correctly
  excludes Exercise Modality Exemptions (never on Hold) and pregnancy (excluded
  per para 2.26.11) from the referral flag, even if a hold-start date is entered.
- **Per-member action checklist** — real, checkable checkboxes, auto-built from
  that member's exemption status, each item citing the specific AFMAN paragraph
  behind it.
- **View Directive / Remove** per roster member.
- **CSV export** and **print** of the roster summary.
- **Environmental & Safety** reference — deliberately limited to what's actually
  been verified against the source documents (no invented WBGT/heat-category
  thresholds; those are left to DAFI 48-151 and the installation safety office).
- **Role Reference** — condensed summaries for the 10 roles most relevant at the
  unit level (Installation Commander through Member), pulled from the actual
  verified Chapter 2 body text, not just paragraph headings. Each row still cites
  its source paragraph for the full, authoritative version.

### Acronym Glossary
47 terms used throughout the tool's own output, sorted alphabetically, each
tagged with its source (AFMAN36-2905, Playbook 2.0, general fitness/AF usage, or
internal to this tool).

## What this is / isn't

- **Is:** a training-programming and light administrative-tracking aid. Everything
  runs client-side in the browser — no data is stored, transmitted, or logged
  anywhere, including the roster (it lives only in memory for the current tab
  unless you explicitly export it to a file yourself).
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
persisted automatically — closing the tab clears everything, including any
roster built up during that session, unless you deliberately export it to a
file first. Treat any exported roster JSON/CSV file with the same care you'd
give real member data, even though this tool only ever contains what you typed
in yourself.

## Status

This is a personal prototype, not an approved or officially hosted DAF tool.
Before any real-member use: a Privacy Impact Assessment, a UFPM/subject-matter
review of the exemption logic, and hosting on DAF-approved infrastructure (not
personal GitHub Pages) would all be required.

## Changelog

Rough build history, in order. Dates aren't tracked per-iteration — treat this as
sequence, not a timeline.

1. **Initial build.** Single generic-member intake (gender/age/height/weight,
   restriction checkboxes), phased training plan generator, 8/6/12-week blocks.
2. **Exercise-level detail.** Added named exercises with sets x reps and
   effort-based (RPE) load recommendations per day, instead of paragraph-style
   day descriptions.
3. **Print/PDF fixes.** Corrected color rendering and page-break handling so the
   EXEMPT/TESTED stamps and tables survive export to PDF.
4. **GitHub Pages deployment.** Moved off ad-hoc file sharing onto a live,
   linkable site.
5. **Accuracy audit.** Found and fixed a body-composition/pregnancy matrix bug,
   wired the lower-body restriction into cardio/strength (it previously only
   affected mobility), added input escaping and clamping.
6. **Grounded in the Warfighter's Fitness Playbook 2.0.** Added Ability Level
   (1/2/3) scaling, LE/UE/Core focus tags, and aligned exercise naming and rep
   schemes to the actual Playbook instead of general fitness knowledge.
7. **Exercise library expansion, part 1.** Grew from ~20 exercises to 133,
   organized by restriction category.
8. **Exercise library expansion, part 2.** Grew to 303 exercises across cardio,
   strength, core, and mobility, with phase-to-phase rotation so a directive
   doesn't repeat the same handful of movements every week.
9. **Grounded in AFMAN36-2905 (24 March 2026).** Added PFRA Hold / Adaptive
   Fitness Program framing, Reconditioning Period due-date calculation, correct
   component scoring weights, and fixed the citation from the superseded
   DAFMAN36-2905 designation. Found and fixed a second pregnancy-matrix bug
   (composite exemption should cover all four components, not just two).
10. **Equipment filtering, exercise swap, and Exercise Modality vs. Component
    Exemption.** Replaced simple restriction checkboxes with per-component
    exemption-type selectors matching the manual's real distinction. Found and
    fixed a bug where the swap function was only cycling through the 5 displayed
    exercises instead of the full filtered pool.
11. **Roster Preview (demo).** Randomized synthetic-member generation, then
    "Add This Profile to Roster" for a non-randomized manual path, name fields
    (demo labels only), and per-member remove.
12. **Acronym Glossary and Administrative tabs.** Roster tracker with AMRO
    Board referral flagging, per-member action checklists citing AFMAN
    paragraphs, CSV export, and environmental/safety and role quick-references
    (intentionally limited to verified content only).
13. **Workflow polish.** Tab reorder (Administrative, Directive Builder,
    Glossary), roster save/load to a JSON file, an objective/exemption
    consistency check, interactive checklist checkboxes, and alphabetizing the
    glossary.
14. **Verified Role Reference.** Replaced the Administrative tab's
    citation-only Role Reference table with condensed summaries pulled from the
    actual AFMAN36-2905 Chapter 2 body text (previously only the paragraph
    headings had been read, not the responsibility text itself).
15. **AMRO exclusion fix and crash fix.** The AMRO Board referral flag now
    correctly excludes members with only an Exercise Modality Exemption (never
    on PFRA Hold, so not eligible per para 4.3) and pregnancy (explicitly
    excluded per para 2.26.11), instead of flagging any member with a hold-start
    date regardless of status. Also fixed a crash in the Administrative tracker
    when a "date placed on hold" was entered without an AF Form 469 expiration
    date — it now shows a prompt instead of throwing an error.
16. **Hardened the exercise database against future edits.** A typo'd or
    missing exercise-prescription reference previously crashed the entire page
    the moment that specific exercise got rotated into view — intermittent and
    hard to reproduce. Now: a bad reference falls back to a generic prescription
    instead of throwing, and a loud warning banner appears directly in the
    generated directive naming the exact problem, so a data-entry mistake is
    caught immediately instead of surfacing as a mystery crash later.
17. **Gender/pregnancy consistency check.** Setting Gender to Male while the
    Pregnancy restriction is checked previously generated a directive with
    correct pregnancy programming but a silently mismatched profile header, with
    no indication anything was off. Now flagged with a visible warning — the
    entered Gender value is never silently overridden, since this is real
    member-entry data, not randomized demo data.


 **The following data will be edited for clarity:
    - REMOVE - "Any component marked EXEMPT is not tested and is awarded maximum points for that component per current scoring rules — training still targets it        for the member's overall readiness, not for test score. Components marked MODALITY are still tested, just on the alternate exercise."
    - CHANGE - ACRONYM GLOSSAY to GLOSSARY
    - CHANGE - "OTHER STATUS to OTHER EXEMPTIONS"
    - CHANGE - Make PFRA Failure its own section 
    - CHANGE - Remove and Replace the "AUS Pursuit" Cardio exercise
    - CHANGE - Give more space for Supervisor and Assigned PFL Signatures / Align the spaces on top of one another "Supervisor over PFL". Add verbiage to show          supervisor acknowledges reciept of plan
    - POTENTIAL CHANGE - Ask for members baseline in fitness based on AFPT Testing "PU/SU/CARDIO", utilize scores to influenece amount of work needed per exercises
    - POTENTIAL ADDITION - Add signature space for member signature acknoledging reciept of plan
    - POTENTIAL ADDITION - References used in developing the tool
    - POTENTIAL ADDITION - Link external workout plans to specific plans such as "Gains Lab Document"
   
      
