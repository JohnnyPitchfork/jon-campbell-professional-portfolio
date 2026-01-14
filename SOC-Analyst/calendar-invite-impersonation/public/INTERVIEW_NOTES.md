# Interview Notes — Calendar Invite Impersonation (.ics)

## 15-second summary
I investigated an external calendar invite impersonation attempt where the attacker used `.ics` metadata—specifically the organizer field—to masquerade as internal IT. There was no malware payload; it was a social-engineering technique designed to leverage trust in calendar invites. I contained it quickly and turned the findings into a reusable detection concept (Sigma + Sentinel KQL).

## What I saw (signals)
- Unsolicited calendar invite (`.ics`) with `METHOD: REQUEST`
- Organizer identity looked internal, but sender was external
- Links were wrapped/redirected (tracking-style URLs)
- Nothing indicated an exploit; the risk was user trust and follow-on interaction

## Why it matters
Calendar invites are high-trust objects:
- they trigger reminders automatically
- users are trained to accept meeting requests quickly
- organizer fields are not validated by SPF/DKIM/DMARC

This makes calendar invites a low-noise impersonation vector that can bypass “auth passed” assumptions.

## What I did (process)
- Treated it as a suspected social-engineering event, not malware
- Reviewed message + calendar metadata in a controlled way
- Identified semantic mismatch: **external sender** vs **internal organizer**
- Documented findings and produced detection artifacts

## Outcome
- No user interaction occurred
- The attempt was contained (sender blocked / monitored)
- A detection concept was produced to identify similar patterns going forward

## Detection engineering takeaway
The durable detection logic is:
- `.ics` attachment + calendar `REQUEST`
- organizer domain matches internal domain
- sender domain is not internal
- organizer domain ≠ sender domain

I expressed this in:
- Sigma (portable concept)
- Sentinel KQL (implementation example)

## MITRE ATT&CK mapping (high confidence)
- T1566 (Phishing)
- T1036 (Masquerading)
- T1204 (User Execution, attempted)

## What I’d do next if this hit multiple users
- Hunt across inbound mail for `.ics` requests with organizer/sender mismatch
- Check for repeat infrastructure (same sender domain, same URL patterns)
- Add allowlist logic for known scheduling vendors to reduce false positives
- Add user comms: “treat unexpected calendar invites like phishing links”
