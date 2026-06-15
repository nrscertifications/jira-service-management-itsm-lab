# Project Overview

## Purpose

This project documents a Jira Service Management ITSM environment configured to model a realistic service desk workflow.

The environment was built around the full ticket lifecycle: customer intake, structured request forms, agent-side triage, queue segmentation, SLA tracking, and escalation routing.

The goal was to create a portfolio-ready ITSM lab that demonstrates how support teams organize incoming requests, prioritize active incidents, track response expectations, and route work to the correct support owner.

---

## Environment Scope

The lab focuses on common Help Desk, Service Desk, IT Support, Tier 1.5, and junior Tier 2 workflows.

The configuration includes:

* A customer-facing support portal
* Request groups organized by support category
* Structured request types and intake forms
* Sample tickets submitted through the portal
* Agent-side ticket review and triage
* Labels and priorities for workload classification
* JQL-based queues for active work segmentation
* SLA metrics for first response and resolution tracking
* Escalation workflow documentation for higher-tier handoff

---

## Customer Portal Structure

The customer portal was organized into clear support categories so users can select the correct request path before submitting a ticket.

Portal categories included:

* Hardware and device issues
* Access and account requests
* Application and software requests
* Network and infrastructure issues

This structure helps reduce incorrect routing and gives the support team better intake data before the ticket reaches the agent queue.

---

## Request Types Configured

The following request types were configured and tested:

* Password reset
* Software install request
* New user access request
* Hardware issue
* Network/Wi-Fi issue
* VPN connectivity issue
* Department network outage

These request types represent common service desk scenarios that appear in real IT support environments.

---

## Intake Form Design

The intake forms were designed to collect useful support context before an agent begins triage.

The forms captured details such as:

* Urgency
* Business impact
* Affected device or service
* Requested systems
* Manager or approver details
* Screenshots or supporting attachments
* Additional issue description

This allows the ticket to arrive with enough information for the support team to begin troubleshooting, prioritization, or escalation without relying only on a vague request summary.

---

## Ticket Triage Model

After sample requests were submitted through the portal, tickets were reviewed from the agent side.

Agent-side triage included:

* Reviewing the request type
* Checking ticket priority
* Applying labels such as network, hardware, access, onboarding, software, and escalated
* Reviewing business impact and affected service details
* Identifying whether the ticket could remain with Tier 1 / Tier 1.5 support or required escalation

This workflow separates routine service requests from higher-impact incidents such as VPN failures, department outages, and access provisioning work.

---

## Queue Design

Custom Jira queues were configured using JQL to keep active work organized.

The queue structure includes:

* New Requests
* High Priority
* Network Issues
* Access / Onboarding
* Hardware Issues
* Software Requests
* Escalated

The purpose of the queue structure is to prevent urgent or specialized work from being buried in one general backlog.

Detailed queue logic is documented in:

[JQL Queues](jql-queues.md)

---

## SLA Configuration

SLA tracking was configured to measure response and resolution expectations.

The SLA setup includes:

* Business-hours calendar
* Time to First Response SLA
* Time to Resolution SLA
* Priority-based response targets
* Priority-based resolution targets
* Pause logic for tickets waiting on customer input

Detailed SLA logic is documented in:

[SLA Configuration](sla-configuration.md)

---

## Escalation Workflow

Escalation logic was documented to define when a ticket should remain with Tier 1 / Tier 1.5 support and when it should be routed to another technical owner.

Escalation paths include:

* Systems administration
* IAM / access support
* Network support
* Endpoint management
* Security or administrator review

Detailed escalation logic is documented in:

[Escalation Workflow](escalation-workflow.md)

---

## Skills Demonstrated

This project demonstrates practical ITSM and service desk skills, including:

* Jira Service Management configuration
* Customer portal organization
* Structured intake form design
* Ticket triage and prioritization
* JQL queue configuration
* SLA setup and validation
* Escalation routing and handoff documentation
* GitHub-based technical documentation
* Organizing screenshots and supporting evidence for a portfolio project

---

## Repository Structure

```text
jira-service-management-itsm-lab/
├── README.md
├── docs/
│   ├── project-overview.md
│   ├── jql-queues.md
│   ├── sla-configuration.md
│   └── escalation-workflow.md
└── screenshots/
    └── redacted project screenshots
```

