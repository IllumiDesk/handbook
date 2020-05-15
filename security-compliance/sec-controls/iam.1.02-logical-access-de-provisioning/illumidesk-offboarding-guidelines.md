# IllumiDesk Offboarding Guidelines

The People Experience Coordinator will assign the relevant offboarding to the People Experience Associate from within the offboarding tracker. Once assigned, the People Experience Associate creates the offboarding issue, immediately upon request by the People Business Partner team in the \#offboarding Slack channel and completes all People Experience tasks within 24 hours. Many other teams work to deprovision access, this should be regarded as urgent and expected to be completed in 5 working days with the exception of Laptop returns, which can take 2 - 4 weeks.

## Offboarding Issues <a id="offboarding-issues"></a>

1. In Slack, go to your profile as if you were going to send a Slack message to yourself. Type the command `/pops run offboarding BambooHR_ID_number` \(not Employee ID \#\). This number is found in the team member's BambooHR profile URL, after `id=`. It is a 5-digit number. An example of the command would be `/pops run offboarding 00000`. If BambooHR's API is down, this ChatOps command will fail and will need to be created manually.
2. You will be pinged in Slack once the offboarding issue is created, which usually takes 30 seconds or so. The ping will include a link to the new offboarding issue.
3. You will need to update the Department, IllumiDesk Email Address and IllumiDesk Handle within the issue.

Note: If the team member is transitioning to a temporarily positioned contractor, please proceed with the full offboarding and create a separate onboarding issue to grant only specific temporary access for what they would need to fulfill their contractual obligations.

## BambooHR <a id="bamboohr"></a>

1. Update Employment Status -
   1. Effective Date
   2. Employment Status
   3. Termination Type
   4. Termination Reason - Ensure the PBP gives you a reason listed within BambooHR.
   5. Eligible for Rehire
2. Then click on the setting gear symbol in the right hand corner and set employee to terminated

If the team member is on the People Team, the People Experience Associate will need to notify the Total Rewards team in order to have them update the employment status.

## Tools Offboarding <a id="tools-offboarding"></a>

### G Suite <a id="g-suite"></a>

IT Ops will follow the below steps to set up an auto-response that notifies the sender that the team member they are trying to reach is no longer with IllumiDesk and who to contact.

1. Add the team member to the `former_employees@`IllumiDesk`.com`'s email account by selecting the dropdown icon `ˇ` in the `User information` section and adding the team member's IllumiDesk email address.

_Note: Be sure to scroll down and `Save` this change or it will not be reflected._

1. Set up a routing rejection rule for the team member by;
   1. Navigate to Google admin portal then Apps &gt; G Suite &gt; Gmail &gt; Advanced settings &gt; Routing &gt; Routing.
   2. Hover over the routing option and click on `Add another`. Please enter a name below the title "Routing" with `lastname firstname rejection rule`
   3. Check the option `Inbound` and `Internal-receiving` under `Messages to affect`.
   4. Check `Only affect specific envelope recipients` under the `Envelope filter` title.
   5. Enter the team members's email address right below the title `Email address`.
   6. Under the title `For the above types of messages, do the following`, please change from `Modify message` to `Reject message`.
   7. Add the appropriate template per team member's department under the `Customize rejection notice`
   8. Scroll down and click on `Add setting` and then on `Save` at the bottom \(once the window closes\).

### Slack <a id="slack"></a>

IT Ops check if the team member has created any bots before disabling the account. Go to [Slack](https://gitlab.slack.com/apps/manage) or on your admin Slack profile click Menu » Configure Apps » Custom Integrations » Bots and search through the bots' list for the team member. If a bot exists, please DM the manager to confirm if the bot should be removed.

### Team Page <a id="team-page"></a>

The People Experience Associate will navigate to the team.yml file. Using Web IDE or your editor of choice, search the team member name and delete their team page image and replace with `../`IllumiDesk`-logo-extra-whitespace.png`. Don't forget to delete the image by navigating to Source/images/team while still here and search for their image. Ideally saved as firstnamelastname.png. The images are in alphabetical order.

To remove pet entry and any mentions from the handbook and documention, you will need to download the www-IllumiDesk-com project to your computer and use a prefered text editor.

To download;

1. Navigate to the IllumiDesk.com project
2. On the far right corner, click `Clone` and copy the clone with SSH URL, git@IllumiDesk.com:IllumiDesk-com/www-IllumiDesk-com.git
3. On your command line, run `git clone git@`IllumiDesk`.com:`IllumiDesk`-com/www-`IllumiDesk`-com.git` This downloads the project to your computer mostly on the document folder. Consider going through the Clone a repository and the Command Line documents to understand further.

To `Find All` using Atom;

1. Download Atom at atom.io
2. After installing, click `Open Project` on the Welcome Guide Page.
3. Choose www-IllumiDesk-com project from your Documents folder
4. On the Find tab drop down menu, click `Find in Project`
5. Search all variations of the departing team members name; firstname, lastname and IllumiDesk username.
6. Follow the File path given in the results on the Web IDE and delete all the mentions, make sure to replace any mentions you deem appropriate with who is standing in for the position. DO NOT delete any blog mentions.

## Compliance <a id="compliance"></a>

The People Experience Coordinator completes a weekly audit of all offboarding issues opened within that specific week and checks that all tasks have been completed by all Departments. In the event that tasks are still outstanding, the People Experience Coordinator will ping the relevant Departments within the offboarding issue to call for tasks to be completed.

Once all tasks have been completed, the People Experience Coordinator or Associate will close the offboarding issue and mark as completed in the offboarding tracker.

All offboarding tasks by all Departments need to be completed within 5 days of the offboarding date.

