# DM.4.01 - Encryption of Data in Transit



### Control Statement

Data in transit is encrypted over public networks according to IllumiDesk policy.

###  Context

Encrypting data transmitted over public networks helps ensure the confidentiality and integrity of that data. Without encryption, data in transit over public networks can easily be intercepted using automated, open source tools and viewed and maliciously modified by malicious actors.

###  Scope

This control applies to red, orange, and yellow data in the production environment. The production environment includes all endpoints and cloud assets used in hosting IllumiDesk.com and its subdomains. This may include third-party systems that support the business of IllumiDesk.com

###  Ownership

* Control Owner: `Infrastructure`
* Process owner\(s\): `Infrastructure`

###  Guidance

* TLS 1.2 or higher should be used to encrypt da`ta in transit Deprecate support for TLS 1.0 and TLS 1.1.`
* `Biannual validation of this control may be done by performing a scan with Qualys SSL Labs and/or scanning with tls-scanner.`
* `Such scans are sufficient for testing this control as the results show whether infrastructure transmitting red, organge, and yellow data over public networks uses TLS.`

###  `Additional control information and project tracking`

`Non-public information relating to this security control as well as links to the work` associated with various phases of project work can be found in the Encryption of Data in Transit control issue.

Examples of evidence an auditor might request to satisfy this control:

* Architecture and design documentation showing the use and high-level implementation details of TLS for production
* Random sampling of connections to/from production

####  Policy Reference

* IllumiDesk Production Architecture
* Encryption in Transit in Google Cloud
* Deprecate support for TLS 1.0 and TLS 1.1

###  Framework Mapping

* SOC2 CC
  * CC6.7

