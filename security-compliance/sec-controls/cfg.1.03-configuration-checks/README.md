# CFG.1.03 - Configuration Checks



### Control Statement

IllumiDesk uses mechanisms to detect deviations from baseline configurations in production environments.

###  Context

This control ensures that we are monitoring for and alerting on configuration deviations to ensure that configuration standards are being applied to all IllumiDesk production systems.

###  Scope

This control applies to all systems within our production environment. The production environment includes all endpoints and cloud assets used in hosting IllumiDesk.com and its subdomains. This may include third-party systems that support the business of IllumiDesk.com.

###  Ownership

* Control Owner: `Infrastructure Team`
* Process owner: `Infrastructure Team`

###  Guidance

The ideal state is for both production configuration management and application deployments to be automated and for any deviations from desired configurations to be either self-corrected or identified and manually corrected as efficiently as possible. Currently, we use a combination of Chef, Terraform, and IllumiDesk \(on the Ops instance\) to deploy and configure the production IllumiDesk environment. With that automation we're able to assure proper configuration and quickly identify and resolve any deviations.

###  Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the control issue.

Examples of evidence an auditor might request to satisfy this control:

* Examples of Chef alerts initiated when Chef fails to run over a period of time
* Examples of issues where deviations from outside of Terraform are reported by team members as they are discovered
* Examples of issues where application deployments fail or are found to deviate from baseline configurations

####  Policy Reference

* Production Change Requests Handbook entry

###  Framework Mapping

* SOC2 CC
  * CC6.1
  * CC7.1
  * CC7.2

