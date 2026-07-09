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
4. Confirm or edit the medicine-specific adverse-event suggestion.
5. Select how the patient is feeling and enter any additional symptoms.
6. Choose **Next** to complete:
   - basic information;
   - medication details;
   - adverse-event timeline.
7. Finish the questionnaire to view the submitted case reference, medication, and adverse event.
8. English and Hindi language controls are available at the top of the page.

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

Choose **Generate Smart Follow-up** to create a visible, case-specific plan containing the medication, reported event, recommended channel, and targeted questions. From the generated plan you can:

- open a prefilled patient questionnaire;
- download the follow-up plan as a text file;
- return to the HCP case.

The patient confirmation screen also provides **Download Case Summary**, which downloads the current case details, workflow status, AI recommendation, and HCP assessment as a text file.

### 4. Pharmacovigilance Dashboard

Open **PV Dashboard** to review:

- active cases and operational metrics;
- priority, status, and days open;
- follow-up, review, and escalation actions;
- simulated new-case, bulk-message, and report-export controls.

The in-browser VigilX follow-up engine recalculates sample case priorities from missing fields, seriousness, previous contact attempts, and case age. It also selects a suggested communication channel using regional rules.

Case data is shared across the prototype and saved in the browser. A submitted patient case appears in the HCP Portal, the HCP assessment opens that same case in AI Case Analysis, Smart Follow-up prefills its details, and the dashboard is generated from those records. Dashboard totals, response rate, average days open, overdue count, priorities, and actions are calculated rather than fixed display values.

Use **Submit Another Patient Case** after confirmation, or **New Case** on the dashboard, to start a fresh patient workflow. No unrelated preset patient records are added to the HCP Portal or dashboard.

## AI prioritization logic

The prototype assigns a weighted score using:

| Signal | Effect |
|---|---|
| Missing information | Raises priority as missing fields increase |
| Event seriousness | Serious events receive the greatest weight |
| Previous attempts | Repeated unsuccessful outreach raises priority |
| Days since report | Older unresolved cases receive additional weight |

The score maps cases to **High**, **Medium**, or **Low** priority and recommends immediate manual outreach, combined automated/human follow-up, or automated follow-up.

### Example high-priority cases to test

Use these examples in the Patient Portal to see the AI Case Analysis and Dashboard show **High Priority** instead of Low:

| Medication name | Reported adverse event | Expected priority |
|---|---|---|
| Warfarin | Unusual bleeding | High |
| Xarelto (Rivaroxaban) | Gastrointestinal bleeding | High |
| Aspirin 75mg | Hospitalization due to bleeding | High |
| Insulin | Loss of consciousness | High |
| Ibuprofen | Shortness of breath | High |

Mild events such as `Cetirizine + Drowsiness` or `Zinc sulfate + Nausea` intentionally remain lower priority so the dashboard demonstrates different triage levels.

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

This repository is a front-end demonstration using browser-local case data. It does not currently include authentication, a backend API, shared server storage, real patient data, a trained ML model, or production regulatory controls. It must not be used to make clinical or patient-safety decisions.

## Deployment

Every push to `main` automatically deploys through GitHub Pages.
