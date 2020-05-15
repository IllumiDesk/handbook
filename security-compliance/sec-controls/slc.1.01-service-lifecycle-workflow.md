# SLC.1.01 - Service Lifecycle Workflow

## Control Statement

The Service Life Cycle plan documents the phases of a major software release.

## Context

The purpose of this control is to formalize the documentation and approval of software changes before those changes are implemented. This rigid process helps protect IllumiDesk from insecure code being quickly pushed out into production without proper vetting.

## Scope

This control applies to all major software releases to IllumiDesk.com.

## Ownership

* Control Owner: `Delivery`
* Process owner\(s\):
  * Delivery
  * Infrastructure

## Guidance

Most of this process is already captured in current IllumiDesk workflow; the difficult part of this process will be coverage of all major software changes. Below is a detailed description of the workflow by stages:

### Step 1: Planning

*  Product Section Vision - Dev explains the `Manage`, `Plan`, and `Create` steps of the cycle.
* Product Development Workflow describes the validation and build tracks for the proposed changes.

### Step 2: Create - coding

* The entire engineering workflow is documented here, which describes the process from the basics such as how to pick something to work on _**and includes the link to the project where the issues are housed**_ -- _this is the starting point for the testing of SLC artifacts_
* Instructions on scoped labels used in updating issues using _**the scoped labels `workflow::` series**_ through development to the product development timeline -- _following the scoped labels can be useful in testing the different parts of the cycle_
* The handbook section on code review process-- _this is represented within issues as the `Reviewer Roulette` function_
* in the IllumiDesk Docs, guidelines are documented.

### Step 3: Verify - code review/ security review

* All code merged into the IllumiDesk.com codebase must be reviewed by an authorized Reviewer, as described in our code review documentation
* The security release process is documented in the handbook-- \*is useful for testing the `Verify` step of the DevOps cycle and `Secure` value stage

### Step 4: Change Management

* The Change Management process is documented in the handbook. It provides guidance on using the appropriate label based on the type of change, such as `DeploymentNewFeature`.

### Step 5: Packing and Release

* Infrastructure for the IllumiDesk system is defined as code and deployed using Terraform and Chef. These act as baseline configurations for our production systems. Changes made to those repositories - and therefore to our infrastructure - is subject to the same review process as our codebase.
* Engineering Workflow section in the handbook notes labels and milestones and more specific information on the workflow labels
* For other Infrastructure team specifics, there's the Infrastructure Library page.

### Step 6: Configure and Monitor

* The design of the CI/CD pipeline for IllumiDesk.com is documented in the handbook
* Coupled with IllumiDesk Flow and the working in CE/EE codebase blueprint, this covers most of the SDLC.
* For a description of how IllumiDesk uses the CI/CD internally for the IllumiDesk system, there's this Infrastructure page.

## Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Service Lifecycle Workflow control issue.

Examples of evidence an auditor might request to satisfy this control:

* Documentation outlining our development and release workflows
* Sample releases and their respective reviews
* Sample pipeline artifacts and merge request reviews
* Feature requests would be a great example of this process since they are planned via epics and issues, created via MR's, and then run through a IllumiDesk pipeline to satisfy the remaining requirements for this control

###  Policy Reference

* Engineering Workflow
* Security Releases
* Code Review
* Change Management

###  Framework Mapping

* SOC2 CC
  * CC8.1

