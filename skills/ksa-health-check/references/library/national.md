# National layer: data protection, cyber, cloud and AI (KSA)

> **Library status:** researched from primary and secondary sources on 2026-10-10. Each item shows its source and confidence. Saudi instruments are authoritative in Arabic; English wording here is a working translation. Rules change: check the "As of" note and the current official text before relying on an item, and treat "Unconfirmed" items as questions, not requirements. Engineering guidance, not legal advice.



Part of the KSA healthcare requirements library. Scope: the **national** layer (SDAIA/PDPL, NDMO, NCA, CST, SDAIA AI guidance, Anti-Cyber Crime Law) as it applies to systems that process health data. Sector rules (MoH, Saudi Health Council, CHI, SFDA, NPHIES, Seha Virtual etc.) belong in the sector file and are mentioned here only where a national instrument points to them.

Researched: 2026-10-10. Not legal advice. The Arabic text of every Saudi instrument prevails over any English translation.

---

## How to read this file

- **ID**: `NAT-xx` is a stable identifier for one requirement in the national layer. IDs are not legal references; the legal reference is in the *Source* field.
- **Requirement**: what the rule requires, in plain language.
- **Engineering implication**: what the build team has to design, configure or produce.
- **Source**: the instrument, plus the article or control number **only where we have checked it** against the text, with a URL.
- **Confidence**:
  - **Confirmed (primary)**: checked against the official text, or an official translation hosted on a government site (sdaia.gov.sa, dgp.sdaia.gov.sa, nca.gov.sa / cdn.nca.gov.sa, cst.gov.sa, misa.gov.sa, mcit.gov.sa).
  - **Confirmed (secondary)**: taken from a reputable law-firm or practice-guide summary (Clyde & Co, Latham, Baker McKenzie, Mayer Brown, Al Tamimi, CMS, Chambers, HSF) because the primary text could not be read in full.
  - **Unconfirmed**: we could not verify the detail. Do not build hard logic on it without checking.
- **As of 2026-10**: the status at the research date, including any pending changes.
- **Applicability tags** in brackets: **[All]** = any controller processing health data of people in KSA; **[Gov]** = government entities and their affiliates (e.g. MoH and health-cluster facilities) and their vendors; **[CNI]** = private owners or operators of Critical National Infrastructure; **[Non-CNI]** = private entities that are not CNI; **[Critical]** = systems classed as critical under CSCC.

---

## Key instruments

| Instrument | Issuer | Version / date (as verified) | Binding on | Status 2026-10 |
|---|---|---|---|---|
| Personal Data Protection Law (PDPL) | Royal Decree M/19, 9/2/1443H; amended by Royal Decree M/148, 5/9/1444H | In force 14 Sep 2023; one-year grace period ended 14 Sep 2024 | All controllers and processors processing personal data in KSA, or data of KSA residents from abroad (Art. 2) | In force and enforced (48 enforcement decisions announced by mid-Jan 2026, per Clyde & Co) |
| PDPL Implementing Regulations | SDAIA | Published 7 Sep 2023 | As PDPL | In force. **Draft amendments under public consultation 6 Oct to 5 Nov 2026** (data localisation, breach threshold, DPO, registration) |
| Regulation on Personal Data Transfer outside the Kingdom | SDAIA | First issued Sep 2023; amended version issued 1 Sep 2024 | As PDPL | In force |
| Standard Contractual Clauses (4 sets), BCR guideline, transfer risk-assessment guideline | SDAIA | 2024 (with the amended Transfer Regulation) | Controllers relying on these safeguards | In force / guidance |
| Rules for Appointing a Personal Data Protection Officer | SDAIA | Published 27 Aug 2024 (secondary) | Controllers meeting the DPO triggers | In force |
| Rules Governing the National Register of Controllers within the Kingdom | SDAIA | Effective on publication; date not shown | Mandatory-registration categories incl. sensitive-data controllers | In force |
| Guidelines: destruction, anonymisation and pseudonymisation; minimum personal data; records of processing; privacy policy; disclosure cases | SDAIA | Dates not shown on portal | Guidance (non-binding) | Published |
| National Data Governance Interim Regulations (incl. Data Classification Policy, Data Sharing Policy) | SDAIA / NDMO | 2020 | Public entities; others when handling government data | In force (interim) |
| National Data Management and Personal Data Protection Standards | NDMO | v1.5, Jan 2021 (secondary) | Public entities and business partners handling government data | In force |
| General Rules for Secondary Use of Data | NDMO | Date not shown | Data-sharing requests involving government entities | Published |
| Essential Cybersecurity Controls ECC-2:2024 | NCA | 2024; 108 controls (down from 114) | Government entities and affiliates (inside and outside KSA); private owners/operators/hosts of CNI | In force |
| Cloud Cybersecurity Controls CCC-2:2024 | NCA | 2024 | CSPs serving in-scope tenants; tenants = government entities and private CNI using cloud | In force |
| Critical Systems Cybersecurity Controls CSCC-1:2019 | NCA | 2019 (no newer version found) | Organisations owning or operating systems they class as critical | In force |
| Data Cybersecurity Controls DCC-1:2022 | NCA | Published 18 Sep 2022 | Extension of ECC (scope as ECC, per secondary sources) | In force |
| Telework Cybersecurity Controls TCC-1:2021 | NCA | Page dated 2 Jun 2022 | Extension of ECC | In force |
| Non-CNI Private Sector Entities Cybersecurity Controls NCNICC-1:2025 | NCA | Adopted 28 Dec 2025 (secondary) | Private non-CNI entities in Category A (large) or B (SME) that NCA notifies | In force; compliance timetable unconfirmed |
| Cloud Computing Services Provisioning Regulations (replace CCRF v3) | CST | Decision 506/1445, 8 Oct 2023 (fourth version) | CSPs and cloud subscribers in KSA | In force |
| AI Ethics Principles (v2.0) | SDAIA | Sep 2023 | All AI stakeholders in KSA; binding force unclear | Published |
| Generative AI Guidelines (for Government; for Public) | SDAIA | Jan 2024 | Guidance | Published |
| Deepfakes Guidelines | SDAIA | Original May 2025; reported as issued May 2026 (secondary) | Guidance | Published |
| Draft Global AI Hub Law | CST | Consultation 14 Apr to 14 May 2025 | Data-centre "hubs" / data embassies | Draft; not enacted as far as we could find |
| Anti-Cyber Crime Law | Royal Decree M/17, 8/3/1428H (26 Mar 2007) | 2007 | Everyone | In force |

---

## Requirements

### A. PDPL: scope, legal basis and transparency

#### NAT-01: Extraterritorial scope, including deceased patients [All]
- **Requirement**: The PDPL applies to any processing of personal data in KSA, and to processing of data of people living in KSA by any party outside KSA. It also covers data of deceased people where it would identify them or a family member.
- **Engineering implication**: Treat every system holding KSA patients' data as in scope, wherever it is hosted or operated. Retention, access and rights logic must not drop protections when a patient dies (status = deceased does not mean out of scope).
- **Source**: PDPL Art. 2(1). https://misa.gov.sa/app/uploads/2025/08/PersonalDataProtectionLaw.pdf (English translation on a government site); Arabic official text: https://dgp.sdaia.gov.sa/wps/portal/pdp/knowledgecenter/details/PDPL
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### NAT-02: Health, genetic and biometric data are Sensitive Data [All]
- **Requirement**: Sensitive Data includes Health Data (physical, mental or psychological condition, or Health Services received, including medication supply), Genetic Data, and biometric data used to identify a person. It also includes data showing that one or both parents are unknown. Stricter rules apply to Sensitive Data throughout the PDPL.
- **Engineering implication**: Tag sensitive fields and record types in the data model (diagnoses, notes, results, prescriptions, appointments at clinical services, genomic results, biometric templates, foundling/unknown-parent indicators). Use the tag to drive consent, access, transfer, DPIA, retention and logging rules. Note that appointment and pharmacy data count as Health Data because they relate to "Health Services received".
- **Source**: PDPL Art. 1(11), 1(12), 1(13), 1(14). URL as NAT-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### NAT-03: Lawful basis; legitimate interest is not available for health data [All]
- **Requirement**: Consent is the default basis for processing and for any change of purpose. Exceptions include: actual interests of the data subject where contact is impossible or difficult; processing under another law or a prior agreement the data subject is party to; public-entity security or judicial purposes; and legitimate interest, which **cannot** be used for Sensitive Data. Collection or processing for new purposes is also allowed where necessary to protect public health, public safety, or the life or health of specific individuals.
- **Engineering implication**: Record a lawful basis per processing purpose (in the processing register and in data lineage). Do not use legitimate interest for any health-data purpose such as analytics or product improvement. Care delivery may rest on "another law / prior agreement" (Art. 6(2)), but how SDAIA applies this to routine clinical care is **Unconfirmed**. Design so purposes that need consent can be switched on and off per patient.
- **Source**: PDPL Art. 5(1), 6(1)–(4), 10(5), 10(7). URL as NAT-01.
- **Confidence**: Confirmed (primary) for the text; how it applies to clinical care is Unconfirmed.
- **As of 2026-10**: In force.

#### NAT-04: Consent quality, explicit consent for health data, guardians and withdrawal [All]
- **Requirement**: Consent must be freely given, for clearly stated specific purposes, given by someone with full legal capacity, documented in a verifiable way, and obtained separately for each purpose. Processing Sensitive Data needs **explicit** consent. A guardian consents for people who fully or partly lack capacity. Consent can be withdrawn at any time. A service cannot be made conditional on consent unless the service is directly related to the processing.
- **Engineering implication**: Build a versioned consent ledger (purpose, text version, timestamp, channel, identity of the consenting person, guardian link). Use an explicit affirmative action for health-data purposes; no pre-ticked boxes or bundled purposes. Provide a self-service withdrawal path that takes effect downstream. Model guardian or proxy relationships for minors and adults lacking capacity. The age of capacity is not defined in the PDPL (Latham), so it is **Unconfirmed**; make it configurable.
- **Source**: PDPL Art. 5(1)–(2), 7; Implementing Regulations Art. 11(1)–(2). https://dgp.sdaia.gov.sa/wps/portal/pdp/knowledgecenter/details/PDPL2 ; Latham: https://www.lw.com/en/insights/2023/12/Saudi-Arabias-data-protection-law-enters-into-force
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force. The draft amendments add verifiable consent evidence and easy withdrawal for marketing (Arts. 28–29).

#### NAT-05: Fully automated decisions need explicit consent and a DPIA [All]
- **Requirement**: Decisions made entirely by automated processing need explicit consent, and fully automated decisions trigger a mandatory impact assessment.
- **Engineering implication**: For AI triage, risk scoring, eligibility or diagnostic-support features, either keep a qualified human in the decision (and log their review), or capture explicit consent and complete a DPIA before go-live. Log model version, inputs and outputs per decision so it can be explained and contested.
- **Source**: Implementing Regulations Art. 11(2), Art. 25(1). URL as NAT-04.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force. The draft amendments keep automated decisions as a DPIA trigger.

#### NAT-06: Privacy policy before collection, and notice at collection [All]
- **Requirement**: A privacy policy must be available before collection. It must cover purposes, the data collected, how data is collected, processed, stored and destroyed, and data subject rights. At direct collection the controller must state: the legal basis; the purpose; which fields are mandatory or optional; the collector's identity; recipients; **whether data will be transferred, disclosed or processed outside KSA**; the consequences of not providing data; and the data subject's rights.
- **Engineering implication**: Show a privacy notice in patient apps and portals before registration, in Arabic and English. Mark mandatory and optional fields in forms. Include an offshore-processing statement that matches the real data-flow map (NAT-25 to NAT-28), and keep the two in sync through configuration rather than hard-coded text.
- **Source**: PDPL Art. 12, 13. URL as NAT-01. SDAIA privacy-policy guideline: https://dgp.sdaia.gov.sa/wps/portal/pdp/knowledgecenter
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force. The draft amendments add a requirement for clear, simplified language suited to the audience, which in practice means Arabic versions (Clyde & Co).

#### NAT-07: Minimisation, purpose limitation, accuracy and propagating corrections [All]
- **Requirement**: Collect only the minimum data needed for a purpose directly related to the controller's activities. Stop collecting and destroy data that is no longer needed. Verify accuracy, completeness and currency before processing. When data is corrected, notify the correction to every entity it was transferred to.
- **Engineering implication**: Review every form and API field for necessity. Do not over-collect into free-text fields. Build correction propagation to downstream recipients (labs, insurers, health-information exchanges, referral partners) with a delivery log.
- **Source**: PDPL Art. 10, 11(1)–(4), 14, 17(1). URL as NAT-01. SDAIA minimum personal data guideline (knowledge centre).
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

### B. PDPL: rights, health-data controls and security

#### NAT-08: Data subject rights, a 30-day response window and lawful refusals [All]
- **Requirement**: Patients have the right to be informed, to access their data, to obtain a copy in a readable and clear format, to correction, completion or updating, and to destruction once data is no longer needed. Controllers must respond without delay and within 30 days. This can be extended by up to 30 more days for unusual effort or multiple requests, with prior notice and reasons. Controllers must verify identity and document all requests, including oral ones. Access may be limited where it would harm the data subject or others, and must be refused in the Art. 16 cases (e.g. violating another person's privacy, or the interests of a person lacking capacity). The PDPL has no data-portability right (Latham).
- **Engineering implication**: Build a rights-request workflow with identity verification, a 30-day SLA timer, an extension path with notice, and an audit trail. Provide record export in a readable, clear format. Include a clinician-review step that can redact third-party data or information judged harmful before release.
- **Source**: PDPL Art. 4, 9, 16, 21; Implementing Regulations Art. 3(1)–(2). URLs as NAT-01 and NAT-04.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force. The draft amendments would treat an unanswered request as **deemed rejected** after 30 days (plus any extension) and let the data subject complain to SDAIA.

#### NAT-09: Additional controls for Health Data: minimum access and segregation [All]
- **Requirement**: Access to Health Data, including medical files, must be limited to the minimum number of staff, and only as far as needed to provide health services or health insurance. The Implementing Regulations add the following. Apply the rules of the relevant health regulators. Reflect the PDPL in internal policies. Separate duties and tier staff access. Document each processing stage and the person responsible for it. Put compliance terms in processor agreements. Keep processing to the minimum.
- **Engineering implication**: Use fine-grained RBAC/ABAC (care-team, encounter or facility scoping) with no default all-patient access, plus an audited break-glass function with a reason code. Keep per-record, per-user access logs that can be reviewed. Map each processing stage to a named owner role. Enforce segregation of duties (for example, billing staff cannot see clinical notes unless needed).
- **Source**: PDPL Art. 23; Implementing Regulations Art. 26. URLs as NAT-01 and NAT-04.
- **Confidence**: Confirmed (primary). The list of health regulators named in IR Art. 26 is from a machine-assisted reading of the Arabic and should be re-checked.
- **As of 2026-10**: In force.

#### NAT-10: Security measures: follow NCA controls or recognised best practice; train staff; confidentiality survives employment [All]
- **Requirement**: Controllers must implement organisational, administrative and technical measures, including during transfer. They must comply with NCA controls and standards, or with recognised best practice where NCA controls are not binding on them. Staff must be trained and processing audited regularly. Anyone who processes personal data must keep it confidential even after their employment or contract ends.
- **Engineering implication**: Use ECC-2 (NAT-32 to NAT-39) or NCNICC (NAT-42) as the security baseline even where NCA controls do not bind you, and document that choice. Include PDPL training in onboarding. Make confidentiality clauses for staff and contractors survive termination.
- **Source**: PDPL Art. 19, 41; Implementing Regulations Art. 23; IR Art. 36 (training and audits, per Al Tamimi). URLs as NAT-01 and NAT-04; https://www.tamimi.com/news/observations-and-tips-on-data-issues-in-ksa/
- **Confidence**: Confirmed (primary) for Art. 19, 41 and IR Art. 23; Confirmed (secondary) for IR Art. 36.
- **As of 2026-10**: In force.

#### NAT-11: Processors and sub-processors [All]
- **Requirement**: Controllers must choose processors that give sufficient guarantees and must monitor their compliance periodically. The processing agreement must cover purpose, data categories, duration, prompt breach notification, whether foreign laws apply to the processor and their effect, and any sub-processors. Processors must follow instructions and flag unlawful ones in writing. Sub-processing needs the controller's prior approval and a chance to object. A processor that departs from instructions is treated as a controller.
- **Engineering implication**: Keep a vendor and sub-processor register that is linked to the data-flow map. Put PDPL-compliant DPAs in place with every SaaS, cloud, AI-model and support vendor, including foreign-law exposure (for example, US CLOUD Act) and breach-notice timelines short enough to meet 72 hours. Build a change-notice process for new sub-processors.
- **Source**: PDPL Art. 8; Implementing Regulations Art. 17(1)–(5). URLs as NAT-01 and NAT-04.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

### C. PDPL: breaches, accountability documents and governance

#### NAT-12: Notify SDAIA of a breach within 72 hours [All]
- **Requirement**: Notify SDAIA within **72 hours** of becoming aware of a breach, damage or unlawful access, where it could harm the data or the data subject's rights or interests. The notice must describe the incident and its timing, the affected subjects and data types, likely risks and measures taken, whether data subjects were told, and contact details. Information that is not yet available may follow later, with reasons for the delay. Keep copies of notifications and corrective actions. Notification goes through the National Data Governance Platform, and the Register Rules repeat the 72-hour requirement.
- **Engineering implication**: Build an incident runbook with a 72-hour clock that starts at awareness, and pre-built evidence capture (scope query for affected patients and data categories). Prepare a notification template matching the required content. Register on the platform in advance (NAT-17). Al Tamimi reports cases where entities could not file through the platform and emailed NDMO within 72 hours instead, so keep that fallback in the runbook.
- **Source**: PDPL Art. 20(1); Implementing Regulations Art. 24(1)–(3); Rules Governing the National Register of Controllers Art. 12. URLs as NAT-04; https://dgp.sdaia.gov.sa/wps/portal/pdp/knowledgecenter/details/Rulesandguidelinesp2 ; https://www.tamimi.com/news/observations-and-tips-on-data-issues-in-ksa/
- **Confidence**: Confirmed (primary). 72 hours confirmed.
- **As of 2026-10**: In force. **The draft amendment to IR Art. 24 would remove the harm threshold**, so every breach would be notified to SDAIA within 72 hours (consultation closes 5 Nov 2026). Design for notify-all now.

#### NAT-13: Notify affected patients without undue delay [All]
- **Requirement**: Notify data subjects without undue delay where the breach could harm them or their rights. Use plain language and describe the breach, the risks, mitigation, the controller or DPO contact, and steps the data subject can take.
- **Engineering implication**: Prepare patient notification templates in Arabic and English, with bulk-send capability (SMS, email, in-app) and delivery evidence. Build a harm-assessment step into the runbook, and record its result.
- **Source**: PDPL Art. 20(2); Implementing Regulations Art. 24(5). URLs as NAT-01 and NAT-04.
- **Confidence**: Confirmed (primary). No fixed hour limit for individuals.
- **As of 2026-10**: In force. The draft keeps a damage-based test for individuals.

#### NAT-14: DPIA before processing health data [All]
- **Requirement**: A written impact assessment is required for products and services. It is mandatory where processing involves Sensitive Data, links datasets from different sources, involves large-scale or repeated processing of minors' data, continuous monitoring, emerging technologies, or fully automated decisions, or is likely to cause serious privacy harm. Minimum content: purpose and legal basis, description, scope, context, necessity and proportionality, risks, and mitigations. Give processors a copy, and repeat the assessment if it finds harm.
- **Engineering implication**: Make a DPIA a release gate for every health product, major feature, AI model and new data integration. Store it with the architecture record, and update it when data flows change.
- **Source**: PDPL Art. 22; Implementing Regulations Art. 25(1)–(4). URLs as NAT-01 and NAT-04.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force. The draft adds explicit triggers for people lacking capacity and for automated decisions affecting rights.

#### NAT-15: Records of processing activities, kept for the processing period plus 5 years [All]
- **Requirement**: Keep written, accurate, current records of processing. They must include controller contact details, purpose, data-subject categories, recipients, transfers outside KSA, and expected retention. Make them available to SDAIA on request. Keep them for the whole processing period plus five years after it ends.
- **Engineering implication**: Keep the register machine-readable (for example YAML or JSON in the repository, or a GRC tool) and generate it from the data inventory where possible. Keep historical versions for 5 years after a processing activity is retired.
- **Source**: PDPL Art. 31; Implementing Regulations Art. 33(1)–(4). URLs as NAT-01 and NAT-04.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force. The draft amendments would simplify the required record content.

#### NAT-16: Data Protection Officer for health-data controllers [All]
- **Requirement**: A DPO is required where core activities involve processing Sensitive Data, where core activities involve regular and systematic monitoring, or where a public entity provides large-scale personal-data services. The DPO Rules give health data from wearables as a monitoring example, and an insurer handling health data as a core activity. The DPO may be an employee or an external contractor. Data subjects need an accessible way to contact the DPO, and the DPO's details must be filed with SDAIA through the National Data Governance Platform and kept up to date. The Register Rules allow DPO details for contractors outside KSA, which implies the DPO need not be in KSA.
- **Engineering implication**: Most hospitals, clinics, health-tech platforms and health insurers should assume they need a DPO. Show DPO contact details in apps and privacy notices. Route rights requests and breach workflows to the DPO.
- **Source**: PDPL Art. 30(2); Implementing Regulations Art. 32(1)–(4); Rules for Appointing a DPO (27 Aug 2024); Register Rules Art. 5–8. https://dgp.sdaia.gov.sa/wps/portal/pdp/knowledgecenter ; https://securiti.ai/saudi-arabia-rules-for-appointing-personal-data-protection-officer
- **Confidence**: Confirmed (primary) for triggers; Confirmed (secondary) for the DPO Rules detail. The DPO-location inference is Unconfirmed.
- **As of 2026-10**: In force. The draft amendments would drop the "large-scale" qualifier for public entities and expand the DPO's role, including being SDAIA's direct contact.

#### NAT-17: Register in the National Register of Controllers [All]
- **Requirement**: Registration on the National Data Governance Platform is mandatory for government entities, for controllers whose main activity is processing personal data, and for **controllers processing Sensitive Data**. Al Tamimi reports that SDAIA and sector regulators actively request registration, usually with a 30-day window.
- **Engineering implication**: Register before go-live. Assign named platform representatives. Registration is also the channel for breach notifications (NAT-12).
- **Source**: Rules Governing the National Register of Controllers within the Kingdom, Art. 2–5. https://dgp.sdaia.gov.sa/wps/portal/pdp/knowledgecenter/details/Rulesandguidelinesp2
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force. Rules for controllers **outside** KSA are said to be issued separately (Unconfirmed whether issued). The draft amendments would move the registration criteria into IR Art. 34 and add controllers that transfer data outside KSA.

#### NAT-18: Retention and destruction, including backups [All]
- **Requirement**: Destroy personal data without undue delay once it is no longer needed. Data may be kept in non-identifying form. Where another law sets a retention period, destroy the data at the end of that period or when the purpose ends, whichever is later. Keep data while it is needed for a pending court case. Destruction is also required when a data subject requests it, when consent (the only basis) is withdrawn, or when processing is unlawful. Destroy all copies, **including backups**, subject to statutory retention, and notify recipients.
- **Engineering implication**: Build a retention schedule engine keyed to record type. Health-record retention periods come from MoH and sector rules, which are out of scope here and **Unconfirmed**. Add a litigation-hold flag. Make backup retention and expiry consistent with the schedule. Use crypto-shredding or other provable destruction, and keep destruction certificates. Archiving is **not** destruction (SDAIA guideline).
- **Source**: PDPL Art. 11(4), 18; Implementing Regulations Art. 8(1)–(2); SDAIA Guideline on Destruction, Anonymisation and Pseudonymisation. URLs as NAT-01 and NAT-04; https://dgp.sdaia.gov.sa/wps/portal/pdp/knowledgecenter/details/PersonalDataDestruction
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### NAT-19: Anonymisation and pseudonymisation [All]
- **Requirement**: Anonymised data is no longer personal data, but the controller must make re-identification impossible, assess re-identification risk, apply controls and test the technique over time. Pseudonymised data remains personal data, and the linking key must be kept separately.
- **Engineering implication**: Before any analytics, AI training or data-sharing extract, run a de-identification pipeline (generalisation, aggregation, suppression, masking) with documented re-identification testing. Keep pseudonymisation keys in a separate store with separate access control (for example a KMS or HSM). Record the technique and rationale.
- **Source**: Implementing Regulations Art. 9(1)–(2); SDAIA Guideline on Destruction, Anonymisation and Pseudonymisation. URLs as NAT-04 and NAT-18.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: Guideline is non-binding; IR Art. 9 is binding.

#### NAT-20: Research, statistics and secondary use [All]
- **Requirement**: Data may be used without consent for scientific, research or statistical purposes if it does not identify the data subject, or if required by law or a prior agreement. The route of "destroy identity before disclosure" is **not available for Sensitive Data**. Secondary use of government data for R&D or the public interest follows NDMO's General Rules for Secondary Use: legitimate non-profit purpose, minimum data, source-entity approval or licence, and a secure sharing method.
- **Engineering implication**: Research and AI-training datasets drawn from health records should be anonymised (NAT-19) or backed by consent or a legal mandate. Data from MoH or government facilities needs the NDMO secondary-use process and a licence. Build cohort-extract tooling that enforces de-identification by default.
- **Source**: PDPL Art. 27; NDMO General Rules for Secondary Use of Data, Sections IV–VI. URL as NAT-01; https://dgp.sdaia.gov.sa/wps/portal/pdp/knowledgecenter/details/GeneralRulesforSecondaryUseofData
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### NAT-21: No marketing using health data; consent and opt-out for promotional messages [All]
- **Requirement**: Sensitive Data may not be processed for marketing. Advertising or awareness messages to personal contact channels need prior consent and a clear opt-out mechanism (public-entity awareness messages are exempt).
- **Engineering implication**: Keep clinical messages (appointment reminders, results) separate from promotional messages in the communications platform. Do not segment or target marketing on diagnoses or services received. Add consent and opt-out flags per channel, with suppression lists.
- **Source**: PDPL Art. 25, 26. URL as NAT-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force. The draft amendments (Arts. 28–29) would require verifiable consent evidence, and destruction of marketing-derived data on withdrawal.

#### NAT-22: Do not copy official identity documents unless required [All]
- **Requirement**: Official documents that identify data subjects may not be copied unless required by law or requested by a competent public authority.
- **Engineering implication**: In patient registration, capture and verify the ID number (for example through an official verification integration) rather than storing scans of ID cards or Iqamas by default. Whether MoH, CHI or NPHIES rules require copies in specific flows is **Unconfirmed**; if they do, cite that requirement in the processing register.
- **Source**: PDPL Art. 28. URL as NAT-01.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### NAT-23: Penalties and enforcement exposure [All]
- **Requirement**: Disclosing or publishing Sensitive Data unlawfully, with intent to harm or for personal benefit, can bring up to 2 years' imprisonment and/or a fine of up to SAR 3 million (which can be doubled for a repeat offence). Other violations can bring a warning or a fine of up to SAR 5 million per violation, doubled for repeats (capped at double). Penalties also include confiscation, publication of decisions, and civil compensation for material or moral damage. Enforcement committees are active: 48 decisions had been announced by mid-January 2026.
- **Engineering implication**: Insider misuse of health records is a criminal risk. Access logging and anomaly alerts (NAT-09, NAT-34) are the main deterrent and evidence base. Keep audit evidence that a regulator would accept.
- **Source**: PDPL Art. 35, 36, 38, 40. URL as NAT-01; Clyde & Co (Mar 2026): https://www.clydeco.com/en/insights/2026/03/enforcement-of-the-saudi-pdp-law
- **Confidence**: Confirmed (primary) for the penalty amounts; Confirmed (secondary) for the enforcement count.
- **As of 2026-10**: Enforced since 14 Sep 2024. Some secondary sources say SAR 5 million for the Art. 35 offence; the amended text we checked says SAR 3 million.

### D. Cross-border transfers

#### NAT-24: Transfer purposes and conditions, with a health-treatment carve-out [All]
- **Requirement**: Transfer or disclosure outside KSA is allowed only for set purposes. These include an agreement KSA is party to, the Kingdom's interests, an obligation to the data subject, and purposes set in the Regulations: centralised operational processing, a service or benefit to the data subject, and scientific research. Conditions: no prejudice to national security or vital interests; adequate protection; and the minimum data needed. The adequacy and minimisation conditions **do not apply** in cases of extreme necessity to preserve the data subject's life or vital interests, or **to prevent, examine or treat disease**.
- **Engineering implication**: Map every flow that leaves KSA (cloud regions, SaaS, AI APIs, support access, teleradiology or second-opinion services). Pin primary storage regions by default. The disease-treatment carve-out may cover overseas treatment, tele-consults and specialist reads, but it does not remove the national-security condition or the need to document the transfer.
- **Source**: PDPL Art. 29(1)–(4); Transfer Regulation Art. 2. URL as NAT-01; https://dgp.sdaia.gov.sa/wps/portal/pdp/knowledgecenter/details/RegulationonPersonalDataTransferOutsidetheKingdom
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### NAT-25: Adequacy or appropriate safeguards; health data is excluded from most exceptions [All]
- **Requirement**: SDAIA publishes, and reviews at least every 4 years, a list of adequate countries and organisations. Without adequacy, the appropriate safeguards are SDAIA's Standard Contractual Clauses (four sets: controller-to-processor, controller-to-controller, processor-to-controller, processor-to-processor, not modifiable), Binding Common Rules for multinational groups, or an accreditation certificate held by the recipient. Exceptions to the adequacy and minimisation conditions exist, but **sensitive data is excluded** from the occasional or limited, direct service, and research exceptions. Centralised processing within a multinational group (with BCRs, SCCs or certification) remains available.
- **Engineering implication**: For any offshore processor of health data (an AI model API, global SaaS or offshore support), put SDAIA SCCs in place, unmodified, or rely on adequacy. Do not rely on "occasional transfer" logic for health data. Check whether the destination is on SDAIA's adequacy list; we could not confirm the current list contents (**Unconfirmed**).
- **Source**: Transfer Regulation Art. 1(4)–(5), 3, 4(1)–(4); SDAIA SCCs; Mayer Brown (Oct 2024). URL as NAT-24; https://www.mayerbrown.com/en/insights/publications/2024/10/updates-to-saudi-arabias-personal-data-protection-regulations-sccs-guidelines-and-more
- **Confidence**: Confirmed (primary) for the regulation text; Confirmed (secondary) for the four SCC sets.
- **As of 2026-10**: Amended regulation in force since its September 2024 issue.

#### NAT-26: Transfer risk assessment, and stopping transfers [All]
- **Requirement**: A written risk assessment is required before transfers relying on the Art. 4 exceptions, and before transferring Sensitive Data or disclosing it abroad continuously or at large scale. It must cover purpose and legal basis, nature and geography, safeguards, minimisation, likely impacts, and mitigations. If safeguards fail or SDAIA finds them inadequate, the transfer must stop and recipients must be notified.
- **Engineering implication**: Produce a transfer risk assessment per offshore flow of health data (SDAIA publishes a guideline). Engineer a switch to suspend replication or API calls to a destination, and a recipient-notification procedure.
- **Source**: Transfer Regulation Art. 6, 7. URL as NAT-24. SDAIA Guideline for assessing risks of transferring personal data outside the Kingdom (knowledge centre).
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### NAT-27: Offshore remote access counts as transfer or disclosure, even with KSA hosting [All]
- **Requirement**: "Disclosure" covers enabling any person to access personal data by any means, and "Transfer" covers moving data for processing. Chambers notes that KSA hosting can still involve a transfer if overseas affiliates or sub-processors access the data.
- **Engineering implication**: Treat offshore developers, support desks, SOC analysts, offshore AI inference, and vendor "follow-the-sun" access to production health data as transfers. Prefer KSA-based support for production. Mask or synthesise data in non-production environments used by offshore teams. Log and restrict access by geography.
- **Source**: PDPL Art. 1(8)–(9); Chambers Cloud Computing 2026 (Saudi Arabia). URL as NAT-01; https://practiceguides.chambers.com/practice-guides/cloud-computing-2026/saudi-arabia/trends-and-developments
- **Confidence**: Confirmed (primary) for the definitions; Confirmed (secondary) for applying them to remote access.
- **As of 2026-10**: In force. If the draft Art. 23 localisation duty is adopted, this becomes more important (see Watch items).

### E. NDMO, data classification and residency

#### NAT-28: Government data classification and NDMO standards [Gov]
- **Requirement**: Data received, produced or handled by public entities must be classified Top Secret, Secret, Confidential or Public, based on the impact of unauthorised disclosure. Aggregated data takes the highest level, and personal data may be classified high. The NDMO Data Management and Personal Data Protection Standards (v1.5, Jan 2021) set 15 domains, including Data Classification, Personal Data Protection and Data Security. They apply to public entities and **business partners handling government data**.
- **Engineering implication**: When building for MoH, health clusters or other government health providers, label datasets with the government classification. Map the classification to CCC levels (Top Secret = Level 1, Secret = Level 2, Confidential = Level 3, Public = Level 4) and to CSP registration class (NAT-30). Expect contractual flow-down of NDMO specifications (data catalogue, quality, sharing).
- **Source**: National Data Governance Interim Regulations, Data Classification Policy (2020); NDMO Standards v1.5; CCC-2:2024 Annex A. Kiteworks summaries: https://www.kiteworks.com/sites/default/files/resources/kiteworks-guide-to-saudi-arabia-ndmo-standards.pdf ; https://www.kiteworks.com/sites/default/files/resources/kiteworks-guide-saudi-data-and-artificial-intelligence-authority-sdaia-national-data-governance-interim-regulations.pdf ; CCC-2: https://cdn.nca.gov.sa/api/files/public/upload/6d5408a3-d8e6-4e96-963b-2c7198e5b7c2_CCC-2-2024-EN-.pdf
- **Confidence**: Confirmed (primary) for the CCC level mapping; Confirmed (secondary) for the NDMO and Classification Policy detail (the SDAIA PDFs did not load in this session).
- **As of 2026-10**: In force. The Interim Regulations are still described as "interim".

#### NAT-29: Data residency for government health data [Gov]
- **Requirement**: Under CST's Cloud Regulations, CSPs and subscribers must not transfer Saudi government-agency data outside KSA, permanently or temporarily (including backups), unless another Saudi law expressly allows it. NCA removed its own localisation controls from ECC-2 (former 4-2-3-3) and CCC-2 (former 2-3-P-1-10 and 2-3-P-1-11), and directs entities to **consult NDMO on data localisation before acting**. There is **no general PDPL localisation duty today**.
- **Engineering implication**: For government health workloads, deploy only in KSA regions, including DR, backups, logs, caches and AI inference. Get NDMO's position documented. For private-sector health data, residency is driven by the PDPL transfer rules (NAT-24 to NAT-27) and sector rules. Design for KSA-only by default so you are ready if the draft PDPL localisation duty passes.
- **Source**: CST Cloud Computing Services Provisioning Regulations, Art. 3-3-5 (per Chambers); ECC-2:2024 Annex (list of updates); CCC-2:2024 Annex D. https://practiceguides.chambers.com/practice-guides/cloud-computing-2026/saudi-arabia/trends-and-developments ; https://cdn.nca.gov.sa/api/files/public/upload/86e09090-44e4-481f-bc28-355673607654_ECC--2024-EN.pdf ; CCC-2 URL as NAT-28
- **Confidence**: Confirmed (primary) for the NCA deletions; Confirmed (secondary) for the CST article; Unconfirmed whether NDMO has issued a standalone localisation instrument.
- **As of 2026-10**: In force. Watch the PDPL IR Art. 23 draft.

### F. CST cloud regulation

#### NAT-30: Use CST-registered cloud providers; contract and offshore-consent terms [All, mainly Gov]
- **Requirement**: The CST Cloud Computing Services Provisioning Regulations (Decision 506/1445, 8 Oct 2023) replace CCRF v3. CSPs register in a Qualifying Category or Class A, B or C; the class limits which government data classification a CSP may host (A = Public, B = adds Confidential, C = adds Secret and Top Secret). Subscribers must classify their content. Contracts must contain minimum terms, and subscribers must be able to retrieve content after termination. A registered CSP must notify the subscriber in advance and **obtain consent before content is transferred, stored or processed outside KSA** (Art. 3-3-7). CSPs notify CST and subscribers of breaches without undue delay.
- **Engineering implication**: Choose a CST-registered CSP whose class matches the data classification. Check registration evidence. Contract for in-Kingdom regions, offshore-processing consent, exit and data retrieval, and breach notice. Classify workloads before choosing a provider.
- **Source**: CST Cloud Computing Services Provisioning Regulations (Decision 506/1445), Arts. 3-3-5, 3-3-7, 3-6, 3-7 (per Chambers). https://www.cst.gov.sa/en/regulations-and-licenses/regulations/Document-1550 ; Al Tamimi: https://turtl.tamimi.com/story/659faaaf5c8b5508162918de
- **Confidence**: Confirmed (primary) for title, decision number and date; Confirmed (secondary) for article content (the CST PDF could not be downloaded).
- **As of 2026-10**: In force. CST launched a Cloud Market Maturity Index on 3 Sep 2026; it does not affect eligibility.

### G. NCA cybersecurity controls

#### NAT-31: Work out which NCA control set applies [All]
- **Requirement**: ECC-2:2024 binds government agencies (ministries, authorities and establishments) and their affiliated companies inside and outside KSA, plus private entities that own, operate or host CNI. CCC-2 binds the same tenants when they use cloud. CSCC binds any organisation for systems it classes as critical. NCNICC-1:2025 binds non-CNI private entities in Category A or B that NCA notifies. DCC-1:2022 and TCC extend ECC for data protection and telework. NCA does not publish its CNI list, so **whether private healthcare is CNI is Unconfirmed**; vendor sources list healthcare as a CNI sector but give no primary citation. Public hospitals, MoH facilities and government-owned health companies are very likely in ECC scope as government entities or affiliates (this is an inference).
- **Engineering implication**: Record the control set that applies in the system's compliance profile: government or affiliate, so ECC + CCC (+ CSCC); private CNI-notified, so ECC + CCC; private non-CNI, so NCNICC. Vendors to in-scope entities inherit ECC/CCC through contracts (ECC 4-1). Ask the customer for NCA notification status.
- **Source**: ECC-2:2024 "Scope of Work and Applicability"; CCC-2:2024 "Scope of Work"; CSCC-1:2019 "Scope of Work"; NCNICC-1:2025 scope (Arabic); DCC page; TCC page. ECC URL as NAT-29; CCC URL as NAT-28; https://nca.gov.sa/ar/cscc-en.pdf ; https://cdn.nca.gov.sa/api/files/public/upload/721bed5c-5304-497c-a5ac-a92a049e6306_NCNICC-AR-.pdf ; https://nca.gov.sa/en/regulatory-documents/controls-list/dcc/ ; https://nca.gov.sa/en/regulatory-documents/controls-list/193
- **Confidence**: Confirmed (primary) for scopes; Unconfirmed for health as CNI.
- **As of 2026-10**: In force. DCC and TCC control detail not verified (the DCC PDF text was not extractable).

#### NAT-32: Identity and access management, MFA and privileged access [Gov][CNI]
- **Requirement**: IAM must include MFA for remote access and privileged accounts, with factors chosen by impact assessment. Authorisation must follow need-to-know and need-to-use, least privilege and segregation of duties. Requirements also include privileged access management and periodic access reviews. External web apps must authenticate users with factors chosen by impact assessment.
- **Engineering implication**: Use SSO with MFA for clinician remote access and all admin consoles, plus a PAM vault for privileged and DBA access. Run quarterly or periodic access recertification. Use risk-based MFA in patient portals.
- **Source**: ECC-2:2024 controls 2-2-3 (2.2.3.1–2.2.3.5), 2-15-3 (2.15.3.5). URL as NAT-29.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### NAT-33: Cryptography to the National Cryptographic Standards [Gov][CNI]
- **Requirement**: Cryptography must meet NCA's National Cryptographic Standards at a level suited to data sensitivity, with secure key lifecycle management and encryption of data in transit and at rest according to classification. Cloud tenants must use strong encryption at the NCS "advanced" level (NCS-1:2020) and encrypt data moving into and out of the cloud.
- **Engineering implication**: Use TLS for all traffic and AES-based encryption at rest for databases, object stores and backups, with a KMS or HSM and documented key rotation. Check algorithm choices against NCS-1:2020; the algorithm list was not reviewed here (**Unconfirmed**).
- **Source**: ECC-2:2024 control 2-8-3 (2.8.3.1–2.8.3.3); CCC-2:2024 2-7-T-1-1, 2-7-T-1-2. URLs as NAT-29 and NAT-28.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### NAT-34: Security event logging, SIEM, and at least 12 months' retention [Gov][CNI]
- **Requirement**: Enable security event logs on critical assets and for privileged, critical and remote-access accounts. Use SIEM, monitor continuously, and **keep logs for at least 12 months**. Critical systems need 18 months (NAT-41).
- **Engineering implication**: Send application audit logs (including PHI access events) and infrastructure logs to SIEM. Use immutable storage with retention of 12 months or more (18 months or more for critical systems). Alert on bulk record access and out-of-hours access.
- **Source**: ECC-2:2024 control 2-12-3 (2.12.3.1–2.12.3.5). URL as NAT-29.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### NAT-35: Vulnerability management and penetration testing [Gov][CNI]
- **Requirement**: Run periodic vulnerability assessment, classify by severity and remediate by risk, and test patches in non-production before applying them. Penetration testing must cover **all internet-facing services and their components, including websites, web apps, mobile apps, email and remote access**, and be repeated periodically. Cloud tenants assess vulnerabilities in cloud services at least every three months.
- **Engineering implication**: Set up a vulnerability-scanning pipeline (SAST, DAST, SCA, infrastructure) with remediation SLAs by severity. Put patient mobile apps and portals in the pen-test scope. Use a staging environment for patch validation.
- **Source**: ECC-2:2024 controls 2-10-3, 2-11-3; CCC-2:2024 2-9-T-1-1. URLs as NAT-29 and NAT-28.
- **Confidence**: Confirmed (primary). ECC sets no pen-test frequency ("periodically").
- **As of 2026-10**: In force.

#### NAT-36: Secure development and web application protection [Gov][CNI]
- **Requirement**: Software projects must use secure coding standards and trusted, licensed tools and libraries, test compliance against the security requirements, integrate securely, and review hardening before release. External web apps need a WAF, multi-tier architecture, secure protocols (HTTPS) and a user secure-usage policy.
- **Engineering implication**: Adopt a secure SDLC (coding standard, dependency allow-list and SBOM, security test gate in CI). Deploy patient portals behind a WAF, with presentation, application and data tiers separated and HTTPS only.
- **Source**: ECC-2:2024 controls 1-6-2, 1-6-3, 2-15-3. URL as NAT-29.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### NAT-37: Backup, recovery and business continuity [Gov][CNI]
- **Requirement**: Backups must cover critical assets and allow quick recovery after incidents, and restores must be tested periodically. BCM must cover the continuity of cybersecurity systems, cyber-incident response plans and disaster recovery plans.
- **Engineering implication**: Set RPO and RTO for clinical systems. Use encrypted, isolated (immutable) backups and scheduled restore tests with evidence. Keep a DR runbook, and keep DR in KSA for government data (NAT-29).
- **Source**: ECC-2:2024 controls 2-9-3, 3-1-3. URL as NAT-29.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### NAT-38: Third parties and cloud, with managed SOC located in KSA [Gov][CNI]
- **Requirement**: Third-party contracts must include non-disclosure, secure removal of data at the end of service, incident communication procedures, and an obligation to apply the entity's security requirements. Outsourced or managed IT and security services need a risk assessment before contracting, and **managed security monitoring centres that use remote access must be located entirely in KSA**. Cloud use requires the CSP to protect data according to classification, return data in a usable format at the end of service, and separate the tenant environment.
- **Engineering implication**: Include the contract clause set in vendor templates. Use a KSA-based MSSP or SOC. Cover cloud exit, data return and tenant isolation in architecture and contracts. Vendors to in-scope hospitals should expect these clauses.
- **Source**: ECC-2:2024 controls 4-1-2, 4-1-3 (4.1.3.2), 4-2-3. URL as NAT-29.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force. ECC-2 also requires cybersecurity positions to be filled by full-time, qualified Saudi nationals (1-2-1), which affects staffing plans.

#### NAT-39: Incident management and reporting to NCA [Gov][CNI]
- **Requirement**: Entities need incident response plans and escalation, incident classification, **reporting of cybersecurity incidents to NCA**, sharing of incident notifications, threat intelligence and indicators with NCA, and threat-intelligence handling.
- **Engineering implication**: Run one incident process that serves both NCA (cyber) and SDAIA (personal-data breach, 72 hours, NAT-12). Set classification criteria and an evidence-preservation and IoC export capability. **NCA's reporting deadline is Unconfirmed**; ECC itself sets none.
- **Source**: ECC-2:2024 control 2-13-3 (2.13.3.1–2.13.3.5). URL as NAT-29.
- **Confidence**: Confirmed (primary) for the duty; Unconfirmed for the timeline.
- **As of 2026-10**: In force.

#### NAT-40: Cloud tenant controls (CCC-2:2024) [Gov][CNI]
- **Requirement**: Tenant controls include: cloud asset inventory; IAM for all cloud credentials, secure session management, and **MFA for privileged cloud users**; an exit strategy with secure disposal; secure export; strong encryption, including of data in transit to and from the cloud; vulnerability assessment at least every 3 months; login and security event logging and monitoring; and DR and BCP. CSP-side controls include monthly external and quarterly internal vulnerability remediation, and **penetration tests of the cloud stack at least every 6 months**. CCC levels follow data classification (Level 1 Top Secret to Level 4 Public).
- **Engineering implication**: Use cloud security posture tooling for inventory and misconfiguration. Enforce MFA on cloud consoles. Document the exit plan. Run a quarterly scan cadence. Request CSP evidence of the 6-monthly pen test.
- **Source**: CCC-2:2024 controls 2-1-T-1-1, 2-2-T-1-1 to 2-2-T-1-5, 2-6-T-1-1 to 2-6-T-1-2, 2-7-T-1-1 to 2-7-T-1-2, 2-9-T-1-1, 2-11-T-1-1 to 2-11-T-1-2, 3-1-T-1-1, 2-9-P-1-1, 2-10-P-1-1; Annex A. URL as NAT-28.
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

#### NAT-41: Critical systems (CSCC-1:2019): stricter access, encryption, hosting and logs [Critical]
- **Requirement**: A system is critical if its failure or compromise would have national-level impact. Criteria include loss of lives, impact on services to more than 5% of the population, and losses above 0.01% of GDP. For critical systems: **no remote access from outside KSA**; remote access from inside KSA only with SOC verification of each attempt; MFA for all users; encryption of all data in transit and at rest (file, database or column level); penetration tests at least every 6 months; logs kept for at least 18 months; security source-code review before release; and **hosting inside the organisation or with government or Saudi-company cloud compliant with CCC**.
- **Engineering implication**: National-scale clinical systems (for example a hospital network's EHR or HIS, or national telehealth) may meet the "loss of lives" or population criteria. If so, use KSA-only admin access, column-level encryption for PHI, code review gates, 18-month log retention, and a Saudi CCC-compliant cloud.
- **Source**: CSCC-1:2019, "Definition and Identification Criteria"; controls 1-3-2-1, 2-2-1-1 to 2-2-1-6, 2-7-1-1 to 2-7-1-3, 2-10-2, 2-11-2, 4-2-1-1. https://nca.gov.sa/ar/cscc-en.pdf
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: CSCC-1:2019 is still the current version on the NCA site; its scope covers government organisations and subsidiaries of government or private organisations that own critical systems.

#### NAT-42: Private non-CNI entities (NCNICC-1:2025) [Non-CNI]
- **Requirement**: NCNICC sets minimum controls for private entities without CNI, applied to entities NCA notifies. Category A is large (more than 250 staff or revenue above SAR 200m): 3 components, 22 sub-components, 65 controls. Category B is SME (6 to 249 staff or SAR 3m to 200m): 26 controls, some only recommended. Controls checked in the Arabic text: **MFA for remote access, email and external applications (2-2-1-2, mandatory for A and B)**; security event logging on sensitive assets; a managed SOC from an NCA-licensed provider (2-12-1-2); and WAF, multi-tier architecture and HTTPS (2-15-1-x, mandatory for A, recommended for B). The controls also cover email authentication (SPF, DKIM, DMARC through NCA's Haseen platform), alignment with the National Cryptographic Standards, and cloud and third-party controls.
- **Engineering implication**: Private hospitals, clinics and health-tech firms that are not CNI should design to Category A controls as a baseline. MFA everywhere external, managed SOC, WAF and email authentication are the quick wins.
- **Source**: NCNICC-1:2025 (Arabic), controls 2-2-1-2, 2-12-1-1, 2-12-1-2, 2-15-1-1 to 2-15-1-5. https://cdn.nca.gov.sa/api/files/public/upload/721bed5c-5304-497c-a5ac-a92a049e6306_NCNICC-AR-.pdf ; Baker McKenzie (Jul 2026): https://www.bakermckenzie.com/en/insight/publications/2026/07/saudi-arabia-cybersecurity-controls-for-private-entities ; CMS (Mar 2026): https://cms.law/en/int/legal-updates/kingdom-of-saudi-arabia-issues-new-cybersecurity-controls-for-the-private-sector
- **Confidence**: Confirmed (primary) for the cited controls (machine-assisted reading of the Arabic); Confirmed (secondary) for thresholds and counts.
- **As of 2026-10**: Adopted 28 Dec 2025 (Digital Policy Alert). The compliance deadline and log-retention period are **Unconfirmed**. Baker McKenzie notes NCA has not publicly named notified entities.

### H. AI governance

#### NAT-43: SDAIA AI Ethics Principles: classify clinical AI by risk [All]
- **Requirement**: Seven principles apply across the AI lifecycle: fairness; privacy and security; humanity; social and environmental benefit; reliability and safety; transparency and explainability; accountability and responsibility. AI is graded by risk: little or no risk (compliance recommended), limited and high risk (comply with principles and controls), and unacceptable risk (prohibited). Adopting entities appoint a Responsible AI Officer and an AI System Assessor and can register with SDAIA for a voluntary compliance "badge".
- **Engineering implication**: Classify each AI feature; clinical decision support should be treated as high risk. Keep model cards, bias and fairness testing on Saudi patient populations, explainability artefacts, human oversight design and post-market monitoring. Assign a Responsible AI Officer. SFDA rules on AI medical devices belong in the sector file.
- **Source**: SDAIA AI Ethics Principles v2.0 (Sep 2023). Legalcommunity MENA: https://legalcommunitymena.com/saudi-arabias-ai-ethics-principles-2-0-a-new-era-of-ai-governance/ ; Al Tamimi, AI in healthcare: https://www.tamimi.com/news/ai-in-healthcare-kingdom-of-saudi-arabia/
- **Confidence**: Confirmed (secondary). Binding force is unclear: HSF states there is no AI-specific regulation in KSA.
- **As of 2026-10**: Published. No AI law enacted as far as we could find.

#### NAT-44: Generative AI and deepfake guidance [All]
- **Requirement**: SDAIA's Generative AI Guidelines (Jan 2024) have a Government version, with a checklist government staff must follow when using GenAI tools, and a Public version for developers and users covering misuse, deepfakes, IP and security risks. The Deepfakes Guidelines (reported as issued May 2026) call for explicit, auditable consent before using a person's likeness, a way to remove a likeness from training datasets, and watermarks on synthetic content. They also name healthcare (for example voice reconstruction) as a beneficial use.
- **Engineering implication**: For GenAI features (clinical documentation, chat assistants), apply the Government checklist when the customer is public sector. Do not send identifiable health data to GenAI services without a PDPL basis and transfer safeguards (NAT-24 to NAT-27). For synthetic patient avatars, voices or "virtual patients", capture likeness consent, watermark outputs and keep provenance logs.
- **Source**: SDAIA Generative AI Guidelines (Government; Public), Jan 2024; SDAIA Deepfakes Guidelines. HSF AI tracker: https://www.hsfkramer.com/insights/reports/ai-tracker/saudi-arabia ; Arab News (May 2026): https://www.arabnews.com/node/2642878/amp
- **Confidence**: Confirmed (secondary). Checklist items not verified (**Unconfirmed**).
- **As of 2026-10**: Guidance; legal force unclear.

### I. Criminal law

#### NAT-45: Anti-Cyber Crime Law: unlawful access and data tampering [All]
- **Requirement**: The following are crimes. Intercepting data on networks, unlawful access to threaten or blackmail, and privacy invasion with camera phones: up to 1 year and/or SAR 500,000 (Art. 3). Unlawful access to delete, destroy, leak, damage or alter data, or disrupting networks or services: up to 4 years and/or SAR 3m (Art. 5). Other offences are in Arts. 4, 6 and 7. The law does not mention medical records specifically.
- **Engineering implication**: Access controls, warning banners and tamper-evident audit logs support prosecution of insiders and attackers. Pen testing and red-teaming need written authorisation. Govern clinical photography on staff phones through policy and a managed app (relevant to Art. 3(4)).
- **Source**: Anti-Cyber Crime Law, Royal Decree M/17 of 8/3/1428H, Arts. 3, 5, 7. https://www.mcit.gov.sa/sites/default/files/anti_cyber_crime_law_en_0.pdf
- **Confidence**: Confirmed (primary)
- **As of 2026-10**: In force.

---

## Watch items

1. **PDPL Implementing Regulations draft amendments** (SDAIA, consultation on Istitlaa 6 Oct to 5 Nov 2026; in force 60 days after Gazette publication if adopted). Key items:
   - **Art. 23 data localisation**: controllers would have to store personal data inside KSA, with transfers still allowed under the PDPL.
   - **Art. 24**: 72-hour notification to SDAIA for all breaches, with no harm threshold.
   - New DPIA triggers.
   - Mandatory registration criteria moved into IR Art. 34, including controllers that transfer data abroad.
   - A 20-business-day deadline to answer SDAIA requests.
   - Rights requests deemed rejected if not answered.
   - DPO changes.
   - Arabic and plain-language privacy policies.

   Source: Clyde & Co, 8 Oct 2026, https://www.clydeco.com/en/insights/2026/10/sdaia-publishes-draft-amendments-to-the-pdpl. We have not read the draft text; exceptions to localisation are **Unconfirmed**.
2. **SDAIA adequacy list**: whether it has been published and which countries are on it is **Unconfirmed**.
3. **Registration rules for controllers outside KSA**: announced as "to be issued separately"; status **Unconfirmed**.
4. **NDMO data localisation instrument**: NCA directs entities to NDMO, but we found no standalone NDMO localisation rule (**Unconfirmed**).
5. **NCNICC-1:2025 compliance timetable** and NCA notifications to individual entities (**Unconfirmed**).
6. **Health as a CNI sector**: there is no public NCA confirmation (**Unconfirmed**). Confirm with each customer.
7. **NCA incident-reporting deadlines** (ECC 2-13-3-3): no deadline in ECC; any separate NCA timeline is **Unconfirmed**.
8. **Draft Global AI Hub Law** (CST, consultation 14 Apr to 14 May 2025): would allow "data embassy" style hubs under foreign law. Enactment status is **Unconfirmed**.
9. **Any KSA AI law**: none enacted as of HSF's update on 12 Feb 2026. Monitor SDAIA.
10. **DCC-1:2022 and TCC-1:2021 control detail**: not verified in this pass (the DCC PDF was not text-extractable). Review before building data-lifecycle and remote-work controls for in-scope entities.
11. **CST Cloud Regulations full text**: article content taken from Chambers and Al Tamimi because cst.gov.sa downloads failed. Verify Arts. 3-3-5 and 3-3-7 against the official PDF.
12. **Penalty discrepancy**: some secondary sources cite SAR 5m for the PDPL Art. 35 criminal offence; the amended English text on misa.gov.sa says SAR 3m. Treat SAR 3m as current.

---

## Primary sources used

- PDPL (English translation, amended text): https://misa.gov.sa/app/uploads/2025/08/PersonalDataProtectionLaw.pdf
- SDAIA Knowledge Centre (index of PDPL instruments): https://dgp.sdaia.gov.sa/wps/portal/pdp/knowledgecenter
  - PDPL (Arabic): https://dgp.sdaia.gov.sa/wps/portal/pdp/knowledgecenter/details/PDPL
  - Implementing Regulations (Arabic): https://dgp.sdaia.gov.sa/wps/portal/pdp/knowledgecenter/details/PDPL2
  - Transfer Regulation (Arabic): https://dgp.sdaia.gov.sa/wps/portal/pdp/knowledgecenter/details/RegulationonPersonalDataTransferOutsidetheKingdom
  - National Register of Controllers Rules: https://dgp.sdaia.gov.sa/wps/portal/pdp/knowledgecenter/details/Rulesandguidelinesp2
  - Destruction, Anonymisation and Pseudonymisation Guideline: https://dgp.sdaia.gov.sa/wps/portal/pdp/knowledgecenter/details/PersonalDataDestruction
  - General Rules for Secondary Use of Data: https://dgp.sdaia.gov.sa/wps/portal/pdp/knowledgecenter/details/GeneralRulesforSecondaryUseofData
- NCA ECC-2:2024 (English): https://cdn.nca.gov.sa/api/files/public/upload/86e09090-44e4-481f-bc28-355673607654_ECC--2024-EN.pdf
- NCA CCC-2:2024 (English): https://cdn.nca.gov.sa/api/files/public/upload/6d5408a3-d8e6-4e96-963b-2c7198e5b7c2_CCC-2-2024-EN-.pdf
- NCA CSCC-1:2019 (English): https://nca.gov.sa/ar/cscc-en.pdf ; page: https://nca.gov.sa/en/regulatory-documents/controls-list/cscc/
- NCA NCNICC-1:2025 (Arabic): https://cdn.nca.gov.sa/api/files/public/upload/721bed5c-5304-497c-a5ac-a92a049e6306_NCNICC-AR-.pdf
- NCA DCC page: https://nca.gov.sa/en/regulatory-documents/controls-list/dcc/ ; TCC page: https://nca.gov.sa/en/regulatory-documents/controls-list/193
- CST Cloud Computing Services Provisioning Regulations page: https://www.cst.gov.sa/en/regulations-and-licenses/regulations/Document-1550
- Anti-Cyber Crime Law (English, MCIT): https://www.mcit.gov.sa/sites/default/files/anti_cyber_crime_law_en_0.pdf

### Secondary sources used
- Clyde & Co: IR draft amendments (Oct 2026) https://www.clydeco.com/en/insights/2026/10/sdaia-publishes-draft-amendments-to-the-pdpl ; enforcement (Mar 2026) https://www.clydeco.com/en/insights/2026/03/enforcement-of-the-saudi-pdp-law ; ECC-2 (Jan 2025) https://www.clydeco.com/en/insights/2025/01/saudi-arabia-essential-cybersecurity-controls ; IR issued (Sep 2023) https://www.clydeco.com/en/insights/2023/09/saudi-arabia-issues-implementing-regulations ; Global AI Hub Law (May 2025) https://www.clydeco.com/en/insights/2025/05/ksa-release-draft-global-ai-hub-law
- Latham & Watkins (Dec 2023): https://www.lw.com/en/insights/2023/12/Saudi-Arabias-data-protection-law-enters-into-force
- Mayer Brown (Oct 2024): https://www.mayerbrown.com/en/insights/publications/2024/10/updates-to-saudi-arabias-personal-data-protection-regulations-sccs-guidelines-and-more
- Baker McKenzie: NCNICC (Jul 2026) https://www.bakermckenzie.com/en/insight/publications/2026/07/saudi-arabia-cybersecurity-controls-for-private-entities ; data localisation handbook https://resourcehub.bakermckenzie.com/en/resources/global-data-and-cyber-handbook/emea/saudi-arabia/topics/data-localization-and-regulation-of-non-personal-data
- CMS (Mar 2026): https://cms.law/en/int/legal-updates/kingdom-of-saudi-arabia-issues-new-cybersecurity-controls-for-the-private-sector
- Al Tamimi: data observations (Sep 2025, updated Mar 2026) https://www.tamimi.com/news/observations-and-tips-on-data-issues-in-ksa/ ; Cloud Regulations (Jan 2024) https://turtl.tamimi.com/story/659faaaf5c8b5508162918de ; AI in healthcare (Jan 2025) https://www.tamimi.com/news/ai-in-healthcare-kingdom-of-saudi-arabia/
- Chambers Cloud Computing 2026, Saudi Arabia: https://practiceguides.chambers.com/practice-guides/cloud-computing-2026/saudi-arabia/trends-and-developments
- DLA Piper, CCRF v3 (Apr 2021): https://www.dlapiper.com/en/insights/publications/2021/04/saudi-arabia-releases-version-3-of-its-cloud-computing-regulatory-framework
- HSF Kramer AI tracker (updated Feb 2026): https://www.hsfkramer.com/insights/reports/ai-tracker/saudi-arabia
- Legalcommunity MENA, AI Ethics Principles 2.0 (Dec 2023): https://legalcommunitymena.com/saudi-arabias-ai-ethics-principles-2-0-a-new-era-of-ai-governance/
- Securiti, DPO Rules (Sep 2024): https://securiti.ai/saudi-arabia-rules-for-appointing-personal-data-protection-officer
- Kiteworks NDMO guides (vendor, used only for version and scope): https://www.kiteworks.com/sites/default/files/resources/kiteworks-guide-to-saudi-arabia-ndmo-standards.pdf
- Digital Policy Alert, NCNICC adoption date: https://digitalpolicyalert.org/event/36912-national-cybersecurity-authority-adopted-non-cni-private-sector-entities-cybersecurity-controls-ncnicc-12025
- Arab News, Deepfakes Guidelines (May 2026): https://www.arabnews.com/node/2642878/amp
