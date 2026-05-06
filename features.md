# Clinical Documentation Improvement — Feature & Functionality Survey

> Candidate #367 · Researched: 2026-05-06

## Solutions Analysed

| Tool | Type | Licence / Model | URL |
|------|------|-----------------|-----|
| Iodine AwareCDI (now Waystar CDI) | Concurrent & retrospective CDI | Commercial SaaS (enterprise) | https://www.waystar.com/our-platform/clinical-integrity-revenue-capture/clinical-documentation-integrity/ |
| Hiteks CAPD360 | Computer-assisted physician documentation | Commercial SaaS | https://hiteks.com/ |
| AGS Health ACDI | Computer-assisted CDI | Commercial SaaS + managed services | https://www.agshealth.com/ai-platform/computer-assisted-cdi/ |
| Solventum (3M) 360 Encompass | Integrated CAC + CDI | Commercial (perpetual + SaaS) | https://www.3m.com/3M/en_US/health-information-systems-us/clinical-documentation-integrity/ |
| Optum CDI / Enterprise CAC | CAC + CDI unified platform | Commercial SaaS (enterprise) | https://www.optum.com/en/business/providers/health-systems/revenue-cycle-performance/coding-documentation/coding-cdi-technology.html |
| Dolbey Fusion CDI | CDI alerts + CAC | Commercial SaaS | https://www.dolbey.com/solutions/coding/fusion-cdi/ |
| Nuance / Microsoft Dragon Copilot | Ambient documentation + coding | Commercial SaaS (per-provider) | https://www.nuance.com/healthcare/dragon-ai-clinical-solutions/dax-copilot.html |
| Suki AI | Ambient documentation + coding + clinical Q&A | Commercial SaaS (per-provider) | https://www.suki.ai/ |
| Artifact Health (acquired by Iodine) | Mobile-first physician query management | Commercial SaaS | https://www.artifacthealth.com/ |

---

## Feature Analysis by Solution

### Iodine AwareCDI (Waystar CDI)

**Core features**
- Concurrent CDI: AI-prioritised worklist of in-progress charts with documentation gaps
- Retrospective CDI (Retrospect module): post-discharge reconciliation queue to capture remaining revenue before billing
- DRG Forecast module: real-time predicted final DRG from admission, used by case managers and finance
- Intelligence module: pre-populated AI-generated physician query drafts (CognitiveML / Cognitive Emulation)
- Risk-adjusted analytics and CMI (case mix index) trend reporting

**Differentiating features**
- CognitiveML engine that emulates clinical expert reasoning, not just rule-based NLP
- Four tightly integrated modules spanning concurrent, retrospective, forecast, and query intelligence
- Deep Waystar revenue cycle platform integration post-acquisition (prior auth, denials, coding in one ecosystem)

**UX patterns**
- Specialist worklist with priority scoring by financial impact and query age
- Dashboard analytics surfaced to CDI leads and revenue cycle directors
- Physician query routing with tracked response workflow

**Integration points**
- FHIR R4-based EHR ingestion (Epic, Oracle Health, Meditech)
- Availity partnership for mid-revenue cycle data exchange

**Known gaps**
- Users reported decreased support quality and proactive guidance following Waystar acquisition
- Some users feel "nickel-and-dimed" for upgrades and fixes
- Weak standalone reporting for physician query compliance metrics (identified in KLAS reviews)

**Licence / IP notes**
- Commercial proprietary; CognitiveML is a patented / trade-secret AI engine
- Enterprise contracts; pricing not publicly disclosed

---

### Hiteks CAPD360

**Core features**
- Real-time CAPD alerts delivered inside the EHR as physicians write notes (pre-save/pre-sign)
- Clinical Decision Support (CDS) triggers at order signing and chart opening — not just note-writing
- NoteReader CDI integration within Epic for embedded physician workflow alerts
- Medical necessity knowledge base for identifying diagnoses lacking justification
- Symptom-combination logic flagging missing stated diagnoses

**Differentiating features**
- Only solution directly powering Epic NoteReader CDI workflows with real-time, pre-signature alerts
- Alerts fire before the note is signed — earlier than any other reviewed tool
- Reduces alert fatigue through specificity-aware false-positive filtering
- Provider-to-provider real-time communication channel

**UX patterns**
- In-workflow alerts embedded in EHR UI (no context switch for physician)
- Query response designed for minimal interaction (physicians respond within the EHR)
- Physician reputation/engagement scoring dashboard (CAPD360)

**Integration points**
- Deep Epic NoteReader CDI integration (certified)
- Supports Oracle Health and other EHRs for CDS hook triggers

**Known gaps**
- Limited standalone query management and reporting outside Epic
- Less prominent outside Epic-centric health systems
- Physician engagement analytics are vendor-reported, limited third-party benchmarks

**Licence / IP notes**
- Commercial proprietary SaaS
- CAPD360 Insight named product; no open-source components disclosed

---

### AGS Health ACDI

**Core features**
- Automated chart analysis with NLP to suggest CDI queries before coding
- Unified collaboration platform for CDI, coding, HIM, and clinical teams
- Real-time quality measure alerts for HACs (Hospital-Acquired Conditions), readmissions, and PSIs
- Intelligent audit worklist (pre-bill and retrospective)
- Real-time EHR note synchronisation for parallel physician/CDIS workflows

**Differentiating features**
- Tight coupling of CDI and CAC (computer-assisted coding) on one platform
- Automated audit suggestions comparing predicted coding to final coding
- Strong offshore CDI staffing complement alongside software (full-service model)

**UX patterns**
- Unified single-pane-of-glass interface for CDI specialist, coder, and auditor roles
- Charts prioritised by suggested query opportunity before coding queues
- Case-search and sampling tools for compliance audit workflows

**Integration points**
- EHR integration via APIs; real-time note synchronisation
- CAC and CDI unified data model

**Known gaps**
- Heavy dependency on AGS managed services — less self-service analytics for lean in-house teams
- Limited publicly documented standalone SaaS pricing model
- AI documentation depth is thinner than Iodine/Solventum for pure concurrent CDI

**Licence / IP notes**
- Commercial proprietary; NLP engine is proprietary
- Service-heavy model; technology is bundled with staffing contracts

---

### Solventum (3M) 360 Encompass

**Core features**
- NLU-based automatic CPT and ICD-10-CM code suggestion from narrative text
- DRGfinder: real-time MS-DRG grouping with MCC/CC identification
- Advanced Analyzer: specificity prompting and frequently-missed-code surfacing
- Reimbursement calculation using national and hospital-specific variables
- Outpatient CDI solution for risk and quality opportunity identification

**Differentiating features**
- Decades of ICD/DRG expertise; industry-leading code crosswalk databases
- Expert-guided AI: explains the logic behind each code suggestion (explainability)
- APR-DRG support (severity of illness, risk of mortality) in addition to MS-DRG
- Regulatory update cadence tied to CMS annual code releases

**UX patterns**
- Coder-centric UI: code suggestions presented with supporting text evidence highlighted
- Advanced Analyzer surfaces missed codes as side-panel suggestions during coding review
- Reimbursement calculator embedded in coding workflow

**Integration points**
- Integration with major EHRs and HIS systems via HL7 and proprietary feeds
- Third-party coding workflow systems can consume 3M grouper APIs

**Known gaps**
- Legacy architecture in some modules; modern UI/UX criticized by users vs. newer SaaS-native tools
- Concurrent CDI alerting less sophisticated than Hiteks/Iodine for real-time physician alerts
- Perpetual license model creates slower upgrade cycles for some clients

**Licence / IP notes**
- Commercial proprietary (Solventum, spun off from 3M in 2024)
- Some grouper logic licensed to third-party vendors

---

### Optum CDI / Enterprise CAC

**Core features**
- LifeCode NLP engine (Clinical Language Intelligence) for automated code suggestion
- CDI 3D: unified CAC, CDI, and auditing on a single shared platform
- HCC (Hierarchical Condition Category) and QPP (Quality Payment Program) code-level icons
- Medication list cross-reference for condition-medication documentation alignment
- Supporting evidence analysis (labs, vitals) to identify documentation weaknesses

**Differentiating features**
- HCC/QPP icon coding aids — rare feature supporting value-based care coding accuracy
- Single platform unifying CAC + CDI + audit roles without data silos
- Clinical validation: flags diagnoses that lack supporting clinical evidence (not just specificity)
- Rich reference library: CDI Desk Reference, Clinical Validation Guide, ICD-10-CM Improvement Training

**UX patterns**
- Unified interface for coders, CDI specialists, and auditors
- Code-level icons for quality/risk programs embedded in coding UI
- Medication cross-reference available inline during chart review

**Integration points**
- FHIR and HL7 integrations with major EHRs
- Enterprise scalability for large health systems and IDNs

**Known gaps**
- Primarily targets large enterprise health systems; not well-suited for mid-market
- Less emphasis on real-time physician-facing CAPD alerting
- Optum/UnitedHealth parent creates perceived conflict-of-interest for some health systems

**Licence / IP notes**
- Commercial proprietary; LifeCode NLP is patented
- Enterprise contract pricing; not publicly listed

---

### Dolbey Fusion CDI

**Core features**
- CDI Alerts: flags clinical findings without a diagnosis, diagnoses without clinical support, lacking specificity, or conflicting diagnoses
- Physician query module: shared query creation, routing, notification, and tracking for all users
- Worklist prioritisation: charts ranked by CDI alert opportunity
- Real-time reporting on CDI alert effectiveness and query outcomes
- Integration with Fusion CAC for combined CDI + coding workflow

**Differentiating features**
- Seven consecutive years as KLAS market leader in CAC (2023)
- Proprietary CDI Alerts technology with evidence-marker pointing directly to the supporting/conflicting text
- Shared query module across CDI, coding, and HIM roles (no siloed query tools per team)

**UX patterns**
- Worklist-driven CDI specialist workflow with alert priority scoring
- Evidence text highlighted directly in document to reduce chart navigation time
- Query response tracked in unified dashboard with trending reports

**Integration points**
- EHR integration via HL7 and FHIR
- Fusion CAC + Fusion CDI combined platform (unified data model)
- Bi-directional query routing to physician EHR inbox

**Known gaps**
- Less sophisticated AI compared to Iodine/Optum for predictive DRG forecasting
- Primarily inpatient; outpatient CDI capabilities are limited
- Physician-facing CAPD (real-time note alerts) less developed than Hiteks

**Licence / IP notes**
- Commercial proprietary SaaS
- No open-source components disclosed

---

### Nuance / Microsoft Dragon Copilot (DAX)

**Core features**
- Ambient listening: captures full patient-clinician conversation; generates structured clinical note automatically
- Specialty-specific note templates (100+ specialties)
- ICD-10, CPT, HCC, and E/M code generation from ambient conversation
- Quality review step before note delivery to EHR for physician signature
- Referral letters, after-visit summaries, and clinical evidence summaries generated without extra work

**Differentiating features**
- Truly ambient — no active dictation required; microphone on during encounter
- AI learning loop: adapts to each clinician's documentation style over time
- Saves up to 7 minutes per encounter; 50% reduction in documentation time (published study)
- Microsoft Teams integration for telehealth consult documentation

**UX patterns**
- Clinician-facing mobile app or embedded EHR widget during encounter
- Brief quality review UX before EHR note submission
- Minimal physician interaction — documentation is generated, not dictated

**Integration points**
- Deep integrations with Epic, Oracle Health, athenahealth, MEDITECH
- Azure cloud infrastructure (Microsoft ecosystem)
- API/SDK available for health system customisation (Nuance Healthcare API)

**Known gaps**
- Focused on note generation, not CDI specialist workflows or query management
- No physician query management or CDI specialist worklist
- DRG optimisation and CC/MCC capture analysis not a primary feature
- Ambient mode requires encounter presence — retrospective documentation not supported

**Licence / IP notes**
- Commercial SaaS; per-provider monthly subscription (~$99–$300/provider/month range)
- Proprietary Microsoft/Nuance models; no open-source components

---

### Suki AI

**Core features**
- Ambient documentation: conversation-to-note generation across 100+ specialties
- ICD-10, HCC, CPT, and E/M code generation for both EHR-integrated and non-integrated deployments
- Clinical Q&A: AI answers clinician questions about the patient using chart context
- Bi-directional EHR integration: pulls vitals, labs, allergies; writes finalized notes back
- Available for integrated and non-integrated EHR environments (broader reach than DAX)

**Differentiating features**
- First ambient AI with enhanced ambient integration across multiple EHR systems simultaneously
- First to integrate ambient AI with MEDITECH Expanse Document APIs
- Combined documentation + coding + clinical reasoning + Q&A in one tool (widest scope)
- Works without deep EHR integration (non-integrated mode) expanding access to smaller practices

**UX patterns**
- Mobile app + EHR widget; designed for low-friction adoption
- Single solution for documentation, coding, and clinical intelligence
- Provider-facing AI assistant feel vs. CDI-team-facing specialist tool

**Integration points**
- Epic, Oracle Health, athenahealth, MEDITECH (deep integrations)
- Non-integrated mode via FHIR export or direct file upload

**Known gaps**
- Like DAX, focused on physician productivity — not CDI specialist workflow management
- No query management, CDI specialist worklist, or DRG forecasting
- CDI team adoption and CDI analytics not primary use cases
- Less mature for inpatient CDI vs. outpatient/ambulatory documentation

**Licence / IP notes**
- Commercial SaaS; per-provider subscription pricing
- Proprietary AI models; no open-source components

---

### Artifact Health (acquired by Iodine / Waystar)

**Core features**
- Mobile-first physician query platform: physicians respond to CDI queries on smartphones (3 taps)
- AHIMA-compliant query template library (standardised, non-leading query formats)
- Automatic query activity tracking and real-time dashboards (eliminates manual CDI logging)
- HIPAA-compliant cloud-based platform
- Bi-directional EHR integration for query routing and response recording

**Differentiating features**
- Only mobile-native physician query engagement platform (reduces response friction to seconds)
- 20x faster physician query response times vs. manual fax/paper processes
- AHIMA partnership providing continuously maintained standardised query templates
- Query activity automatically tracked — no manual CDI logging required

**UX patterns**
- Smartphone-first: push notification → query view → 3-tap response
- CDI specialist dashboard with auto-populated query metrics and response rates
- Real-time dashboards replacing manual Excel tracking

**Integration points**
- All major EHR systems (Epic, Oracle Health, Meditech, Cerner)
- Now embedded within Iodine AwareCDI (Intelligence module)

**Known gaps**
- Standalone product absorbed into Iodine/Waystar; no longer available independently
- Did not include concurrent CDI worklist or DRG analytics (query management only)
- Physician query templates require AHIMA licence for full library

**Licence / IP notes**
- Acquired by Iodine Software (2021); now part of Waystar CDI
- AHIMA query templates are licensed content

---

## Cross-Cutting Feature Themes

### Table-Stakes Features
- AI-assisted chart review with NLP to flag documentation gaps (missing diagnoses, lacking specificity, conflicting entries)
- Physician query creation, routing, and response tracking
- CDI specialist worklist with priority scoring (financial impact, query age, discharge risk)
- ICD-10-CM/PCS and MS-DRG grouping with CC/MCC capture analysis
- EHR integration (Epic, Oracle Health, Meditech at minimum)
- Analytics dashboard: query volume, response rates, DRG shift rates, CMI trends
- HIPAA-compliant data handling with audit trails

### Differentiating Features
- Real-time CAPD alerts delivered inside the physician's EHR note-writing workflow (pre-signature)
- Ambient listening: automatic note generation from provider-patient conversation
- DRG forecasting from admission (predicting final DRG before discharge)
- Mobile-first physician query response (3-tap response on smartphone)
- HCC/QPP flag icons at the code level for value-based care accuracy
- Clinical validation: flagging diagnoses that lack supporting clinical evidence (not just specificity gaps)
- AI learning loops that adapt to individual clinician documentation style

### Underserved Areas / Opportunities
- Small-to-mid-market hospitals and independent physician practices lack affordable CDI tooling — most solutions target large enterprise health systems
- Outpatient and ambulatory CDI is significantly less mature than inpatient CDI across all tools reviewed
- Explainability of AI suggestions: most tools provide recommendations without sufficient reasoning for physician and compliance trust
- Integrated CDI + physician burnout tracking — documentation burden metrics tied to provider wellness data
- Cross-facility benchmarking: most analytics are intra-facility; peer-group benchmarking is rare
- Open-source or open-standards query template libraries: AHIMA templates are licensed/paywalled
- Real-time denial prediction linked to CDI gaps before claim submission
- Autonomous query drafting with full physician approval workflow (most tools still require significant CDI specialist involvement)

### AI-Augmentation Candidates
- Concurrent note analysis to suggest query language automatically (moving beyond flag → generate draft query)
- Ambient conversation analysis for inpatient CDI (extending ambient AI from outpatient to inpatient rounding)
- Clinical validation using structured data (labs, vitals, imaging results) cross-referenced against documentation — largely manual today
- Predictive denial risk scoring linked to documentation completeness before discharge
- Physician query response classification: auto-categorising physician responses to update DRG immediately without coder review

---

## Legal & IP Summary

The CDI software market is dominated by proprietary commercial vendors. Key IP concerns include: Iodine/Waystar's CognitiveML (trade secret/patented AI engine), Optum's patented LifeCode NLP, and Solventum's proprietary DRG grouper logic (though grouper APIs are licensed to third parties). AHIMA query templates are licensed content and cannot be freely reproduced. No significant open-source CDI platforms were identified in this survey. An open-source AI-native CDI tool would need to build its own NLP models or leverage open LLM APIs, and would need to source ICD-10 code data from CMS public datasets (freely available). There are no known patent blockers on the core CDI workflow (worklist, query management, analytics) provided the NLP approach is independently developed.

---

## Recommended Feature Scope

**Must-have (MVP)**
- Concurrent CDI worklist: NLP-powered chart review flagging documentation gaps (missing specificity, conflicting diagnoses, missing CC/MCC capture) with priority scoring
- Physician query management: compliant query drafting (AHIMA-aligned templates), routing to physician EHR inbox, response tracking, and automatic audit logging
- DRG impact analysis: expected vs. assigned DRG comparison with estimated financial impact per case
- ICD-10-CM/PCS and MS-DRG grouping engine (built on CMS public grouper logic)
- FHIR R4 EHR integration (Epic and Oracle Health as primary targets)
- Role-based access: CDI specialist, HIM coder, and compliance officer views
- Analytics dashboard: query volume, response rates, CC/MCC capture rate, CMI trend

**Should-have (v1.1)**
- Real-time CAPD physician alerts delivered inside the EHR during note writing (pre-signature)
- DRG forecasting from admission using available structured data
- Mobile-first physician query response (push notification + quick-response UI)
- Clinical validation engine: cross-referencing diagnoses against structured data (labs, vitals)
- Outpatient/ambulatory CDI queue for HCC capture and quality measure documentation
- Denial prediction scoring linked to documentation gaps before claim submission

**Nice-to-have (backlog)**
- Ambient conversation capture for CDI (inpatient rounding documentation)
- Cross-facility benchmarking with peer-group CMI and query response rate comparisons
- AI-generated physician query drafts (full query text, not just flag)
- Automated physician query response classification for immediate DRG update
- Physician engagement and burnout metrics dashboard
- Open query template library (Creative Commons or equivalent, AHIMA-aligned)
