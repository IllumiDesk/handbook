# CFG.1.01 - Baseline Configuration Standard



### Control Statement

IllumiDesk ensures security hardening and baseline configuration standards have been established according to industry standards and are reviewed and updated quarterly.

###  Context

Baseline hardening standards make it clear how systems should be hardened and configured. To ensure we these standards are always relevant, we need to regularly review these documents and update them as needed. The goal of this control is to remove as much subjectivity as possible from the process of configuring systems. If we create a standard for each system type within IllumiDesk, it will be easier to automate system configuration and ensure that all systems are configured the same. This consistent configuration becomes critical when critical vulnerabilities are discovered and need to be rapidly deployed to all applicable systems. This control should be tested to ensure IllumiDesk has established a standardized policy, procedure and guidelines documentation in the handbook, that follows through with the industry standards for Baseline system configurations. It should also be tested to see if these standards documentation were reviewed and updated quarterly.

###  Scope

This control applies to all systems within our production environment and team member laptops. The production environment includes all endpoints and cloud assets used in hosting IllumiDesk.com and its subdomains. This may include third-party systems that support the business of IllumiDesk.com.

###  Ownership

* Control Owner: `Security`
* Process owner\(s\):
  * Infrastructure
  * IT Ops
  * Security

###  Guidance

* The related pages in the handbook listed below in the Policy reference section, can be more comprehensive, covering all details including all OS hardening guidelines, For ex:Linux hardening guide, etc
* We don't have to reinvent the wheel with these. Whenever possible we should be referencing industry standards for system configurations \(e.g., NIST guidelines\).

###  Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Baseline Configuration Standard control issue.

Examples of evidence an auditor might request to satisfy this control:

* Configuration standards, guides, Chef cookbooks, and Terraform configs.
* Documentations showing the configuration standards are consistently applied.

####  Policy Reference

* Laptop or Desktop System configuration
* Configuring New Laptops
* Security Best Practices

###  Framework Mapping

* SOC2 CC
  * CC7.1
  * CC7.2

