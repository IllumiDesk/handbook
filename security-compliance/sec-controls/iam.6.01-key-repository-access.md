# IAM.6.01 - Key Repository Access



### Control Statement

Access to the cryptographic keystores is limited to authorized personnel.

###  Context

One of the fundamental and most important security considerations of encryption is protecting cryptographic keys, particularly private keys. This controls aims to protect the confidentiality and integrity of data for customers, IllumiDesk team-members, and partners by limiting the number of people with access to view, modify, and create new cryptographic keys. A malicious actor with access to IllumiDesk's cryptographic keys could decrypt all sensitive data stored and transmitted by IllumiDesk, rending the encryption useless.

###  Scope

This control applies to all cryptographic keystores for the production environment. The production environment includes all endpoints and cloud assets used in hosting IllumiDesk.com and its subdomains. This may include third-party systems that support the business of IllumiDesk.com.

###  Ownership

Control Owner: `Infrastructure`

* Process owner\(s\):
  * Infrastructure

###  Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Key Repository Access control issue.

Examples of evidence an auditor might request to satisfy this control:

* Sample of access requests for Google Cloud and specifically KMS; Chef Data Bags; any servers which store the Data Bags private key; and any servers which store the TLS private key
* Documentation or some form of record demonstrating access to a keystore or server containing the private key to a keystore is only provisioned to GitLabbers where there is a clear need for access
* A copy of Google Cloud users with access to production KMS, Data Bags, and servers storing private keys to either

###  Framework Mapping

* SOC2 CC
  * CC6.1
  * CC6.3

