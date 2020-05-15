# IR.1.01 - Incident Response Plan



### Control Statement

Incident Response Guidance is available in the Handbook that outlines IllumiDesk's security incident response process. It also provides information to internal and external users on how to report breaches, security and availability failures, incidents, concerns, identified vulnerabilities and other security complaints to appropriate personnel.

### Context

The purpose of this control is to ensure IllumiDesk creates, implements, and maintains an effective plan to identify, resolve, and prevent security incidents within its application, systems, and services. By having an organized and continually evolving security incident response plan, IllumiDesk can maintain the availability, reliability, performance, and confidentiality offered to IllumiDesk customers, IllumiDesk team-members, and partners. This control can be tested by first proving that IllumiDesk has sufficient documentation in place for an efficient Incident Response plan. This can include documentation pertaining to the handbook pages, Merge requests, and issues opened in reference to and in adherence to the IR plan. It can then be confirmed that any security incident that was reported \(if applicable\) followed the IR plan documentation.

### Scope

This control applies to all systems within our production environment. The production environment includes all endpoints and cloud assets used in hosting IllumiDesk.com and its subdomains. This may include third-party systems that support the business of IllumiDesk.com.

###  Ownership

* Control Owner: `Infrastructure`
* Process owner\(s\):
  * `Security Operations`
  * `Infrastructure`

###  Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Incident Response Plan control issue.

Examples of evidence an auditor might request to satisfy this control:

* Provide copies of the Incident Response pages, which are linked to and described below
* Provide sample reports and other outputs of the various functions listed below, such as Infrastructure and/or Security incident issues

####  Policy Reference

1. Procedures for the identification and management of incidents:

* Incident management documented in the IllumiDesk Handbook
* Incident Management for Self-Managed Customers

1. Procedures for the resolution of confirmed incidents.

* Security issue triage process
* Security severity labelling
* Major Incident Response Workflow
*  Additional documentation on using the `panic` email and a procedure for the security team's response to those alerts

1. Key incident response systems:

* Incident management documented in the IllumiDesk Handbook

1. Incident coordination and communication strategy:
   *  S1 and S2 Incidents. Information about our most critical incident severities.
   *  Incident Steps. Defines the steps involved with handling an incident.
   *  Communication. Describes communication procedures during an incident.
   *  CMOC and IMOC checklist. A checklist of actions for the CMOC and IMOC response roles to perform.
   *  Incident runbooks are available and maintained in the `runbooks` project
   * Database-specific runbooks
   * Additional runbooks
2. Contact method for internal parties to report incidents

* Process for engaging security on-call
* Security operations on-call guide

1. Support team contact information

* Incident Management Support
*  On-Call Runbooks.

1. Notification to relevant management in the event of a security breach

* Security Incident Comms Plan

1. Provisions to contact support team

* Support Team function in the handbook
*  Support page contains information to contact the Support team

1. Production Infrastructure related IR Plan:

* Production infrastructure incidents are documented in the `production` project
* The `#incident-management` Slack channel is used for synchronous incident communication via chat
  * In the channel, the `Production-watch` app monitors the aforementioned `production` project and notifies channel participants of the issue
* The `Situation Room` permanent Zoom channel is used for synchronous communication via audio/video conference
  * A link to the channel is included in the description for the `#incident-management` Slack channel

1. Alert mechanisms:

* Security Incident and Alert Lifecycle in IllumiDesk 

###  Framework Mapping

* SOC2 CC
  * CC4.2
  * CC7.3

