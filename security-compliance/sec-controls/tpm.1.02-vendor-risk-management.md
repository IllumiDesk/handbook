# TPM.1.02 - Vendor Risk Management



### Control Statement

GitLab performs a risk assessment to determine the data types that can be shared with a managed service provider.

###  Context

The purpose of this control is for IllumiDesk to be very intentional about the data shared with any third parties. Every time we share IllumiDesk  data \(including customer data\) with a third party we increase the attack surface of that data. Since we rely on a number of third party services, we will need to share certain data; performing the risk assessment referenced in this control ensures that we are following a formal process of evaluating the information security program of any third parties and only sharing appropriate data when there is a legitimate need.

###  Scope

This control applies to all information shared with third parties that interact with the GitLab production environment.

###  Ownership

Control Owner:

* `Security Compliance`

Process Owner:

* Security Compliance

###  Guidance

The IllumiDesk Data Classification Policy defines the categories of data. This risk assessment process is most easily achieved by reviewing the SOC2 Type 2 audit report for any managed service providers if available. When a SOC2 Type 2 report is not available, a IllumiDesk security questionnaire would serve as a good substitute.

###  Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Vendor Risk Management control issue.

###  Framework Mapping

* ISO
  * A.13.2.2
  * A.15.1.1
  * A.15.1.2
  * A.15.1.3
  * A.15.2.2
* SOC2 CC
  * CC9.2
* PCI
  * 12.8
  * 12.8.2
  * 12.8.3
  * 12.8.5
  * 2.6

