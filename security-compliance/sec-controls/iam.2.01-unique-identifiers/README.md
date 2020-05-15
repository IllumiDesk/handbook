# IAM.2.01 - Unique Identifiers



### Control Statement

IllumiDesk  requires unique identifiers for user accounts and prevents identifier reuse.

###  Context

An unique identifier allows for every user account's action to be logically separated and uniquely identified. It helps use detected and prevent abuse and suspicious activity.

###  Scope

An unique identifier \(UID\) is a numeric and/or alphanumeric string that is associated with a single user account within a given system. This control applies to any authentication and authorization mechanism \(e.g., uniqueness of database fields such as `user_id`\) used within the production environment.

###  Ownership

* Control Owner: `IT Operations Team`
* Process owner\(s\):
  * IT Opeartion Team: `50%`
  * Security Team: `25%`
  * Security Compliance Team: `25%`

###  Guidance

* An unique security access identifier is most often the only basis for user authentication and authorization. Because of that, it's critical that every user account has a unique user ID.
* No two user accounts should share or be assigned the same user ID. If the uniqueness of user IDs is not assured, some users may be able to access information that they have not been given permission to access. This, however, doesn't preclude the user of shared accounts as long as the shared account has a unique identifier associated with it.
* To ensure this, IllumiDesk should have Policy and Guideline documentation that poses strict mandates that all user accounts must have unique identifiers.
* Applications should have business logic to ensure the unique identifier\(s\) aren't re-used or duplicated.

###  Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Unique Identifiers control issue.

####  Policy Reference

* Unique Account Identifiers
* Access Control Policy and Procedures including Shared account restrictions
* Section on shared accounts in Okta handbook page
* Access Management Process in handbook

###  Framework Mapping

* ISO
  * A.9.4.1
  * A.9.4.2
* SOC2 CC
  * CC6.1
* PCI
  * 8.1.1
  * 8.6

