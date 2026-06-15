# Service Level Agreement (SLA) Configuration

## Overview

This document outlines the Service Level Agreement (SLA) configuration used in this Jira Service Management ITSM environment.

The objective of this configuration is to track operational response and resolution expectations across different ticket priorities. This lab focuses on two core SLA metrics: Time to First Response (TTFR) and Time to Resolution (TTR). Both SLAs are governed by priority-based targets and an operational business-hours calendar.

---

## Operational Calendar Configuration

The underlying SLA calendar was configured to reflect standard enterprise support hours.

| Calendar Setting | Value              |
| :--------------- | :----------------- |
| Workdays         | Monday to Friday   |
| Support Hours    | 9:00 AM to 5:00 PM |
| Time Zone        | Toronto            |

This configuration ensures SLA timers only run during defined working hours. This prevents timers from breaching overnight or over weekends when the desk is outside normal support coverage, giving a more accurate view of service desk performance during operational hours.

![Business-hours calendar](../screenshots/sla-business-hours-calendar.png)

---

## Metric 1: Time to First Response (TTFR)

The TTFR SLA tracks the maximum allowable time before a support agent provides an initial customer-facing response. This metric helps ensure that incoming requests are acknowledged, reviewed, and triaged within the expected timeframe.

### SLA Logic

| Condition Type | Configuration Trigger                             |
| :------------- | :------------------------------------------------ |
| Start Counting | Issue/request created                             |
| Pause Counting | Ticket status transitions to Waiting for Customer |
| Stop Counting  | Customer-visible/public response is logged        |

### Priority Targets

| Priority | First Response Target |
| :------- | :-------------------- |
| Highest  | 30 minutes            |
| High     | 1 hour                |
| Medium   | 4 hours               |
| Low      | 8 hours               |
| Lowest   | 16 hours              |

Higher-priority incidents, such as department-wide outages or urgent access issues, require faster acknowledgment because they carry greater business impact. The Waiting for Customer pause condition prevents the SLA timer from continuing while the support team is waiting for user input, confirmation, screenshots, or additional troubleshooting details.

![Time to first response SLA configuration](../screenshots/sla-time-to-first-response.png)

---

## Metric 2: Time to Resolution (TTR)

The TTR SLA tracks the expected time to resolve an active ticket based on the ticket's priority level.

### SLA Logic

| Condition Type | Configuration Trigger                             |
| :------------- | :------------------------------------------------ |
| Start Counting | Issue/request created                             |
| Pause Counting | Ticket status transitions to Waiting for Customer |
| Stop Counting  | Resolution state is set                           |

### Priority Targets

| Priority | Resolution Target |
| :------- | :---------------- |
| Highest  | 4 hours           |
| High     | 8 hours           |
| Medium   | 16 hours          |
| Low      | 40 hours          |
| Lowest   | 40 hours          |

Resolution targets scale with business impact. A high-impact infrastructure issue should have a shorter resolution target than a routine software request or lower-impact service request.

![Time to resolution SLA configuration](../screenshots/sla-time-to-resolution.png)

---

## SLA Execution and Validation

After configuration, the SLA timers were validated against active sample tickets. The timers appeared on the agent-side ticket view and reflected the configured priority targets and business-hours calendar.

Validation examples:

* High-impact incident validation: Department-wide network outage
  ![Network outage SLA view](../screenshots/ticket-network-outage-sla-redacted.png)

* Asset incident validation: Hardware / printer issue
  ![Hardware printer SLA view](../screenshots/ticket-hardware-printer-sla-redacted.png)

---

## Operational Governance and Impact

In a service desk environment, SLA tracking helps support teams manage urgency, accountability, and escalation decisions.

This SLA configuration supports several operational outcomes:

* SLA visibility: Helps agents identify tickets that require timely response or resolution.
* Metric protection: Pause conditions prevent the IT team from being measured unfairly while waiting on customer input or approval.
* Escalation awareness: Helps identify tickets that may need higher-tier attention before targets are missed.
* Performance reporting: Supports review of first response and resolution performance against defined business expectations.

---

## Skills Demonstrated

This SLA configuration demonstrates:

* Configuring SLA metrics in Jira Service Management
* Building a business-hours calendar
* Setting priority-based first response targets
* Setting priority-based resolution targets
* Defining SLA start, pause, and stop conditions
* Understanding the difference between response time and resolution time
* Validating SLA timers against active sample tickets
* Connecting SLA behavior to ticket priority and support workflow
