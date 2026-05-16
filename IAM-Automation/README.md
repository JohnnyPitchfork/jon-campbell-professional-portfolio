# Identity & Access Management — Automation & Engineering

Real-world identity lifecycle automation, Entra ID governance, delegation patterns, and automation engineering.

---

## Projects

### 1. Entra Shared Mailbox Manager

**Language:** C# / .NET 8 (WPF)  
**Status:** v1.0 release imminent  
**Repository:** [github.com/JohnnyPitchfork/entra-shared-mailbox-manager](https://github.com/JohnnyPitchfork/entra-shared-mailbox-manager)

**What it does:**
A production-grade Windows desktop tool that solves three operational pain points in Microsoft 365:

1. **Bulk Permission Management** — Grant/revoke `FullAccess`, `SendAs`, and `SendOnBehalf` across shared mailboxes in bulk, with mandatory preview validation
2. **Safe Delegation to Non-Admins** — Team leads can manage only their team's shared mailboxes via Exchange RBAC management scopes (no tenant-wide admin role needed)
3. **Orphaned Permission Cleanup** — Identify and remove delegates whose Entra sign-in is blocked, with interactive cleanup workflows

**Architecture Highlights:**
- **Dual-Layer Security Model:**
  - Layer 1 (Enforced): Exchange Online RBAC management scopes prevent any operation outside the delegated scope
  - Layer 2 (UX): Application-side filtering shows each user only the mailboxes they can access
- **No Standing Privileges:** Every operation runs in the operator's delegated context; bugs in the tool cannot grant unauthorized access
- **Flexible Deployment:** Three patterns from one binary — Intune + SharePoint central config, Intune + static config, or standalone install

**Why This Matters:**
- Demonstrates identity systems thinking (security model centered on RBAC and Entra groups)
- Shows product engineering maturity (evolving from single-purpose script to scalable tool)
- Solves real enterprise operational challenges at scale
- Emphasizes least-privilege and security-first architecture

---

## Coming Soon

- **M365 / Exchange / Entra Admin Script Library** — PowerShell and Microsoft Graph API utilities for lifecycle automation, governance workflows, and operational tasks
- **Identity Governance Patterns** — Reference implementations for SSO, federation, lifecycle automation, and access governance

---

