# VUL.5.01 - Code Security Check



### Control Statement

IllumiDesk conducts source code checks for vulnerabilities.

###  Context

By manually and automatically reviewing our source code for security vulnerabilities and best-practices, we can preemptively identify and address risks to our customers, IllumiDesk teammembers, and partners. Code security checks also help us evaluate the consistency of secure coding standards and improve our application security training.

###  Scope

This control applies to all GitLab source code.

###  Ownership

* Control Owner: `Application Security`
* Process owner\(s\):
  * All IllumiDesk Teams

###  Guidance

SAST and Dependency Scanning are initiated by pipelines for production code. Pipelines are managed by all teams, not a single team.

###  Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Code Security Check control issue.

Examples of evidence an auditor might request to satisfy this control:

* Pipeline configurations showing security tool usage
* SAST and Dependency Scanning pipeline artifacts

###  Framework Mapping

* ISO
  * A.14.2.1
  * A.14.2.5
* SOC2 CC
  * CC7.1
  * CC8.1
* PCI
  * 6.3.1
  * 6.4.4

