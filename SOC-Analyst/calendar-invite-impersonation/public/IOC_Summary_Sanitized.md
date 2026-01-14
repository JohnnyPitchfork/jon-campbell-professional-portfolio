# Indicator of Compromise (IOC) Summary — Sanitized

This document provides a **sanitized IOC summary** derived from a calendar invite impersonation attempt. All values are placeholders and do not correspond to real infrastructure.

## Email Characteristics

| Field | Value |
|------|------|
| Message Type | Calendar Invite (.ics) |
| Method | REQUEST |
| Delivery Vector | Email |
| Payload | None (social engineering only) |

## Identity Indicators

| Indicator Type | Placeholder Value |
|---------------|------------------|
| Impersonated Organizer | it-admin@[internal-domain].com |
| Sender Domain | external-sender[.]tld |
| Sender Alignment | External |

## Calendar Metadata

| Field | Placeholder |
|-----|------------|
| SUMMARY | Internal IT Meeting |
| ORGANIZER | mailto:it-admin@[internal-domain].com |
| ATTENDEE | mailto:user@[internal-domain].com |
| LOCATION | Video Conference |
| VALARM | Present |

## URL Indicators (Rendered / Redirected)

| Type | Placeholder |
|----|------------|
| Redirect Host | redirect-service[.]example |
| Final Host | phishing-endpoint[.]example |

## Detection Notes

- Authentication checks (SPF/DKIM/DMARC) may pass
- Impersonation occurs at the **content layer**, not SMTP layer
- Strong signal when organizer domain ≠ sender domain

## Usage Guidance

This IOC summary is provided for:
- Training
- Detection development
- Tabletop exercises

It is **not** intended for direct blocking or production use.
