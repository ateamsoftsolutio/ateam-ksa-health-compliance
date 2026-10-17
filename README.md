# Saudi Healthcare Compliance by ATeam

**Know what Saudi regulators require, see what your system already does, and build the rest.**

This Claude plugin checks a healthcare software system against Saudi Arabia's healthcare rules. It produces an engineering checklist: every applicable requirement, its source, the evidence found in your system, and the concrete task to close each gap. The checklist is kept as a register in your project and exported to Excel, and it is re-checked as engineers build.

It works in Claude Code and in Claude Cowork with a project folder. It was built by [ATeam Soft Solutions](https://www.ateamsoftsolutions.com), a software and AI engineering firm with a Riyadh entity that builds healthcare systems for GCC providers. We share it as a contribution to the community.

## Install

Search for "Saudi Healthcare Compliance by ATeam" in Claude's plugin directory, or in Claude Code run:

```
/plugin install ateam-ksa-health-compliance --marketplace ateamsoftsolutio/ateam-ksa-health-compliance
```

## The three skills

| Skill | Say | What it does |
|---|---|---|
| `ksa-health-check` | "Run KSA Health Check" | Scopes the system (customer type, NCA scope, AI, telehealth, NPHIES), checks code, configuration and infrastructure for evidence, asks about what code can't show, and writes the checklist and Excel file |
| `ksa-health-recheck` | "Recheck KSA compliance" | Re-checks after fixes, updates statuses on evidence, flags anything that went backwards, and re-exports the Excel file |
| `ksa-health-explain` | "Can we use an LLM API with Saudi patient data?" | Explains any requirement in plain language, with its source and a design suggestion |

## What it covers (library dated 10 October 2026)

| Layer | Covers |
|---|---|
| Data protection (SDAIA) | PDPL and Implementing Regulations: health data as sensitive data, consent, data subject rights, 72-hour breach notice, impact assessments, DPO, registration, retention and destruction. The Personal Data Transfer Regulation (2024): adequacy, SDAIA standard contract clauses, risk assessment, and offshore remote access treated as a transfer. |
| Cybersecurity (NCA) | Which control set applies (ECC-2:2024, CCC-2:2024, CSCC, NCNICC-1:2025) and the engineering controls: MFA, logging retention, cryptography, pen testing, backup, KSA-based security operations |
| Cloud and data governance | CST cloud rules, NDMO standards, government data residency |
| Health sector (MoH and NHIC) | Saudi Health Information Exchange Policies (purpose of use, opt-out and break-glass, session and MFA rules, audit, breach timelines, no deletion of exchanged records), interoperability, National ID/Iqama, confidentiality under the Law of Practising Healthcare Professions, Wasfaty, Sehhaty |
| Telehealth | Licensing, approved technology, e-consent, identity verification, documentation, practitioners abroad, prescribing |
| Insurance (CHI/NPHIES) | FHIR R4 messaging, profiles, mutual TLS, message limits, code systems, vendor certification |
| Medical devices (SFDA) | Software and AI as a medical device: marketing authorisation, Rule 11 classification, AI/ML guidance (MDS-G010) with local validation, cybersecurity guidance, adverse event reporting, Arabic/English interfaces |
| AI | SDAIA AI Ethics Principles, generative AI and deepfake guidelines |

Every requirement cites its source and is marked **Confirmed (primary)**, **Confirmed (secondary)** or **Unconfirmed**, with an "as of" note. Unconfirmed items become questions in your checklist, never hard requirements. Saudi instruments are authoritative in Arabic.

The library also flags the draft PDPL amendments under consultation in October 2026 (a general duty to store personal data in KSA, and breach notice without a harm threshold) as a watch item.

## How it works

1. Open your project folder and say **"Run KSA Health Check"**.
2. Confirm the scope Claude drafts from your project.
3. Claude checks the system theme by theme: hosting and residency, offshore data flows, identity and access, audit logging, data model, encryption, NPHIES and national platforms, development lifecycle, backup, AI, telehealth and language.
4. Answer one round of questions about what code can't show, such as registration, contracts, approvals and team location.
5. You get `.ksa-health-compliance/CHECKLIST.md`, plus an Excel checklist with Summary, Checklist, Questions, Watch items and Sources sheets.
6. Build the tasks, then say **"Recheck KSA compliance"**.

## Make it yours

Copy `compliance-house-rules.template.md` into your project as `compliance-house-rules.md` and edit it. You can set the approver, the Excel font, where the register is kept, and your own internal requirements.

## Important limits

- **Engineering readiness, not certification.** The plugin shows which requirements have evidence in your system. It does not replace a regulator's assessment, an audit or legal advice.
- **Rules change.** The library is dated, and Claude warns you when it's out of date or a watch item has moved. Check the current official text before relying on a requirement.
- **Instructions only.** It contains instructions for Claude and a requirements library. It has no MCP servers, hooks or scripts, and it sends no data anywhere.

## Privacy

See the [Privacy policy](PRIVACY.md).

## Licence

MIT. See [LICENSE](LICENSE).
