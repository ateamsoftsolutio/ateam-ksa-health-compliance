---
name: ksa-health-explain
description: Explains Saudi Arabia's healthcare compliance requirements to engineers in plain language, with sources and design guidance. Covers the PDPL and data transfers, NCA cybersecurity controls, CST cloud rules, MoH/NHIC HIE policies, telehealth regulations, NPHIES, Wasfaty and SFDA software and AI medical device rules. Use when someone asks "can we use OpenAI with Saudi patient data", "what does NCA ECC require for logging", "how does NPHIES certification work", or "explain NAT-27".
---

# KSA Health Explain

This skill answers engineers' questions about Saudi healthcare requirements, using the library in `../ksa-health-check/references/library/`, and helps them design a compliant way to build things.

## How to answer

1. **Find the requirement(s)** in `national.md` or `health-sector.md`, by topic, regulator or ID.
2. **Answer in plain language:**
   - what the rule says
   - who it applies to: government entities, CNI, notified private entities, all controllers, medical-device software
   - what it means for the system
3. **Cite the library ID and source,** for example "NAT-27 (PDPL Art. 1(8)–(9))", together with the item's confidence and its "as of" note. Mention that the Arabic text prevails where wording matters.
4. **Give a design suggestion:** one or two practical ways to meet it, for example KSA-hosted models, SDAIA contract clauses plus a transfer risk assessment, synthetic test data, versioned clinical records, or NPHIES mutual TLS.
5. **Flag uncertainty honestly:**
   - If the library marks an item Unconfirmed, say so and suggest how to confirm it.
   - If the library doesn't cover the question, say so. Label any general knowledge as unverified.
6. **Point out pending changes,** such as the draft PDPL amendments (KSA storage duty, 72-hour breach notice without a harm threshold).
7. **Close with:** "Engineering guidance from a library dated <date>, not legal advice."

## Common questions to be ready for

- **Offshore services, AI APIs and offshore teams:** NAT-24 to NAT-27 and NHIC-11, plus NAT-29 for government data and NAT-38 for security operations.
- **Which NCA controls apply:** NAT-31, plus NAT-32 to NAT-42.
- **Consent and the HIE opt-out model:** NAT-03, NAT-04 and NHIC-06. Explain how PDPL explicit consent relates to the HIE opt-out model.
- **Deleting and correcting records:** NHIC-03, NAT-18, and MOH-06 (unconfirmed retention period).
- **NPHIES integration:** CHI-01 to CHI-07.
- **Whether a feature is a medical device:** SFDA-01 to SFDA-03, and SFDA-07 for AI.

If the engineer wants the answer applied to their project, suggest running `ksa-health-check`.
