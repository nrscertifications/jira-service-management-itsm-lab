# Jira Service Management ITSM Lab

## Project Overview

This repository documents a Jira Service Management environment configured for service desk request intake, ticket triage, queue management, SLA tracking, and escalation workflow documentation.

I configured the project to show how an IT support team can collect user requests through a customer portal, organize incoming work into agent queues, apply priority and impact context, and track response/resolution expectations through SLA rules.

The lab uses simulated tickets and demo data to represent common IT support scenarios, including password resets, software requests, hardware issues, VPN connectivity problems, Wi-Fi troubleshooting, onboarding requests, and department-wide outages.

> **Data note:** All tickets, users, and request examples use demo data. Screenshots were reviewed before publishing and do not include production customer data or live business records.

---

## Core Technical Skills & Tools

* **ITSM Platform:** Jira Service Management
* **Request Intake:** Customer portal groups, request types, required fields, and structured forms
* **Ticket Triage:** Urgency, impact, priority mapping, labels, and support categories
* **Queue Management:** JQL-based queues for new requests, high-priority work, network issues, access/onboarding, hardware, software, and escalated tickets
* **SLA Tracking:** Time to first response, time to resolution, business-hours calendar, and priority-based targets
* **Escalation Documentation:** Support handoff paths for service desk, systems, network, and security-related issues
* **Technical Documentation:** Markdown documentation, screenshots, Git/GitHub repository structure

---

## Functional Architecture

### 1. Structured Intake Design

I configured the customer portal into clear support categories so users can submit requests with the correct context from the start.

The portal separates requests into common IT support areas:

* Hardware and device issues
* Access and account requests
* Application and software requests
* Network and infrastructure issues

This structure helps agents receive cleaner ticket details and reduces the need for repeated clarification.

### 2. Request Type & Form Configuration

I built request forms for common service desk scenarios, including:

* **Access:** Password resets and new user access requests
* **Endpoint & Software:** Software installation requests and local hardware issues
* **Network:** Wi-Fi issues, VPN connectivity drops, and department-wide network outages

Each form captures practical support details such as urgency, business impact, affected service, device/location information, and manager or approval context where needed.

### 3. Agent-Side Ticket Review

I created a simulated ticket workload and reviewed the tickets from the agent side. This allowed me to validate that request details, priorities, labels, and impact context were visible where an agent would need them.

This workflow separates routine service requests from higher-impact incidents such as VPN failures or department network outages.

### 4. JQL-Based Queue Segmentation

I created custom queues using Jira Query Language to separate work by priority and support area.

Queues included:

* **New Requests:** Inbound tickets awaiting triage
* **High Priority:** Urgent or high-impact tickets
* **Network Issues:** Wi-Fi, VPN, and connectivity-related tickets
* **Access / Onboarding:** Password resets and new user access requests
* **Hardware Issues:** Printer, workstation, and peripheral issues
* **Software Requests:** Application installation and software access requests
* **Escalated:** Tickets requiring higher-level support review

This gives agents a clearer view of active work instead of relying only on a chronological ticket list.

### 5. SLA Tracking

I configured SLA rules for response and resolution tracking using a business-hours calendar.

The SLA work included:

* **Time to First Response:** Priority-based initial response expectations
* **Time to Resolution:** Priority-based resolution targets
* **Business-Hours Calendar:** SLA timing aligned to working hours

This demonstrates how service desk teams can track time-sensitive work and identify tickets that may require escalation.

---

## Configuration Walkthrough & Evidence

### Customer Portal

The customer portal presents clear service categories to help users select the correct request path.

![Customer portal homepage](screenshots/customer-portal-homepage.png)

---

### Structured Intake Forms

These forms collect important troubleshooting and routing details before the request reaches the support queue.

#### New User Access Request Form

Captures requested systems, business impact, urgency, and manager/approver context.

![New user access request form](screenshots/new-user-access-blank-form-redacted.jpg)

#### Network/Wi-Fi Issue Form

Captures symptoms, affected location/device details, and supporting information for network-related troubleshooting.

![Network Wi-Fi request form](screenshots/network-wifi-blank-form-redacted.jpg)

---

### Simulated Ticket Workload

A simulated ticket backlog was created to validate request intake, labels, priorities, and SLA visibility.

![All open Jira tickets](screenshots/all-open-tickets-redacted.png)

---

### Customer-Side Ticket Examples

These screenshots show how users can view their submitted requests and ticket status from the customer side.

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

These views show custom JQL queue separation by priority and technical area.

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

These examples show how ticket details appear from the agent workspace, including priority, request context, and support metadata.

#### Department Network Outage

Example of a higher-impact network incident affecting multiple users or a department-level service.

![Agent-side network outage ticket](screenshots/agent-ticket-network-outage-redacted.png)

#### New User Access Request

Example of an onboarding/access request with provisioning context.

![Agent-side new user access ticket](screenshots/agent-ticket-new-user-access-redacted.png)

#### Hardware / Printer Issue

Example of a local hardware/peripheral support ticket.

![Agent-side hardware printer ticket](screenshots/agent-ticket-hardware-printer-redacted.png)

---

### SLA Target Configuration

I configured SLA tracking around business-hour response and resolution expectations.

#### Business-Hours Calendar

![SLA business hours calendar](screenshots/sla-business-hours-calendar.png)

#### Time to First Response SLA

Priority-based targets for initial response tracking.

![Time to first response SLA configuration](screenshots/sla-time-to-first-response.png)

#### Time to Resolution SLA

Priority-based targets for resolution tracking.

![Time to resolution SLA configuration](screenshots/sla-time-to-resolution.png)

---

### SLA Applied to Tickets

These ticket examples show SLA timers applied to active support work.

#### Network Outage SLA View

![SLA timers on network outage ticket](screenshots/ticket-network-outage-sla-redacted.png)

#### Hardware Printer SLA View

![SLA timers on hardware printer ticket](screenshots/ticket-hardware-printer-sla-redacted.png)

---

## Core Competencies Demonstrated

* Configured Jira Service Management request types and customer portal categories.
* Built structured intake forms for common IT support scenarios.
* Created a simulated ticket workload to validate request routing, priority, labels, and SLA behavior.
* Created JQL-based queues to separate tickets by priority and technical area.
* Reviewed ticket examples from both customer-side and agent-side views.
* Configured SLA tracking for response and resolution workflows.
* Documented escalation paths and service desk handoff logic.
* Organized screenshots and documentation in a GitHub portfolio format.

---

## Project Documentation

Detailed documentation is located in the [`docs/`](docs/) folder:

* [Project Overview](docs/project-overview.md)
* [JQL Queues Matrix](docs/jql-queues.md)
* [SLA Configuration Guide](docs/sla-configuration.md)
* [Escalation & Handoff Workflow](docs/escalation-workflow.md)

---

## Repository Scope

This repository contains a simulated Jira Service Management configuration using demo data. It does not contain production customer data, production credentials, private user data, or live business records.
