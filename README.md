# Clinical Documentation Improvement

> Part of the [worlds-biggest-software-project](https://github.com/worlds-biggest-software-project) initiative.
>
> An open, AI-native Clinical Documentation Improvement (CDI) platform that surfaces documentation gaps as physicians write, not after discharge.

Clinical Documentation Improvement (CDI) is the discipline that ensures physician notes accurately capture patient complexity so that DRG assignment, claims reimbursement, and quality reporting reflect the care actually delivered. This project is for hospital CDI specialists, HIM coders, compliance officers, and the physicians they support — particularly at mid-market and smaller facilities currently priced out of enterprise CDI suites. It tackles the slow, retrospective, manual chart-review loop that drives undercoded complexity, claim denials, and compliance risk.

---

## Why Clinical Documentation Improvement?

- Hospitals with modern CDI programs have collectively recovered at least $1.5 million per facility in additional reimbursement, yet many mid-sized and smaller facilities still lack AI-assisted CDI tooling.
- Incumbents like Iodine (Waystar), Optum, and Solventum target large enterprise health systems with enterprise-only pricing and lengthy implementations, leaving the mid-market underserved.
- Service-heavy vendors such as AGS Health and Corrohealth bundle technology with offshore staffing contracts rather than offering self-service software.
- Real-time concurrent CDI — alerts that fire while physicians write, before note signature — is becoming the standard of care, shrinking query response times from five days to under 48 hours, but tools like Hiteks CAPD that deliver this are tied to specific EHR ecosystems.
- No significant open-source CDI platforms exist; AHIMA query templates are licensed/paywalled, and proprietary NLP engines (CognitiveML, LifeCode) lock customers into single vendors.

---

## Key Features

### Concurrent CDI and Alerting

- Real-time NLP analysis of in-progress clinical notes, flagging documentation gaps, conflicting diagnoses, and under-specified conditions
- CDI specialist worklist ranked by financial impact, discharge risk, and query age
- Evidence-marker pointing directly to the supporting or conflicting text in the chart
- Pre-signature CAPD alerts delivered inside the EHR note-writing workflow (v1.1)

### Physician Query Management

- Structured query creation using compliant, non-leading templates (AHIMA-aligned)
- Automated routing to the responsible physician's EHR inbox with response tracking
- Mobile-first physician query response with push notification and quick-response UI (v1.1)
- Automatic query activity tracking and audit logging — no manual CDI logging required

### DRG and Coding Intelligence

- Expected vs. assigned DRG comparison with estimated financial impact per case
- CC/MCC (Complication/Comorbidity) capture analysis
- ICD-10-CM/PCS and MS-DRG grouping built on CMS public grouper logic
- AI-assisted ICD/CPT code suggestions surfaced to coders from narrative text
- DRG forecasting from admission using available structured data (v1.1)

### Analytics and Compliance

- Dashboards for query volume, response rates, DRG shift rates, CC/MCC capture rate, and CMI trends
- Compliance and audit trail: query history, physician response logs, and coding rationale
- Role-based access for CDI specialist, HIM coder, physician, and compliance officer
- Clinical validation engine: cross-referencing diagnoses against labs, vitals, and imaging (v1.1)

### Integration

- FHIR R4 EHR integration with Epic and Oracle Health as primary targets, with Meditech support
- Bidirectional data exchange for note ingestion and alert delivery within EHR workflow
- HIPAA-compliant data architecture with BAA-aware PHI handling

---

## AI-Native Advantage

Unlike rule-based legacy CDI tools, this project applies clinical NLP trained on discharge summaries, progress notes, and operative reports — including clinical abbreviations and shorthand — to detect documentation gaps as notes are written rather than after discharge. AI augmentation extends beyond simple flagging: candidate capabilities include autonomous draft query generation, clinical validation that cross-references diagnoses against structured data (labs, vitals, imaging), and predictive denial risk scoring linked to documentation completeness before claim submission. Explainability is a first-class concern, addressing a gap noted across incumbent tools where AI suggestions lack sufficient reasoning for physician and compliance trust.

---

## Tech Stack & Deployment

The platform is designed around a clinical NLP pipeline, an ICD-10-CM/PCS and MS-DRG grouping engine built on CMS public grouper logic, and a FHIR R4 integration layer for Epic, Oracle Health (Cerner), and Meditech. ICD-10 code data is sourced from CMS public datasets. Deployment supports on-premise or private-cloud installations for health systems with strict data residency requirements, alongside a HIPAA-compliant managed option. Role-based access separates CDI specialist, HIM coder, physician, and compliance officer views.

---

## Market Context

CDI is a well-established hospital revenue-cycle category with documented per-facility reimbursement recovery of at least $1.5 million where modern programs are deployed (Iodine Software). Incumbents are predominantly enterprise SaaS with non-public contract pricing (Iodine/Waystar, Optum, Solventum 360 Encompass) or service-bundled models (AGS Health, Corrohealth); ambient-documentation adjacents such as Nuance DAX and Suki AI price per provider per month in the roughly $99–$300 range but do not address CDI specialist workflows. Primary buyers are hospital CDI directors, HIM leaders, and revenue cycle executives, with the strongest unmet need at mid-market and smaller facilities.

---

## Project Status

> This project is in the **research and specification phase**.  
> Contributions, feedback, and domain expertise are welcome.

---

## Contributing

We welcome contributions from developers, domain experts, and potential users.
See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Important:** All contributions must be your own original work or clearly attributed
open-source material with a compatible licence. Copyright infringement and licence
violations will not be tolerated and will result in immediate removal of the offending
contribution. If you are unsure whether a piece of code, text, or other material is
safe to contribute, open an issue and ask before submitting.

---

## Licence

Licence to be determined. See [discussion](#) for context.
