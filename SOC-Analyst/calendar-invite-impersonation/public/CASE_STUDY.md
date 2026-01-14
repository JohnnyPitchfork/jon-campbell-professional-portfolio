# 📅 Calendar Invite Impersonation — Detection & Forensics Case Study

## Overview

This case study documents a real-world **calendar-based impersonation attempt** in which an external actor delivered a malicious `.ics` meeting request designed to impersonate an internal IT administrative identity.

The technique relied on **calendar metadata trust**—specifically manipulation of the `ORGANIZER` field—rather than malware, exploits, or credential harvesting. The incident demonstrates how social engineering can bypass traditional email security assumptions and why content-level inspection remains critical in security operations.

This writeup is **sanitized for public sharing** and focuses on investigative reasoning, threat classification, and detection design.

---

## Incident Summary

- **Threat Type:** Phishing – Impersonation (Calendar Invite Abuse)  
- **Delivery Vector:** Email-delivered calendar invite (`.ics`)  
- **Technique:** Organizer masquerading via calendar metadata  
- **Payload:** None (social engineering only)  
- **Impact:** None (prevented)  

An unsolicited meeting invitation was received that appeared to originate from internal IT administration. While the email itself was externally sourced, the calendar object embedded within the message claimed an internal organizer identity.

This mismatch was the primary indicator of malicious intent.

---

## What Made This Suspicious

Calendar invite metadata is **not validated** by SPF, DKIM, or DMARC. As a result, attackers can arbitrarily set fields such as `ORGANIZER`, `SUMMARY`, and `LOCATION` to convey authority and legitimacy.

Key red flags included:

- The email originated from an **external sender**
- The calendar `ORGANIZER` field claimed an **internal administrative identity**
- The invite framing suggested internal IT coordination
- No prior context or legitimate scheduling activity existed

This pattern is consistent with social engineering designed to prompt user trust, acceptance of the invite, or follow-on interaction.

---

## Investigation Actions (Sanitized)

The investigation focused on **content semantics**, not malware analysis.

Actions performed included:

- Reviewing email and calendar metadata in a controlled environment
- Decoding and inspecting the `.ics` calendar object
- Identifying key calendar fields:
  - `METHOD: REQUEST`
  - `SUMMARY` indicating an internal IT meeting
  - `ORGANIZER` masquerading as an internal identity
  - `ATTENDEE` entries targeting internal recipients
  - `VALARM` present (reminder behavior)
- Reviewing rendered links and redirect patterns associated with the invite
- Confirming the absence of executable content, scripts, or exploit payloads

No user interaction occurred, and the incident was contained without impact.

---

## Threat Classification

- **Category:** Social Engineering / Impersonation  
- **Objective:** User execution (accept invite, join meeting, trust organizer)  
- **Severity:** Low (attempted, no interaction)  

### MITRE ATT&CK Mapping (High Confidence)

- **T1566** – Phishing  
- **T1566.002** – Spearphishing Link  
- **T1566.003** – Spearphishing via Service  
- **T1036** – Masquerading  
- **T1204** – User Execution (Attempted)

---

## Detection Engineering

The incident was converted into a **reusable detection concept** rather than treated as an isolated event.

Core detection logic:

- Incoming email with a `.ics` attachment  
- Calendar `METHOD` set to `REQUEST`  
- Calendar organizer domain appears internal  
- Sender domain is external  
- Organizer domain ≠ sender domain  

A **sanitized, Sigma-style detection rule** is included in this repository to demonstrate how this pattern can be operationalized in a SIEM or email security platform.

📄 See: `detections/sigma_calendar_invite_impersonation.yml`

---

## Why This Matters for Security Operations

Calendar invites are **high-trust objects**:

- They trigger reminders automatically
- They imply authority and legitimacy
- Users are conditioned to accept them with minimal scrutiny

Because this attack occurs at the **content and context layer**, authentication checks alone are insufficient. Calendar-based impersonation represents a low-noise, high-impact social engineering vector that deserves explicit detection coverage.

---

## Lessons Learned

- “Pass” results for email authentication do not guarantee legitimacy
- Metadata trust can be exploited without malware or exploits
- Semantic mismatches (sender vs organizer) are powerful detection signals
- Translating incidents into detections increases long-term defensive value

---

## Disclaimer

All details in this case study are **anonymized and sanitized**.  
Raw forensic artifacts and environment-specific metadata are intentionally excluded to avoid disclosure of internal infrastructure details.

---

## Attribution

This case study was authored by the repository owner as part of a professional security operations portfolio.

The investigation reflects real-world SOC workflows, adapted and sanitized for public demonstration.
