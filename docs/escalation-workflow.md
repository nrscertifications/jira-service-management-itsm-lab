# Operational Escalation & Routing Workflow

## Overview

This document outlines the escalation architecture and technical handoff protocols governing this Jira Service Management ITSM environment.

In an enterprise service desk, escalation is not simply passing a ticket to another queue. It is a structured transfer of technical ownership executed when an incident exceeds the scope, access level, or troubleshooting boundary of the primary support team.

This workflow defines how Tier 1.5 analysts conduct initial discovery, document findings, and route incidents to the correct technical stakeholders, such as systems administration, network support, identity and access management, or security review.

---

## Ticket Lifecycle & State Management

This environment utilizes an ITSM-aligned ticket lifecycle to maintain clear state visibility for support teams and end users.

| Status               | Operational Purpose                                                                              |
| :------------------- | :----------------------------------------------------------------------------------------------- |
| Open                 | Inbound ticket has been ingested and is awaiting initial triage                                  |
| In Progress          | Agent has assumed technical ownership and is actively troubleshooting or coordinating next steps |
| Waiting for Customer | Remediation is paused pending user input, manager approval, or validation                        |
| Escalated            | Incident exceeds Tier 1.5 scope and requires higher-tier technical ownership                     |
| Resolved             | Remediation is complete, and the service has been restored or fulfilled                          |
| Closed               | Ticket lifecycle is finalized and no further support action is expected unless reopened          |

---

## Escalation Governance & Principles

Tickets are escalated when they breach the operational or permission-based boundaries of the service desk. Escalation is required when an incident meets one or more of the following criteria:

* Scope of Impact: The fault affects multiple users, a shared resource, or an entire department.
* Permission Boundaries: Remediation requires administrator privileges, directory modifications, or backend system access.
* Infrastructure Faults: Initial triage points to core network routing, server availability, VPN backend services, or shared infrastructure.
* Security Risk: The ticket involves suspected account compromise, unauthorized access attempts, or malware indicators.
* SLA Jeopardy: The ticket is at risk of breaching response or resolution targets without higher-tier intervention.

---

## Escalation & Routing Matrix

| Incident Scenario                | Tier 1.5 Discovery & Action                                                                        | Technical Escalation Path                                                     |
| :------------------------------- | :------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------- |
| Single-user password reset       | Verify identity, confirm IAM scope, execute reset according to policy                              | Resolved at Tier 1.5 if policy allows                                         |
| User account lockout             | Confirm identity, verify lockout status, unlock if within policy                                   | IAM support if lockout persists or access policy review is required           |
| New user provisioning            | Validate request details, identify required access groups, secure manager approval                 | SysAdmin / IAM support                                                        |
| Software deployment              | Verify device, business justification, approval status, and licensing requirement                  | SysAdmin / endpoint management                                                |
| Printer fault affecting one user | Check local print queue, printer selection, driver state, and IP connectivity                      | Tier 2 / infrastructure if print server or network printer fault is suspected |
| Laptop Wi-Fi issue               | Validate local adapter state, credentials, signal, and whether other users are affected            | Network support if access point or authentication issue is suspected          |
| Remote VPN failure               | Confirm local internet access, VPN client behavior, MFA prompt, and error message                  | Network support / systems administration                                      |
| Department network outage        | Identify affected users, location, service impact, and outage scope                                | Network support immediately                                                   |
| Account compromise concern       | Capture indicators, advise the user to stop activity, and avoid unnecessary changes without review | Security / administrator review immediately                                   |

---

## Operational State Strategies

### Priority vs. Escalation

Priority defines urgency. Escalation defines ownership.

Separating urgency from ownership prevents higher-tier queues from being flooded with high-priority but low-complexity tasks.

* A single-user password reset may be Highest priority to that specific user, but it can still remain Tier 1.5 work.
* A software deployment request may be Low priority, but it may still require escalation to an administrator or endpoint management team because of installation permissions.
* A department-wide network outage should be escalated quickly because the scope and business impact are broader.
* A suspected security issue should be escalated even before the full impact is known.

### Waiting for Customer Protocol

The Waiting for Customer status is a key SLA protection mechanism. It is used when Tier 1.5 cannot proceed without external action, such as manager approval, user confirmation, a reboot, missing device information, or diagnostic screenshots.

Moving the ticket to this status pauses the SLA timer when configured, ensuring the support team is not measured unfairly while waiting on stakeholder input.

---

## Technical Handoff Protocol

To prevent higher-tier support from starting from zero, escalated tickets require clear discovery documentation.

Required handoff details:

1. Impact Scope: Who or what is affected?
2. Business Urgency: Why does this matter right now?
3. Discovery Completed: What steps did Tier 1.5 already take?
4. Escalation Rationale: Why does this require another technical owner?

> Example handoff note:
>
> User reports VPN connection failure while working remotely. Confirmed local internet access is stable and the user can access public websites. VPN client opens but fails during the connection attempt. Issue is currently isolated to one remote user and is blocking access to internal file shares. Ticket is marked High priority due to business impact. Escalating to network/admin support to review VPN authentication, access policy, and backend connectivity.

---

## Workflow Simulation & Validation

To validate this logic, the following simulated workloads were processed through the JSM environment to confirm routing logic and escalation handling:

| Ticket Payload            | Applied Routing Logic                                                                              |
| :------------------------ | :------------------------------------------------------------------------------------------------- |
| Department network outage | Rapid scope confirmation -> immediate escalation to network support                                |
| VPN connection failure    | Tier 1.5 client-side triage -> escalation for backend VPN or authentication review if unresolved   |
| New user access request   | Intake validation and approval confirmation -> routed to SysAdmin / IAM support for provisioning   |
| Hardware / printer issue  | Local troubleshooting -> escalation if driver, print server, or network printer issue is suspected |
| Software install request  | Approval verification -> routed to endpoint/admin support if permissions or licensing are required |

---

## Skills Demonstrated

This escalation workflow demonstrates:

* Understanding ticket lifecycle states
* Separating urgency from technical ownership
* Identifying when Tier 1.5 support should escalate
* Routing tickets based on impact, access requirements, and technical ownership
* Documenting escalation notes clearly
* Connecting escalation decisions to SLA visibility
* Recognizing handoff paths for systems administration, network support, IAM, endpoint management, and security review

