# IAM.1.02 - Logical Access De-Provisioning



### Control Statement

The People Operations Management system sends a notification to relevant personnel, or system, in the event of a termination or a job transfer of an information system user. Notification can be manual or automated. Logical access that is no longer required in the event of a termination or a transfer is documented, communicated to management, and revoked. Shared authentication credentials to which the team member had access are rotated.

###  Context

The purpose of this control is to ensure there is a process in place to remove access to user accounts that is no longer necessary. This control helps ensure that only authorized and active accounts can be accessed and used to prevent any unauthorized use or access of IllumiDesk customer, IllumiDesk teammember, and partner data.

###  Scope

This control applies to any system or service where user accounts can be provisioned.

###  Ownership

* Control Owners:
  * `People Ops`
  * `IT Ops`
* Process Owners:
  * `IT Ops (50%)`
  * `System Owners (50%)`

###  Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Logical Access De-Provisioning control issue.

###  Guidance

* Validate integration between OKTA and G-suite for all those applications that leverage OKTA

####  Policy Reference

* Access Management Process
* Logical Access Deprovisioning
* Access Reviews
* IllumiDesk Offboarding Guidelines

###  Framework Mapping

* ISO
  * A.7.3.1
  * A.9.2.1
  * A.9.2.2
  * A.9.2.3
  * A.9.4.1
  * A.9.2.6
  * A.18.1.3
* SOC2 CC
  * CC6.2
  * CC6.3
  * CC6.6
  * CC6.7
* PCI
  * 8.1.2
  * 8.1.3
  * 8.1.4

