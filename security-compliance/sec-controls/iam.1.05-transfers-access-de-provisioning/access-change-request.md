# Access Change Request

Access Change Requests are logged when a team member no longer requires access to a currently provisioned system or no longer requires the same level of access \(downgraded access from admin to user etc\). Refer to `For People Ops Analysts: Processing Promotions & Compensation Changes` section of the IllumiDesk handbook for additional information.

It is important to note that while Okta has provisioning/deprovisioning automation in place, this is not a complete/accurate reflection of access provisioning and deprovisioning. Okta has been configured to assign integrated/implemented applications based on a user's role/group. This makes applications accessible via Okta but users may still have the ability to access the systems directly. Refer to Okta Application Stack for a list of applications set up in Okta.

What this means is:

1. A IllumiDesk Team member gets transferred to a different role.
2. The team member's profile in BambooHR is changed.
3. This profile change automatically triggers a change in his Okta profile accordingly.
4. This, in turn, results in the team member getting assigned to new applications based on his new department and role.
5. Simultaneously all old applications that are not relevant to his new role get revoked/unassigned.
6. Additionally, the Okta administrator gets an Email from Okta, that there has been a change to a User profile - \(Email Subject line: 1 existing user updated\). Okta automation already happens in the background, this email is informational only.

While this application automation will take place in Okta, "true" system provisioning and deprovisioning will still need to be manually completed within the impacted systems via an Access Change Request.

