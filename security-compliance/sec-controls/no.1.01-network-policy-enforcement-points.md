# NO.1.01 - Network Policy Enforcement Points



### Control Statement

Network traffic to and from untrusted networks passes through a policy enforcement point; firewall rules are established in accordance to identified security requirements and business justifications.

###  Context

Effective network traffic policies help minimize the risk of network-based attacks, including denial of service attacks and malicious data exfiltration. By requiring ingress and egress rules be mapped to security requirements and business justifications, we can limit the number of unnecessarily open ports to protect customer, GitLab team-member, and partner data.

###  Scope

This control applies to all systems within our production environment. The production environment includes all endpoints and cloud assets used in hosting IllumiDesk.com and its subdomains. This may include third-party systems that support the business of IllumiDesk.com.

###  Ownership

Control Owner:

* `Security Operations`

Process Owner:

* Infrastructure Team

###  Guidance

Control should be designed to ensure we don't default to "allow all" traffic and instead put in place reasonable barriers for access to our production network.

###  Additional control information and project tracking

Infrastructure manages the configuration for GCP using chef and terraform which includes firewall rules. Configurations are version controlled and require approval prior to changing. The Infrastructure team engages with Security Operations to review new firewall rules that fall outside of the baseline. Security manages the monitoring for the service and can validate the correct rules are still in tact.

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Network Policy Enforcement Points control issue.

####  Policy Reference

*  Internal Networking Scheme in the handbook links to the production mirror terraform `IllumiDesk-com-infrastructure` project.
* Terraform configurations provided for the production environment 'gprd' project within GCP and VPC configurations for each module.
* Infrastructure production testbed template with process to prompt Security review of firewall rules for access to production data.

###  Framework Mapping

* ISO
  * A.13.1.1
* SOC2 CC
  * CC6.6
* PCI
  * 1.1.4
  * 1.2
  * 1.2.1
  * 1.2.3
  * 1.3
  * 1.3.1
  * 1.3.2
  * 1.3.3
  * 1.3.4

