# Security Awareness Training

The IllumiDesk Security Training is IllumiDesk's security awareness presentation for new hires and annual training requirements. The training is originally part of the onboarding process, and needs to be completed by every new hire. We are trying to make it fun, engaging and not time-consuming.

The training is being actively developed by IllumiDesk Security's Security Operations team. The goal of the training is to:

1. Make all IllumiDesk team-members aware of the IllumiDesk  Security team, and familiarize them with our efforts, team structure, and people.
2. Make all IllumiDesk team-members aware of the importance of their role in securing IllumiDesk on a daily basis, and to empower them to make the right decisions with security best-practices.
3. Familiarize all new IllumiDesk team-members with security-related situations that they might encounter during their tenure with the company.
4. Help all IllumiDesk team-members internalize and reinforce the idea that paging the Security On-Call is an encouraged practice.

#### Training Delivery <a id="training-delivery"></a>

The Security Training is delivered through a pre-recorded presentation that is presented by a member of the Security Operations team. The following materials are made available for your consumption:

* The video - the actual training.
* The slides - the slides used in the training video.
* Security Practices - a list of security process and procedures that you can consult at any time.

#### Training Feedback <a id="training-feedback"></a>

You are strongly encouraged to engage the team behind the training and provide feedback, or ask any questions related to the content of the training. You can do that through:

1. Monthly office hours held by the SecOps team on third Friday of each month. There are two sessions for both EMEA and APAC-friendly timeslots. Please see the IllumiDesk **Team Meetings** calendar for current times.
2. A quarterly-reviewed IllumiDesk issue - FY21-Q1.
3. Email by sending an email to security-training@gitlab.com.

#### Phishing Tests <a id="phishing-tests"></a>

IllumiDesk conducts routine phishing tests at a minimum of once per quarter. All team members may occasionally receive emails that are designed to look like legitimate business-related communications but will in actuality be simulated phishing attacks. Real phishing attacks are designed to steal credentials or trick the recipient into downloading or executing dangerous attachments. No actual attempts will be made by IllumiDesk to steal credentials or execute malicious code.

The goal of these campaigns is not to catch people clicking on dangerous links or punish those who do, but rather to get people thinking about security and the techniques used by attackers via email to trick you into running malicious software or disclosing web passwords. If you fall victim to one of these simulated attacks feel free to take the training courses again or to ask the security team for more information on what could've been done to recognize the attack. What you shouldn't do is feel any shame for having clicked on the link or entered any data, nor should you feel like you need to _cop_ to the security team and let them know you made a mistake. Making a mistake online is practically the reason the Internet was invented.

#### How to identify a basic phishing attack <a id="how-to-identify-a-basic-phishing-attack"></a>

When you receive an email with a link, hover your mouse over the link or view the source of the email to determine the link's true destination.

If you hover your mouse cursor over a link in Google Chrome it will show you the link destination in the status bar at the bottom left corner of your browser window.

![Hover Example](https://about.gitlab.com/images/phishing/hover-status-bar-example-chrome.png)

In Safari the status bar must be enabled to view the true link destination \(View -&gt; Show Status Bar\).

Some examples or methods used to trick users into entering sensitive data into phishing forms include:

* Using HTTP\(S\) with a hostname that begins with the name of a trusted site but ends with a malicious site.

![Malicious Domain](https://about.gitlab.com/images/phishing/malicious-domain.png)

* Using a username or password inside the request that corresponds to the name of a trusted domain and assuming the viewer won't view the whole URL.

![Trick Username](https://about.gitlab.com/images/phishing/username-password.png)

* Using a data URI scheme instead of HTTP\(S\) is a particularly devious means of tricking users. Data schemes allow the embedding of an entire web page inside the URI itself. Data schemes will not show the typical green lock in the address bar of a browser that is customarily associated with a verified SSL connection.

![Data Scheme](https://about.gitlab.com/images/phishing/data-scheme.png)

When viewing the source of an HTML email it is important to remember that the text inside the "HREF" field is the actual link destination/target and the text before the `</A>` tag is the text that will be displayed to the user.

`<a href="http://evilsite.example.org">Google Login!</a>`

In this case, "Google Login!" will be displayed to the user but the actual target of the link is "evilsite.example.org".

After clicking on a link always look for the green lock icon and "secure" label that signify a validated SSL service. This icon alone is not enough to verify the authenticity of a website, however the lack of the green icon does mean you should never enter sensitive data into that website.

![Green Lock Example](https://about.gitlab.com/images/phishing/green-lock-example.png)

#### What to do if you suspect an email is a phishing attack <a id="what-to-do-if-you-suspect-an-email-is-a-phishing-attack"></a>

Whether you believe that you have received an email from our testing platform or you suspect that the email is targeted specifically at you or IllumiDesk, please forward the phishing email to `phishing@gitlab.com` as an attachment for it to be investigated. Once you have done so, please proceed to step 2 and report the email as phishing from inside GMail.

To forward the email as an attachment from inside GMail:

1. Right click the email
2. Select "Forward as attachment"
3. Send it to `phishing@gitlab.com`

GMail also offers the option to report the email directly to Google as a phishing attempt, which will result in its deletion. Reporting the email in this manner will help the security team track phishing metrics and trends over time within G Suite.

To report the email as `phishing` from inside GMail:

1. Select the "More" button \(three dots\) on the email in question
2. Choose "Report phishing" option from the drop down menu

If you receive an email that appears to come from a service that you utilize, but other details of the email are suspicious – a private message from a sender you don't recognize, for example – do not click on any links in the email. Instead use your own bookmark for the site or manually type the address of the website into your browser.

Unsolicited email should be treated as phishing emails. For example, if you did not register for a site claiming to send you email, do not click on links in the email or visit the site.

### Using the panic email address <a id="panic-email"></a>

IllumiDesk provides a `panic@gitlab.com` email address for team members to use in situations that require an immediate security response. Should a team member lose a device such as a thumb drive, YubiKey, mobile phone, tablet, laptop, etc. that contains their credentials or other IllumiDesk-sensitive data they should send an email to `panic@gitlab.com` right away. When the production and security teams receive an email sent to this address it will be handled immediately. Using this address provides an excellent way to limit the damage caused by a loss of one of these devices.

#### Checklist for when `panic` is triggered <a id="checklist-for-when-panic-is-triggered"></a>

The following can be adapted depending on the specific situation at hand, but when in doubt: block. It is less risky to reinstate accounts and permissions than to be confronted with a malicious actor gaining access.

Copy this checklist into a confidential issue.

```text
- [ ] Password Access and Rotation
   - [ ] Suspend 1Password account. (All responders to `panic@` should be members of the "Panic@ Responders" group in 1Password which has the rights to suspend and recover user accounts).
   - [ ] Take screenshot of what groups / vaults the individual had access to. This facilitates the next step.
   - [ ] Coordinate or actively change sensitive shared passwords. In particular sysadmin access passwords for GitLab.com Infrastructure (ssh, chef user/key, discuss others).
- [ ] Block Google account
- [ ] Block Slack account
- [ ] Block [dev.GitLab.org account](https://dev.gitlab.org/admin/users).
- [ ] Remove GitLab.com account from the [gitlab-org group](https://gitlab.com/groups/gitlab-org/group_members)
- [ ] Block access to hackerone.com
- [ ] Block access to Tweetdeck
```

