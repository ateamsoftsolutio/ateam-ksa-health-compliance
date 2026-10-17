# Questions for the engineering team

Ask only what the code and documents couldn't answer. Group the questions into one round, offering your best guess where you have one. Record each answer with the person's name, marked "(stated)".

## Scope (asked first, in Step 1 of the check skill)

1. What does the system do, and who uses it (clinicians, patients, admin staff, insurers)?
2. Who is the customer?
   - a government health provider (MoH, a health cluster, Health Holding)
   - a private hospital or clinic
   - an insurer or TPA
   - a product sold to many
3. Has NCA designated the customer as critical national infrastructure, or notified it under the private-sector controls (NCNICC)? If unknown, say so.
4. Does it have AI features? Does any of them diagnose, treat, monitor or support clinical decisions?
5. Does it offer telehealth or virtual care?
6. Does it handle insurance eligibility, pre-authorisation or claims (NPHIES)? Does it prescribe (Wasfaty)? Does it integrate with Sehhaty or Seha?
7. Where is it hosted (provider and region), including backups and disaster recovery?
8. Is it used in a CBAHI-accredited hospital?

## Follow-up questions (only where evidence is missing)

**Offshore access and transfers:**

- Do any engineers, support staff or vendors access production systems or patient data from outside KSA? If yes, from where? What transfer mechanism and risk assessment cover it? *(Blocker-priority for every scope.)*
- Do development or testing ever use real patient data, in KSA or abroad?
- Which third-party services receive any patient data? Where do they process it, and under what transfer basis?

**PDPL governance:**

- Is the controller registered in SDAIA's National Register? Is a DPO named?
- Has a data protection impact assessment been done for the health data processing?
- Is there a breach runbook that meets SDAIA's 72-hour notice and the HIE policy timelines?
- Are there data processing agreements with every processor?

**Security:**

- When was the last penetration test, and did it cover mobile apps?
- Who runs security monitoring, and from where?

**National platforms:**

- Has NPHIES vendor certification been completed?
- Which implementation guide version is pinned?
- Are the connecting IPs whitelisted?
- Does the team hold ICD-10-AM licences?

**AI and medical devices:**

- Where are models hosted? Is patient data used for training, and with what approval?
- Has SFDA classification or marketing authorisation been sought for medical software?
- Has the AI been validated on local data?

**Telehealth:**

- Is the facility licensed for telehealth? Is the technology approved?
- Where are recordings stored?
- Are any practitioners abroad, and are they registered in KSA?
