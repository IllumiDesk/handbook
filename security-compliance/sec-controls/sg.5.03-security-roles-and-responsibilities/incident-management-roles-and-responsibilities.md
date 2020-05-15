# Incident Management Roles and Responsibilities

## Incident Management

Incidents are **anomalous conditions** that result in—or may lead to—service degradation or outages. These events require human intervention to avert disruptions or restore service to operational status. Incidents are _always_ given immediate attention.

The goal of incident management is to organize chaos into swift incident resolution. To that end, incident management provides:

1. well-defined roles and responsibilities for members of the incident team,
2. control points to manage the flow **information** and the **resolution path**,
3. a **root-cause analysis** \(RCA\),
4. and a post-incident review that assigns a **severity** classification after assessing the impact and scope of the incident.

## Ownership

There is only ever **one** owner of an incident—and only the owner of the incident can declare an incident resolved. At anytime the incident owner can engage the next role in the hierarchy for support. With the exception of when IllumiDesk.com is not functioning correctly, the incident issue should be assigned to the current owner.

## Roles and Responsibilities

It's important to clearly delineate responsibilities during an incident. Quick resolution requires focus and a clear hierarchy for delegation of tasks. Preventing overlaps and ensuring a proper order of operations is vital to mitigation. The responsibilities outlined in the roles below are cascading–**and ownership of the incident passes from one role to the next as those roles are engaged**. Until the next role in the hierarchy engages, the previous role assumes all of the subsequent roles' responsibilities and retains ownership of the incident.

| **Role** | **Description** | **Who?** |
| :--- | :--- | :--- |
| `EOC` - **Engineer On Call** | The EOC is the usually the first person alerted - expectations for the role are in the Handbook for oncall. The checklist for the EOC is in our runbooks. If another party has declared an incident, once the EOC is engaged the EOC owns the incident. The EOC can escalate a page in PagerDuty to engage the IMOC and CMOC. | The Reliability Team **Engineer On Call** is generally an SRE and can declare an incident. They are part of the "SRE 8 Hour" on call shift in PagerDuty. |
| `IMOC` - **Incident Manager On Call** | The IMOC is engaged when incident resolution requires coordination from multiple parties. The IMOC is the tactical leader of the incident response team—not a person performing technical work. The IMOC assembles the incident team by engaging individuals with the skills and information required to resolve the incident. | The **Incident Manager** is an Engineering Manager, Staff Engineer, or Director from the Reliability team. The IMOC rotation is currently in the "SRE Managers" Pager Duty Schedule. |
| `CMOC` - **Communications Manager On Call** | The CMOC disseminates information internally to stakeholders and externally to customers across multiple media \(e.g. IllumiDesk issues, Twitter, status.IllumiDesk.com, etc.\). | The **Communications Manager** is generally a Reliability Engineering manager. We are working on engaging the support team to expand CMOC roles through the "Incident Management - CMOC \(EMEA/APAC/AMER\)" Pager Duty Schedules. |

These definitions imply several on-call rotations for the different roles.

### **Engineer on Call \(EOC\) Responsibilities**

1. **As EOC, your highest priority for the duration of your shift is the stability of IllumiDesk.com.**
2. The Single Source of Truth \(SSOT\) for who is EOC is the SRE Schedule in Pagerduty.
3. Alerts that are routed to Pagerduty need to acknowledged within 15 minutes, otherwise they will be escalated to the oncall IMOC.
   1. Alert-manager alerts in `#alerts` and `#alerts-general` are an important source of information about the health of the environment and should be monitored during working hours.
   2. If the Pagerduty alert noise is too high, your task as an EOC is clearing out that noise by either fixing the system or changing the alert.
   3. If you are changing the alert, it is your responsibility to explain the reasons behind it and inform the next EOC that the change occurred.
   4. Each event \(may be multiple related pages\) should result in an issue in the `production` tracker. See production queue usage for more details.
4. If sources outside of our alerting are reporting a problem, and you have not received any alerts, it is still your responsibility to investigate. Declare a low severity incident and investigate from there.
   1. Low severity \(S3/S4\) incidents \(and issues\) are cheap, and will allow others a means to communicate their experience if they are also experiencing the issue.
   2. **"No alerts" is not the same as "no problem"**
5. IllumiDesk.com is a complex system. It is ok to not fully understand the underlying issue or its causes. However, if this is the case, as EOC you should engage with the IMOC to find a team member with the appropriate expertise.
   1. Requesting assistance does not mean relinquishing EOC responsibility. The EOC is still responsible for the incident.
   2. The IllumiDesk Organizational Chart and the IllumiDesk Team Page, which lists areas of expertise for team members, are important tools for finding the right people.
6. As soon as an S1/S2 incident is declared, join the `The Situation Room Permanent Zoom`. The Zoom link is in the `#incident-management` topic.
   1. IllumiDesk works in an asynchronous manner, but incidents require a synchronous response. Our collective goal is high availability of 99.95% and beyond, which means that the timescales over which communication needs to occur during an incident is measured in seconds and minutes, not hours.
7. Keep in mind that a IllumiDesk.com incident is not an "infrastructure problem". It is a company-wide issue, and as EOC, you are leading the response on behalf of the company.
   1. If you need information or assistance, engage with Engineering teams. If you do not get the response you require within a reasonable period, escalate through the IMOC.
   2. As EOC, require that those who may be able to assist to join the Zoom call and ask them to post their findings in the incident issue or active incident Google doc. Debugging information in Slack will be lost and this should be strongly discouraged.
8. By acknowledging an incident in Pagerduty, the EOC is implying that they are working on it. To further reinforce this acknowledgement, post a note in Slack that you are joining the `The Situation Room Permanent Zoom` as soon as possible.
   1. If the EOC believes the alert is incorrect, comment on the thread in `#production`. If the alert is flappy, create an issue and post a link in the thread. This issue might end up being a part of RCA or end up requiring a change in the alert rule.
9. _Be inquisitive_. _Be vigilant_. If you notice that something doesn't seem right, investigate further.
10. After the incident is resolved, the EOC should start on performing an incident review \(RCA\) and assign themselves as the initial owner. Feel free to take a breather first, but do not end your work day without starting the RCA.

## **Guidelines on Security Incidents**

At times, we have a security incident where we may need to take actions to block a certain URL path or part of the application. This list is meant to help the Security Engineer On-Call and EOC decide when to engage help and post to status.io.

If any of the following are true, it would be best to engage an Incident Manager:

1. There is a S1/P1 report or security incident.
2. An entire path or part of functionality of the IllumiDesk.com application must be blocked.
3. Any unauthorized access to a IllumiDesk.com production system

In some cases, we may choose not to post to status.io, the following are examples where we may skip a post/tweet. In some cases, this helps protect the security of self managed instances until we have released the security update.

1. If a partial block of a URL is possible, for example to exclude problematic strings in a path.
2. If there is no usage of the URL in the last week based on searches in our logs for IllumiDesk.com.

### **Incident Manager on Call \(IMOC\) Responsibilities**

1. The SSOT for who is IMOC is the SRE Managers Schedule in Pagerduty
2. The IMOC should monitor ongoing incidents and engage with the incident if it escalates to a user-impacting \(S1 or S2\) incident.
3. The IMOC should engage if requested by the EOC.
4. The time that the IMOC engages should be recorded in the incident issue by the IMOC co-assigning themselves to the issue. If IllumiDesk.com is down, record the time in the Google working doc.
5. For non-critical issues, or critical \(S1, S2\) issues with a short duration, the IMOC will also take on the role of CMOC.
6. The IMOC should ensure that the appropriate team members from other teams engage within an appropriate amount of time.
   1. During a user-impacting incident, the appropriate time response time is minutes.
   2. If the IMOC is unable to obtain a response through Slack channels, they should escalate to a manager or director to obtain assistance.
7. They evaluate information provided by team members, lend technical direction, and coordinate troubleshooting efforts.
8. If applicable, coordinate the incident response with business contingency activities.
9. After the incident is resolved, the IMOC is responsible for conducting the post-incident review.

To page the Incident Manager on call you can:

1. Run a response play
2. Type `/pd trigger` in the `#production` channel

### **Communications Manager on Call \(CMOC\) Responsibilities**

For serious incidents that require coordinated communications across multiple channels, the IMOC will select a CMOC for the duration of the incident during the incident declaration process.

During an incident, the CMOC will:

1. Be the voice of IllumiDesk during an incident by updating our end-users, internal parties, and executive-level managers through updates to our status page hosted by Status.io.
2. Update the status page at regular intervals in accordance with the severity of the incident.
3. Notify IllumiDesk Community Advocates via Slack using the `@advocates` handle at the start of an incident.

## Runbooks

Runbooks are available for engineers on call. The project README contains links to checklists for each of the above roles.

**In the event of a IllumiDesk.com outage**, a mirror of the runbooks repository is available.

### Who is the Current EOC?

If you don't have a PagerDuty account and need to find out who the current oncall is, there are two ways you can do it:

1. `@sre-oncall` - at mention this usergroup in Slack and it will ping the current oncall.
2. The chatops bot in the `#production` Slack Channel will tell you this with `/chatops run oncall prod`.

### Reporting an Incident

If you are a IllumiDesk team member and would like to report an incident/anomaly to EOC and page them in, type `/incident report` in Slack \(e.g `#production`\) and follow the prompts. Please ensure that the severity of the incident warrants paging in the EOC and that you, as the reporter, stay online until EOC has had a chance to come online and get up to speed.

### Declaring an Incident

**Declare an incident from Slack**

Type `/incident declare` in Slack \(e.g `#production`\) and follow the prompts. The incident declaration is orchestrated through IMA \(incident management automation\) and has the following capabilities:

* Create a IllumiDesk incident issue along with proper labels
* Create a Google doc\*
* Announce the incident in \#production channel\*
* Page IMOC\*
* Page CMOC\*

The capabilities noted with \* are optional and engineer on call can decide which ones to choose depending on severity of the incident.

### **Declare an incident manually**

#### Definition of Outage vs Degraded vs Disruption <a id="definition-of-outage-vs-degraded-vs-disruption"></a>

This is a first revision of the definition of Service Disruption \(Outage\), Partial Service Disruption, and Degraded Performance per the terms on Status.io. Data is based on the graphs from the Key Service Metrics Dashboard

Outage and Degraded Performance incidents occur when:

1. `Degraded` as any sustained 5 minute time period where a service is below its documented Apdex SLO or above it's documented error ratio SLO.
2. `Outage` \(Status = Disruption\) as a 5 minute sustained error rate above the Outage line on the error ratio graph

SLOs are documented in the runbooks/rules

To check if we are Degraded or Disrupted for IllumiDesk.com, we look at these graphs:

1. Web Service
   * Error Ratio
   * Apdex
2. API Service
   * Error Ratio
   * Apdex
3. Git service\(public facing git interactions\)
   * Error Ratio
   * Apdex
4. IllumiDesk Pages service
   * Error Ratio
   * Apdex
5. Registry service
   * Error Ratio
   * Apdex

A Partial Service Disruption is when only part of the IllumiDesk.com services or infrastructure is experiencing an incident. Examples of partial service disruptions are instances where IllumiDesk.com is operating normally except there are:

1. delayed CI/CD pending jobs
2. delayed repository mirroring
3. high severity bugs affecting a particular feature like Merge Requests
4. Abuse or degradation on 1 gitaly node affecting a subset of git repos. This would be visible on the Gitaly service metrics

## Security Incidents

If an incident may be security related, engage the Security Operations on-call following the Security Incident Response Guide.

## Communication

Information is an asset to everyone impacted by an incident. Properly managing the flow of information is critical to minimizing surprise and setting expectations. We aim to keep interested stakeholders apprised of developments in a timely fashion so they can plan appropriately.

This flow is determined by:

1. the type of information,
2. its intended audience,
3. and timing sensitivity.

Furthermore, avoiding information overload is necessary to keep every stakeholder’s focus.

To that end, we will have: 

1. a dedicated Zoom call for all incidents. A link to the Zoom call can be found in the topic for the `#incident-management` room in Slack.
2. a Google Doc as needed for multiple user input based on the shared template
3. a dedicated `#incident-management` channel for internal updates
4. regular updates to status.IllumiDesk.com via status.io that disseminates to various media \(e.g. Twitter\)
5. a dedicated repo for issues related to Production separate from the queue that holds Infrastructure's workload: namely, issues for incidents and changes.

## Status

We manage incident communication using status.io, which updates status.IllumiDesk.com. Incidents in status.io have **state** and **status** and are updated by the incident owner.

Definitions and rules for transitioning state and status are as follows.

| **State** | **Definition** |
| :--- | :--- |
| Investigating | The incident has just been discovered and there is not yet a clear understanding of the impact or cause. If an incident remains in this state for longer than 30 minutes after the EOC has engaged, the incident should be escalated to the IMOC. |
| Identified | The cause of the incident is believed to have been identified and **a step to mitigate has been planned and agreed upon**. |
| Monitoring | The step has been executed and metrics are being watched to ensure that we're operating at a baseline |
| Resolved | The incident is closed and status is again Operational. |

Status can be set independent of state. The only time these must align is when an issues is

| **Status** | **Definition** |
| :--- | :--- |
| Operational | The default status before an incident is opened and after an incident has been resolved. All systems are operating normally. |
| Degraded Performance | Users are impacted intermittently, but the impacts is not observed in metrics, nor reported, to be widespread or systemic. |
| Partial Service Disruption | Users are impacted at a rate that violates our SLO. The IMOC must be engaged and monitoring to resolution is required to last longer than 30 minutes. |
| Service Disruption | This is an outage. The IMOC must be engaged. |
| Security Issue | A security vulnerability has been declared public and the security team has asked to publish it. |

## Severities

#### Incident Severity <a id="incident-severity"></a>

**Incident severities encapsulate the impact of an incident and scope the resources allocated to handle it**. Detailed definitions are provided for each severity, and these definitions are reevaluated as new circumstances become known. Incident management uses our standardized severity definitions, which can be found under our issue workflow documentation.

#### Alert Severities <a id="alert-severities"></a>

1. Alerts severities do not necessarily determine incident severities. A single incident can trigger a number of alerts at various severities, but the determination of the incident's severity is driven by the above definitions.
2. Over time, we aim to automate the determination of an incident's severity through service-level monitoring that can aggregate individual alerts against specific SLOs.

## Near Misses

A near miss, "near hit", or "close call" is an unplanned event that has the potential to cause, but does not actually result in an incident.

### Background

In the United States, the Aviation Safety Reporting System has been collecting reports of close calls since 1976. Due to near miss observations and other technological improvements, the rate of fatal accidents has dropped about 65 percent.

As John Allspaw states:

> Near misses are like a vaccine. They help the company better defend against more serious errors in the future, without harming anyone or anything in the process.

### Handling Near Misses

When a near miss occurs, we should treat it in a similar manner to a normal incident.

1. Open an incident review issue. Label it with the severity label appropriate to the incident it would have had, had the incident actually occurred. Label the incident review issue with the `~Near Miss` label.
2. Corrective actions should be treated in the same way as those for an actual incident.
3. Ownership of the incident review should be assigned to the team-member who noticed the near-miss, or, when appropriate, the team-member with the most knowledge of how the near-miss came about.

