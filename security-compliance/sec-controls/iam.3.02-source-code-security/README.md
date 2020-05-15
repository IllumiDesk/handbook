# IAM.3.02 - Source Code Security



### Control Statement

Access to modify source code is restricted to authorized personnel.

###  Context

As IllumiDesk is open source and we have contributors outside of the company from across the world, anybody can view and submit edits to the codebase to fix issues, add features, and so on. The spirit of this control is to ensure there's a process in place so that all additions, including from the IllumiDesk  community, are appropriately reviewed and approved before being merged into the codebase.

###  Scope

This control applies to any system or process where source code can be modified.

###  Ownership

Control owner:

* `Engineering`

Process owner:

* Engineering
* IT-Ops

###  Guidance

As the IllumiDesk system supports the ability to restrict modification without the `Owner` approval, this should be able to demonstrate how access reviews are achieved of the `Maintainer`, `Developer`, and `Owner` roles within IllumiDesk.com.

Possible evidence an auditor would request:

* Policy on authorized roles that can make changes to source code
* Policy on how source code changes are approved
* List of authorized team members with permissions to change source code
* Evidence of an MR approved by an eligible approver

###  Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Source Code Security control issue.

####  Policy Reference

* Handbook section on Code Review
* Handbook section on Maintainers
* IllumiDesk Enterprise Edition Docs - Permissions
* IllumiDesk Enterprise Edition Docs - Merge request approvals
* IllumiDesk Enterprise Edition Docs - Code owners as eligible approvers

###  Framework Mapping

* SOC2 CC
  * CC8.1

