# VigilX — AI Case Analysis Prototype

VigilX is an interactive pharmacovigilance prototype that demonstrates how patient follow-up, healthcare-provider review, AI-assisted case analysis, and safety-team monitoring can work in one application.

## Live prototype

**[Open the VigilX prototype](https://kiruthiganesan2020-blip.github.io/VigilX--AI-case-Analysis/)**

The prototype runs entirely in the browser. No account or installation is required.

## Working flow

```text
Patient follow-up
      ↓
HCP reviews and submits a response
      ↓
VigilX analyzes the case and recommends priority
      ↓
Smart follow-up is generated
      ↓
PV team monitors cases on the dashboard
```

### 1. Patient Portal

1. Open **Patient Portal**.
2. Enter or update the supplied Case ID.
3. Type a medication name or select one from the A–Z tablet suggestions.
4. Select how the patient is feeling and enter any additional symptoms.
5. Choose **Next** to complete:
   - basic information;
   - medication details;
   - adverse-event timeline.
6. Finish the questionnaire to view the submitted case reference and medication.
7. English and Hindi language controls are available at the top of the page.

### 2. Healthcare Provider Portal

1. Open **HCP Portal**.
2. Review the medication, adverse event, patient reference, and priority.
3. Select a clinical assessment and add relevant notes.
4. Choose **Submit Response**.
5. The prototype confirms the response and automatically opens **AI Case Analysis**.

The second sample case also demonstrates the quick-resolution and detailed-response actions.

### 3. AI Case Analysis

The analysis view presents:

- case summary;
- AI priority recommendation;
- confidence score;
- reasons for the priority;
- missing information;
- suggested next action.

Choose **Generate Smart Follow-up** to simulate generation of a targeted follow-up request, or **Back to Case** to return to the HCP view.

### 4. Pharmacovigilance Dashboard

Open **PV Dashboard** to review:

- active cases and operational metrics;
- priority, status, and days open;
- follow-up, review, and escalation actions;
- simulated new-case, bulk-message, and report-export controls.

The in-browser VigilX follow-up engine recalculates sample case priorities from missing fields, seriousness, previous contact attempts, and case age. It also selects a suggested communication channel using regional rules.

Case data is shared across the prototype: an edited Case ID and medication are used by AI Case Analysis, prefilled by Smart Follow-up, and added to the generated dashboard table. Dashboard totals, response rate, average days open, overdue count, priorities, and actions are calculated from the current case records rather than fixed display values.

## AI prioritization logic

The prototype assigns a weighted score using:

| Signal | Effect |
|---|---|
| Missing information | Raises priority as missing fields increase |
| Event seriousness | Serious events receive the greatest weight |
| Previous attempts | Repeated unsuccessful outreach raises priority |
| Days since report | Older unresolved cases receive additional weight |

The score maps cases to **High**, **Medium**, or **Low** priority and recommends immediate manual outreach, combined automated/human follow-up, or automated follow-up.

## Run locally

Because the application is a self-contained static page, you can either open `index.html` directly or serve the folder with any static web server.

Example:

```bash
npx serve .
```

Then open the local URL shown in the terminal.

## Technology

- HTML5
- CSS3
- Vanilla JavaScript
- GitHub Pages
- GitHub Actions

## Prototype scope

This repository is a front-end demonstration using synthetic case data and simulated actions. It does not currently include authentication, a backend API, persistent storage, real patient data, a trained ML model, or production regulatory controls. It must not be used to make clinical or patient-safety decisions.

## Deployment

Every push to `main` automatically deploys through GitHub Pages.
