# Jira Service Management ITSM Lab

## Project Overview

This project is a hands-on Jira Service Management lab I built to practice customer intake, ticket triage, queues, SLAs, and escalation workflow documentation.

The goal was to create a realistic service desk setup where users can submit requests through a customer portal, and an IT support agent can review, prioritize, organize, and track the work from the agent side.

This lab is focused on the type of workflow used in Help Desk, Service Desk, IT Support Technician, and junior Tier 1 / Tier 1.5 support roles.

All screenshots use demo data and redacted customer information.

---

## Tools Used

* Jira Service Management
* Jira Customer Portal
* Jira Queues
* JQL filters
* SLA configuration
* Business-hours calendar
* Ticket priorities and labels
* Markdown documentation
* GitHub for project documentation

---

## What I Built

I configured a Jira Service Management project with customer-facing request types and agent-side ticket management.

The customer portal includes request groups for:

* Hardware and device issues
* Access and account requests
* Application/software requests
* Network and infrastructure issues

I created structured request forms for common IT support scenarios, including:

* Password reset
* Software install request
* New user access request
* Hardware issue
* Network/Wi-Fi issue
* VPN issue
* Department network outage

On the agent side, I created sample tickets, applied priorities and labels, and built queues to organize incoming work by support category and urgency.

I also configured SLA tracking for first response and resolution targets using a business-hours calendar.

---

## Screenshots

### Customer Portal

The customer portal was organized into clear request groups so users can select the correct support request type.

---

### Structured Intake Forms

The request forms were designed to collect useful information before the ticket reaches the support queue. This helps reduce back-and-forth and gives the support agent better information for triage.

#### New User Access Request Form

#### Network/Wi-Fi Issue Form

---

### Sample Ticket Workload

I submitted multiple sample tickets through the customer portal to test the intake process and agent-side workflow.

---

### Customer-Side Ticket Examples

These screenshots show what submitted requests look like from the customer portal side.

#### Department Network Outage

#### New User Access Request

#### Hardware / Printer Issue

#### VPN Issue

#### Laptop Wi-Fi Issue

#### Password Reset Request

#### Software Install Request

---

### Queues and JQL Filters

I configured queues to organize unresolved tickets by priority, request type, label, and support category.

#### New Requests Queue

#### High Priority Queue

#### Network Issues Queue

#### Access / Onboarding Queue

#### Hardware Issues Queue

#### Software Requests Queue

#### Escalated Queue

---

### Agent-Side Ticket Triage

These screenshots show the agent-side view used to review ticket details, priority, labels, reporter, request type, and support context.

#### Department Network Outage

#### New User Access Request

#### Hardware / Printer Issue

---

### SLA Configuration

I configured a business-hours calendar for SLA tracking.

I configured a T to First Response SLA with targets based on ticket priority.

I also configured a Time to Resolution SLA with priority-based resolution targets.

---

### SLA Applied to Tickets

These screenshots show SLA timers applied to real tickets after the SLA rules were configured.

#### Network Outage SLA View

#### Hardware Printer SLA View

---

## Skills Demonstrated

This project demonstrates practical service desk and IT support skills, including:

* Configuring Jira Service Management request types
* Building a customer-facing support portal
* Creating structured intake forms
* Using priorities, labels, and request types for ticket triage
* Creating queues with JQL filters
* Organizing tickets by urgency and support category
* Configuring SLAs for first response and resolution
* Using a business-hours calendar for SLA tracking
* Reviewing tickets from both customer-side and agent-side views
* Documenting escalation logic for Tier 1, Tier 2, admin, network, and security handoff
* Writing clear technical documentation for a support workflow

---

## Documentation

More detailed documentation is available in the `docs` folder:

* [Project Overview](docs/project-overview.md)
* [JQL Queues](docs/jql-queues.md)
* [SLA Configuration](docs/sla-configuration.md)
* [Escalation Workflow](docs/escalation-workflow.md)

---

## Interview Summary

I built this Jira Service Management lab to practice how a service desk handles incoming IT support requests. I configured a customer portal, created structured request forms, generated sample tickets, organized tickets using queues and JQL filters, configured SLA targets, and documented escalation rules.

This project helped me understand how support teams collect ticket information, prioritize work, track first response and resolution times, and decide when to escalate issues to higher support levels.

