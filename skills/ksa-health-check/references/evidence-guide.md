# Finding evidence in the system

For each applicable requirement, look for evidence in the code, configuration, infrastructure files and documents. Record what you found and where (file and line, or document and section).

Some things can't be seen in code: contracts, SDAIA registration, the DPO, NCA designation, approvals and team location. Ask the engineer for those (see `questions.md`) and record the answer as **stated by** that person.

## Handling what you find

- **Secrets:** never print them. Mask them (first 4 and last 4 characters) and recommend a security audit.
- **Real patient data in the repository** (seed files, fixtures, logs, dumps):
  - don't reproduce it anywhere, including the register, Excel file or chat
  - record only the file and the type of data
  - raise it as a High item: it may be a reportable breach (NAT-12, NHIC-10), and it breaks the minimisation and access rules (NAT-07, NAT-09)
  - recommend removing it from the repository and its history
- **Application-security flaws** (for example IDOR, self-assigned roles, injection) are outside this library. Note them under the closest access-control item, and recommend a security audit (for example the Security Audit Loop plugin).

## 1. Hosting and data residency

NAT-24 to NAT-30, NAT-40, NAT-41

- **Where to look:**
  - infrastructure-as-code (Terraform, CloudFormation, Bicep, Pulumi)
  - Kubernetes and Helm values, docker-compose files
  - CI/CD deploy steps, `.env.example`, cloud SDK configuration
  - database host names (never print credentials)
- **KSA locations** (confirm against each provider's current list and CST registration, NAT-30):
  - Google Cloud `me-central2` (Dammam)
  - Oracle Cloud Jeddah and Riyadh
  - KSA-based providers such as STC Cloud, and Alibaba Cloud and Huawei Cloud KSA regions
- **AWS and Azure:** the library doesn't record whether their KSA regions are live. If the system uses one, record it as Needs confirmation and ask the team to confirm the region's location and CST registration.
- **Not KSA:**
  - AWS `me-central-1` is the UAE
  - AWS `me-south-1` is Bahrain
  - Azure `uaenorth` and `uaecentral` are the UAE
  - any other region is outside KSA
- **Also check:**
  - backup, disaster recovery and replica regions
  - CDN caching of patient data
  - where logs, analytics and backups land

## 2. Offshore data flows through third-party services

NAT-24 to NAT-27, NHIC-11

Search dependencies and code for SDKs and endpoints that could receive patient data:

| Category | Examples |
|---|---|
| Analytics | Google Analytics, Mixpanel, Segment, Amplitude |
| Error tracking and logging/APM | Sentry, Bugsnag, Datadog, New Relic |
| Email, SMS, push and WhatsApp | SendGrid, Twilio, Firebase messaging |
| Video for telehealth | Zoom, Agora, Twilio Video, Vonage |
| AI and LLM APIs | OpenAI, Anthropic, Google Gemini, Azure OpenAI (check the region) |
| Storage and backend-as-a-service | Firebase, Supabase |

For each one, decide:

- whether patient data or identifiers can reach it (prompts, error payloads, event properties, message bodies)
- where it processes data
- whether a valid transfer basis exists: adequacy, SDAIA standard contract clauses, binding corporate rules or certification, plus a risk assessment (NAT-25, NAT-26)

Health data is excluded from most exceptions.

## 3. Identity and access

NAT-09, NAT-32, NHIC-07, NHIC-08, NAT-41

- **Authentication:** auth library or identity provider, and MFA for remote and privileged access (NHIC-08, NAT-32).
- **Sessions:** a 30-minute session timeout on clinical access (NHIC-08).
- **Least privilege:** minimum-necessary, tiered roles with separation of duties for health data (NAT-09).
- **Break-glass:** with a recorded reason (NHIC-06).
- **Accounts:** unique accounts, no shared logins, and account review and removal.
- **Clinical user identity proofing** before HIE accounts are issued (NHIC-07).

## 4. Audit logging

NHIC-09, NAT-34, NAT-41

- **What to log:** who accessed which patient record, when, and for what purpose of use (NHIC-01, NHIC-09). Logs must be tamper-resistant and time-synchronised.
- **Retention:**
  - NCA in-scope entities: at least 12 months (NAT-34), or 18 months for critical systems (NAT-41)
  - check NHIC-09 for the HIE audit retention rules
- **Breach scoping:** a query that answers "which patients were affected?" (NAT-12, NHIC-10).

## 5. Data model and records

NHIC-03, NHIC-05, NHIC-06, NHIC-14, MOH-06, NAT-04, NAT-08, NAT-18

- **Patient identifier:** National ID or Iqama, as the national patient reference (NHIC-14).
- **No deletion of exchanged clinical records:** corrections create versions linked to the original (NHIC-03). Look for hard deletes and in-place updates.
- **Consent:** explicit consent for health data where consent is the legal basis (NAT-04), recorded with scope, timestamp and withdrawal. Check the HIE opt-out model and break-glass handling (NHIC-06).
- **Patient rights:** access, correction and disclosure reports, with a 30-day response window (NAT-08, NHIC-05).
- **Retention and destruction, including backups** (NAT-18). Check the record retention rule (MOH-06); it's unconfirmed in the library, so raise it as a question.

## 6. Encryption and keys

NHIC-04, NAT-33

- TLS on all endpoints and internal calls (NHIC-04).
- Encryption at rest for databases, files and backups.
- For NCA in-scope entities, cryptography to the National Cryptographic Standards (NAT-33).

## 7. Interoperability and national platforms

NHIC-12, NHIC-13, NHIC-15, CHI-01 to CHI-07, MOH-04, MOH-05

- **FHIR R4 libraries and NPHIES profiles** (CHI-02, CHI-03). Check:
  - mutual TLS with NPHIES-issued certificates (CHI-04)
  - message limits and duplicate handling (CHI-05)
  - code systems such as ICD-10-AM, and terminology licences (CHI-06)
- **IHE-based HIE profiles,** if relevant (NHIC-12).
- **Wasfaty and Sehhaty/Seha integrations** (MOH-04, MOH-05).

## 8. Development lifecycle and supply chain

NAT-35, NAT-36, NAT-11

- **CI pipeline:** static analysis, dependency scanning and vulnerability management. Pen tests covering everything internet-facing, including mobile apps (NAT-35).
- **Test data:** no production patient data in test or development. Use synthetic data, or properly anonymised data (NAT-19).
- **Processors and sub-processors:** contracts and oversight (NAT-11).

## 9. Backup and continuity

NAT-37, NAT-18

Backup schedules, restore tests, recovery objectives, and the location of backups.

## 10. AI features

NAT-05, NAT-43, NAT-44, AI-01, SFDA-07 to SFDA-09, NHIC-11

- **Hosting:** where models are hosted and where inference runs (transfers, NAT-25).
- **Training data:** whether patient data is used for training, and with what basis, approval and de-identification (NHIC-11, NAT-20).
- **Automated decisions:** explicit consent and an impact assessment for fully automated decisions (NAT-05).
- **Governance:** risk classification under the SDAIA AI Ethics Principles (NAT-43); logging, human oversight and override; generative AI safeguards (NAT-44).
- **Medical purpose:** if the feature diagnoses, treats, monitors or supports clinical decisions, raise the SFDA questions. These cover marketing authorisation, Rule 11 classification, and clinical evaluation with local data (SFDA-01 to SFDA-03, SFDA-07).

## 11. Telehealth

TEL-01 to TEL-08

- Licensed facility and approved technology (TEL-01, TEL-02).
- E-consent before each service, with the right to withdraw (TEL-03).
- Identity verification (TEL-04).
- Documentation in the medical record (TEL-05).
- Recording storage location, including interim storage at the video provider.
- Practitioner licensing for clinicians abroad (TEL-07).
- Prescribing rules (TEL-08).

## 12. Patient-facing language

SFDA-06, NAT-06

- Privacy notices in Arabic and English (NAT-06).
- An Arabic and English interface for lay users of medical software (SFDA-06).

## 13. Source code and CI hosting

Where the repository and CI runners are hosted, if they can contain patient data.

## 14. Possible additional checks (not in the library)

Raise these only as questions, under "Possible additional requirements (not in library)":

- ZATCA e-invoicing for any billing module
- Nafath or other official identity verification for patients and practitioners
- SCFHS licence verification for practitioners
- NCA telework controls for remote production support
- how long telehealth recordings are kept, and the consent given for recording

## 15. Things only people can answer

- SDAIA registration and DPO (NAT-16, NAT-17)
- NCA designation or notification (NAT-31)
- transfer mechanisms and risk assessments
- data processing contracts
- ethics approvals
- NPHIES certification status
- SFDA classification
- telehealth licence
- team location and remote access

Use `questions.md`.
