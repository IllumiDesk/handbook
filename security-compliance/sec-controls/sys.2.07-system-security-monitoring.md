# SYS.2.07 - System Security Monitoring



### Control Statement

Critical systems are monitored in accordance to predefined security criteria and alerts are sent to authorized personnel. Confirmed incidents are tracked to resolution.

###  Context

Having standards for security configurations and performance is useless without the ability to detect deviations from those standards. This control requires all critical systems to be monitored to ensure those systems are configured and performing the way we intend. If this monitoring identifies a security incident, this control also requires us to manage that incident fully until it is marked as resolved. To test this control, review relevant issues in the Security Operations issue tracker. This testing is sufficient because it shows security incidents are being reported on, acknowledged, handled, and closed appropriately by authorized team members.

###  Scope

This control applies to all systems within our production environment. The production environment includes all endpoints and cloud assets used in hosting IllumiDesk.com and its subdomains. This may include third-party systems that support the business of IllumiDesk.com.

###  Ownership

* Control Owner: `Security Operations`
* Process owner\(s\):
  * Security Operations
  * Infrastructure

###  Guidance

It is up to us as a company to define what criteria we use for this monitoring and how an incident is defined. This control simply holds IllumiDesk accountable for fully monitoring systems and managing resulting incidents.

###  Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the System Security Monitoring control issue.

Examples of evidence an auditor might request to satisfy this control:

* Documentation describing the monitoring of IllumiDesk.com.
* Evidence, such as configuration files or playbooks, showing the monitoring is for predefined security criteria.
* Evidence that when alerts are trigged based on predefined security criteria, the alerts are sent to the Security team.
* Samples of issues tracking alerted security incidents through completion.

###  Framework Mapping

* ISO
  * A.12.4.3
* SOC2 CC
  * CC3.2
  * CC3.3
  * CC3.4
  * CC4.2
  * CC5.1
  * CC5.2
  * CC6.1
  * CC7.2
  * CC7.3
* PCI
  * 10.2
  * 10.2.4
  * 10.5.5
  * 10.6
  * 10.6.1
  * 10.6.2
  * 10.6.3
  * 10.8.1
  * 12.10.5

