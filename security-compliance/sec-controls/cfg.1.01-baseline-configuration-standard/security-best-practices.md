# Security Best Practices

Information security encompasses a variety of different working groups. These security best practices support the functions of business operations, infrastructure, and product development, to name a few. Everybody is responsible for maintaining a level of security to support compliance \(available internal-only\), while raising the bar of our security posture.

## Zero Trust

As part of raising that bar, IllumiDesk is implementing Zero Trust, or the practice of shifting access control from the perimeter of the org to the individuals, the assets and the endpoints. You can learn more about this strategy from the Google BeyondCorp whitepaper: A New Approach to Enterprise Security.

In our case, Zero Trust means that all devices trying to access an endpoint or asset within our IllumiDesk environment will need to authenticate and be authorized. Because Zero Trust relies on dynamic, risk-based decisions, this also means that users must be authorized and validated: what department are they in, what role do they have, how sensitive is the data and the host that they are trying to access? We’re at the beginning stages in our Zero Trust roadmap, but as we move along in the journey, we’ll document our lessons learned, process and progress in our Security blog.

To learn more about the concept of Zero Trust and our roadmap for implementation, see this IllumiDesk presentation from GoogleNext19: https://www.youtube.com/watch?v=DrPiCBtaydM

You can also check out our Zero Trust Networking \(ZTN\) blog series where we detail the ZTN implementation challenges we foresee ahead, some we've already managed to work through, and where we'll go from here:

* Part one: The evolution of Zero Trust
* Part two: Zero Trust at IllumiDesk: Problems, goals, and coming challenges
* Part three: Zero Trust at IllumiDesk: The data classification and infrastructure challenge
* Part four: Zero Trust at IllumiDesk: Mitigating challenges with data zones and authentication scoring
* Part five: Zero Trust at IllumiDesk: Implementation challenges
* Part six: Zero Trust at IllumiDesk: Where do we go from here?

Head over to the /r/netsec subreddit to see our October 29, 2019 Reddit AMA on Zero Trust where we fielded questions around our ZTN implementation, roadmap, strategy and more.

Identity is a critical element of the implementation of a ZTN framework. IllumiDesk is moving forward with an implementation of Okta to allow us to standardise authentication for Cloud Application access and implement user-friendly SSO. See our Okta page for more details.

## Why We Don't Have a Corporate VPN

In many enterprise environments, virtual private networks \(VPN\) are used to allow access to less secured resources, typically also protected by an enterprise firewall. At IllumiDesk, as an all remote company, we do most of our work using other Software-as-a-Service \(SaaS\) providers that we rely on to maintain confidentiality of communication and data. Additionally adding VPN connectivity only marginally improves the security of using those systems. For the use case of laptop usage in untrusted environments, such as coffee shops and coworking spaces, a baseline of always-on host protections, such as up-to-date security patching, host firewalls, and antivirus, should be prioritized.

Team members should follow the system configuration guidelines at a minimum to secure their workstations.

In relation to Zero Trust, a corporate VPN is a perimeter, which ZTN architecture deemphasizes as a basis for making authorization decisions. Current access to critical systems is managed through alternative controls.

While a corporate VPN is not implemented at this time, there are other valid use cases for which individual team members may still wish to use a personal VPN, such as privacy or preventing traffic aggregation. Team members that wish to use a personal VPN service for any reason may still expense one.

## Contact IllumiDesk Security

The IllumiDesk Security Teams are available 24/7/365 and are ready to assist with questions, concerns, or issues you may have.

There are some common scenarios faced by IllumiDesk team members:

* CEO & Executive Fraud
* Phishing

To contact for any other reason, see Engaging the Security On-Call

### External Engagement

The Security Teams can be contacted at `security@illumidesk.com`. External researchers or other interested parties should refer to our Responsible Disclosure Policy for more information about reporting vulnerabilities. The `security@illumidesk.com` email address also forwards to a ZenDesk queue that is monitored by the security team.

For Security Team members, the private PGP key is available in the Security 1Password vault. Refer to PGP process for usage.

## CEO & Executive Fraud

The CEO will not send you an email to wire cash, the CFO won't send you a text message to ask for gift cards, or anything else that feels like CEO fraud or CEO scam. These types of spear fishing events will be more common as we grow. Feel free to verify any unusual requests with a video call.

What should you do if you receive a potential phishing email or text from IllumiDesk's CEO?

1. If you are unsure whether the text or email is legitimate, confirm the request via Video Call or contact Security to review.
2. If the email is determined to be fake, follow the instructions for phishing attacks below.
3. If the text is determined to be fake: block the number, notify Security, and delete the text.

## Security Process and Procedures for Team Members

### Accounts and Passwords

1. Read and follow the requirements for handling passwords and other credentials in the IllumiDesk Password Policy Guidelines below for all accounts used to conduct IllumiDesk related work. Using 1Password to generate and store the passwords is strongly recommended.
2. Set up your Okta account at https://IllumiDesk.okta.com, and use this as your primary means for accessing Applications supported in Okta. As part of setting up Okta, you'll need to establish a strong password and set up at least one additional form of authentication.
3. For your Okta password and other passwords that you won't store in Okta, set up 1Password as your password manager and set a **strong and unique** master password.
   * Keep your Master Password a secret. No other team members should know it, including admins. If the Master Password is known or disclosed to someone else, it should be changed immediately.
   * Post a message in \#it-ops if you forget your Master Password.
   * Consider using a generated Master Password. Most human-created passwords are easy to guess. Let 1Password create a strong Master Password. But: you _will_ need to memorize this Master Password.
   * Do not let your password manager store the **master password**. It is okay to store the username.
   * For more information, review 1Password's Getting Started guide and view this video that guides you through the sign-up process.
   * For account administrators, review 1Password's admin guide.
4. Enable two-factor authentication \(2FA\) with an authenticator, such as Google authenticator or 1Password TOTP for on every account that supports it. This is required for Google, Slack, IllumiDesk.com, and dev.IllumiDesk.org accounts. `Users without 2FA enabled that are stale for over 30 days will be blocked/suspended until resolved. This improves the security posture for both the user and` IllumiDesk`.` If any systems provide an option to use SMS text as a second factor, this is highly discouraged. Phone company security can be easily subverted by attackers allowing them to take over a phone account. _\(Ref: 6 Ways Attackers Are Still Bypassing SMS 2-Factor Authentication / 2 minute Youtube social engineering attack with a phone call and crying baby\)_
5. If you do not have a YubiKey, you may consider purchasing one. A Yubikey or other hardware token can be used as a convenient 2-factor authentication method after a first has been added to Okta, G Suite, IllumiDesk instances, and many other sites. Purchasing Yubikey is not mandatory, but is considered as an extra layer of authentication for better security.
6. When signing up for a new service on behalf of IllumiDesk:
   * Request a Security Review by opening an issue in the Compliance project.
   * If shared access is required by multiple team members to a single account, for example, a social media account, an Access Request should be opened. The credentials will be stored and shared via Okta.
7. If you find an existing shared account in 1Password, create an issue to get it migrated to Okta.

### Laptop or Desktop System Configuration

**The following instructions are for Apple \(MacBook Pro or Air\) users. Linux users please go to the Linux Tools section of the handbook.**

1. Set up **full disk encryption** with FileVault \(for details, refer to Apple Support\)
2. Set up a screen saver with **password lock** on your laptop with a timeout of 5 minutes or less.
3. Never leave your unlocked computer **unattended**. Activate the screensaver, lock the desktop, or close the lid.
4. For backups on macOS follow this tutorial: How to use Time Machine
5. If you backup your computer make sure the backup drive is encrypted and use a strong password.
6. Purchase \(if necessary\) and install security related software.
7. Little Snitch is an excellent personal firewall solution for macOS. Recommended to monitor application network communications.
8. An anti-virus/antimalware program such as Malwarebytes, ESET, or Norton.
9. Refer to Why We Don't Have A Corporate VPN for more information about personal VPN usage at IllumiDesk 
10. Do not allow your web browser \(e.g. Chrome, Safari, Firefox\) to store passwords when prompted. This presents an unnecessary risk and is redundant.
11. Do not install software with many known security vulnerabilities. At this point IllumiDesk's vendor security review scope does not include services individually deployed on endpoint devices. After a decision regarding deployment of an endpoint management solution is made the process will be redesigned accordingly and services, where applicable, will be retroactively reviewed. Please ensure you continue to follow the requirements defined in the acceptable use policy.
12. Enable automatic software updates for security patches. On macOS, this is found under "System Preferences" -&gt; "Software Update", "Automatically keep my Mac up to date".
13. Enable your system's built in firewall. In macOS, this can be found in `System Settings` -&gt; `Security & Privacy` under the `Firewall` tab. It is recommended to select "Block all incoming connections"; however, if choosing not to block all incoming traffic, apply the following configuration \(see screenshot\):
    * Deselect "Automatically allow downloaded signed software to receive incoming messages"
    * Select "Enable stealth mode"

![macOS Firewall Settings](https://about.gitlab.com/handbook/security/macos_firewall_settings.png)

### Other Services/Devices

1. Do not configure email **forwarding** of company emails \(@IllumiDesk.com\) to a non-company email address. Follow the Unacceptable Email and Communications Activities policy.
2. There are security implications involved in the use of "smart home devices" such as Amazon Echo or Google Home. In rare instances these devices can record conversations you might not have intended them to record. Many smart home devices will provide a visual and/or auditory indicator to let you know they're activated; for many such devices, when they're activated, they're recording you and save a transcript of what you say while it's active. If a smart home device is activated while you're verbalizing sensitive information, wait for it to turn off or manually turn it off. If you think a smart device may have been activated while verbalizing sensitive information, most smart home devices allow you to delete transcripts and recordings. Please use your best judgement about the placement of these devices and whether or not to deactivate the microphone during sensitive discussions related to IllumiDesk. If you ever have any questions or concerns, you can always contact the Security team.

## Security Awareness

1. Follow the guidelines for identifying phishing emails provided in the training and How to identify a basic phishing attack.
   * During the onboarding process you may receive account registration emails for your baseline entitlements. Before clicking these links feel free to confirm with \#it-ops that they initialized the process. Clicking itself is a problem even when you don't enter a password, because a visit can already be used to execute a 0-day attack. Security Team will, from time to time, simulate phishing attacks to our company email addresses to ensure everyone is aware of the threat.
2. If you get strange emails personally or other things related to security feel free to ask the security team for help, they might be aiming for the company.
3. If you receive a security report of any kind \(issue, customer ticket, etc.\) never **dismiss** it as invalid. Please bring it to the attention of the Security Team, and follow the steps outlined on that team's handbook page.
4. **Report** suspect situations to an officer of the company or use the engage the Security Oncall.
5. If you have security **suggestion**, create an issue on the security issue tracker and ping the security team. New security best practices and processes should be added to the company call agenda.
6. Do not sign in to any IllumiDesk related account using public computers, such as library or hotel kiosks.

## 

## IllumiDesk Password Policy Guidelines

Passwords are one of the primary mechanisms that protect IllumiDesk information systems and other resources from unauthorized use. Constructing secure passwords and ensuring proper password management is essential. IllumiDesk's password guidelines are based, in part, on the recommendations by NIST 800-63B. To learn what makes a password truly secure, read this article or watch this conference presentation on password strength.

### IllumiDesk team-members Password Requirements

* At IllumiDesk, we enforce a strong password requirement, which consists of minimum length of 12 characters.
* To make a secure password you can remember, consider using a combination of 5 or more random words
* The use of special characters is not required or even recommended.
* Avoid creating predictable passwords.
* Passwords cannot be reused.
* Passwords should not be the same as username.
* Passwords should be unique from the previous passwords used.

### Password Management

* Password "hints" are not to be used. If a password is forgotten, a mechanism must be in place to replace a password/passphrase with sufficient controls to verify the identity of the requester of the password reset.
* Passwords must be stored in a way that is resistant to offline attacks and must be salted and hashed using a suitable one-way key derivation function.
* If a password is required to be stored, it must be stored within an approved password manager application and may be pasted from this using a master password function \(e.g. 1Password\).
* Passwords are to be kept private and secured.
* If an account or password is suspected to have been compromised, report the incident to Security and promptly follow their instructions.
* Passwords are not to be shared or be in clear text or be written down.

### System Password Requirements

* For systems where a password can be configured the minimum password length needs to be set to 12 characters.
* To make a secure password you can remember, consider using a combination of 5 or more random words
* The use of special characters is not required or even recommended.
* If a particular system will not support 12 character passwords, then the maximum number of characters allowed by that system shall be used.
* If a particular system requires a password history, configuration should be set for 25 remembered passwords.
* Passwords are not acceptable if they match the subsequent patterns, and must be checked against commonly used or expected patterns, including known breached password lists, dictionary words, repetitive or sequential characters, or context specific words, such as the name of the service, username, or derivatives thereof.
* System administrators of applications and or devices must change default passwords.
* System administrators need to enable password strength on third party applications and or tools, where applicable.
* For applications where a password is the only source of authentication a password must be expired within a maximum of 90 calendar days.
* Systems should monitor and log failed login attempts.
* Authentication failed login attempts information needs to be recorded within the application logs such as: name, date, number of failed attempts, unique log identifier.
* Repeated failed login attempts must trigger a temporary account lockout after 10 failed attempts. The lockout may end after a designated period of time, or require a manual unlock, depending on the profile of the application.

### Application Authentication Requirements

* Authentication to an application should contain Multi-Factor authentication \(Token, OTP Generator, SSO, YubiKey/Titan or equivalent\) and or a SAML Assertion after logging into an authentication portal is recommended \(e.g., Okta\).
* Authentication to an application should support individual users, not groups.
* Acceptable secondary authentication factors include Google Authenticator or similar software implementing a One-time Password algorithm. The use of biometrics is acceptable.

### Exceptions to Password Policy

Any application that can not meet MFA and or Password requirements needs to submit an exception for the Compliance team to review. A duration of an exception is valid for 90 days followed by a proper remediation plan. After 90 days the exception will be reevaluated.

## Security Awareness Training

The IllumiDesk Security Training is IllumiDesk's security awareness presentation for new hires and annual training requirements. The training is originally part of the onboarding process, and needs to be completed by every new hire. We are trying to make it fun, engaging and not time-consuming.

The training is being actively developed by IllumiDesk Security's Security Operations team. The goal of the training is to:

1. Make all IllumiDesk team-members aware of the IllumiDesk Security team, and familiarize them with our efforts, team structure, and people.
2. Make all IllumiDesk team-members aware of the importance of their role in securing IllumiDesk on a daily basis, and to empower them to make the right decisions with security best-practices.
3. Familiarize all new IllumiDesk team-members with security-related situations that they might encounter during their tenure with the company.
4. Help all IllumiDesk team-members internalize and reinforce the idea that paging the Security On-Call is an encouraged practice.

### Training Delivery

The Security Training is delivered through a pre-recorded presentation that is presented by a member of the Security Operations team. The following materials are made available for your consumption:

* The video - the actual training.
* The slides - the slides used in the training video.
* Security Practices - a list of security process and procedures that you can consult at any time.

### Training Feedback

You are strongly encouraged to engage the team behind the training and provide feedback, or ask any questions related to the content of the training. You can do that through:

1. Monthly office hours held by the SecOps team on third Friday of each month. There are two sessions for both EMEA and APAC-friendly timeslots. Please see the IllumiDesk **Team Meetings** calendar for current times.
2. A quarterly-reviewed IllumiDesk issue - FY21-Q1.
3. Email by sending an email to security-training@IllumiDesk.com.

### Phishing Tests

IllumiDesk conducts routine phishing tests at a minimum of once per quarter. All team members may occasionally receive emails that are designed to look like legitimate business-related communications but will in actuality be simulated phishing attacks. Real phishing attacks are designed to steal credentials or trick the recipient into downloading or executing dangerous attachments. No actual attempts will be made by IllumiDesk to steal credentials or execute malicious code.

The goal of these campaigns is not to catch people clicking on dangerous links or punish those who do, but rather to get people thinking about security and the techniques used by attackers via email to trick you into running malicious software or disclosing web passwords. If you fall victim to one of these simulated attacks feel free to take the training courses again or to ask the security team for more information on what could've been done to recognize the attack. What you shouldn't do is feel any shame for having clicked on the link or entered any data, nor should you feel like you need to _cop_ to the security team and let them know you made a mistake. Making a mistake online is practically the reason the Internet was invented.

#### How to identify a basic phishing attack

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

#### What to do if you suspect an email is a phishing attack

Whether you believe that you have received an email from our testing platform or you suspect that the email is targeted specifically at you or IllumiDesk, please forward the phishing email to `phishing@`IllumiDesk`.com` as an attachment for it to be investigated. Once you have done so, please proceed to step 2 and report the email as phishing from inside GMail.

To forward the email as an attachment from inside GMail:

1. Right click the email
2. Select "Forward as attachment"
3. Send it to `phishing@`IllumiDesk`.com`

GMail also offers the option to report the email directly to Google as a phishing attempt, which will result in its deletion. Reporting the email in this manner will help the security team track phishing metrics and trends over time within G Suite.

To report the email as `phishing` from inside GMail:

1. Select the "More" button \(three dots\) on the email in question
2. Choose "Report phishing" option from the drop down menu

If you receive an email that appears to come from a service that you utilize, but other details of the email are suspicious – a private message from a sender you don't recognize, for example – do not click on any links in the email. Instead use your own bookmark for the site or manually type the address of the website into your browser.

Unsolicited email should be treated as phishing emails. For example, if you did not register for a site claiming to send you email, do not click on links in the email or visit the site.

### Using the panic email address

IllumiDesk provides a `panic@illumidesk.com` email address for team members to use in situations that require an immediate security response. Should a team member lose a device such as a thumb drive, mobile phone, tablet, laptop, etc. that contains their credentials or other IllumiDesk-sensitive data they should send an email to `panic@illumidesk.com` right away. When the production and security teams receive an email sent to this address it will be handled immediately. Using this address provides an excellent way to limit the damage caused by a loss of one of these devices.

#### Checklist for when `panic` is triggered

The following can be adapted depending on the specific situation at hand, but when in doubt: block. It is less risky to reinstate accounts and permissions than to be confronted with a malicious actor gaining access.

Copy this checklist into a confidential issue.

```text
- [ ] Password Access and Rotation
   - [ ] Suspend 1Password account. (All responders to `panic@` should be members of the "Panic@ Responders" group in 1Password which has the rights to suspend and recover user accounts).
   - [ ] Take screenshot of what groups / vaults the individual had access to. This facilitates the next step.
   - [ ] Coordinate or actively change sensitive shared passwords. In particular sysadmin access passwords for IllumiDesk.com Infrastructure (ssh, chef user/key, discuss others).
- [ ] Block Google account
- [ ] Block Slack account
- [ ] Block [dev.IllumiDesk.org account](https://dev.IllumiDesk.org/admin/users).
- [ ] Remove IllumiDesk.com account from the [IllumiDesk-org group](https://IllumiDesk.com/groups/IllumiDesk-org/group_members)
- [ ] Block access to hackerone.com
- [ ] Block access to Tweetdeck
```

