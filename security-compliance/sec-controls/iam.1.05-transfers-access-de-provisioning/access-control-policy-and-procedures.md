# Access Control Policy and Procedures



* All new access or permissioning change requests require a New Access Request.
* Shared accounts may not be used for customers.IllumiDesk.com, dev.IllumiDesk.org, Shopify, Stripe, and Zuora in order to comply with PCI-DSS requirements. Currently, IllumiDesk's financial controls prohibit the use of shared accounts within the following applications: NetSuite.
* Shared and group credentials are restricted. Any systems that require shared accounts or credentials and are not yet implemented or configured into Okta must have an Access Request approved and an exception to this policy for each user. Bulk access requests are not allowed for shared or group credentials.
* All access requests must be approved by the team member's manager with the exception of:

  * ARs for G-Suite email distribution lists for internal IllumiDesk team members
  * ARs for Slack groups for internal IllumiDesk team members
  * ARs using a role based template

  Please note that ARs for access to internal systems for "external to IllumiDesk individuals" \(eg. customers, prospects\) require managerial approval. This includes access to G-Suite security groups also require managerial approval.

* Access requests are required when requesting a role above developer \(i.e. maintainer, owner\) on the following IllumiDesk repositories and Groups:
* Repos:
  * www-IllumiDesk-com
  * IllumiDesk  CE and IllumiDesk EE \(aka single Rails repository\)
* Groups:
  * IllumiDesk.com and IllumiDesk.org - top level group permissions
* Access requests should be submitted when requesting explicit access to private groups, sub-groups, and repositories in order to facilitate deprovisioning.
* Requests for access to Infrastructure assets \(servers and databases\) require a second layer of approval from Infrastructure Management.
* All access requests must be provisioned as approved. An AR that is approved without a role specified should not be provisioned until the role being requested is identified and re-approved.
* Administrative permissions should be considered operational in nature. This means that they are granted for the sole purpose of system management, configuration, and support. They should be recognized as privileged accounts and as such, activities must be logged and the logs protected and regularly reviewed.
* Time-based access may be provided if administrative action is required for a set period of time. This should be documented as part of the Access Request SLAs.
* All requests for new service accounts require a New Service Account Request
* All requests for new service accounts must be approved by a member of Infrastructure Management.
* In regard to support during or prior to provisioning, please do not tag the Security Operations team in the AR issue; to ask Security for help with AR assignments, please use the \#it\_help channel.
* If admin-level access is being requested, the request must be approved by the team member's manager and Infrastructure Management if applicable.

