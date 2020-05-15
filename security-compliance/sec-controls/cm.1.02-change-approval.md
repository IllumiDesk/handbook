# CM.1.02 - Change Approval



### Control Statement

Prior to introducing changes into the production environment, approval from authorized personnel is required based on the following:

* Change description
* Impact of change
* Test results

###  Context

This control aims to ensure important information about the change, its impacts, and ability to revert the change are documented and a part of the approval process. This allows everyone involved to have the information they need to make informed decisions about and execute on a change effectively. It also sets out to ensure all changes which could impact IllumiDesk customers, IllumiDesk team-members, and partners are approved by the appropriate person\(s\). This control can be tested by reviewing the criticality 1 and 2 change issues in the `production` issue tracker. This testing is sufficient because the issue template contains a row naming the change reviewer\(s\) and a review of the issue activity can show whether the change reviewer\(s\) did approve of the change.

###  Scope

This control applies to all systems within our production environment. The production environment includes all endpoints and cloud assets used in hosting IllumiDesk.com and its subdomains. This may include third-party systems that support the business of IllumiDesk.com.

###  Ownership

Control Owner: `Infrastructure`

* Process owner\(s\):
  * Infrastructure

###  Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Change Approval control issue.

Examples of evidence an auditor might request to satisfy this control:

* A copy of the Change Approval process for software and infrastructure, along with specific templates and workflows
* Sample infrastructure Change Plans and related reviews/discussions
* Sample Merge Request reviews and approvals

###  Framework Mapping

* SOC2 CC
  * CC8.1

