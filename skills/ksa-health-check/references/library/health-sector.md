# Health sector layer: MoH, NHIC, telehealth, CHI/NPHIES, SFDA (KSA)

> **Library status:** researched from primary and secondary sources on 2026-10-10. Each item shows its source and confidence. Saudi instruments are authoritative in Arabic; English wording here is a working translation. Rules change: check the "As of" note and the current official text before relying on an item, and treat "Unconfirmed" items as questions, not requirements. Engineering guidance, not legal advice.


Part of the KSA healthcare requirements library. Scope: the **health-sector** layer — Ministry of Health (MoH), National Health Information Center (NHIC) and Saudi Health Council (SHC) eHealth standards, the Law of Practising Healthcare Professions, telehealth rules, Wasfaty/Sehhaty, the Council of Health Insurance (CHI) and NPHIES, SFDA medical-device rules for software and AI, and CBAHI accreditation. The national layer (PDPL, NDMO, NCA, CST, SDAIA AI guidance) is in `national.md` (IDs `NAT-xx`) and is only cross-referenced here.

Researched: 2026-10-10. Not legal advice. The Arabic text of every Saudi instrument prevails over any English translation.

---

## How to read this file

- **ID**: a stable identifier for one requirement. Prefixes: `NHIC-` (national eHealth interoperability and HIE policies, now published by NHIC/SHC), `MOH-` (Law of Practising Healthcare Professions and MoH platforms), `TEL-` (telehealth), `CHI-` (CHI and NPHIES), `SFDA-` (medical devices, SaMD and AI), `SHC-` (Saudi Health Council / CBAHI accreditation), `AI-` (AI-in-health guidance). IDs are not legal references; the legal reference is in *Source*.
- **Requirement**: what the rule requires, in plain language.
- **Engineering implication**: what the build team has to design, configure or produce.
- **Source**: the instrument, plus a section or article number **only where we checked it** against the text, with a URL.
- **Confidence**:
  - **Confirmed (primary)**: checked against the official text or an official translation hosted on a government or regulator site (moh.gov.sa, nhic.gov.sa, portal.nphies.sa, nphies.sa, chi.gov.sa, sfda.gov.sa, misa.gov.sa).
  - **Confirmed (secondary)**: taken from a reputable law-firm, practice-guide, journal or unofficial-translation source (Al Tamimi, Chambers, Addleshaw Goddard, Clyde & Co, Qanoniah, peer-reviewed articles), or from a copy of a primary document hosted by a third party.
  - **Unconfirmed**: we could not verify the detail. Do not build hard logic on it without checking.
- **Status words in eHealth standards**: the Saudi interoperability documents use SHALL / SHOULD / MAY. We keep that distinction; a SHOULD is not a hard requirement, but auditors and hospital clients often treat it as one.
- **As of 2026-10**: the status at the research date, including any pending changes.
- **Important context**: the Saudi eHealth Interoperability Specifications and HIE Policies were written in 2014–2016 for an IHE/XDS-based "Saudi eHealth Exchange" (SeHE). Since then, the national exchange effort has moved to **NPHIES** (FHIR R4), which is live for insurance transactions and is being extended to clinical data (Unified Health Record). We found no instrument that formally withdraws the HIE Policies, and they are still published on nhic.gov.sa, so the policy-level rules (privacy, audit, breach, consent) remain the best available sector baseline. Their IHE technical profiles may no longer be what a live integration uses.

---

## Key instruments

| Instrument | Issuer | Version / date (as verified) | Binding on | Status 2026-10 |
|---|---|---|---|---|
| Statute of the National Health Information Center | Council of Ministers Resolution No. 333, 19/10/1434H | 1434H (2013) | NHIC mandate; sets basis for unified EHR and exchange rules | In force (per Qanoniah) |
| IS0303 Saudi Health Information Exchange Policies | MoH (v1.0, 22 Feb 2015); re-issued under Saudi Health Council (v1.0, 21 Apr 2016), hosted on nhic.gov.sa | v1.0 | Participants in the Saudi HIE ("PHCSs" — participating healthcare systems) and HIE operators | Published; no withdrawal found; operational scope today unclear |
| IS0101 Saudi eHealth Security and Privacy Interoperability Specification | Saudi Health Council | v1.0, 21 Apr 2016 | Systems claiming conformance to Saudi Core Interoperability Specifications | Published |
| IS0102 Saudi eHealth Document Sharing Interoperability Specification (and other IS00xx/IS01xx/UC000x specs) | MoH National eHealth Strategy Office | v1.0, 22 Feb 2015 | Systems exchanging via SeHE | Published; IHE-based; current use unconfirmed |
| IS0304 Saudi HIE Testing and Certification Policies | MoH | v1.0, 22 Feb 2015 | IT products acting as HIE nodes | Published; whether the scheme operates today is unconfirmed |
| Law of Practising Healthcare Professions | Royal Decree M/59, 4/11/1426H (6 Dec 2005) | English translation on misa.gov.sa | All licensed healthcare professionals | In force |
| Legal Regulations for Telehealth Services | MoH, under Royal Order 47455 (9/8/1441H) | Header "March 2022"; Art. 3(2) says in force until 31 Dec 2021 | MoH-licensed facilities offering telehealth | **Status unclear** (see TEL-01) |
| Telemedicine Regulations in the Kingdom of Saudi Arabia | NHIC (Saudi Health Council) | V1.3, 29 Jun 2018, "final draft", effective date blank | Telemedicine entities and HCPs | Draft; superseded or not is unconfirmed |
| Annex 24 to the Private Health Institutions Law regime (Telemedicine and Remote Care Centres licence) | MoH | Dec 2018 (secondary) | Private telemedicine centres | Reported in force (secondary) |
| NPHIES Healthcare Financial Services IG Edition 1 | NPHIES (CHI with NHIC) | 1.0.0 STU, FHIR R4.0.1, "Draft as of 2025-12-03" | All parties exchanging insurance transactions via NPHIES | Published on portal.nphies.sa |
| NPHIES System Vendor Certification Programme | NPHIES | Programme documentation V4.0 (per NPHIES Academy page) | Software vendors linking to NPHIES | Active |
| CHI → Insurance Authority transfer announcement | CHI | 4 Mar 2024 | Health-insurance sector supervision moved to Insurance Authority; CHI keeps NPHIES, compulsory insurance, provider accreditation | In effect |
| Law of Medical Devices | Royal Decree M/54, 6/7/1442H | — | Manufacturers, ARs, importers, distributors, users of medical devices (incl. software) | In force |
| Implementing Regulation of the Medical Devices Law | SFDA Board decree 3-29-1443, 19/2/1443H | — | As above | In force |
| MDS-REQ 1 Requirements for Medical Devices Marketing Authorization | SFDA | v6.0, 19/12/2021 | MDMA applicants | Latest version we could retrieve; check for newer |
| MDS-G010 Guidance on AI and ML technologies based Medical Devices | SFDA | v1.0, version date 29/11/2022 (doc code MDS-G-010-V1/230103; listed 2023-01-03) | Guidance for AI/ML MDMA applicants | Published |
| MDS-G27 Guidance on Digital Health Products | SFDA | v1.0, 11/8/2025 (MDS-G-027-V1/250811) | Guidance: SaMD, mHealth, DTx, HIT, telemedicine, wearables, AI/ML, wellness | Published |
| MDS-G23 Guidance on Software as a Medical Device | SFDA | Version/date not retrieved | Guidance | Referenced by MDS-G27; text not read |
| MDS-G38 Guidance to Pre-Market Cybersecurity of Medical Devices | SFDA | v1.0, 18/6/2019 | MDMA applicants | Published; new cybersecurity guidance under development (IMDRF, Mar 2026) |
| MDS-G37 Guidance to Post-Market Cybersecurity of Medical Devices | SFDA | v1.0, 18/6/2019 | Manufacturers | Published |
| MDS-REQ 11 Requirements for Post-Market Surveillance of Medical Devices | SFDA | v2, 23/03/2023 | Manufacturers, ARs, importers, distributors, healthcare providers | In force |
| MDS-REQ 7 Requirements for Unique Device Identification | SFDA | 2025 update (IMDRF slide, secondary) | Manufacturers / ARs | In force; details not read |
| CBAHI National Hospital Standards | CBAHI | 3rd edition, 1436H/2015, effective 1 Jan 2016 | Hospitals seeking CBAHI accreditation | Later edition not confirmed |
| SDAIA AI Ethics Principles 2.0; Generative AI Guidelines | SDAIA | Sep 2023; Jan 2024 | See `national.md` NAT-43, NAT-44 | Published |

---

## Requirements

### A. National eHealth interoperability and HIE policies (NHIC / SHC)

#### NHIC-01: Purpose-of-use control on every disclosure
- **Requirement**: Health information may be exchanged for treatment, healthcare operations and public health. Research, education and payment uses are allowed only subject to secondary-use conditions. Market studies, legal investigations without a court order, and undeclared or unknown purposes are not allowed.
- **Engineering implication**: Every query, export or API call that releases patient data should carry a coded purpose-of-use. Deny requests with a missing or unknown purpose. Route research/education requests into the secondary-use workflow (NHIC-11). Log the purpose in the audit record.
- **Source**: IS0303 Saudi Health Information Exchange Policies v1.0, §3.3.1–3.3.3. https://nhic.gov.sa/standards/Policies/IS0303-Saudi-Health-Information-Exchange-Policies-v1.0.pdf (2016 SHC edition); 2015 MoH edition: https://moh.gov.sa/en/Ministry/ehealthstd/Documents/eHealth%20Standards%20Files/Policies/IS0303%20Saudi%20Health%20Information%20Exchange%20Policies%20v1.0.pdf
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published; written for HIE participants, widely used as the sector privacy baseline.

#### NHIC-02: Baseline security programme for systems handling exchanged PHI
- **Requirement**: Systems must implement access control, automatic logoff, audit logs, emergency access, integrity controls, authentication and encryption. HIE systems SHALL be managed under ISO 27000 or SAS70/SSAE 16, SHOULD follow ISO 27799, and SHALL have contingency and disaster-recovery plans and intrusion detection. Personnel handling health information need privacy training, and a privacy/security officer and sanctions policy are required.
- **Engineering implication**: Build these controls in as product features (RBAC, idle logoff, tamper-evident audit, break-glass, integrity checks, encryption). Provide DR runbooks and RPO/RTO evidence. Hosting/operations should be ISO 27001-aligned so the client can show conformance.
- **Source**: IS0303 §4.3.1, §4.3 items 2, 4, 5, 8, 9 (2016 edition numbering), and §4.3.5, 4.3.8–4.3.11 (2015 edition). URLs as NHIC-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published. For government and CNI clients, NCA controls apply on top (see `national.md` NAT-31 to NAT-41).

#### NHIC-03: No deletion of exchanged health data; amend instead; indefinite retention
- **Requirement**: Data SHALL NOT be deleted from the Saudi HIE at any time; corrections are made by amendment. Retention for HIE-managed PHI is indefinite.
- **Engineering implication**: Use an append-only or versioned clinical record model: corrections create a new version linked to the original, with author, time and reason. Do not offer hard-delete for clinical data in HIE-connected repositories. Plan storage growth for indefinite retention. Reconcile with PDPL destruction duties (`national.md` NAT-18) by documenting the sector retention basis.
- **Source**: IS0303 §4.3 items 3 and 6 (2016); §4.3.3 and §4.3.6 (2015). URLs as NHIC-01.
- **Confidence**: Confirmed (primary). Scope limited to "HIE-managed PHI"; whether it applies to every provider EMR is not stated.
- **As of 2026-10**: Published.

#### NHIC-04: Encrypt health information in transit
- **Requirement**: All HIE systems SHALL encrypt communications when exchanging PHI, minimally supporting AES or 3DES. IS0101 requires TLS between nodes and names TLS_RSA_WITH_AES_128_CBC_SHA as the required suite, noting stronger algorithms may be activated.
- **Engineering implication**: Use TLS 1.2+ (prefer 1.3) with AES-GCM suites. Do not use 3DES; it is deprecated. If connecting to a legacy SeHE-style node that only offers the 2016 suite, isolate that link and record the exception. Encrypt at rest as well (PDPL/NCA expectation).
- **Source**: IS0303 §4.3 item 7 (2016) / §4.3.7 (2015); IS0101 v1.0 SP-006. https://nhic.gov.sa/standards/General/IS0101-Saudi-eHealth-Security-and-Privacy-IS-v1.0.pdf
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published; cipher list is outdated relative to current practice.

#### NHIC-05: Patient access, amendment and disclosure-report rights
- **Requirement**: Patients (or their agents) must be able to access their relevant PHI, ideally directly and securely without physician mediation (SHOULD). They may request amendments without fees or burdensome process, request a report of electronic disclosures, and request investigation of suspected breaches.
- **Engineering implication**: Provide a patient portal or export function, an amendment-request workflow with status tracking, and a per-patient "who accessed/received my data" report generated from audit logs. Design audit records so that this report is cheap to produce.
- **Source**: IS0303 §5.3.1, 5.3.1.3, 5.3.1.6, 5.3.8, 5.3.9. URLs as NHIC-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published. PDPL rights (30-day window) also apply: `national.md` NAT-08.

#### NHIC-06: Opt-out consent model, break-glass and sensitive-data restrictions
- **Requirement**: PHI may be shared unless the patient opts out; patients may opt out and opt back in. Consent/opt-out status is checked at the time of use. After opt-out, access is limited to emergencies; only physicians may break the glass, which triggers notification and review. Sensitive PHI must be marked and restricted to specialised providers. Every user must hold at least one standard healthcare role. Provider registry entries must hide email, mobile and home address unless the provider authorises it.
- **Engineering implication**: Build a consent registry queried at access time (not cached at login). Implement break-glass as a separate, physician-only action with mandatory reason, real-time alert and post-hoc review queue. Add a sensitivity flag on records/segments (e.g. mental health, HIV, reproductive) with stricter access rules. Map all user accounts to a standard role vocabulary.
- **Source**: IS0303 §5.3.5, 5.3.11–5.3.12, 8.3.2, 8.3.6–8.3.8, 8.3.10, 8.3.13, 8.3.15, 8.3.17 (2015 numbering; 2016 edition §8.3 item 8 confirms opt-out check at enforcement). URLs as NHIC-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published. Note PDPL generally requires explicit consent for health data unless another basis applies (`national.md` NAT-03, NAT-04); the HIE opt-out model must be reconciled with that.

#### NHIC-07: Identity proofing for users and certificates for systems
- **Requirement**: Organisation system certificates must be attested by a trusted third party; self-signed certificates are prohibited; certificates are issued by the National Center for Digital Certification. Individual users must complete face-to-face identity proofing with a government-issued photo ID, and regulated professionals must hold a current SCFHS licence. Accounts SHOULD be revoked within two business days of severance.
- **Engineering implication**: Support certificates from the national PKI (not self-signed). User onboarding must record ID-proofing evidence and SCFHS licence number and expiry, with automatic suspension on licence expiry. Integrate leaver feeds (HR/AD) so deprovisioning happens within two business days.
- **Source**: IS0303 §6.3.1, 6.3.3, 6.3.5.1–6.3.5.2.3, 6.3.8.3 (2015 numbering). IS0101 SP-003/SP-004 (node certificates under a Saudi eHealth root CA branch of the National Center for Digital Certificates). URLs as NHIC-01, NHIC-04.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published.

#### NHIC-08: Session timeout, MFA for remote access, credential checks
- **Requirement**: Sessions SHOULD log off after no more than 30 minutes of inactivity. HIE nodes must use TLS node authentication. Remote user access to the HIE requires multi-factor authentication; PHCSs SHOULD require MFA for remote access to their own systems from outside the organisation's physical control. Credentials are checked for revocation and expiry at logon.
- **Engineering implication**: Configurable idle timeout (default ≤30 min). MFA on all remote and privileged access paths — this also covers vendor support staff and offshore developers connecting into client environments. Check certificate/credential revocation at authentication time.
- **Source**: IS0303 §7.3.2, 7.3.3, 7.3.4, 7.3.8–7.3.9 (2015); 2016 edition §7.3 items 4–5. URLs as NHIC-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published.

#### NHIC-09: Audit logging content, review and retention
- **Requirement**: Record access, creation, modification and deletion of electronic PHI, including failed logons. Audit records capture request details, break-glass use, sensitivity markings and requester/responder IDs. Logs are reviewed at least quarterly; anomaly documentation is kept 10 years; audit logs are kept as long as the PHI (SHOULD in 2016 edition). External audits at least annually and after major changes. Clocks synchronised; log access restricted to approved officers.
- **Engineering implication**: Central, immutable audit store with the listed fields; NTP time sync (IS0101 requires IHE Consistent Time, 1-second accuracy). Retention policy for audit = retention of the clinical data (effectively indefinite for HIE data). Build a quarterly review report and restrict audit-log access to a security/privacy role.
- **Source**: IS0303 §9.3.1, 9.3.4, 9.3.5, 9.3.7, 9.3.8.3, 9.3.8.5, 9.3.11, 9.3.13, 9.3.15. IS0101 SP-001/SP-002 (time), SP-010 to SP-012 (ATNA audit events). URLs as NHIC-01, NHIC-04.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published. NCA's 12-month minimum log retention also applies to in-scope entities (`national.md` NAT-34).

#### NHIC-10: Breach detection, reporting and notification timelines
- **Requirement**: Privacy/security officers monitor access at least monthly. Reportable events are reported internally within 2 business days. Breach investigation reports are due within 30 calendar days (extendable by 30) and kept at least 10 years. The HIE notifies affected PHCSs within 10 business days of discovery; required public notification is due within 30 days of discovery; notices must describe what happened, PHI involved, protective steps and contacts. Breaches affecting large numbers (typically >500 with continuing risk) SHOULD be reported publicly.
- **Engineering implication**: Incident-management module with timers for each deadline, templates for the notice content, and 10-year retention of investigation reports. Run monthly access-anomaly reports. Note that the PDPL 72-hour notification to SDAIA (`national.md` NAT-12) is shorter and runs in parallel — build to the shortest clock.
- **Source**: IS0303 §10.3.1, 10.3.2.1.1, 10.3.3.5.1, 10.3.3.5.3, 10.3.4.1–10.3.4.4. URLs as NHIC-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published.

#### NHIC-11: Secondary use (research, analytics, AI training) needs ethics approval and a DUA
- **Requirement**: Non-care use needs case-by-case approval from a designated ethics committee and a Data Use Agreement limited to the approved purpose. De-identified data needs a re-identification risk assessment, and recipients must contractually agree not to re-identify. Records of approved requests are kept at least 10 years.
- **Engineering implication**: Any pipeline that feeds patient data to analytics or model training must check for an approval ID and DUA reference, apply de-identification with a documented re-identification risk assessment, and log the release. Keep release records 10 years. Do not reuse production clinical data for AI training without this trail.
- **Source**: IS0303 §11.3.2.1, 11.3.2.6, 11.3.3.1, 11.3.3.5.2, 11.3.4.3. URLs as NHIC-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published. PDPL research rules also apply (`national.md` NAT-20).

#### NHIC-12: Saudi eHealth interoperability specifications (IHE-based) and security profiles
- **Requirement**: The Saudi Core Interoperability Specifications are based on IHE profiles: document sharing uses IHE XDS.b with Saudi constraints (plus XDM, DSUB, Metadata Update, On-Demand Documents); security uses IHE ATNA, Consistent Time, XUA and BPPC. The patient ID in shared documents SHALL be a verified Health ID under the KSA registration OID; metadata SHALL use Saudi value sets from the IS0200 Saudi eHealth Terminology Repository; portable media index files SHALL be in Arabic and English.
- **Engineering implication**: If a client asks for SeHE/IHE conformance, implement these profiles and Saudi value sets; otherwise treat them as design guidance. Keep coded metadata configurable. Support Arabic and English in exported media/document indexes.
- **Source**: IS0102 v1.0 (KXDS-003 to -011, -013, -090); IS0101 v1.0 §1–3. https://moh.gov.sa/en/Ministry/ehealthstd/Documents/eHealth%20Standards%20Files/eReferral%20and%20eTransfer%202/IS0102%20Saudi%20eHealth%20Document%20Sharing%20Interoperability%20Specification%20v1.0.pdf ; IS0101 URL as NHIC-04; background: https://www.ihe.net/ihe-saudi-arabia/
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published 2015/2016. Whether any live national service still requires these IHE profiles is Unconfirmed.

#### NHIC-13: Testing and certification of HIE-connected products
- **Requirement**: Products used as HIE nodes are tested by an ISO/IEC 17025-accredited lab against published test scripts and certified by a single national certification body (ISO/IEC 17065). Certificates are valid four years. Re-certification is triggered by a major product version, a minor release with significant functional change, or a major update to a Core Interoperability Specification.
- **Engineering implication**: If certification is required by a client, map product versioning to the re-certification triggers (semantic versioning with a documented definition of "major"). Keep test evidence for the certificate's life.
- **Source**: IS0304 Saudi HIE Testing and Certification Policies v1.0, §3.1–3.3, §4.3 items 1–12, §5.3. https://www.moh.gov.sa/en/Ministry/ehealthstd/Documents/eHealth%20Standards%20Files/Policies/IS0304%20Saudi%20Health%20Information%20Exchange%20Testing%20and%20Certification%20Policies%20v1.0.pdf
- **Confidence**: Confirmed (primary) for the text; whether the scheme operates today is Unconfirmed.
- **As of 2026-10**: Published 2015. For NPHIES, see the separate vendor certification (CHI-07).

#### NHIC-14: National ID / Iqama as the national patient reference; unified EHR
- **Requirement**: NHIC's statute tasks it with creating a unified electronic health record for each patient, using the national ID (or residence number) as the national reference number. NHIC also sets data-exchange rules, standardises health terminology, adopts the international disease classification, and sets healthcare IT and database standards.
- **Engineering implication**: Store national ID / Iqama (and border number or passport for visitors) as a first-class, validated patient identifier, separate from the local MRN. Design the master patient index to link to a future national Health ID. Expect NHIC-issued terminology and exchange rules to bind integrations.
- **Source**: Statute of the National Center for Health Information, Council of Ministers Resolution 333 (1434H), Arts. 2, 3(2)–3(5), 3(8), 5. https://qanoniah.com/en/File/DmWqyAxNgpoPlkJoP26zvBXaE-Statute-of-the-National-Center-for-Health-Information
- **Confidence**: Confirmed (secondary) — unofficial English translation.
- **As of 2026-10**: In force (per Qanoniah status field).

#### NHIC-15: FHIR for clinical exchange and the NPHIES Unified Health Record
- **Requirement**: NPHIES was introduced by CHI and NHIC with two parts: insurance transactions and clinical services for a unified digital health record. No national FHIR base/core implementation guide for clinical data was found; the FHIR community registry states none exists yet, and FHIR R4 is the version in use nationally.
- **Engineering implication**: Build clinical interfaces on FHIR R4 base resources with a pluggable profile layer, so Saudi clinical profiles can be added when published. Do not hard-code a "Saudi Core" IG. Ask each client whether they are onboarding to the NPHIES clinical/Unified Health Record service and obtain its specifications directly.
- **Source**: Karger, Saudi Journal of Health Systems Research 2024/2025, "Unveiling the National Platform for Health and Insurance Exchange Services" https://karger.com/sjh/article/5/1/1/917352/Unveiling-the-National-Platform-for-Health-and ; FHIR registry jurisdiction page https://packages.fhir.org/jurisdictions/SA ; Lean product page https://lean.sa/en/products-and-solutions/nphies-unified-health-record
- **Confidence**: Confirmed (secondary) for the existence of the clinical component and the absence of a public national core IG. Any mandate or deadline for providers to connect clinically is **Unconfirmed**.
- **As of 2026-10**: Unified Health Record live in some form (KLAS report May 2026); public specs not found.

### B. Law of Practising Healthcare Professions and MoH platforms

#### MOH-01: Professional confidentiality and the closed list of disclosure grounds
- **Requirement**: A healthcare professional must keep confidential what they learn in practice and may disclose it only: (a) to report a death from a criminal act or prevent a crime (to competent authorities only), to report communicable or epidemic diseases, or to rebut accusations about their competence or conduct by the patient or family; (b) with the patient's written consent, or to the family where beneficial to treatment; or (c) on a judicial order. Separately, professionals must immediately notify security and health authorities of suspected crime-related injuries or infectious diseases (Art. 11).
- **Engineering implication**: Every release of information outside the treating team should record a legal ground from this list (written consent reference, court-order reference, notifiable-disease report, etc.). Support capture and storage of written (e-signed) disclosure consent. Provide a notifiable-disease reporting path (format and channel to MoH Unconfirmed). Penalties fall on the professional, so clinicians will expect the system to stop casual disclosure.
- **Source**: Law of Practising Healthcare Professions, Royal Decree M/59, Arts. 11, 21. https://misa.gov.sa/app/uploads/2025/07/Law-of-Practicing-Healthcare-Professions.pdf (MoH copy: https://www.moh.gov.sa/en/Ministry/Rules/Documents/Law-of-Practicing-Healthcare-Professions.pdf)
- **Confidence**: Confirmed (primary) — English translation on a government site.
- **As of 2026-10**: In force. Implementing Regulations not reviewed in full.

#### MOH-02: Patient-nominated recipients and patient reports on request
- **Requirement**: For incurable or life-threatening disease, the physician decides whether to inform the patient or family, unless the patient prohibits it or designates one or more persons to be exclusively informed. The professional must give the patient, on request, reports on their condition and test results.
- **Engineering implication**: Store patient communication preferences: designated recipients, "do not inform family" flags, and display them prominently to clinicians. Provide patient-requested report generation (clinical summary, results) with a request log.
- **Source**: Law of Practising Healthcare Professions, Arts. 15, 18. URL as MOH-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### MOH-03: Prescription constraints that e-prescribing must model
- **Requirement**: A pharmacist may dispense only on a prescription from a physician licensed in the Kingdom (except medicines the Ministry specifies), may not substitute a different medicine without the prescriber's approval except a generic equivalent with patient approval (with Ministry exceptions), may not refill unless the prescription says so, and must query suspected errors with the prescriber.
- **Engineering implication**: E-prescription data model needs: prescriber licence ID (SCFHS), refill count/allowed flag, "substitution not permitted" flag, a list of Ministry-excluded medicines for generic substitution, and a pharmacist-to-prescriber query channel.
- **Source**: Law of Practising Healthcare Professions, Art. 23(A)(2)–(5). URL as MOH-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### MOH-04: Wasfaty national e-prescribing
- **Requirement**: Wasfaty is the MoH e-prescribing platform (introduced 2019) connecting MoH hospitals and primary care centres with community pharmacies; published research describes its use as mandatory for doctors and pharmacies in that programme.
- **Engineering implication**: Pharmacy systems serving MoH-patient prescriptions, and prescribing systems in MoH facilities, must integrate with Wasfaty. Obtain the interface specification and onboarding process from the operator; we found no public technical specification.
- **Source**: Alharthi, Frontiers in Medicine 2024, 11:1487852. https://www.frontiersin.org/journals/medicine/articles/10.3389/fmed.2024.1487852/full
- **Confidence**: Confirmed (secondary) for existence and scope; integration requirements, operator and private-prescriber coverage **Unconfirmed**.
- **As of 2026-10**: Live.

#### MOH-05: Sehhaty and Seha platforms (patient-facing national services)
- **Requirement**: Sehhaty (MoH) gives patients access to medical reports and sick leaves, a health record, appointments (including remote), prescriptions/medicines review and vaccination records, for services "provided by various entities in the health sector". The Seha platform handles sick-leave reports (MHRSD approved it in 2022 for sick leave issued abroad).
- **Engineering implication**: Clients will expect sick leaves, medical reports and appointments to appear in Sehhaty/Seha. Treat sick-leave issuance and medical reports as national-platform integrations, not local PDFs. Obtain integration specs from the client/operator.
- **Source**: MoH Sehhaty page https://www.moh.gov.sa/en/eservices/sehhaty/pages/default.aspx ; Saudi Gazette 15 Sep 2022 https://saudigazette.com.sa/article/625018
- **Confidence**: Confirmed (primary) for Sehhaty service list; Confirmed (secondary) for Seha sick leave. Any mandate on private providers to issue sick leave only via Seha is **Unconfirmed**.
- **As of 2026-10**: Live.

#### MOH-06: Medical record retention period
- **Requirement**: Apart from the HIE rule (NHIC-03: indefinite for HIE-managed PHI), we did not find a confirmed general retention period for provider medical records in MoH law or regulations. Older guidance points to the Document Records and Archives Law (Royal Decree M/54, 23/10/1409H) without a health-specific period.
- **Engineering implication**: Make retention configurable per record type and per client. Default to no automatic destruction of clinical records; require a documented, client-approved schedule before enabling deletion. Keep deletion logs.
- **Source**: Chambers Digital Healthcare 2022 – Saudi Arabia (Hammad & Al-Mehdar) https://practiceguidesdev.chambers.com/practice-guides/digital-healthcare-2022/saudi-arabia
- **Confidence**: **Unconfirmed** (no specific period found)
- **As of 2026-10**: Open item; ask client legal/medical records department.

### C. Telehealth / virtual care

#### TEL-01: Telehealth only by licensed (and accredited) facilities
- **Requirement**: Telehealth may only be provided by MoH-licensed facilities. Public-sector services need prior approval from the Centre for Digital Health Excellence; private facilities are licensed through the MoH licensing department before starting. Facilities need written contracts with partner facilities, insurance covering telehealth, and accreditation within 18 months. The 2018 NHIC draft and Al Tamimi report mandatory CBAHI accreditation and a separate private "Telemedicine and Remote Care Centre" licence under Annex 24.
- **Engineering implication**: A telehealth platform sold to providers must let each tenant record its facility licence, approval references and accreditation status, and should refuse to activate clinical services for an unlicensed tenant. If ATeam or a client operates a direct-to-patient service, it needs its own facility licence.
- **Source**: Legal Regulations for Telehealth Services, Arts. 4–5, 7(7), 8. https://www.moh.gov.sa/en/Ministry/Rules/Documents/Legal-Regulations-for-Telehealth-Services.pdf ; NHIC Telemedicine Regulations V1.3 §3.1.7–3.1.9 https://www.dataguidance.com/sites/default/files/saudi_arabia_telemedicine_policy.pdf ; Al Tamimi https://www.tamimi.com/news/healthcare-licences-now-available-for-telemedicine-and-remote-care-centres-in-saudi-arabia
- **Confidence**: Confirmed (primary) for the text. **Current status of the instrument is Unconfirmed**: the MoH PDF header says "March 2022 till valid" while Art. 3(2) says it is in force until 31 Dec 2021, and Qanoniah lists a related "Regulatory Rules for Telemedicine Services" as cancelled (effective until Sha'ban 1443H).
- **As of 2026-10**: Licensing requirement itself is consistent across all sources.

#### TEL-02: Ministry-approved technology and declared solution provider
- **Requirement**: Facilities must install equipment, software and peripherals approved by the Ministry, and medical devices must be SFDA-approved. The NHIC 2018 draft requires facilities to declare their telemedicine solution provider to the Saudi Telemedicine Unit of Excellence (STUE) before starting, with contracts meeting STUE criteria.
- **Engineering implication**: Prepare a technical dossier for MoH/NHIC approval (architecture, hosting location, security controls, interoperability). If the platform includes diagnostic or monitoring functions, check SFDA qualification (SFDA-02). Contract templates should anticipate regulator-set criteria.
- **Source**: Legal Regulations for Telehealth Services, Arts. 5(3), 10(5); NHIC Telemedicine Regulations V1.3 §3.1.13–3.1.16. URLs as TEL-01.
- **Confidence**: Confirmed (primary); approval process details Unconfirmed.
- **As of 2026-10**: See TEL-01 status caveat.

#### TEL-03: Informed e-consent before each telehealth service; right to withdraw
- **Requirement**: Informed consent must be obtained before a telehealth service, signed by the patient on a standard form, and available for verification (online). Patients may refuse or cancel participation at any time without giving a reason. The 2018 draft adds that an inpatient's consent lasts for the stay.
- **Engineering implication**: Capture e-consent (versioned form, timestamp, e-signature, identity of signer, guardian where relevant) before the session can start; store it retrievably. Offer one-click withdrawal that stops scheduled sessions and records the withdrawal.
- **Source**: Legal Regulations for Telehealth Services, Art. 12(1)–(3); NHIC Telemedicine Regulations V1.3 §3.1.20–3.1.22. URLs as TEL-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: See TEL-01 status caveat.

#### TEL-04: Verify patient identity; secure and private setting; follow HIE policy
- **Requirement**: Facilities and professionals must have sufficient evidence of the patient's identity before and during the service. Facilities must provide a secure, private workspace protecting personal information and consultation privacy, and comply with Saudi HIE policy and KSA privacy, security and interoperability frameworks.
- **Engineering implication**: Build an identity-verification step (national ID / Iqama match, plus a strong digital-identity method where the client has one) and record the verification evidence on the encounter. End-to-end encrypted media, no third-party consumer apps, access-controlled session links, and the NHIC-01 to NHIC-11 controls.
- **Source**: Legal Regulations for Telehealth Services, Art. 11(1)–(3); NHIC Telemedicine Regulations V1.3 §3.1.17–3.1.18. URLs as TEL-01.
- **Confidence**: Confirmed (primary). Use of a specific national digital-identity service for telehealth is Unconfirmed.
- **As of 2026-10**: See TEL-01 status caveat.

#### TEL-05: Document every telehealth activity in the medical record
- **Requirement**: All telemedicine activities must be recorded in the patient's medical record (in the telemedicine solution or the facility's EHR), including provider identification, location, date and time, type of activity, prescriptions or investigations, technical incidents and adverse events. ICD coding may be applied.
- **Engineering implication**: Auto-create an encounter record with these fields; capture technical incidents (dropped calls, poor quality) as structured events. Recording of audio/video itself: no rule found — make session recording off by default, consent-gated, and retention-configured.
- **Source**: NHIC Telemedicine Regulations V1.3 §3.2.6, §3.3.1–3.3.3. URL as TEL-01. Al Tamimi 2019 summary https://tamimi.com/law-update-articles/the-regulation-and-licensing-of-telemedicine-in-saudi-arabia
- **Confidence**: Confirmed (secondary) — primary text of a 2018 draft hosted by a third party. Rules on recording sessions: **Unconfirmed**.
- **As of 2026-10**: Draft status.

#### TEL-06: Audio-only teleconsultation
- **Requirement**: The 2018 NHIC draft says teleconsultation must not be audio-only (video, images, text and data may be used).
- **Engineering implication**: Make video the default consultation mode; keep audio-only as a tenant-configurable option that is off by default until the client confirms current MoH rules.
- **Source**: NHIC Telemedicine Regulations V1.3 §2.1.3, §2.2.3. URL as TEL-01.
- **Confidence**: Confirmed (secondary) for the 2018 text; current applicability **Unconfirmed**.
- **As of 2026-10**: May have been relaxed; check with client.

#### TEL-07: Practitioner licensing and partners outside KSA
- **Requirement**: Only credentialed and privileged professionals with a valid licence may provide telehealth, and diagnosis/treatment telehealth is physician-led. Professionals licensed abroad must register in the Kingdom to provide telemedicine there (2018 draft). Where a partner facility is outside KSA jurisdiction, there must be a written contract defining roles, and the licensed Saudi facility must ensure compliance in both jurisdictions.
- **Engineering implication**: Practitioner registry with SCFHS licence number, scope and expiry checks before a practitioner can join a session. Flag practitioners located outside KSA, require evidence of Saudi registration, and capture the partner-facility contract reference. Cross-border consultations also trigger PDPL transfer rules (`national.md` NAT-24 to NAT-27).
- **Source**: Legal Regulations for Telehealth Services, Arts. 5(4), 5(5), 5(7), 6, 7; NHIC Telemedicine Regulations V1.3 §3.1.11. URLs as TEL-01; Qanoniah summary of cancelled rules https://qanoniah.com/en/File/EPj1RJOmdzLRbOeLDZAYpM5wN-Regulatory-Rules-for-Telemedicine-Services
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: See TEL-01 status caveat.

#### TEL-08: Prescribing and investigations through telehealth
- **Requirement**: Permitted telehealth services include appointments, assessment, prescribing and dispensing of medicines and exchange of medical reports. Online prescriptions and investigations must follow Saudi prescribing rules, and the ordering professional is responsible for them.
- **Engineering implication**: Integrate the same e-prescribing controls as in-person care (MOH-03, MOH-04), including prescriber licence and controlled-medicine rules; do not allow prescriptions from unverified practitioners or unverified patients.
- **Source**: Legal Regulations for Telehealth Services, Art. 13(1); NHIC Telemedicine Regulations V1.3 §3.2.7–3.2.8. URLs as TEL-01.
- **Confidence**: Confirmed (primary). Restrictions on prescribing controlled drugs via telehealth: **Unconfirmed**.
- **As of 2026-10**: See TEL-01 status caveat. Seha Virtual Hospital (MoH) is the national public virtual-care service; we did not research its vendor requirements.

### D. Council of Health Insurance and NPHIES

#### CHI-01: NPHIES is the single exchange hub for insurance transactions
- **Requirement**: NPHIES is a centralised, standards-based gateway connecting healthcare providers and payers in KSA; exchanges are no longer peer to peer. All private insurers and/or their TPAs exchange e-claims through it, and the public health system is joining. It validates format and coding but does not adjudicate. Use cases: eligibility, prior authorisation, advanced authorisation, claims and batch claims, payment reconciliation and notification, information request/submission, cancellation, error notice, polling and status check.
- **Engineering implication**: Any HIS/RCM product for KSA private care needs a native NPHIES connector covering all these use cases. Do not design direct provider-to-payer integrations for these transactions.
- **Source**: NPHIES Healthcare Financial Services IG, Introduction and Use Cases. https://portal.nphies.sa/ig/introduction.html ; https://portal.nphies.sa/ig/usecases.html
- **Confidence**: Confirmed (primary). A formal CHI circular making NPHIES use mandatory was not retrieved; mandatory status is evidenced by the IG statements and vendor-certification requirement.
- **As of 2026-10**: Live.

#### CHI-02: FHIR R4 messaging to a pinned IG version
- **Requirement**: Exchanges use HL7 FHIR R4 (4.0.1) messages as defined in the "Healthcare Financial Services IG Edition 1" (NPHIES_FS), version 1.0.0 STU, which replaces the earlier PDF implementation guide V2.6 and its spreadsheets.
- **Engineering implication**: Use a FHIR R4 library; pin to the IG package version; subscribe to NPHIES change notices and budget for IG upgrades (ValueSet and field-length changes are listed in the Roadmap). Keep profile validation data-driven so new IG releases can be loaded without code changes.
- **Source**: NPHIES IG home and Roadmap. https://portal.nphies.sa/ig/index.html ; https://portal.nphies.sa/ig/roadmap.html
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Portal shows "1.0.0 – STU, Draft as of 2025-12-03". Confirm with NPHIES which version is production.

#### CHI-03: Conform to profiles; populate required and MustSupport elements only
- **Requirement**: All implementations SHALL conform to the IG's definitional artefacts. Elements that are required (1..) and MustSupport are in scope; senders should avoid populating other elements or extensions, and receivers may reject messages containing out-of-scope data if their retention policies don't allow it. Receivers must not send elements where data is absent and the reason unknown.
- **Engineering implication**: Validate every outbound bundle against the IG profiles before sending; strip non-profiled elements (also good data minimisation). Handle rejections caused by extra data.
- **Source**: NPHIES IG Conformance. https://portal.nphies.sa/ig/conformance.html
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published.

#### CHI-04: Mutual-TLS with NPHIES-issued certificates; protect PHI in messages
- **Requirement**: All message exchanges SHALL use mutually authenticated HTTPS to the NPHIES endpoint using X.509 certificates issued by NPHIES. Parties SHALL protect their certificates, report suspected compromise and replace the certificate; all parties must safeguard PII/PHI in messages.
- **Engineering implication**: Store NPHIES private keys in an HSM or managed key vault, never in code or shared drives; per-facility certificates; expiry monitoring and rotation runbook; incident procedure for certificate compromise. Encrypt and access-control message logs, which contain PHI.
- **Source**: NPHIES IG Message Exchange. https://portal.nphies.sa/ig/message-exchange.html
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published.

#### CHI-05: Message-exchange limits, polling and duplicate handling
- **Requirement**: Each party exposes a `$process-message` endpoint (payers also expose an availability endpoint). Sessions SHALL have a maximum up-time of 60 seconds; messages are capped at 10 MB and batches at 200 claims; poll requests return at most 100 messages and cannot be used for eligibility or status check. A duplicate (same MessageHeader.id and focal resource identifier) gets a "queued" response or the most recent stored response; NPHIES queues requests when a payer cannot respond.
- **Engineering implication**: Client timeouts under 60 s, attachment-size checks under 10 MB, batch splitting at 200, a polling scheduler, and idempotent resend using the same MessageHeader.id. Payer-side products must implement both endpoints.
- **Source**: NPHIES IG Message Exchange. URL as CHI-04.
- **Confidence**: Confirmed (primary). Note the page names `$process-request` in one HCP section — confirm with NPHIES.
- **As of 2026-10**: Published.

#### CHI-06: Mandated code systems and terminology licences
- **Requirement**: Diagnoses use ICD-10-AM; procedures, services, laboratory, imaging, medical devices, medications (medication codes and scientific codes), MoH category and dental (FDI oral region) use NPHIES-published code systems. Terminology licences SHALL be obtained from the third-party IP owner for each code system.
- **Engineering implication**: Licence ICD-10-AM (and any related classification used for procedures) for every deployment; load NPHIES code tables as versioned reference data with update jobs; map local charge masters and drug files to NPHIES codes.
- **Source**: NPHIES IG Artifacts, ValueSet pages and Conformance. https://portal.nphies.sa/ig/artifacts.html ; https://portal.nphies.sa/ig/ValueSet-professional-billing.html ; URL as CHI-03.
- **Confidence**: Confirmed (primary). The commonly cited name "Saudi Billing System (SBS)" for the procedure/services codes did not appear in the pages we read — Unconfirmed.
- **As of 2026-10**: Published.

#### CHI-07: Vendor certification, onboarding and IP whitelisting
- **Requirement**: System vendors must complete the NPHIES System Vendors Qualification Course as a mandatory part of the vendor certification programme, described as one of the requirements for linking with NPHIES. Onboarding includes an Expression of Interest form and an IP whitelisting form, a readiness and activation guide, FHIR and clinical-standards training and tests.
- **Engineering implication**: Plan certification into the delivery timeline. Connections come from whitelisted IPs, so use fixed egress IPs (NAT gateway) for test and production. Assign named staff to complete the course. Check whether non-KSA egress IPs are accepted before planning offshore integration testing.
- **Source**: NPHIES Academy, System Vendors Onboarding Course. https://v-academy.nphies.sa/courses/11/system-vendors-onboarding-course?lang=en
- **Confidence**: Confirmed (primary). Content of Vendor Certification Program documentation V4.0 not read; restrictions on non-KSA IPs **Unconfirmed**.
- **As of 2026-10**: Active.

#### CHI-08: Know which regulator is which after the Insurance Authority transfer
- **Requirement**: From 4 March 2024, health-insurance sector supervision and its authorities moved from CHI to the Insurance Authority (operational since 23 Nov 2023). CHI keeps enforcement of compulsory health insurance, accreditation of providers serving its beneficiaries, operation of NPHIES, and supervision of providers' compliance.
- **Engineering implication**: For payer/TPA products, look to the Insurance Authority for insurer cybersecurity and data rules; for provider-side NPHIES integration, CHI/NPHIES remain the authority. Record the regulator per tenant type in the compliance matrix.
- **Source**: CHI announcement, 4 Mar 2024. https://www.chi.gov.sa/en/MediaCenter/News/Pages/CHI-announces-transferring-roles-and-responsibilities-of-the-health-insurance-sector-to-IA.aspx ; US ITA note https://www.trade.gov/index.php/market-intelligence/saudi-arabia-financial-services-new-insurance-regulatory-body-launched
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In effect. Specific Insurance Authority cybersecurity requirements for insurers/TPAs are Unconfirmed (SAMA's Cyber Security Framework historically applied to insurers).

### E. SFDA: medical device software and AI

#### SFDA-01: Software with a medical purpose needs SFDA marketing authorisation (MDMA)
- **Requirement**: The Medical Devices Law defines a medical device to include software intended for diagnosis, prevention, monitoring, treatment or alleviation of disease, among other purposes. Article 8 provides that medical devices cannot be marketed or used without registration and marketing authorisation (SFDA may exempt some devices).
- **Engineering implication**: Do a documented SaMD qualification assessment at product inception and at every change of intended use or claims. Marketing copy, UI text and app-store descriptions are part of "intended use" — control them.
- **Source**: Law of Medical Devices, Royal Decree M/54, 6/7/1442H, Arts. 1, 8 (as quoted in SFDA MDS-G010 and MDS-REQ 1 Background); Implementing Regulation, SFDA Board decree 3-29-1443. https://sfda.gov.sa/sites/default/files/2023-01/MDS-G010ML.pdf ; https://www.sfda.gov.sa/sites/default/files/2021-12/REQ1En.pdf
- **Confidence**: Confirmed (primary) via SFDA documents quoting the law.
- **As of 2026-10**: In force.

#### SFDA-02: SaMD qualification and the wellness boundary (MDS-G27)
- **Requirement**: Software is SaMD if it has a medical purpose, performs it without being part of a hardware device, does more than storage, archiving, communication or simple search, and is intended to benefit individual patients. Software that only operates a device is not SaMD; standalone software driving a device with its own medical purpose is SaMD. General wellness products must state in English and Arabic labelling that they are not for medical purposes, and manufacturers must report known medical use to SFDA promptly.
- **Engineering implication**: Classify each module: an EMR, scheduling or billing module is usually not SaMD; a risk score, triage, diagnostic suggestion or image analysis usually is. For wellness apps, add a bilingual "not intended for medical purposes" statement in-app and in store listings, and monitor for medical use.
- **Source**: SFDA MDS-G27 Guidance on Digital Health Products v1.0 (11/8/2025). https://sfda.gov.sa/sites/default/files/2026-08/MDS-G027.pdf (earlier copy: https://www.sfda.gov.sa/sites/default/files/2025-08/MDS-G027.pdf)
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published.

#### SFDA-03: SaMD risk class under Rule 11
- **Requirement**: Software providing information used for diagnostic or therapeutic decisions is Class B, unless the decisions may cause death or irreversible deterioration (Class D) or serious deterioration or surgical intervention (Class C). Software monitoring physiological processes is Class B, or Class C for vital parameters where variations could cause immediate danger. All other software is Class A. Software driving or influencing a device takes that device's class.
- **Engineering implication**: Record the class rationale in the technical file. Class drives evidence depth, QMS scrutiny and change-notification effort; scope features to avoid unintentionally moving into C/D.
- **Source**: MDS-REQ 1 v6.0, Annex (5) Rule 11 and implementing rules. URL as SFDA-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: v6.0 is the latest version we retrieved.

#### SFDA-04: MDMA route, applicant, QMS and technical documentation
- **Requirement**: Applications go through the GHAD system by a local manufacturer (with a manufacturing licence), an overseas manufacturer, or the overseas manufacturer's authorised representative (licensed through GHAD; an AR is a person established in KSA). ISO 13485:2016 QMS evidence is required. Technical documentation follows Annex 3 (device description, information supplied, design and manufacturing, essential principles, benefit-risk and risk management, verification and validation, PMS plan, PSUR/PMS report). SFDA may request technical documentation at any time, to be supplied within 10 days.
- **Engineering implication**: Maintain a living technical file in a document-controlled repository, exportable within 10 days. Run development under an ISO 13485 QMS. Budget for a KSA authorised representative if ATeam is not the KSA-established legal manufacturer.
- **Source**: MDS-REQ 1 v6.0, Requirements items 3–4 and Annexes 3, 5, 12; MDS-G010 Annex 1 (AR definition). URLs as SFDA-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### SFDA-05: Notify SFDA of changes within 10 or 30 days
- **Requirement**: SFDA must be informed via the electronic system within 10 days of any significant change and 30 days of a non-significant change. MDS-G010 defines significant changes as those reasonably expected to directly affect safety or effectiveness, and requires QMS procedures for change control, categorisation and notification; all changes must be verified and validated.
- **Engineering implication**: Add a regulatory-impact step to the release pipeline that classifies each release (including model retraining, new training data, threshold changes, new input types) as significant/non-significant/none and creates the GHAD notification task with a due date.
- **Source**: MDS-REQ 1 v6.0, Requirements item 5; MDS-G010 "Change Notification". URLs as SFDA-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force. SFDA has not published a predetermined change-control plan mechanism that we could find (Unconfirmed).

#### SFDA-06: Essential principles for software, IT security and bilingual lay-user interfaces
- **Requirement**: Software must be designed for repeatability, reliability and performance, and developed according to the state of the art considering life-cycle, risk management including information security, and verification and validation. Mobile-platform software must account for platform features and use environment. Manufacturers must state minimum hardware, IT network and IT security requirements, including protection against unauthorised access. For devices used by lay persons, the electronic user interface must be in Arabic and English.
- **Engineering implication**: Document the software life-cycle (IEC 62304-style is the usual evidence, though SFDA does not name it in this text). Publish minimum hardware/network/security requirements in the IFU. Patient-facing SaMD needs full Arabic and English UI (with RTL layout).
- **Source**: MDS-REQ 1 v6.0, Annex 1 Essential Principles 17.1–17.4, 22.1, and IFU item (bb). URL as SFDA-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### SFDA-07: Clinical evaluation of AI/ML devices, including representative and local data
- **Requirement**: AI/ML devices need clinical evidence before marketing, covering valid clinical association, analytical/technical validation and clinical validation, with metrics such as sensitivity, specificity, PPV, NPV and likelihood ratios. Reference datasets should reflect target-condition prevalence, come from several centres, match the demographic and health characteristics of the target region, be justified in size, and not be publicly available. Performance should be shown across sites and subgroups, ideally with multi-site and prospective studies comparing clinicians with and without the device. Devices developed and approved elsewhere should be locally validated.
- **Engineering implication**: Keep a sealed, non-public test set; plan a KSA validation study (Saudi sites and population) even for devices cleared by FDA/CE; build subgroup performance reporting (age, sex, nationality, site) into the evaluation pipeline.
- **Source**: SFDA MDS-G010 v1.0, "Clinical Evaluation". URL as SFDA-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published.

#### SFDA-08: AI-specific risk management
- **Requirement**: Risk management should follow ISO 14971:2019, address AI-specific risks (data management, feature extraction, training, evaluation, cyber security, data drift, bias, automation bias), include data scientists, and have a plan covering criteria that trigger an update, risk management of the update process and provisions for returning to a previous version. Risk controls should cover data integrity across the lifecycle and operational controls such as human oversight and, for autonomous systems, a hand-off strategy.
- **Engineering implication**: Maintain an AI hazard log; implement model versioning with one-click rollback; drift monitoring with defined retraining triggers; human-in-the-loop confirmation for clinical outputs; documented hand-off for any autonomous action.
- **Source**: SFDA MDS-G010 v1.0, "Risk Management" (citing AAMI CR34971:2022). URL as SFDA-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published.

#### SFDA-09: QMS, traceability and real-world performance monitoring for AI
- **Requirement**: AI/ML devices are designed, manufactured and monitored under ISO 13485, including configuration and change management that records change history and enables recovery or recreation of past versions. Manufacturers must continuously monitor safety, effectiveness and performance in real-world use, and maintain vigilance for security threats.
- **Engineering implication**: Version code, model weights, training-data snapshots and configuration together so any past release can be rebuilt. Ship telemetry for real-world performance (with privacy controls) and feed it into PMS reports.
- **Source**: SFDA MDS-G010 v1.0, "Clinical Evaluation" (post-market monitoring) and "Quality Management Systems". URL as SFDA-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published.

#### SFDA-10: Pre-market cybersecurity file (MDS-G38)
- **Requirement**: Submit cybersecurity information through the MDMA system: cybersecurity risk management complementing ISO 14971 with hazard analysis and a risk-to-control traceability matrix; secure design keeping software malware-free; security properties and dependencies; security-relevant third-party components; applied standards, test reports and weakness testing; role-based authentication, no hard-coded or default passwords, two-factor authentication for privileged access, and secure (e.g. code-signed) updates.
- **Engineering implication**: Produce a threat model, traceability matrix, component inventory (SBOM is the practical way to meet the third-party component requirement, though G38 does not use the term), penetration/SAST/DAST reports, and enforce signed updates and MFA for admin access.
- **Source**: SFDA MDS-G38 v1.0 (18/6/2019). https://sfda.gov.sa/sites/default/files/2019-10/MDS-G38.pdf
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published; SFDA reported (Mar 2026) a new guidance on medical device cybersecurity risks is under development.

#### SFDA-11: Post-market cybersecurity (MDS-G37)
- **Requirement**: Manufacturers should run a cybersecurity risk-management programme: monitor vulnerability sources, monitor third-party components through the product life, verify and validate patches, assess vulnerability impact, run intake and handling processes, use threat modelling, adopt a coordinated vulnerability disclosure policy, and deploy mitigations early. No numeric remediation deadlines are set.
- **Engineering implication**: Publish a vulnerability disclosure policy and security contact; continuous SCA/CVE monitoring of dependencies; a patch-release process with V&V; customer security advisories.
- **Source**: SFDA MDS-G37 v1.0 (18/6/2019). https://sfda.gov.sa/sites/default/files/2019-10/MDS-G37.pdf
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Published.

#### SFDA-12: Adverse event and FSCA reporting to the NCMDR
- **Requirement**: Report adverse events or complaints within 2 days if they represent a serious public health threat, 10 days if they may cause or contribute to death or serious injury, and 30 days otherwise; respond to NCMDR follow-ups within 5 days. FSCAs affecting KSA are reported within 2 days of the FSCA letter. Healthcare providers appoint an NCMDR contact officer; manufacturers and ARs appoint an authorised person and keep written incident procedures.
- **Engineering implication**: In-product incident and complaint capture with timestamps and severity triage, so the 2/10/30-day clocks can be met; ability to identify affected installations and versions quickly for FSCA.
- **Source**: SFDA MDS-REQ 11 v2 (23/03/2023). https://www.sfda.gov.sa/sites/default/files/2023-08/MDS_REQ%2011_V2_En.pdf
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### SFDA-13: UDI and the SAUDI-DI database
- **Requirement**: Medical devices and accessories carry a UDI (UDI-DI plus UDI-PI, which may include software identification) from GS1, HIBCC or ICCBBA; data must be in the SAUDI-DI database when the device is placed on the market, checked at least annually, and revised within 10 days of a change. SFDA cites "MDS-REQ 7 Requirements for Unique Device Identification" (2025 update).
- **Engineering implication**: Display the UDI in the software (e.g. About screen) with the software version as UDI-PI; process to update SAUDI-DI within 10 days of a release that changes registered data.
- **Source**: SFDA presentations to IMDRF: https://www.imdrf.org/sites/default/files/2025-09/UDI%20%28SFDA%29.pdf ; https://www.imdrf.org/sites/default/files/2026-03/Saudi%20Arabia.pdf
- **Confidence**: Confirmed (secondary) — regulator slides; MDS-REQ 7 text, class deadlines and SaMD-specific UDI rules **Unconfirmed**.
- **As of 2026-10**: In force.

### F. Accreditation and AI-in-health guidance

#### SHC-01: CBAHI hospital standards include Management of Information and Medical Records chapters
- **Requirement**: CBAHI's National Hospital Standards (3rd edition, 2015, effective 1 Jan 2016) include chapters MOI (Management of Information) and MR (Medical Records). Telemedicine entities are expected to hold CBAHI accreditation (NHIC 2018 draft).
- **Engineering implication**: Hospital clients will test EMR features (record completeness, authentication of entries, confidentiality, availability/downtime, abbreviations, retention) against MOI/MR during surveys. Obtain the client's current CBAHI manual and map features to its standards.
- **Source**: CBAHI National Hospital Standards, 3rd edition (copy hosted by KFSH&RC). https://eservices.kfshrc.edu.sa/store/media/bwr.pdf
- **Confidence**: Confirmed (secondary) for chapter existence; individual MOI/MR standard texts and any newer edition **Unconfirmed**.
- **As of 2026-10**: Check whether a 4th edition is in force.

#### AI-01: AI-in-health governance is principles-based outside SFDA
- **Requirement**: Beyond SFDA's device rules (SFDA-07 to SFDA-09), the AI guidance we found is national and general: SDAIA AI Ethics Principles 2.0 (risk tiers; compliance required for limited/high-risk systems; Version 2.0 removed the v1.0 waiver for systems serving public health) and SDAIA Generative AI Guidelines (Jan 2024). No binding MoH/SHC AI-in-health regulation was confirmed.
- **Engineering implication**: Treat clinical AI as high-risk under SDAIA principles: name a Responsible AI officer, run the self-assessment, document transparency and human oversight. Details in `national.md` NAT-43 and NAT-44.
- **Source**: Al Tamimi, "AI Ethics Principles Version 2.0" https://www.tamimi.com/news/ai-ethics-principles-version-2-0 ; Digital Policy Alert https://digitalpolicyalert.org/event/17196-published-sdaia-generative-ai-guidelines
- **Confidence**: Confirmed (secondary). Absence of a MoH/SHC AI-in-health instrument: **Unconfirmed** (journal articles in 2026 describe Saudi "AI health policy" but we could not read them).
- **As of 2026-10**: Published.

### G. Cross-references to the national layer (not counted)

- **PDPL health data**: Health Data is Sensitive Data; Implementing Regulations Art. 26 (per Addleshaw Goddard) requires documenting all stages of health-data processing with a responsible person identified for each stage; sector regulators are to add controls with SDAIA. See `national.md` NAT-02, NAT-09. Source: https://www.addleshawgoddard.com/en/insights/insights-briefings/2023/data-protection/impact-regulations-saudi-personal-data-protection-law/ (Confirmed (secondary)).
- **Transfers and offshore access**: see `national.md` NAT-24 to NAT-27 (remote access from abroad treated as a transfer).
- **Hosting / residency**: see `national.md` NAT-28 to NAT-30, NAT-38, NAT-41 (government health data residency, CST cloud, NCA managed-SOC-in-KSA, CSCC hosting).

---

## Offshore access and development: what restricts it (summary)

| Rule | Effect on non-KSA access or development | Confidence |
|---|---|---|
| No explicit health-data hosting rule in the MoH/NHIC instruments we read (HIE Policies, IS0101, telehealth regulations are silent on location) | The health-sector instruments themselves do not localise data; restrictions come from the national layer | Confirmed (primary) for silence of those texts |
| `national.md` NAT-27 (PDPL transfer regulation / SCCs) | Offshore remote access to Saudi patient data counts as a transfer: needs a transfer basis, safeguards and a risk assessment; health data is excluded from most exceptions | See national file |
| `national.md` NAT-29, NAT-30 (NDMO / CoM Resolution 555 / CST) | MoH, health-cluster and other government health data: hosting in KSA expected | See national file |
| `national.md` NAT-38 (NCA ECC 4-1-3-2) | Managed security operations using remote access for in-scope entities must be fully inside KSA | See national file |
| NHIC-08 (IS0303 §7.3.4) | MFA mandatory for remote access to HIE; SHOULD for remote access to PHCS systems — applies to offshore support staff | Confirmed (primary) |
| NHIC-07 (IS0303 §6.3.5) | HIE user accounts need face-to-face ID proofing with government photo ID (and SCFHS licence for clinicians) — offshore engineers should not hold clinical HIE user accounts; use separate, non-PHI support roles | Confirmed (primary) |
| NHIC-11 (IS0303 §11.3) | Moving data offshore for analytics/AI training needs ethics approval, DUA and de-identification risk assessment | Confirmed (primary) |
| CHI-07 (NPHIES IP whitelisting) and CHI-04 (NPHIES-issued certificates) | NPHIES connections come from whitelisted IPs with NPHIES certificates; whether non-KSA IPs are accepted for test or production is unknown | Confirmed (primary) / Unconfirmed |
| TEL-07 | Practitioners abroad must register in KSA; foreign partner facilities need contracts and Saudi compliance | Confirmed (primary) |
| SFDA-04, SFDA-07 | Overseas manufacturers may need a KSA authorised representative; AI devices developed abroad should be locally validated | Confirmed (primary) |

Practical default for builds: host Saudi patient data in KSA, give offshore teams access only to synthetic or properly de-identified data, and route any production support through KSA-based or PDPL-transfer-compliant arrangements with MFA and full audit.

---

## Watch items

1. **Telehealth regulation status**: the MoH "Legal Regulations for Telehealth Services" has inconsistent dates (header March 2022; Art. 3(2) to 31 Dec 2021); a related set is marked cancelled on Qanoniah; the NHIC 2018 regulations were a draft. A secondary 2025 article mentions an update "in late 2023" that we could not verify. Confirm the current instrument before finalising TEL-01 to TEL-08.
2. **NPHIES IG version**: portal shows "Edition 1, 1.0.0 – STU, Draft as of 2025-12-03" replacing PDF IG V2.6; track production version and DRG-related releases.
3. **NPHIES clinical / Unified Health Record**: likely to become the clinical exchange route; watch for published FHIR profiles and any connection mandate for private providers.
4. **SFDA cybersecurity**: new "Medical Device Cybersecurity Risks" guidance under development (IMDRF, Mar 2026) may replace or add to MDS-G37/G38.
5. **SFDA MDS-REQ 1**: v6.0 (2021) is the latest we retrieved; check for a newer version. Also MDS-REQ 8 (SFDA approval for medical-device advertising and campaigns, listed 2026-07-20) may affect SaMD marketing and app-store content.
6. **SFDA device bundling** (draft MDS-G-028) and the updated Innovative Medical Devices pathway may change MDMA routes for multi-module software.
7. **PDPL health-data controls**: SDAIA and sector regulators were to issue additional health-data controls; PDPL Implementing Regulation amendments are in consultation until 5 Nov 2026 (see `national.md`).
8. **Insurance Authority**: watch for insurer/TPA cybersecurity and data requirements now that it supervises health insurance.
9. **Eng. note**: IS0101 names TLS_RSA_WITH_AES_128_CBC_SHA and IS0303 allows 3DES; if a regulator or client insists on these literally, raise a deviation rather than weakening security.

---

## What could not be confirmed

- A general **medical-record retention period** for providers (MOH-06).
- Any **explicit MoH/NHIC/CHI rule requiring health data to be hosted in KSA**; we found none in the health-sector texts read (the national layer covers this).
- **CHI-specific data protection or cybersecurity requirements** on providers, payers, TPAs or vendors; and the Insurance Authority's equivalents.
- A formal **CHI circular or deadline mandating NPHIES** use (mandatory status is inferred from the IG and vendor-certification requirement).
- Whether NPHIES accepts **non-KSA source IPs**; content of the **Vendor Certification Program V4.0** and the **Readiness & Activation Guide**.
- A **national clinical FHIR implementation guide** or Saudi Core profiles; any **mandate to connect to the Unified Health Record**.
- **Wasfaty** technical integration requirements, operator, and coverage of private prescribers; whether private providers must issue sick leave only via **Seha**.
- Current **telehealth** instrument; rules on **recording** consultations, **audio-only** consultations today, **controlled-drug** e-prescribing via telehealth, and use of a specific national digital-identity service.
- **SFDA MDS-G23** (Guidance on Software as a Medical Device) version, date and content; **MDS-REQ 7** text and UDI deadlines for software; whether SFDA accepts a predetermined change-control plan for AI.
- Whether the **IS0304 certification scheme** and the **SeHE IHE profiles** are still operated.
- **CBAHI** MOI/MR standard texts and whether a newer hospital standards edition is in force.
- A binding **MoH/SHC AI-in-health** instrument.
- The exact PDPL article number on health-data controls in the Law itself (secondary sources disagree; see `national.md`).
- Unreliable claims found and excluded: one 2025 law-firm blog said Saudi private facilities must interoperate with "NABIDH" (that is Dubai's platform); a 2026 secondary article described MDS-G38 as "Guidance on Pre-Market Submission" (the SFDA PDF title is "Guidance to Pre-Market Cybersecurity of Medical Devices").

---

## Primary sources consulted

- IS0303 Saudi Health Information Exchange Policies v1.0 (SHC, 21 Apr 2016): https://nhic.gov.sa/standards/Policies/IS0303-Saudi-Health-Information-Exchange-Policies-v1.0.pdf
- IS0303 Saudi Health Information Exchange Policies v1.0 (MoH, 22 Feb 2015): https://moh.gov.sa/en/Ministry/ehealthstd/Documents/eHealth%20Standards%20Files/Policies/IS0303%20Saudi%20Health%20Information%20Exchange%20Policies%20v1.0.pdf
- IS0101 Saudi eHealth Security and Privacy IS v1.0 (SHC, 21 Apr 2016): https://nhic.gov.sa/standards/General/IS0101-Saudi-eHealth-Security-and-Privacy-IS-v1.0.pdf
- IS0102 Saudi eHealth Document Sharing IS v1.0: https://moh.gov.sa/en/Ministry/ehealthstd/Documents/eHealth%20Standards%20Files/eReferral%20and%20eTransfer%202/IS0102%20Saudi%20eHealth%20Document%20Sharing%20Interoperability%20Specification%20v1.0.pdf
- IS0304 Saudi HIE Testing and Certification Policies v1.0: https://www.moh.gov.sa/en/Ministry/ehealthstd/Documents/eHealth%20Standards%20Files/Policies/IS0304%20Saudi%20Health%20Information%20Exchange%20Testing%20and%20Certification%20Policies%20v1.0.pdf
- Law of Practising Healthcare Professions (English translation): https://misa.gov.sa/app/uploads/2025/07/Law-of-Practicing-Healthcare-Professions.pdf
- Legal Regulations for Telehealth Services (MoH): https://www.moh.gov.sa/en/Ministry/Rules/Documents/Legal-Regulations-for-Telehealth-Services.pdf
- MoH Sehhaty service page: https://www.moh.gov.sa/en/eservices/sehhaty/pages/default.aspx
- NPHIES Healthcare Financial Services IG (index, introduction, conformance, message exchange, roadmap, artifacts, value sets): https://portal.nphies.sa/ig/index.html
- NPHIES Academy, System Vendors Onboarding Course: https://v-academy.nphies.sa/courses/11/system-vendors-onboarding-course?lang=en
- CHI announcement on transfer to Insurance Authority (4 Mar 2024): https://www.chi.gov.sa/en/MediaCenter/News/Pages/CHI-announces-transferring-roles-and-responsibilities-of-the-health-insurance-sector-to-IA.aspx
- SFDA MDS-G010 (AI/ML) v1.0: https://sfda.gov.sa/sites/default/files/2023-01/MDS-G010ML.pdf ; listing https://www.sfda.gov.sa/en/regulations/87661
- SFDA MDS-G27 Digital Health Products v1.0: https://sfda.gov.sa/sites/default/files/2026-08/MDS-G027.pdf
- SFDA MDS-REQ 1 v6.0: https://www.sfda.gov.sa/sites/default/files/2021-12/REQ1En.pdf
- SFDA MDS-G38 v1.0: https://sfda.gov.sa/sites/default/files/2019-10/MDS-G38.pdf
- SFDA MDS-G37 v1.0: https://sfda.gov.sa/sites/default/files/2019-10/MDS-G37.pdf
- SFDA MDS-REQ 11 v2: https://www.sfda.gov.sa/sites/default/files/2023-08/MDS_REQ%2011_V2_En.pdf
- SFDA regulatory updates and UDI slides (IMDRF): https://www.imdrf.org/sites/default/files/2026-03/Saudi%20Arabia.pdf ; https://www.imdrf.org/sites/default/files/2025-09/UDI%20%28SFDA%29.pdf

### Secondary sources used

- NHIC Telemedicine Regulations V1.3 (2018 draft; primary text hosted by DataGuidance): https://www.dataguidance.com/sites/default/files/saudi_arabia_telemedicine_policy.pdf
- Qanoniah: Statute of the National Center for Health Information https://qanoniah.com/en/File/DmWqyAxNgpoPlkJoP26zvBXaE-Statute-of-the-National-Center-for-Health-Information ; Regulatory Rules for Telemedicine Services https://qanoniah.com/en/File/EPj1RJOmdzLRbOeLDZAYpM5wN-Regulatory-Rules-for-Telemedicine-Services
- Al Tamimi: telemedicine licensing (2019) https://www.tamimi.com/news/healthcare-licences-now-available-for-telemedicine-and-remote-care-centres-in-saudi-arabia ; telemedicine regulation https://tamimi.com/law-update-articles/the-regulation-and-licensing-of-telemedicine-in-saudi-arabia ; AI Ethics Principles 2.0 https://www.tamimi.com/news/ai-ethics-principles-version-2-0
- Chambers Digital Healthcare 2022 – Saudi Arabia: https://practiceguidesdev.chambers.com/practice-guides/digital-healthcare-2022/saudi-arabia ; Chambers Data Protection & Privacy 2026 – Saudi Arabia: https://practiceguides.chambers.com/practice-guides/data-protection-privacy-2026/saudi-arabia
- Addleshaw Goddard on PDPL Implementing Regulations: https://www.addleshawgoddard.com/en/insights/insights-briefings/2023/data-protection/impact-regulations-saudi-personal-data-protection-law/
- Bird & Bird, health data under the PDPL (2025): https://twobirds.com/en/insights/2025/saudi-arabia-health-data-under-the-personal-data-protection-law
- Clyde & Co on ECC-2:2024: https://www.clydeco.com/en/insights/2025/01/saudi-arabia-essential-cybersecurity-controls
- Karger SJHSR, NPHIES article (2024/2025): https://karger.com/sjh/article/5/1/1/917352/Unveiling-the-National-Platform-for-Health-and
- Frontiers in Medicine 2024 (Wasfaty): https://www.frontiersin.org/journals/medicine/articles/10.3389/fmed.2024.1487852/full
- Saudi Gazette (Seha sick leave, 2022): https://saudigazette.com.sa/article/625018
- CBAHI National Hospital Standards 3rd ed. (KFSH&RC copy): https://eservices.kfshrc.edu.sa/store/media/bwr.pdf
- IHE Saudi Arabia: https://www.ihe.net/ihe-saudi-arabia/ ; FHIR registry Saudi jurisdiction: https://packages.fhir.org/jurisdictions/SA
- Lean Business Services, NPHIES Unified Health Record: https://lean.sa/en/products-and-solutions/nphies-unified-health-record
- Digital Policy Alert, SDAIA Generative AI Guidelines: https://digitalpolicyalert.org/event/17196-published-sdaia-generative-ai-guidelines
- US ITA, Insurance Authority launch: https://www.trade.gov/index.php/market-intelligence/saudi-arabia-financial-services-new-insurance-regulatory-body-launched
