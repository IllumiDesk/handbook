# IAM.1.04 - Logical Access Review



### Control Statement

IllumiDesk performs account and access reviews quarterly; corrective action is taken where applicable.

###  Context

Access review is often viewed as a pain, but it's among the easiest ways to secure an environment. Many other security controls depend on the assumption that only authorized individuals have access to production systems. This control is meant to capture any deficiencies in our access provisioning and de-provisioning processes.

###  Scope

This control applies to all systems within our production environment. The production environment includes all endpoints and cloud assets used in hosting IllumiDesk.com and its subdomains. This may include third-party systems that support the business of IllumiDesk.com.

###  Ownership

* Control Owner: Security
* Process owner\(s\):
  * System Owners
  * Business Operations
  * Security Operations
  * Security Compliance

###  Guidance

Quarterly access reviews should be established, and where possible, use automation to preserve the validity of the user access list. The bulk of these reviews can be automated and only the outliers will need to be manually reviewed. The process owner should use role-based authentication whenever possible to make this control easier.

###  Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Logical Access Review control issue.

Examples of evidence an auditor might request to satisfy this control:

* Quarterly Access Reviews

###  Policy Reference

* Access Review Policy and Procedures
* Timing of Quarterly Access Reviews
* User Access Listing Generation Procedures and Guidelines Runbook

###  Framework Mapping

* SOC2 CC
  * CC6.2
  * CC6.3
  * CC6.7

