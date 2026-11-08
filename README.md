# Awesome-Workflow-Automation-Sla-Triggers

# Awesome Workflow Automation & SLA Triggers

> A curated list of top Workflow Automation and SLA Trigger platforms — both SaaS/Hosted commercial solutions and open-source alternatives for business process automation, service-level agreement enforcement, and escalation management.  
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Freshworks Workflows](#freshworks-workflows)
  - [Zapier](#zapier)
  - [Make](#make)
  - [Workato](#workato)
  - [Nintex](#nintex)
  - [ProcessMaker](#processmaker)
  - [Kissflow](#kissflow)
  - [Camunda](#camunda)
  - [Pipefy](#pipefy)
  - [Appian](#appian)
- [Open-Source Software](#-open-source-software)
  - [Apache jBPM](#apache-jbpm)
  - [Flowable](#flowable)
  - [AlgaPSA SLA Module](#alga-psa-sla-module)
  - [Temporal](#temporal)
  - [Camunda 8 SLA Tutorial](#camunda-8-sla-tutorial)
  - [freeitsm](#freeitsm)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Workflow Automation and SLA Trigger platforms. These are not open-source but are included as reference points for feature comparison.

### Freshworks Workflows
**Type:** Workflow automation within Freshworks suite  
Freshworks provides workflow automation capabilities across its product suite (Freshdesk, Freshservice, Freshsales), including SLA management, escalation rules, and trigger-based automations. Supports multi-channel ticketing with automated assignment and time-based escalation policies.

### Zapier
**Type:** General-purpose automation platform  
Zapier connects 7,000+ apps with trigger-action workflows. Supports scheduled triggers (cron-like), webhook triggers, and time-based automation through delayed actions and filters. While not a dedicated SLA platform, it is frequently used for lightweight SLA notifications and escalation workflows when combined with ticketing tools.

### Make
**Type:** Visual automation platform  
Make provides visual scenario building with scheduling, webhooks, and time-based triggers. Supports complex branching logic and error handling. Can implement SLA timers through scheduled scenarios and date-based filters, though it lacks native SLA policy management.

### Workato
**Type:** Enterprise automation with workflow and SLA support  
Workato provides enterprise-grade automation with recipes, triggers, and actions across 1,000+ connectors. Supports time-based triggers, conditional logic, and error handling. Often used for approval workflows and SLA-driven escalations in enterprise environments.

### Nintex
**Type:** Process automation and workflow platform  
Nintex offers workflow automation with a focus on forms, document generation, and process intelligence. Includes approval workflows with escalation and time-based reminders. Supports both SharePoint-based and cloud-native workflows.

### ProcessMaker
**Type:** BPM and workflow automation  
ProcessMaker is a low-code BPM platform with workflow design, form building, and SLA management. Supports timer events, escalation rules, and deadline enforcement. Available as both cloud and self-hosted (open-source core) options, though the commercial edition adds enterprise features.

### Kissflow
**Type:** No-code workflow automation  
Kissflow provides no-code workflow and process automation with SLA tracking, escalation, and deadline reminders. Focused on business-user-friendly design with pre-built templates for common processes like approvals, procurement, and HR.

### Camunda
**Type:** Enterprise BPM with SLA enforcement via timers  
Camunda's commercial platform (Camunda 8) provides BPMN-based workflow automation with robust timer event support for SLA enforcement. Timer events can be configured as interrupting or non-interrupting boundary events, enabling both alerting (non-interrupting) and automatic escalation (interrupting). The Camunda 8 tutorials include a dedicated "Enforcing SLA" solution demonstrating timer events for time-sensitive tasks . Camunda 7 (open-source) remains available for self-hosted deployments.

### Pipefy
**Type:** Workflow management with SLA tracking  
Pipefy provides process management with SLA tracking, due date enforcement, and automated escalation. Features include time-based triggers, conditional logic, and dashboards showing SLA compliance. Focused on operations and service delivery workflows.

### Appian
**Type:** Low-code automation with SLA management  
Appian's low-code platform includes workflow automation with SLA tracking, escalation, and deadline management. Supports complex approval chains and process orchestration. Often used in regulated industries requiring audit trails and compliance controls.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Workflow Automation and SLA Trigger tools. All listed projects offer source code you can deploy on your own infrastructure.

### Apache jBPM
**Stack:** Java | **License:** Apache 2.0  
A lightweight, extensible workflow engine for BPMN 2.0 business processes. Supports human tasks with deadlines, notifications, and pluggable lifecycles [citation:14]. Designed for long-running processes with durable state, timers, signals, message correlation, and **service-level agreements**. Timer events provide the foundation for SLA enforcement, enabling both reminder notifications and automatic escalation. Integrates with Drools for business rules and DMN decisions within the same service.  
**Best for:** Java-centric organizations wanting an Apache-governed BPM engine with native SLA and timer support.

### Flowable
**Stack:** Java | **License:** Apache 2.0  
A BPMN engine that provides reliable timer-based SLA enforcement through BPMN timer events. **Critical distinction:** task `dueDate` is merely a display/query field; actual time-triggered execution requires BPMN timer events (boundary timers or intermediate events) backed by the async executor [citation:11]. Supports three timer types: `timeDate` (fixed point), `timeDuration` (relative), and `timeCycle` (recurring). Non-interrupting boundary timers enable reminders without canceling the task; interrupting timers enable automatic escalation or re-routing. The async executor persists timers as runtime jobs and executes them reliably, with dead-letter handling for failures [citation:5].  
**Best for:** Organizations needing proven BPMN-based SLA enforcement with fine-grained control over reminder vs. escalation semantics.

### AlgaPSA SLA Module
**Stack:** TypeScript / PostgreSQL | **License:** Open Source (per repository)  
A dedicated SLA management module for the AlgaPSA platform, tracking two milestones per ticket: first response and resolution. Each milestone has configurable time targets per priority level, measured against business hours with timezone and holiday awareness [citation:3]. Features threshold-based notifications (50%, 75%, 90%, 100%), 3-level escalation management, pause/resume with deadline shifting, and compliance reporting. Two timer backends: Community Edition uses PgBoss polling (every 5 minutes); Enterprise Edition uses Temporal workflows with per-ticket durable timers. Includes ITIL standard auto-configuration.  
**Best for:** Teams wanting a ready-made SLA module for PSA/ticketing use cases with business-hours awareness and escalation.

### Temporal
**Stack:** Go / Java / TypeScript / Python | **License:** MIT  
A workflow-as-code platform with durable execution and first-class timer support. The **Updatable Timer** pattern is specifically designed for SLA management with grace periods, approval workflows with deadline extensions, and time-based escalations that can be postponed [citation:6]. Workflows wait on a deadline while also listening for signals; if approval arrives first, the timer is cancelled; if the deadline expires first, the rejection path executes. Supports multiple deadline extensions through signal handlers that recalculate remaining duration. All timing is based on workflow time for replay consistency.  
**Best for:** Engineering teams building custom SLA workflows as code, especially where deadlines may need extension or modification at runtime.

### Camunda 8 SLA Tutorial
**Stack:** BPMN / Camunda 8 | **License:** Tutorial (Apache 2.0 for Camunda 7)  
A reference implementation from the official Camunda 8 tutorials demonstrating SLA enforcement using timer events for time-sensitive tasks . Covers alerting as well as ensuring processes do not wait indefinitely for external service responses. Useful as a learning resource and pattern reference for implementing SLA timers in Camunda or compatible BPMN engines.  
**Best for:** Teams learning BPMN-based SLA enforcement patterns or evaluating Camunda for SLA-driven workflows.

### freeitsm
**Stack:** PHP / MySQL | **License:** Open Source (per GitHub)  
An ITSM/helpdesk system with a dedicated **time-based workflow trigger** implementation for SLA breach detection [citation:13]. The core challenge addressed is that time-based events ("SLA about to breach", "contract expires in 30 days") have no write-path moment to hang a trigger off — time simply passes. The solution uses a `workflowEmitOnce()` function with a database-backed ledger (UNIQUE key over event, entity, and state fingerprint) to guarantee exactly-once firing even when cron runs overlap. The state fingerprint enables re-arming when deadlines change (e.g., priority change alters SLA target). Skips ledger writes when no workflow is listening, so activating a workflow later fires for all currently in-window items.  
**Best for:** Teams building ITSM or ticketing systems that need reliable, deduplicated time-based SLA triggers without a full BPM engine.

---

## 📊 Comparison at a Glance

| Software | License | Type | Timer Mechanism | Escalation | Self-Hosted | Best For |
|----------|---------|------|-----------------|------------|-------------|----------|
| **Freshworks** | Proprietary | Suite automation | SLA rules | ✅ | ❌ | Freshdesk users |
| **Zapier** | Proprietary | General automation | Scheduled/webhook | Via filters | ❌ | Lightweight notifications |
| **Make** | Proprietary | Visual automation | Scheduled scenarios | Via branching | ❌ | Complex visual workflows |
| **Workato** | Proprietary | Enterprise automation | Time triggers | ✅ | ❌ | Enterprise recipes |
| **Nintex** | Proprietary | Process automation | Approval timers | ✅ | ❌ | SharePoint workflows |
| **ProcessMaker** | Proprietary | BPM | Timer events | ✅ | ✅ (core) | Low-code BPM |
| **Kissflow** | Proprietary | No-code workflow | SLA deadlines | ✅ | ❌ | Business-user automation |
| **Camunda** | Proprietary | Enterprise BPM | BPMN timers | ✅ | ✅ (v7) | BPMN SLA enforcement |
| **Appian** | Proprietary | Low-code automation | SLA management | ✅ | ❌ | Regulated industries |
| **Apache jBPM** | Apache 2.0 | BPM engine | BPMN timers | ✅ | ✅ | Apache-governed BPM |
| **Flowable** | Apache 2.0 | BPM engine | BPMN timers | ✅ | ✅ | Proven BPMN SLA |
| **AlgaPSA SLA** | Open Source | SLA module | PgBoss / Temporal | ✅ (3-level) | ✅ | Ticketing SLA + business hours |
| **Temporal** | MIT | Workflow-as-code | Updatable timers | ✅ | ✅ | Custom SLA with extensions |
| **freeitsm** | Open Source | ITSM triggers | Cron + ledger | ✅ | ✅ | Deduplicated time triggers |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Workflow Automation or SLA Trigger tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source. Note that the open-source ecosystem for dedicated SLA trigger platforms is limited; many available tools are BPM engines with timer capabilities or SLA modules within broader platforms.

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
