# VUL.4.01 - Enterprise Protection

## Control Statement

Where applicable and technically feasible, IllumiDesk implements mechanisms to protect in-scope endpoints from threats such as malware and malicious actors.

## Context

This control outlines the components of a successfully deployed protection program which helps add another layer of risk mitigation to the IllumiDesk environment. The applicability in this control is left vague since we have to apply some reason to this control. The intent of this control is to monitor and protect IllumiDesk endpoints.

## Scope

This control applies to all systems within our production environment. The production environment includes all endpoints and cloud assets used in hosting IllumiDesk.com and its subdomains. This may include third-party systems that support the business of IllumiDesk.com.

## Ownership

* IllumiDesk.com and live production environments
  * Security Operations - responsible for maintenance and monitoring of Uptycs
  * Infrastructure - responsible for addressing Uptycs findings
* Laptops
  * Security Management- responsible for enforcement of endpoint management
  * IT-Ops - responsible for rolling out endpoint management tool, monitoring tool, reporting on non-compliance devices - trigger an alert

## Guidance

It is fine to have different tools securing different systems, but the more different solutions we use, the more complexity we introduce into the maintenance of this control.

Apple Macbook Pro Laptops

* Provides application sandboxing to protect systems and users by limiting the privileges of an app to its intended functionality, malware will have to escape to do harm
* Requires by default that all applications installed are signed \(this provides `integrity`\)

## Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Enterprise Protection control issue.

### Framework Mapping

* SOC2 CC
  * CC6.8
  * CC7.1

