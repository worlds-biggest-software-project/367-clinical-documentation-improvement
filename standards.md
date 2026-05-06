# Standards & API Reference

> Project: Clinical Documentation Improvement · Generated: 2026-05-06

---

## Industry Standards & Specifications

### HL7 & FHIR Standards

**HL7 FHIR R4 (Fast Healthcare Interoperability Resources, Release 4)**
- Official URL: https://www.hl7.org/fhir/R4/
- The foundational standard for healthcare data exchange. A CDI platform must ingest clinical notes, diagnosis codes, lab results, and encounter data via FHIR R4 resources (DocumentReference, Condition, DiagnosticReport, Encounter, Patient). The ONC Cures Act Final Rule mandates FHIR R4 as the required API standard for EHR certification. All new EHR integrations should target FHIR R4 exclusively — DSTU-2 APIs are being retired by Oracle Health/Cerner in 2025.

**HL7 Clinical Document Architecture Release 2 (CDA R2 / C-CDA)**
- Official URL: https://www.hl7.org/implement/standards/product_brief.cfm?product_id=7
- XML-based standard for clinical document exchange (discharge summaries, operative reports, progress notes). Many EHRs export clinical documents as C-CDA (Consolidated CDA) bundles. A CDI NLP pipeline must be able to parse C-CDA XML in addition to raw narrative text. FHIR DocumentReference resources frequently wrap C-CDA documents.

**HL7 v2.x (Messaging Standard)**
- Official URL: https://www.hl7.org/implement/standards/product_brief.cfm?product_id=185
- Legacy message-based standard still in widespread use for ADT (Admission-Discharge-Transfer) feeds, order messages, and results. CDI platforms integrating with older EHR configurations will receive HL7 v2 ADT messages (A01, A03, A08) and ORU lab result messages. The DRG segment (DRG) in HL7 v2.6+ carries assigned DRG information.

**SMART on FHIR v2 (App Launch Framework)**
- Official URL: https://build.fhir.org/ig/HL7/smart-app-launch/
- Standard for EHR-embedded app authorization using OAuth 2.0 + OpenID Connect. CDI alerts delivered inside an EHR (e.g., Epic NoteReader) require the application to launch via SMART on FHIR, receive patient/encounter context, and use scopes (e.g., `user/DocumentReference.rs`, `user/Condition.rs`) to access chart data without re-authentication.

**United States Core Data for Interoperability (USCDI)**
- Official URL: https://www.healthit.gov/isa/united-states-core-data-interoperability-uscdi
- ONC-defined minimum data set that EHRs must expose via FHIR APIs. Relevant USCDI elements for CDI include: Problems/Conditions, Encounter Information, Clinical Notes (discharge summaries, progress notes, consultation notes), Diagnoses, and Procedures. USCDI v3+ is the current baseline required by the ONC Cures Act Final Rule.

---

### ISO Standards

**ISO 27799:2025 — Health Informatics: Information Security Controls**
- Official URL: https://www.iso.org/standard/84647.html
- Healthcare-specific extension of ISO/IEC 27002. Provides implementation guidance for protecting PHI (Protected Health Information) in health software systems. A CDI SaaS platform handling patient notes and diagnosis data must align with ISO 27799 controls, including access control, audit logging, encryption at rest and in transit, and incident response.

**ISO 27789:2021 — Health Informatics: Audit Trails for Electronic Health Records**
- Official URL: https://cdn.standards.iteh.ai/samples/75313/5ff648d7c6e047a1bb4c9a119a13345e/ISO-27789-2021.pdf
- Specifies the minimum set of audit trail entries for EHR systems, including read/write access to patient records. CDI platforms that access, query, and annotate patient records must maintain HIPAA-compliant audit trails; ISO 27789 provides a reference model for what those trails should capture.

**ISO 13606 — Electronic Health Record Communication**
- Reference: https://www.researchgate.net/publication/270014952_The_ISOEN_13606_Standard_for_the_Interoperable_Exchange_of_Electronic_Health_Records
- Standard for the interoperable exchange of EHR data. Relevant when CDI platforms need to interoperate with EHR systems in international markets (Europe, Australia) that implement ISO 13606 rather than HL7 FHIR.

---

### Coding & Classification Standards

**ICD-10-CM / ICD-10-PCS (International Classification of Diseases, 10th Revision)**
- Official source: https://www.cms.gov/medicare/coding-billing/icd-10-codes
- The primary diagnosis and procedure classification system used in the United States for inpatient billing, DRG assignment, and quality reporting. A CDI platform's NLP engine must map clinical concepts to ICD-10-CM (diagnoses) and ICD-10-PCS (inpatient procedures) codes. CMS publishes annual code updates (effective October 1) with full ICD-10 tabular and index files available for free download.

**MS-DRG (Medicare Severity Diagnosis-Related Groups) — CMS Grouper**
- Official URL: https://www.cms.gov/medicare/payment/prospective-payment-systems/acute-inpatient-pps/ms-drg-classifications-and-software
- CMS provides the official MS-DRG Grouper software (Java source + binaries) free of charge under FOIA. The grouper takes principal diagnosis, secondary diagnoses (with CC/MCC flags), procedures, patient age, sex, and discharge status and assigns an MS-DRG with its relative payment weight. A CDI platform's DRG impact analysis module should embed or interface with the CMS grouper logic.

**CPT (Current Procedural Terminology)**
- Official source: https://www.ama-assn.org/practice-management/cpt
- AMA-maintained procedure code set used for outpatient/physician services. CDI platforms that support outpatient or ambulatory CDI must reference CPT codes. Note: CPT is a licensed/copyrighted code set; use requires an AMA licence.

**SNOMED CT (Systematized Nomenclature of Medicine – Clinical Terms)**
- Official URL: https://www.nlm.nih.gov/healthit/snomedct/index.html
- The most comprehensive clinical terminology system, mapping clinical concepts to structured codes. FHIR Condition and DiagnosticReport resources use SNOMED CT as the preferred terminology for problem/diagnosis coding. A CDI NLP pipeline can use SNOMED CT for clinical concept extraction and mapping, bridging free-text mentions to structured terminology before ICD-10 encoding. Available at no cost in the US via the NLM.

**LOINC (Logical Observation Identifiers Names and Codes)**
- Official URL: https://loinc.org/
- Standard vocabulary for clinical observations, lab tests, and clinical document section headers. FHIR DocumentReference and Observation resources use LOINC codes to classify note types (e.g., 11488-4 = Consultation Note; 18842-5 = Discharge Summary). CDI NLP models should use LOINC note-type codes to route documents to appropriate analysis pipelines. Freely available under the LOINC licence.

**RxNorm**
- Official URL: https://www.nlm.nih.gov/research/umls/rxnorm/
- NLM-maintained drug terminology used in FHIR MedicationRequest and MedicationStatement resources. CDI clinical validation logic cross-referencing documentation against prescribed medications requires RxNorm lookups. Freely available.

---

### Regulatory & Compliance Frameworks

**HIPAA (Health Insurance Portability and Accountability Act) — Privacy & Security Rules**
- Official URL: https://www.hhs.gov/hipaa/
- US federal law governing PHI handling. A CDI SaaS platform is a Business Associate under HIPAA; it must execute BAAs with all covered entity clients, implement AES-256 encryption at rest and TLS 1.2/1.3 in transit, enforce RBAC with least-privilege access, log all PHI access, and support HIPAA breach notification procedures. Violations carry fines up to $2.13M per category per year.

**ONC 21st Century Cures Act Final Rule (Interoperability & Information Blocking)**
- Official URL: https://www.healthit.gov/topic/oncs-cures-act-final-rule
- Mandates FHIR R4 API access to patient data and prohibits information blocking by EHR vendors. This rule creates the legal framework that requires Epic, Oracle Health, and others to provide FHIR R4 APIs — directly enabling CDI platform integrations. A CDI platform consuming EHR data via these mandated APIs must comply with the rule's data use and privacy requirements.

**CMS Interoperability and Patient Access Final Rule (CMS-9115-F)**
- Official URL: https://www.cms.gov/priorities/burden-reduction/overview/interoperability/policies-regulations/cms-interoperability-patient-access-final-rule-cms-9115-f
- Companion rule to the ONC Cures Act rule, applying to CMS-regulated payers. Establishes FHIR-based payer APIs that CDI platforms may eventually leverage for prior authorisation data and claims history to enrich CDI analysis.

**AHIMA-ACDIS Guidelines for Achieving a Compliant Query Practice (2022, updated 2026)**
- Official URL: https://www.ahima.org/landing-pages/ahima-acdis-guidelines-for-achieving-a-compliant-query-practice/
- The de facto industry standard for compliant physician query construction. Defines requirements for non-leading queries, valid query types (yes/no, multiple choice, open-ended), mandatory "unable to determine" options, and documentation standards. Any CDI platform generating or templating physician queries must comply with these guidelines. A 2026 update is in final comment phase.

**AHIMA Ethical Standards for CDI Professionals (2020)**
- Official URL: https://www.ahima.org/media/r2gmhlop/ethical-standards-for-clinical-documentation-integrity-cdi-professionals-2020.pdf
- Ethical framework governing CDI practice including query neutrality, clinical validity requirements, and prohibition on leading queries that inflate severity. Software-generated query suggestions must be validated against these ethical guidelines.

---

### Security & Authentication Standards

**OAuth 2.0 (RFC 6749) and OpenID Connect**
- OAuth 2.0: https://datatracker.ietf.org/doc/html/rfc6749
- OpenID Connect: https://openid.net/developers/how-connect-works/
- SMART on FHIR uses OAuth 2.0 for authorization and OpenID Connect for identity. All CDI platform API access to EHR data uses these standards. Backend service access (CDI engine to EHR, no user present) uses the OAuth 2.0 Client Credentials grant with SMART Backend Services.

**TLS 1.2 / 1.3 (RFC 5246 / RFC 8446)**
- All PHI in transit must be encrypted with TLS 1.2 minimum; TLS 1.3 preferred. HIPAA compliance and NIST FIPS SP 140-2 guidance require strong cipher suites. This applies to EHR-to-CDI API calls, CDI-to-physician query routing, and any CDI analytics data exports.

**NIST SP 800-53 (Security and Privacy Controls for Federal Information Systems)**
- Official URL: https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final
- Reference framework for healthcare security controls. Relevant control families for CDI platforms: AC (Access Control), AU (Audit and Accountability), SC (System and Communications Protection), and SI (System and Information Integrity).

---

## Similar Products — Developer Documentation & APIs

### Epic on FHIR

- **Description:** Epic's public FHIR R4 API platform enabling third-party apps to access clinical notes, diagnoses, encounters, and medications from any Epic installation worldwide. CDI platforms use the DocumentReference and Condition APIs to ingest notes and structured diagnoses.
- **API Documentation:** https://fhir.epic.com/Documentation
- **Specifications:** https://fhir.epic.com/Specifications
- **Open Platform:** https://open.epic.com/
- **Vendor Services Portal:** https://vendorservices.epic.com/OpenEpicApis
- **Clinical Notes API:** https://fhir.epic.com/Specifications?api=1048 (DocumentReference.Search)
- **Standards:** HL7 FHIR R4, SMART on FHIR v2, USCDI
- **Authentication:** SMART on FHIR (OAuth 2.0 + OpenID Connect); Backend Services for server-to-server

---

### Oracle Health (Cerner) / Millennium Platform APIs

- **Description:** Oracle Health's FHIR R4 API suite for the Millennium EHR platform (formerly Cerner). Provides access to clinical documents, patient demographics, encounters, and structured clinical data. Required integration target for any CDI platform deployed at Oracle Health/Cerner sites.
- **API Documentation:** https://docs.oracle.com/en/industries/health/millennium-platform-apis/mfrap/r4_overview.html
- **FHIR API Documentation (Ignite):** https://fhir.cerner.com/
- **GitHub Repository:** https://github.com/cerner/fhir.cerner.com
- **Developer Program:** https://www.oracle.com/health/developer/api/
- **Standards:** HL7 FHIR R4 (DSTU-2 being retired 2025), SMART on FHIR v2
- **Authentication:** SMART on FHIR (OAuth 2.0); system accounts for backend CDI integrations

---

### Waystar CDI (formerly Iodine AwareCDI)

- **Description:** Enterprise CDI platform with concurrent review, retrospective reconciliation, DRG forecasting, and AI-generated physician query drafts. Now part of Waystar's revenue cycle platform after the 2025 acquisition.
- **Product Page:** https://www.waystar.com/our-platform/clinical-integrity-revenue-capture/clinical-documentation-integrity/
- **Developer Portal:** https://developer.patientco.com/ui/ (requires registration)
- **Integration Guide:** https://tateeda.com/blog/integrate-waystar-with-custom-healthcare-applications
- **Standards:** X12 (claims), HL7 FHIR R4 (clinical data ingestion), HL7 v2 (legacy feeds)
- **Authentication:** API key + OAuth 2.0 for REST APIs; HL7 FHIR for clinical data

---

### Hiteks CAPD360

- **Description:** CAPD (Computer-Assisted Physician Documentation) platform delivering real-time CDI alerts inside Epic NoteReader during note writing. The only third-party solution powering Epic NoteReader CDI workflows with pre-signature alerts.
- **Product Page:** https://hiteks.com/capd360/
- **Epic NoteReader CDI integration announcement:** https://hiteks.com/hiteks-and-rush-university-medical-center-implement-concurdi-for-epics-notereader-cdi-to-enhance-physician-and-cdi-and-quality-workflow/
- **Standards:** Epic NoteReader CDI API (proprietary Epic extension); HL7 FHIR R4; CDS Hooks for clinical decision support triggers
- **Authentication:** SMART on FHIR (Epic-hosted); Epic App Orchard certification required

---

### Solventum (3M) 360 Encompass

- **Description:** Integrated CAC + CDI platform with ICD-10 code suggestion, MS-DRG grouping, CC/MCC analysis, and outpatient CDI. Historically the market reference for grouper logic; grouper APIs are licensed to third parties.
- **Product Page:** https://www.solventum.com/en-us/home/health-information-systems/platforms/solventum-360-encompass-system/
- **Partner/API Overview:** https://www.3m.com/3M/en_US/company-us/partners-suppliers/api/
- **Standards:** HL7 FHIR R4; HL7 v2; CMS ICD-10-CM/PCS grouper logic (licensed)
- **Authentication:** Partner/enterprise agreements required; no public API

---

### CMS MS-DRG Grouper (Free Public Software)

- **Description:** The official US government MS-DRG Grouper — Java source code and binaries provided free by CMS under FOIA. Assigns MS-DRGs based on ICD-10-CM/PCS codes, patient demographics, and discharge status. An open-source CDI tool can embed this grouper directly.
- **Download Page:** https://www.cms.gov/medicare/payment/prospective-payment-systems/acute-inpatient-pps/ms-drg-classifications-and-software
- **ICD-10-CM/PCS Definitions Manual (v39):** https://www.cms.gov/icd10m/version39-fullcode-cms/fullcode_cms/P0001.html
- **Standards:** ICD-10-CM/ICD-10-PCS; CMS IPPS payment rules
- **Licence:** Public domain (US government work); no licence restrictions

---

### Suki AI (Developer API)

- **Description:** Ambient clinical documentation and coding platform with a developer API for embedding ambient note generation and ICD-10/HCC/CPT coding into third-party health applications. Supports integrated and non-integrated EHR deployments.
- **Developer Documentation:** https://developer.suki.ai/documentation/ambient-documentation
- **Product Page:** https://www.suki.ai/
- **Standards:** HL7 FHIR R4 for EHR write-back; REST/JSON API for developer integration
- **Authentication:** API key + OAuth 2.0

---

### Nuance / Microsoft Dragon Copilot (Healthcare API)

- **Description:** Ambient clinical documentation platform (formerly DAX Copilot) embedded in Epic, Oracle Health, athenahealth, and MEDITECH. Microsoft exposes a Healthcare API for integrating clinical AI capabilities. No standalone public CDI-specific API documented, but the ambient note generation infrastructure is available to health system partners.
- **Product Page:** https://www.nuance.com/healthcare/dragon-ai-clinical-solutions/dax-copilot.html
- **Microsoft Healthcare APIs:** https://learn.microsoft.com/en-us/azure/healthcare-apis/
- **Standards:** FHIR R4 (Azure Health Data Services); SMART on FHIR for EHR launch
- **Authentication:** Azure Active Directory / Entra ID; OAuth 2.0

---

### UMLS Metathesaurus & NLM APIs

- **Description:** NLM's Unified Medical Language System — the authoritative source linking SNOMED CT, ICD-10, RxNorm, LOINC, and 200+ other vocabularies. CDI NLP models use UMLS for clinical concept normalisation and terminology mapping. NLM provides a free REST API.
- **UMLS API Documentation:** https://documentation.uts.nlm.nih.gov/rest/home.html
- **SNOMED CT at NLM:** https://www.nlm.nih.gov/healthit/snomedct/index.html
- **RxNorm API:** https://lhncbc.nlm.nih.gov/RxNav/APIs/RxNormAPIs.html
- **Standards:** UMLS, SNOMED CT, ICD-10-CM, RxNorm, LOINC
- **Authentication:** UMLS API key (free NLM account required); SNOMED CT and RxNorm APIs are public

---

## Notes

- The CDI standards landscape is driven primarily by US regulatory frameworks (HIPAA, ONC Cures Act, CMS IPPS). International CDI implementations will require consideration of local equivalents (GDPR for EU data, ICD-11 for markets beyond the US).
- CDS Hooks (https://cds-hooks.hl7.org/) is an emerging standard for real-time clinical decision support delivery within EHR workflows. It is the most promising interoperability path for delivering CDI alerts at the point of note-writing — particularly for Epic and Oracle Health integrations — without requiring deep vendor-specific certification. CDI platforms should evaluate CDS Hooks as a more portable alternative to proprietary NoteReader CDI integrations.
- ICD-11 (released by WHO) is not yet adopted for US billing but is gaining traction internationally. An open-source CDI platform with international ambitions should plan for ICD-11 support in the roadmap.
- The AHIMA-ACDIS physician query guidelines are undergoing a 2026 revision with comment period ending June 12, 2026. Any AI-generated query system must align with the finalised 2026 brief before production deployment.
