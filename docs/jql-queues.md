# JQL Queue Configuration

## Purpose

This document outlines the Jira Service Management queues configured for this ITSM environment and the JQL logic utilized to segment incoming workloads by urgency, support category, and escalation status.

Rather than relying on a single chronological ticket stream, this architecture provides IT support agents with a focused, categorized view of active work. This configuration effectively separates inbound triage, high-priority incidents, specialized technical domains (network/hardware/software), and escalated tasks.

The queues were engineered using Jira Query Language (JQL) and validated against a simulated, multi-priority ticket workload.

## Queue Design Approach

The queue structure was engineered to reflect active service desk triage workflows. The core operational objectives were to:

* Isolate inbound requests for immediate triage
* Ensure high-priority and high-impact incidents remain highly visible
* Segment technical domains to align with specialized support skills
* Prevent escalated tickets from decaying in the general backlog
* Maintain visibility of unresolved work until final remediation

Labels and priorities were applied to the ticket workload from the agent console, and specific JQL filters were implemented to surface these tickets dynamically.

## Project Scope

The Jira project key utilized in this environment is:
`project = NDIV`

All queue filters are scoped explicitly to this project to ensure isolation from other Jira environments.

## Queue Summary

| Queue               | Operational Purpose                                                              |
| :------------------ | :------------------------------------------------------------------------------- |
| New Requests        | Primary inbound triage; shows all unresolved tickets, newest first.              |
| High Priority       | Isolates critical incidents; shows unresolved High/Highest priority tickets.     |
| Network Issues      | Groups infrastructure faults; shows unresolved network-related tickets.          |
| Hardware Issues     | Tracks physical assets; shows unresolved hardware-related tickets.               |
| Access / Onboarding | Segregates IAM workflows; shows unresolved access and onboarding tickets.        |
| Software Requests   | Manages application deployments; shows unresolved software-related requests.     |
| Escalated           | Escalation visibility view; shows unresolved tickets marked for tier escalation. |

---

## Queue Definitions & JQL Logic

### New Requests Queue

Serves as the primary inbound triage landing zone for open work.
`project = NDIV AND resolution = Unresolved ORDER BY created DESC`
This filter prevents new tickets from sitting unaddressed by isolating unassigned traffic and ordering it to minimize initial acknowledgment times.

### High Priority Queue

Surfaces unresolved tickets marked as High or Highest priority.
`project = NDIV AND priority in (High, Highest) AND resolution = Unresolved ORDER BY priority DESC, created ASC`
This logic ensures critical blockers (e.g., department-wide outages) bypass routine maintenance traffic and remain highly visible to protect SLA targets.

### Network Issues Queue

Surfaces infrastructure and remote-connectivity incidents.
`project = NDIV AND labels = network AND resolution = Unresolved ORDER BY priority DESC, created ASC`
Examples include Wi-Fi faults, VPN connection drops, and widespread connectivity outages.

### Hardware Issues Queue

Consolidates physical asset lifecycles and endpoint malfunctions.
`project = NDIV AND labels = hardware AND resolution = Unresolved ORDER BY priority DESC, created ASC`
Examples include local workstation failures, peripheral issues, and shared printing hardware faults.

### Access / Onboarding Queue

Segregates Identity & Access Management (IAM) workflows and provisioning tasks.
`project = NDIV AND labels in (access, onboarding) AND resolution = Unresolved ORDER BY priority DESC, created ASC`
Examples include new user profile creation, Microsoft 365 access provisioning, and shared drive access modifications.

### Software Requests Queue

Manages application deployments and licensing tasks.
`project = NDIV AND labels = software AND resolution = Unresolved ORDER BY priority DESC, created ASC`
Examples include specific application installation requests and local software patching.

### Escalated Queue

Provides a focused view for tickets requiring higher-tier intervention.
`project = NDIV AND labels = escalated AND resolution = Unresolved ORDER BY priority DESC, created ASC`
This queue captures tickets that demand additional technical ownership from higher-tier support, systems administration, network/admin support, or security review.

---

## Queue Behavior

The queues update dynamically based on current ticket metadata. When a ticket matches the JQL conditions, it populates the respective queue.

A single high-impact incident (such as a department-wide network outage) can populate multiple queues simultaneously:

* New Requests
* High Priority
* Network Issues
* Escalated

This overlapping architecture is intentional, providing different operational lenses on the same critical incident. Once a ticket achieves a "Resolved" state, the `resolution = Unresolved` constraint ensures it drops out of these active working views.

