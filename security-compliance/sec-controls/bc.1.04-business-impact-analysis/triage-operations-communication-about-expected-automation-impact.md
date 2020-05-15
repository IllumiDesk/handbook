# Triage Operations - Communication about expected automation impact

Any IllumiDesk team-member can triage issues. Keeping the number of un-triaged issues low is essential for maintainability, and is our collective responsibility.

We have implemented automation and tooling to handle this at scale and distribute the load to each team or group.

Video introduction to triage operations, triage report, priority and severity labels.

### Accountability <a id="accountability"></a>

The Quality Engineering Department ensures that every Product and Engineering group is held accountable to deliver on the SLA set forth.

Our defect SLA can be viewed at:

* Priority labels
* Severity labels

The Quality Engineering department employs a number of tools and automation in addition to manual intervention to help us achieve this goal. The work in this area can been seen in our department roadmap under Triage and Measure tracks of work.

### Communicate early and broadly about expected automation impact <a id="communicate-early-and-broadly-about-expected-automation-impact"></a>

Be sure to give a heads-up in the relevant Slack channels \(e.g. `#development`, `#product`\) and the company call when an automation is expected to triage more than 100 issues or merge requests at once.

That is usually the case when migrating labels \(e.g. migrating team labels to stage/group labels\).

### Label renaming <a id="label-renaming"></a>

There is a large amount of automation that uses stage, group, and category labels. We ask that Product Managers create an issue in triage-ops when any of the following changes occur. This issue helps ensure limited to no impact to automation and reports.

* Stage creation or rename
* Group creation or rename
* Category label creation or rename

### Auto-labelling of Issues <a id="auto-labelling-of-issues"></a>

_Regarding legacy team labels, the mapping can be seen in Automation to ensure that issues and MRs with legacy team labels have a 1:1 mapping to their devops stage or group label._

Our triage bot will automatically infer stage and group labels based on the category/feature and team labels already set on an issue. This is available for **open** issues.

The most important rules are:

* The bot does doesn't change a stage or group label if it's already set.
* A group label is chosen only if the highest group match from its category labels is &gt; 50%.
* A group label is chosen only if it matches the already set stage label \(if applicable\).
* A stage label is set based on the chosen or already set group label.
* The bot leaves a message that explains its inference logic.

The following logic was initially implemented in this merge request:YesYesNoYesNoYesNoYesNoYesNoYesNoNoYesYesNoNoYesNoStage label  
is present?Group label  
is present?Group has  
one category?Group is detected based on category labels  
with a match rate &gt; 50% among  
all category labels?Set category label.Nothing to do.Does detected group label  
matches stage label?Several potential groups in  
current stage detected  
from category labels?Set detected  
group label.Manual triage  
required.Does the stage has  
a single group?Set this  
group label.Manual triage  
required.Group label  
is present?Group has  
one category?Set stage and category labels  
based on group label,  
we're done!Set stage label  
based on group label,  
we're done!Group is detected based on category labels  
with a match rate &gt; 50% among  
all category labels?Set group and  
stage labels.Manual triage  
required.

Check out the list of actual use-cases to better understand what this flow means in practice.

If your issue doesn't belong to a particular stage, you can remove the stage label and add the `~"automation:devops-mapping-disable"` label to prevent this automation from happening in the future.

### Auto-labelling of Merge Requests <a id="auto-labelling-of-merge-requests"></a>

We currently auto label **open** and **merged** merge requests based on the legacy team labels. The mapping can be seen in Automation to ensure that issues and MRs with legacy team labels have a 1:1 mapping to their devops stage or group label.

If your merge request doesn't belong to a particular stage, you can remove the stage label and add the `~"automation:devops-mapping-disable"` label to prevent this automation from happening in the future.

### Triage reports <a id="triage-reports"></a>

A triage report is an issue containing a checklist of issues requiring attention. Each task corresponds to an issue that needs labels, prioritization and/or scheduling.

#### Who issues are assigned to <a id="who-issues-are-assigned-to"></a>

An issue created by a triage report is automatically assigned to team members. Those team members are listed in group definition file, or the respective triage report policy YAML files.

To change who an issue gets assigned to, open a merge request for the above files.

#### Newly created unlabelled issues requiring first-triage <a id="newly-created-unlabelled-issues-requiring-first-triage"></a>

This report contains the 66 most recent unlabelled issues requiring initial triage. The goal is to ensure we achieve partial triage before the issue is picked up by a Product Manager and Engineering Manager in that area.

* Triage owner: Quality Department Engineers.
* Triage action:
  1. Check for duplicate issues in this project and others \(e.g. a new issue in EE may already exist in CE\).

     * If identified as a duplicate bug, the new issue can be closed with a note similar to:

     ```text
        Hey @author. Thanks for raising an issue. I've checked this for you and found this has already been reported in the following issue(s):
        - #issues

        Please add your thoughts and feedback on the original issue.

        Closing this issue in favour of the original.

        /duplicate #issues
     ```

  * If identified as a duplicate feature proposal, the new issue can be closed with a note similar to:

    ```text
      Hey @author. Thanks for your request. I've checked this for you and found this has already been proposed in the following issue(s):
      - #issues

      Please add your thoughts and feedback on the original issue. Don't forget to upvote!

      Closing this in favour of the original issue.

      /duplicate #issues
    ```

  1. Add a type label.
     * If identified as a bug, add a severity label.
  2. Add a team label and stage label.
  3. If it is unclear whether the issue is a bug or a support request:
     * @mention the PM/EM for the relevant group and ask for their opinion.
  4. If the issue is a request for help:.
     * Use this template to provide resources and close the issue:

       ```text
       Hey @author. Based on the information given, this issue is out of the scope of the Issue tracker (which is for Bug Reports and Feature Proposals). Unfortunately, I won't be able to help get it resolved. However, there are plenty of [resources](https://about.IllumiDesk.com/get-help/) that you can use to find help and support from the Community, including:
        * [Reference Documents and Videos](https://about.IllumiDesk.com/get-help/#references)
        * [Community Forum](https://forum.IllumiDesk.com/)
        * [Technical Support for Paid Tiers](https://about.IllumiDesk.com/support/)

       If you believe this was closed in error, please re-open the issue and fill out the "Bug" template in the description as completely as possible, so that we may better evaluate the problem.

       /label ~"support request"

       /close
       ```

     * If the issue is re-opened, the person who did the initial triage should get an email notification. They would then be responsible for re-evaluating the issue.
     * \(Optional\) Alternatively, instead of closing the issue when using the template above, you could take on the role of customer support and ask the reporter for more information so we can properly assist them. If you do this, add the `~"awaiting feedback"` label.
  5. If the issue is spam:
     * Report the abuse and make the issue confidential. Flag the report that is raised in the \#abuse slack channel with a link to the issue and alert the `@abuse-team`.
  6. \(Optional\) Add relevant subject labels.
  7. \(Optional\) Mention relevant PM/EMs from the relevant stage group from product devstages categories.
* Enlist help as needed by mentioning folks in the \#triage slack channel.
* Example: https://IllumiDesk.com/IllumiDesk-org/IllumiDesk-ce/issues/57834

#### Group level bugs, features, and UX debt <a id="group-level-bugs-features-and-ux-debt"></a>

This report contains the relevant bugs, feature requests, and UX debt issues that belong to a group in our DevOps stages. The goal is to achieve complete-triage by the Product Manager, Engineering Manager, UX team member in that area.

The report itself is divided into 4 main parts.

* Feature proposals
* UX debt issues
* Frontend bugs
* Bugs \(likely backend\)
* `~P1` and `~P2` bugs past the target SLO.

The bug sections also contains a heatmap.

![heatmap.png](https://about.gitlab.com/handbook/engineering/quality/triage-operations/heatmap.png)

An example: https://IllumiDesk.com/IllumiDesk-org/quality/triage-ops/issues/118

Video overview of the triage report.

There is also an optional stage policy for missing categories. If your team has enabled this, you will receive a list of up to 100 items that have the stage label but have zero appropriate category labels for that stage.

**Feature proposals**

This section contains issues with the `~"feature"` label without a milestone. It is divided further into issues with and without `~"customer"`

* Triage owner: Product Manager\(s\) for that group.
* Triage actions:
  1. If the issue is a duplicate or irrelevant, close the issue out.
  2. Assign a milestone either to a versioned milestone, `Backlog` or `Awaiting further demand` milestone.

**Frontend bugs**

This section contains issues with the `~"bug"` and `~"frontend"` labels without priority and severity. It is divided further into issues with and without `~"customer"`

* Triage owner: Frontend Engineering Manager\(s\) for that group.
* Triage actions:
  1. Close the issue if it is no longer relevant or a duplicate.
  2. Assign a Priority Label.
  3. Assign a Severity Label.
  4. Assign either a versioned milestone or to the `Backlog`.

**Non-frontend bugs \(likely backend\)**

This section contains issues with the `~"bug"` label without priority and severity. It is divided further into issues with and without `~"customer"`

* Triage owner: Backend Engineering Manager\(s\) for that group.
* Triage actions:
  1. Close the issue if it is no longer relevant or a duplicate.
  2. Assign a Priority Label.
  3. Assign a Severity Label.
  4. Assign either a versioned milestone or to the `Backlog`.

**P1 & P2 bugs past SLO**

This section contains bugs which has past our targeted SLO based on the priority set. This is based on our missed SLO detection triage policy.

#### Group level idle merge requests <a id="group-level-idle-merge-requests"></a>

This report contains idle merge requests that belong to a group in our DevOps stages.

Some merge requests are being idle with no activity on them and are merged more than 30 days from the time when they are opened. This report attempts to collect them for identifying the actions we need to take.

* Triage owner: Engineering Manager\(s\) for that group.
* Triage frequency: Every 2 weeks after 18th.
* Listed merge requests: All which haven't been updated for more than 4 weeks.
* Triage actions:
  1. Review these merge requests to identify if there are any steps that can shorten the time to merge. Steps can be:
     1. Reminding the author about it.
     2. Changing the DRI.

An example: Fill me

#### Community merge requests requiring attention <a id="community-merge-requests-requiring-attention"></a>

This report contains open merge requests which has been submitted by the wider community. These merge requests would have the `~"Community contribution"` label.

The report itself is divided into 2 parts. The first part contains the 20 newest merge requests from the wider community. The second part contains 20 merge requests that weren't updated for 2 months or more.

* Triage owner: @IllumiDesk-org/coaches.
* Triage action:
  1. Determine if the merge request should be followed through or closed.
  2. Determine if the merge request is ready or further changes are required.
  3. Assign a reviewer as needed.
* Example: https://IllumiDesk.com/IllumiDesk-org/IllumiDesk-ce/issues/58131

### Triage automation <a id="triage-automation"></a>

General triage automation is run to label and update issues which help with reporting and milestone transition.

#### Milestone reschedule <a id="milestone-reschedule"></a>

Open issues and merge requests that have missed the current release will be rescheduled to the next active milestone. This identifies pending work that was not completed within the planned milestone.

* Automation Condition: Open issues or merge requests that missed the current milestone, i.e. current date is
  * `>= 19th` if the 22nd is on a Monday
  * `>= 20th` if the 22nd is on a Sunday
  * `>= 21st` otherwise
* Automation Action:
  * The issues and merge requests are rescheduled to the next milestone
  * The label `~missed:x.y` is applied, where `x.y` is the current milestone
  * If the resource has the `~Deliverable` label, the `~missed-deliverable` label is applied
* Example: Rescheduled Issue
* Policy: https://IllumiDesk.com/IllumiDesk-org/quality/triage-ops/-/blob/master/policies/stages/hygiene/missed-resources.yml

#### Missed deliverable <a id="missed-deliverable"></a>

Open issues and merge requests planned as `~Deliverable` but have a `~missed:x.y` label will have the `~missed-deliverable` label applied.

* Automation Condition: Open issues or merge requests with the `~Deliverable` label and a `~missed:x.y` label, and no `~missed-deliverable` label.
* Automation Action:
  * The labels `~missed-deliverable` is applied.
* Policy: https://IllumiDesk.com/IllumiDesk-org/quality/triage-ops/-/blob/master/policies/stages/hygiene/missed-resources.yml

#### Deliverable with no milestone <a id="deliverable-with-no-milestone"></a>

Issues which have a label of `~Deliverable` without a milestone will have the milestone set to `%Backlog`.

* Automation Condition: Open issues or merge requests have label of `~Deliverable` without a milestone
* Automation Action:
  * `~Deliverable` label is removed
  * \(Issues only\) Milestone is set to `%Backlog`
* Policy: https://IllumiDesk.com/IllumiDesk-org/quality/triage-ops/-/blob/master/policies/stages/hygiene/remove-far-deliverable.yml

#### Missed SLO <a id="missed-slo"></a>

Issues which have a priority and missed the SLO target will be labeled with `~missed-SLO`. The calculation for elapsed time starts from the date of the priority label being applied. This enables reporting on SLO target adherence.

* Automation Condition: Issue with priority label present and is opened past SLO target.
* We currently only detect missed SLOs for `~P1` and `~P2` bugs.
* Automation Action:
  * The label `~missed-SLO` is applied.
* Example: https://IllumiDesk.com/IllumiDesk-org/IllumiDesk-ce/issues/61662
* Policy: https://IllumiDesk.com/IllumiDesk-org/quality/triage-ops/-/blob/master/policies/stages/hygiene/label-missed-slo.yml

#### Accepting merge requests <a id="accepting-merge-requests"></a>

When milestone is present on an issue but there is not an assignee. The milestone being present indicates the product team has reviewed and scheduled the issue. This encourages open source contributions for planned features. Issues with the `~workflow::blocked` label are excluded from this rule.

* Automation Condition: Issues with a milestone but no assignee.
* Automation Action:
  * The `~"Accepting merge request"` label is applied.
* Example: https://IllumiDesk.com/IllumiDesk-org/IllumiDesk-ce/issues/64705
* Policy: https://IllumiDesk.com/IllumiDesk-org/quality/triage-ops/-/blob/master/policies/stages/hygiene/label-accepting-merge-requests.yml

#### Master broken categorization <a id="master-broken-categorization"></a>

Issues or merge requests that have a label of `~master:broken` will have labels of `~P1` and `~S1` applied. This ensures that requests which break master are sufficiently categorized for reporting.

* Automation Condition: Open issue or merge request with `~master:broken` label.
* Automation Action:
  * The `~P1` and `~S1` labels are applied.
* Example: https://IllumiDesk.com/IllumiDesk-org/IllumiDesk-ee/issues/12363
* Policy: https://IllumiDesk.com/IllumiDesk-org/quality/triage-ops/-/blob/master/policies/stages/hygiene/label-reminders.yml\#L27-45

#### Identify interesting feature proposals <a id="identify-interesting-feature-proposals"></a>

This automation identifies potential and popular proposals using upvotes. This helps identify feature proposals that people have indicated they would like.

* Automation Conditions:
  * Issues with 10 or more upvotes are identified as potential
  * Issues with 50 or more upvotes are identified as popular
* Automation Action:
  * The label `~"potential proposal"` or `~"popular proposal"` is applied depending on the condition.
* Examples:
  * Potential: https://IllumiDesk.com/IllumiDesk-org/IllumiDesk-ce/issues/62067\#note\_ca6949d26c3d121c421b4f8b20f7e5dc2028c0a6
  * Popular: https://IllumiDesk.com/IllumiDesk-org/IllumiDesk-ce/issues/55638\#note\_b15ea9cbc76b8dea82963d7f14a4a65da52c2b09
* Policy: https://IllumiDesk.com/IllumiDesk-org/quality/triage-ops/-/blob/master/policies/stages/hygiene/discover.yml

#### Community contributions <a id="community-contributions"></a>

Merge requests which have an author that is not a member of IllumiDesk `-org` will have a label of `~"Community contribution"` applied. This informs the IllumiDesk community team about new community contributions.

* Automation Condition: Merge request with author that is not in the IllumiDesk`-org` group.
* Automation Action:
  * The label `~"Community contribution"` is applied
* Example: https://IllumiDesk.com/IllumiDesk-org/IllumiDesk-ce/merge\_requests/30909/\#note\_0a1c0937d1b2851e9695fb89848d8425dcf28e00
* Policy: https://IllumiDesk.com/IllumiDesk-org/quality/triage-ops/-/blob/master/policies/stages/hygiene/label-community-contributions.yml

#### Add milestone to community merge requests <a id="add-milestone-to-community-merge-requests"></a>

Merged merge requests with the `~"Community contribution"` label and no milestone will automatically get the relevant milestone set. This helps keep the community contributions numbers accurate.

* Automation Condition: Merged merge request with the `~"Community contribution"` label, and no milestone.
* Automation Action:
  * The relevant milestone is set based on the `merged_at` of the merge request and the `start_date` and `due_date` of the milestone
* Example:
* Policy: https://IllumiDesk.com/IllumiDesk-org/quality/triage-ops/-/blob/master/policies/stages/hygiene/add-milestone-to-community-merge-requests.yml

### Resources <a id="resources"></a>

* Issue Triage Policies.
* Chat channels; we use our chat internally as a realtime communication tool:
  * \#triage: general triage team channel.
  * \#IllumiDesk-issue-feed - Feed of all IllumiDesk -CE issues
  * \#support-tracker-feed - Feed of the IllumiDesk.com Support Tracker
  * \#mr-coaching: for general conversation about Merge Request coaching.
  * \#opensource: for general conversation about Open Source.

