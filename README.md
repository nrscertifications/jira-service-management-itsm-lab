# Jira Service Management (JSM) ITSM Configuration Lab

## Project Overview

This repository documents a functional Jira Service Management (JSM) ITSM environment focused on structured data ingestion, ticket triage, queue design, SLA tracking, and multi-tier escalation logic. 

I engineered this operational service desk workflow to seamlessly bridge user-facing request portals with back-end agent management. The core objective was to simulate how an enterprise IT support infrastructure captures, segregates, prioritizes, and routes service requests and active incidents.

This environment aligns directly with operational workflows utilized in high-volume Help Desk, Service Desk Analyst, Tier 1.5, and Junior Tier 2 Support environments. 

> **Note:** All configurations were validated using a simulated multi-priority workload. All screenshots feature demo data and redacted customer identifiers.

---

## Core Technical Skills & Tools

* **ITSM Platform:** Jira Service Management (JSM)
* **Data Ingestion:** Jira Customer Portal, request type mapping, structured intake forms
* **Queue Architecture:** Ticket segmentation, custom JQL (Jira Query Language) filtering
* **Ticket Triage:** Urgency & business impact mapping, priority tiering, operational labeling
* **SLA Management:** Time to First Response, Time to Resolution, custom business-hours calendars
* **Technical Documentation:** Escalation workflows, multi-tier handoff logic, Markdown configuration
* **Repository Versioning:** Git, GitHub file structure synchronization

---

## Functional Architecture

### 1. Structured Intake & Shift-Left Design
I configured the user-facing customer portal into distinct, logical support categories. This operational design encourages user self-categorization at the point of ingestion, routing issues to the correct framework before an agent ever touches the ticket.

The portal segregates requests into four foundational categories:
* Hardware and device issues
* Access and account requests
* Application and software requests
* Network and infrastructure issues

This framework establishes clean data input, drastically reducing ticket bounce rates and minimizing unnecessary back-and-forth communication cycles between users and the service desk.

### 2. Request Type & Ingestion Form Engineering
I built structured intake forms for common enterprise IT support scenarios, including:
* **Self-Service & Identity:** Password resets, New user access requests
* **Endpoint & Software:** Software installation requests, Local hardware issues
* **Infrastructure & Network:** Network/Wi-Fi faults, VPN connectivity drops, Department-wide network outages

Each form enforces field requirements to capture critical triage details—such as urgency, business impact, affected services, and necessary approval managers—ensuring support agents have immediate context to begin troubleshooting or escalation.

### 3. Agent-Side Workspace & Triage Logic
To validate the portal’s ingestion logic, I processed a simulated multi-priority workload through the system. From the agent console, I evaluated ticket payloads and applied operational metadata (priorities, component labels, and impact scopes). This process successfully isolated standard service fulfillment tasks from high-urgency incidents like VPN drops or department outages.

### 4. JQL-Based Queue Segmentation
Instead of relying on standard out-of-the-box Jira views, I constructed custom queues utilizing precise **Jira Query Language (JQL)** expressions. This architecture dynamically prioritizes unresolved issues by urgency and technical silo:
* **New Requests:** Inbound unassigned tickets awaiting initial triage.
* **High Priority:** P1/P2 incidents threatening business continuity.
* **Network Issues:** Local and wide-area connectivity faults.
* **Access / Onboarding:** Identity management and account provisions.
* **Hardware Issues:** Physical workstation, peripheral, and printer assets.
* **Software Requests:** Application deployments and licensing requests.
* **Escalated:** Tickets breaching or nearing SLA limits requiring tier transitions.

This configuration ensures an active support team maintains clear visibility over high-impact tickets rather than scrolling through an unorganized, chronological list.

### 5. SLA Metric Enforcement
I engineered automated Service Level Agreement (SLA) tracking rules tied to an organizational business-hours calendar. This configuration includes:
* **Time to First Response SLA:** Aggressive, priority-driven response targets to ensure rapid initial evaluation.
* **Time to Resolution SLA:** Defined resolution timelines mapped to incident severity.
* **Business-Hours Integration:** Calendar constraints that pause SLA countdowns during non-operational hours, protecting team metrics from artificial decay.

---

## Configuration Walkthrough & Evidence

### Customer Portal
The user portal interface presents clean service categories to prevent incorrect ticket routing by end-users.

![Customer portal homepage](screenshots/customer-portal-homepage.png)

---

### Structured Intake Forms
These forms capture diagnostic data before requests hit the support queue, accelerating initial triage workflows.

#### New User Access Request Form
Surfaces required fields for requested systems, business impact tiers, urgency, and manager/approver selection.
![New user access request form](screenshots/new-user-access-blank-form-redacted.jpg)

#### Network/Wi-Fi Issue Form
Gathers symptom details, affected hardware locations, and supporting logs or screenshots upfront.
![Network Wi-Fi request form](screenshots/network-wifi-blank-form-redacted.jpg)

---

### Simulated Ticket Workload
A diverse operational backlog was generated to validate the ingestion rules, labeling mechanics, and active SLA behavior.

![All open Jira tickets](screenshots/all-open-tickets-redacted.png)

---

### Customer-Side Ticket Examples
These screenshots demonstrate the transparency loop from the user's perspective as they track ticket lifecycle status.

#### Department Network Outage
![Customer-side network outage ticket](screenshots/customer-ticket-network-outage-redacted.png)

#### New User Access Request
![Customer-side new user access ticket](screenshots/customer-ticket-new-user-access-redacted.png)

#### Hardware / Printer Issue
![Customer-side hardware printer ticket](screenshots/customer-ticket-hardware-printer-redacted.png)

#### VPN Connectivity Issue
![Customer-side VPN ticket](screenshots/customer-ticket-vpn-redacted.png)

#### Laptop Wi-Fi Issue
![Customer-side laptop Wi-Fi ticket](screenshots/customer-ticket-laptop-wifi-redacted.png)

#### Password Reset Request
![Customer-side password reset ticket](screenshots/customer-ticket-password-reset-redacted.png)

#### Software Install Request
![Customer-side software install request](screenshots/customer-ticket-software-install-redacted.png)

---

### JQL-Driven Agent Queues
These views showcase the custom JQL queue separation, effectively categorizing workloads by technical domain and priority.

#### New Requests Queue
![New requests queue](screenshots/queue-new-requests-redacted.png)

#### High Priority Queue
![High priority queue](screenshots/queue-high-priority-redacted.png)

#### Network Issues Queue
![Network issues queue](screenshots/queue-network-issues-redacted.png)

#### Access / Onboarding Queue
![Access and onboarding queue](screenshots/queue-access-onboarding-redacted.png)

#### Hardware Issues Queue
![Hardware issues queue](screenshots/queue-hardware-issues-redacted.png)

#### Software Requests Queue
![Software requests queue](screenshots/queue-software-requests-redacted.png)

#### Escalated Queue
![Escalated queue](screenshots/queue-escalated-redacted.png)

---

### Agent-Side Ticket Triage
The internal agent view surfaces key metadata layout optimizations, allowing agents to instantly evaluate impact boundaries and escalation contexts.

#### Department Network Outage
An example of a critical infrastructure incident impacting multi-user system access.
![Agent-side network outage ticket](screenshots/agent-ticket-network-outage-redacted.png)

#### New User Access Request
An identity management payload displaying workflow progress and provisioning paths.
![Agent-side new user access ticket](screenshots/agent-ticket-new-user-access-redacted.png)

#### Hardware / Printer Issue
A typical local asset incident mapping localized disruption context.
![Agent-side hardware printer ticket](screenshots/agent-ticket-hardware-printer-redacted.png)

---

### SLA Target Configuration
I aligned the backend SLA engine with corporate constraints by defining operational calendars and metric objectives.

#### Business-Hours Calendar
![SLA business hours calendar](screenshots/sla-business-hours-calendar.png)

#### Time to First Response SLA
Priority-stratified targets defining the initial acknowledgment matrix.
![Time to first response SLA configuration](screenshots/sla-time-to-first-response.png)

#### Time to Resolution SLA
Enforced timelines defining strict bounds for complete incident remediation.
![Time to resolution SLA configuration](screenshots/sla-time-to-resolution.png)

---

### SLA Applied to Tickets
These live ticket instances prove the background SLA engine actively monitors and holds support operations accountable to operational deadlines.

#### Network Outage SLA View
![SLA timers on network outage ticket](screenshots/ticket-network-outage-sla-redacted.png)

#### Hardware Printer SLA View
![SLA timers on hardware printer ticket](screenshots/ticket-hardware-printer-sla-redacted.png)

---

## Core Competencies Demonstrated

* **ITSM Tool Configuration:** Mapping business operational needs directly into Jira Service Management components.
* **Data Integrity Architecture:** Engineering rigid intake structures to capture rich, diagnostic context from users.
* **Workload Optimization:** Leveraging advanced JQL filter syntax to isolate critical issues and prioritize agent focus.
* **SLA Compliance Controls:** Configuring dual-layer response/resolution SLA tracking around explicit business-hour policies.
* **Technical Workflow Documentation:** Formulating clear, markdown-based escalation pathways mapping technical handoffs to specialized system admins, network engineers, and security teams.

---

## Project Documentation

Deep-dive operational playbooks and exact structural configurations are located in the `docs` folder:
* [Project Overview](docs/project-overview.md)
* [JQL Queues Matrix](docs/jql-queues.md)
* [SLA Configuration Guide](docs/sla-configuration.md)
* [Escalation & Handoff Workflow](docs/escalation-workflow.md)

---

## Interview Summary (The Pitch)

I configured this Jira Service Management environment to thoroughly master how a modern, efficient IT service desk scales its ticket handling. Instead of just learning how to close tickets, I focused on the administrative logic behind queue architecture and data quality. 

I engineered a 'shift-left' strategy using structured portal intake forms to capture technical variables upfront, removing the standard back-and-forth communication cycle. I then designed targeted JQL filters so the queues automatically surface the right work, separating standard provisioning requests from critical, high-impact infrastructure incidents. Finally, I applied a custom business-hours calendar to govern first-response and resolution SLA metrics. 

This project demonstrates my practical understanding of the complete incident lifecycle, workload management, and the exact tool configurations needed to maximize service desk efficiency.
