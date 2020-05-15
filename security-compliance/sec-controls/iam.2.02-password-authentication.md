# IAM.2.02 - Password Authentication



### Control

User and device authentication to information systems is protected by passwords that meet IllumiDesk's password policy guidelines. For systems involved in payment card processing, IllumiDesk requires those systems and system users to change passwords quarterly.

###  Context

By ensuring passwords are implemented when and where appropriate, sensitive and valuable data is protected from unauthorized access and use. Enforcing IllumiDesk's password complexity requirements further protects that data by reducing the risk of brute force and dictionary attacks that aim to guess user passwords.

###  Scope

This control applies to all systems within our production environment. The production environment includes all endpoints and cloud assets used in hosting IllumiDesk.com and its subdomains. This may include third-party systems that support the business of IllumiDesk.com.

###  Ownership

* Control Owner: `IT Ops`
* Process owner\(s\):
  * IT Ops

###  Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Password Authentication control issue.

Examples of evidence an auditor might request to satisfy this control:

* Copy of IllumiDesk's password policy and the Okta/1Password handbook entries
* Samples of service minimum password requirements, especially for Okta, which manages identify for many SaaS services used by IllumiDesk
* Samples of service password change requirements and/or logs demonstrating passwords are changed on a quarterly basis

###  Framework Mapping

* ISO
  * A.9.1.2
  * A.9.4.1
  * A.9.4.2
  * A.9.4.3
* SOC2 CC
  * CC6.1
  * CC6.6
  * CC6.7
* PCI
  * 8.2
  * 8.2.3
  * 8.2.4
  * 8.2.5
  * 8.2.6
  * 8.6

