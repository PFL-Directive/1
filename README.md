# PFL Fitness Directive Builder

A single-page, no-backend tool for USAF Physical Fitness Leaders (PFLs) to generate
exemption-aware training directives.

Enter a generic member profile (gender, age, height, weight, documented restrictions,
and objective), and the tool generates a phased training plan — cardio, strength, core,
and mobility work for each day, with exercises, sets x reps, and recommended load —
that routes around whatever restrictions are checked (e.g. no-running, no upper-body
loading, no core flexion, pregnancy profile, lower-body/joint restriction).

## Live site

Once GitHub Pages is enabled for this repo (Settings → Pages → Deploy from branch →
`main` / root), it will be available at:

`https://<your-github-username>.github.io/<repo-name>/`

## What this is / isn't

- **Is:** a training-programming aid. Everything runs client-side in the browser —
  no data is stored, transmitted, or logged anywhere.
- **Isn't:** an official myFitness tool. It does not calculate PFA/HPA scores, and
  it does not replace guidance from a medical provider, HAWC, or UFPM. Component
  exemption logic is a simplified summary and should be verified against the
  current DAFMAN 36-2905 and the member's actual AF Form 469 before use.

## Usage

Open `index.html` in any browser — no build step, no dependencies, no server required.

## Privacy note

Do not enter names or other identifying information — this tool is designed for
generic/anonymized profiles only.
