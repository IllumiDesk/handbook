# IAM.4.01 - Remote Connections



### Control Statement

Remote connections to production systems are controlled with a combination of SSH and multi-factor authentication.

###  Context

Where and only if applicable, appropriate, and technically feasible, and with the understanding IllumiDesk is a cloud-native, fully-remote and international organization favoring a Zero Trust network without a traditional corporate network infrastructure, access will be managed with a combination of ssh and Multi-factor Authentication \(MFA\) technologies.

###  Scope

This control applies to all systems within our production environment. The production environment includes all endpoints and cloud assets used in hosting IllumiDesk.com and its subdomains. This may include third-party systems that support the business of IllumiDesk.com.

###  Ownership

Control owner:

* `Security Management`

Process owner:

* Security Operations
* IT-Ops

###  Guidance

Identity access management systems should enforce SSH and MFA for connections to production systems and networks.

Evidence an auditor may request:

* Policy requiring SSH/MFA for roles that will access production
* Chef logs to aduit team member connectivity methods

###  Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Remote Connections control issue.

###  Framework Mapping

* ISO
  * A.11.2.6
* SOC2 CC
  * CC6.6
  * CC6.7
* PCI
  * 8.1.1
  * 8.6

