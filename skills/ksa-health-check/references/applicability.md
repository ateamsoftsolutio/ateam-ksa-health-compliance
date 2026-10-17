# Which requirements apply

Use the scope answers to pick requirements from the library: `library/national.md` (NAT-xx) and `library/health-sector.md` (NHIC, MOH, TEL, CHI, SFDA, SHC, AI). When in doubt, include the requirement and let the engineer mark it Not applicable with a reason.

## Who is the customer?

| Customer | What changes |
|---|---|
| Government health provider: MoH, a health cluster, Health Holding, or another government hospital | Government data classification and KSA residency (NAT-28 to NAT-30). NCA ECC-2 and CCC-2 apply (NAT-31 to NAT-40). |
| Private hospital, clinic or health-tech company designated as critical national infrastructure (CNI) by NCA | ECC-2 and CCC-2 apply (NAT-31 to NAT-40). Add CSCC (NAT-41) for systems classed as critical. |
| Private entity notified by NCA under NCNICC-1:2025 | NAT-42 |
| Other private provider or vendor | The PDPL layer applies in full. Use ECC-2 as the recommended security baseline (NAT-10), recorded at High priority, not as a legal requirement. |

NCA doesn't publish which private healthcare entities are CNI or notified. Ask the customer (see `questions.md`), and record the answer as stated.

## Base set: every system processing Saudi patient data

- NAT-01 to NAT-22, NAT-24 to NAT-27, NAT-31
- NHIC-01 to NHIC-11 (the Saudi Health Information Exchange Policies are the sector's privacy and security baseline)
- MOH-01, MOH-02, MOH-06
- NHIC-14

NAT-01 (scope), NAT-23 and NAT-45 (penalties) and CHI-08 (which regulator does what) are scope, penalty or status provisions. Record them as **Informational**.

## Add-ons by feature or situation

| If the system… | Add |
|---|---|
| Is operated by or for a government health entity | NAT-28 to NAT-30, NAT-32 to NAT-40 |
| Is CNI or has systems NCA classes as critical | NAT-32 to NAT-41 |
| Is a private entity notified under NCNICC | NAT-42 |
| Uses cloud hosting | NAT-30, plus NAT-40 if government or CNI |
| Sends data outside KSA, uses an offshore service that receives patient data, or gives offshore staff remote access | NAT-24 to NAT-27. Add NAT-38 (KSA-based security operations): a legal requirement for government and CNI scopes, and a High-priority recommended baseline otherwise. |
| Connects to a health information exchange or exchanges clinical data | NHIC-12, NHIC-13, NHIC-15 |
| Handles insurance eligibility, pre-authorisation or claims | CHI-01 to CHI-08 (NPHIES) |
| Supports prescribing | MOH-03, MOH-04 (Wasfaty) |
| Integrates with Sehhaty or Seha platforms | MOH-05 |
| Offers telehealth or virtual care | TEL-01 to TEL-08 |
| Has AI features of any kind | NAT-43, NAT-44, AI-01, NAT-05 (automated decisions) |
| Might have a medical purpose (diagnosis, treatment, monitoring, clinical decision support), or is part of a medical device | **Gate first:** add SFDA-01 and SFDA-02 only, as the qualification question. Add SFDA-03 to SFDA-13 (SFDA-07 to SFDA-09 for AI or machine learning) only once the software is confirmed as a medical device. |
| Is used in a CBAHI-accredited hospital | SHC-01 |
| Holds patient data in the source code repository, CI logs or build artefacts | Treat the git host and CI region as storage and transfer under NAT-24 to NAT-27 |
| Uses data for research, analytics or AI training | NAT-19, NAT-20, NHIC-11 |

## Always ask: offshore access and development

Under the PDPL, remote access from outside KSA to Saudi patient data counts as a transfer, even when the data is hosted in KSA (NAT-27). Health data is excluded from most transfer exceptions (NAT-25).

- Government health data is expected to stay in KSA (NAT-29).
- NCA requires managed security operations to be inside KSA for in-scope entities (NAT-38).
- Clinical HIE user accounts need face-to-face identity proofing (NHIC-07).

Include this as a **Blocker-priority question** for every scope. It matters most for teams with offshore engineering or support. This is a reading of the texts; a compliant transfer mechanism (SDAIA contract clauses plus a risk assessment) or KSA-based operations may resolve it. Flag it; don't decide it.

## Pending change to watch

SDAIA has published draft PDPL amendments for consultation (comments until 5 Nov 2026). They reportedly add:

- a general duty to store personal data in KSA
- 72-hour breach notice without a harm threshold

Mention this in every summary as a watch item until the final text is issued. Design for KSA hosting now.

## Items that are partly unconfirmed

Keep the confirmed part as the requirement, and add the unconfirmed detail as a question in the same item. Use Needs confirmation only when the outcome depends on the unconfirmed detail. If the confirmed part alone already shows a gap, mark it Missing (or Partly met) and keep the question open.

## Regulator value in the register

Use `PDPL/SDAIA`, `SDAIA` (AI guidance), `NCA`, `CST`, `NDMO`, `MoH/NHIC`, `CHI/NPHIES`, `SFDA`, `SHC/CBAHI`, `Other law` (for example the Anti-Cyber Crime Law) or `Internal`.

## What to list

List the base set and the add-ons that apply. Don't list library sections that don't apply to this scope. Instead, name them once in `scope.md` under "Out of scope", for example "NCA CSCC (NAT-41): no systems classed as critical". Use Not applicable only for items inside a selected set that don't apply, and give a reason.

## Who is responsible

Many duties belong to the client rather than the team building the system: registration, DPO, impact assessments, licences, transfer contracts. Record a `responsible` value on every item:

- `Client` (the controller, facility or licensee)
- `Vendor` (the team building or running the system)
- `Shared`

Route each question to the right party.
