# VUL.3.01 - Infrastructure Patch Management

## Control Statement

IllumiDesk installs security-relevant patches, including software or firmware updates monthly.

## Context

This control details security best practices in relation to infrastructure patching. This control is trying to ensure that all IllumiDesk productions systems are up to date according to our own patching standards. We need to prove that patching is prioritized and we consistently apply all possible patches and decommission systems as appropriate.

## Scope

This control applies to all systems within our production environment. The production environment includes all endpoints and cloud assets used in hosting IllumiDesk.com and its subdomains. This may include third-party systems that support the business of IllumiDesk.com.

## Ownership

Control Owner:

* Infrastructure \(.com\)
* Security Operations \(everything else\)

Process Owner:

* Infrastructure \(.com\)
* Security Operations \(everything else\)

##  Guidance

* This control is related to control VUL.1.01.
* The implementation of this control will depend on the use of idempotent or immutable infrastructure. This patching can be done manually but can also be satisfied by tearing down and deploying new systems as updates are made available.

## Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Infrastructure Patch Management control issue.

### Framework Mapping

* SOC2 CC
  * CC7.1

