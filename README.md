# Jon Campbell — Professional Portfolio

This repository is a curated, real-world professional portfolio showcasing hands-on work across identity and access management, systems engineering, security operations, and infrastructure automation.

It is organized by **role and function**, with each section containing practical artifacts, documentation, and case studies drawn from real environments.

---

## 🔑 **Identity & Access Management — Flagship Project**

### **Entra Shared Mailbox Manager**

A production-grade Windows desktop tool for delegated administration of Microsoft 365 shared mailboxes at scale. Solves three hard problems: bulk permission management, safe delegation to non-admin team leads, and orphaned permission cleanup — all enforced by Exchange Online RBAC, not application logic.

**Key Points:**
- **Language/Stack:** C# / .NET 8 (WPF), Microsoft Graph API, Exchange Online PowerShell
- **Architecture:** Dual-layer security model (platform-enforced + UX filtering)
- **Deployment:** Three patterns from one binary (Intune + central config, Intune + static, solo)
- **Status:** v1.0 release imminent
- **Showcase:** Real engineering that solves genuine operational pain points

📂 **See full project:** [github.com/JohnnyPitchfork/entra-shared-mailbox-manager](https://github.com/JohnnyPitchfork/entra-shared-mailbox-manager)

**Why This Project Matters:**
- **Identity Systems Thinking** — Security model built around Exchange RBAC management scopes and Entra group membership, not application-layer ACLs
- **Least-Privilege Delegation** — No standing privileges; all operations execute in the operator's delegated context
- **Product Engineering** — Evolves a single-purpose PowerShell script into a scalable, productized tool with deployment flexibility
- **Security-First Architecture** — Dual-layer authorization ensures the platform (Exchange Online) enforces access boundaries, not the application
- **Enterprise Operations** — Solves real pain points at scale (hundreds of shared mailboxes, complex delegation models)

---

## 🔐 **Identity & Automation**

Identity lifecycle automation, Entra ID governance, PowerShell tooling, and access control design.

📂 [`IAM-Automation/`](./IAM-Automation)

---

## 🖥️ **Systems Administration**

Microsoft 365, Windows administration, operational hardening, reliability, and infrastructure management.

📂 [`Systems-Administrator/`](./Systems-Administrator)

---

## 💻 **Endpoint Management**

Intune, device compliance, application packaging, baseline enforcement, and deployment workflows.

📂 [`Endpoint-Management/`](./Endpoint-Management)

---

## 🔐 **Security Operations (SOC Analyst)**

Hands-on incident response, email security investigations, detection engineering, and threat analysis.

📂 [`SOC-Analyst/`](./SOC-Analyst)

---

## 📝 **Technical Communication**

Incident reports, executive summaries, runbooks, proposals, and security documentation.

📂 [`Technical-Communication/`](./Technical-Communication)

---

## 📁 **Assets**

Shared images, diagrams, screenshots, and supporting materials.

📂 [`assets/`](./assets)

---

## ⚠️ **Disclaimer**

All materials in this repository are **sanitized** and **de-identified**.  
No proprietary, confidential, or customer-identifiable information is included.

