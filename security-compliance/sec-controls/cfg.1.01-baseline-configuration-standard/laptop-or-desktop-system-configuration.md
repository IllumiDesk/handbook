# Laptop or Desktop System configuration



#### Laptop or Desktop System Configuration <a id="laptop-or-desktop-system-configuration"></a>

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

#### Other Services/Devices <a id="other-servicesdevices"></a>

1. Do not configure email **forwarding** of company emails \(@IllumiDesk.com\) to a non-company email address. Follow the Unacceptable Email and Communications Activities policy.
2. There are security implications involved in the use of "smart home devices" such as Amazon Echo or Google Home. In rare instances these devices can record conversations you might not have intended them to record. Many smart home devices will provide a visual and/or auditory indicator to let you know they're activated; for many such devices, when they're activated, they're recording you and save a transcript of what you say while it's active. If a smart home device is activated while you're verbalizing sensitive information, wait for it to turn off or manually turn it off. If you think a smart device may have been activated while verbalizing sensitive information, most smart home devices allow you to delete transcripts and recordings. Please use your best judgement about the placement of these devices and whether or not to deactivate the microphone during sensitive discussions related to IllumiDesk. If you ever have any questions or concerns, you can always contact the Security team.

#### Security Awareness <a id="security-awareness"></a>

1. Follow the guidelines for identifying phishing emails provided in the training and How to identify a basic phishing attack.
   * During the onboarding process you may receive account registration emails for your baseline entitlements. Before clicking these links feel free to confirm with \#it-ops that they initialized the process. Clicking itself is a problem even when you don't enter a password, because a visit can already be used to execute a 0-day attack. Security Team will, from time to time, simulate phishing attacks to our company email addresses to ensure everyone is aware of the threat.
2. If you get strange emails personally or other things related to security feel free to ask the security team for help, they might be aiming for the company.
3. If you receive a security report of any kind \(issue, customer ticket, etc.\) never **dismiss** it as invalid. Please bring it to the attention of the Security Team, and follow the steps outlined on that team's handbook page.
4. **Report** suspect situations to an officer of the company or use the engage the Security Oncall.
5. If you have security **suggestion**, create an issue on the security issue tracker and ping the security team. New security best practices and processes should be added to the company call agenda.
6. Do not sign in to any IllumiDesk related account using public computers, such as library or hotel kiosks.

### IllumiDesk Password Policy Guidelines <a id="gitlab-password-policy-guidelines"></a>

Passwords are one of the primary mechanisms that protect IllumiDesk information systems and other resources from unauthorized use. Constructing secure passwords and ensuring proper password management is essential. IllumiDesk's password guidelines are based, in part, on the recommendations by NIST 800-63B. To learn what makes a password truly secure, read this article or watch this conference presentation on password strength.

#### IllumiDesk team-members Password Requirements <a id="gitlab-team-members-password-requirements"></a>

* At IllumiDesk, we enforce a strong password requirement, which consists of minimum length of 12 characters.
* To make a secure password you can remember, consider using a combination of 5 or more random words
* The use of special characters is not required or even recommended.
* Avoid creating predictable passwords.
* Passwords cannot be reused.
* Passwords should not be the same as username.
* Passwords should be unique from the previous passwords used.

#### Password Management <a id="password-management"></a>

* Password "hints" are not to be used. If a password is forgotten, a mechanism must be in place to replace a password/passphrase with sufficient controls to verify the identity of the requester of the password reset.
* Passwords must be stored in a way that is resistant to offline attacks and must be salted and hashed using a suitable one-way key derivation function.
* If a password is required to be stored, it must be stored within an approved password manager application and may be pasted from this using a master password function \(e.g. 1Password\).
* Passwords are to be kept private and secured.
* If an account or password is suspected to have been compromised, report the incident to Security and promptly follow their instructions.
* Passwords are not to be shared or be in clear text or be written down.

#### System Password Requirements <a id="system-password-requirements"></a>

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

#### Application Authentication Requirements <a id="application-authentication-requirements"></a>

* Authentication to an application should contain Multi-Factor authentication \(Token, OTP Generator, SSO, YubiKey/Titan or equivalent\) and or a SAML Assertion after logging into an authentication portal is recommended \(e.g., Okta\).
* Authentication to an application should support individual users, not groups.
* Acceptable secondary authentication factors include Google Authenticator or similar software implementing a One-time Password algorithm. The use of biometrics is acceptable.

#### Exceptions to Password Policy <a id="exceptions-to-password-policy"></a>

Any application that can not meet MFA and or Password requirements needs to submit an exception for the Compliance team to review. A duration of an exception is valid for 90 days followed by a proper remediation plan. After 90 days the exception will be reevaluated.

### 1Password Guide <a id="1password-guide"></a>

1Password is a password manager. Ideally you memorize one strong password - hence the name - and let 1Password generate and manage strong, unique passwords for every site for which you have a login.

#### Terminology <a id="terminology"></a>

Following this guide, it will be helpful to understand a few terms we'll be using throughout.

* **App:** A native 1Password application \(macOS, iOS, Windows, Android\).
* **Extension:** A web browser extension/plugin that communicates with the **App** to provide access to your passwords securely without leaving the browser.
* **Vault:** What 1Password calls any grouping of secure data, such as logins or secure notes. Sometimes called a "keychain".

#### 1Password <a id="1password"></a>

1Password can be used in two different ways - as a standalone application \(by purchasing a standalone license\) or as a hosted service \(by subscribing\). IllumiDesk uses 1Password for Teams which is a hosted service.

IllumiDesk is transitioning to use Okta as a primary entry and access point for SaaS and other company applications. This does not mean that 1Password will be deprecated completely, but it is preferred that, where possible, you use Okta as your primary entry point into applications. IllumiDesk will be using Okta for SAML/SSO and passwordless authentication for many applications, so the need to store passwords in a password manager will diminish over time.

If you want to use 1Password for your private passwords not related to your work at IllumiDesk, there are a few options.

#### 1Password Guidelines <a id="1password-guidelines"></a>

1. If you install the macOS application, install 1Password via the Mac App Store to ensure a more secure update process.
2. If you have a YubiKey or other hardware token, it can be added as a 2-factor method to your 1Password account for convenience.
3. When traveling, consider using 1Password in "Travel Mode", see more on that below.
4. Do not share credentials via email, issue comments, chat etc. This includes email addresses to login and API keys. Use 1Password vaults for this.
5. If you do not have access to a vault that is part of the baseline entitlements for your role and team, mention IllumiDesk`-com/business-ops/itops` in your onboarding issue or in \#it-ops on slack. For all other access, create an access request issue.
6. Use Watchtower to find passwords that need to be changed. Watchtower tells users about password breaches and other security problems on the websites they have saved in 1Password Teams, so users can take action. This is not something account administrators can review for team members, so it is up to you to enable! Enable Watchtower by going to your 1Password app and then to **Preferences &gt; Watchtower**.
7. Use the "Security Audit" functionality of 1Password meet the password policy. It will report reused passwords, weak passwords, accounts that are missing 2-factor authorization, and so forth that can then be fixed.
8. Do not copy passwords from inside a 1Password vault to a personal password vault or other password store. 1Password should be the only password vault used for teams. Team passwords should not be duplicated or placed in personal password vaults where they can potentially be exposed to compromise.
9. When asked security questions \(what is your favorite pet, etc.\) do not answer truthfully since that is easy to research. Make up an answer and write both the question and answer in 1Password. Consider using the Password Generator function in 1Password for this.
10. During offboarding, your 1Password account is deleted, which includes the **Private** vault in the IllumiDesk team account. If you want to keep your personal passwords, please copy/move them to your **Primary** vault which you will have if you signed up for an individual account before joining the IllumiDesk Team account.
11. **Deprecated** When documenting the location of shared credentials in the handboook refer to the items with NAME\_OF\_SITE credentials in VAULT\_NAME. For example: "for access please see the AOL credentials in the Luddite vault".
    * Deprecation note: This is for existing accounts only. New accounts should be created by creating an issue to add it to Okta.

#### 1Password for Teams <a id="1password-for-teams"></a>

1Password for Teams stores all **Vaults** on the 1Password servers and allows for sharing between multiple people on the same team.

Everyone at IllumiDesk should already be signed up for our Teams account. This gives you access to the web interface, allowing you to view the Vaults we've configured and given you access to.

In addition to the shared **Team** vault, each member of the team has a vault called **Private** which _only you can see_, and allows you to store personal credentials _within our team's account_. See the Google sheet titled "1Password Shared Folders" in Google Drive to see a listing of the available vaults and which groups or individuals have access to them. If you need access to a vault beyond the access that your onboarding process already gave you, please make a comment in the sheet and ping one of the 1Password admins in the comment. A listing of the 1Password admins can be found in a secure note in the Team vault in 1Password.

To really get the full benefit of 1Password, you'll need to hook our Teams account up to one of the native apps.

#### Adding the IllumiDesk Team to a 1Password app <a id="adding-the-gitlab-team-to-a-1password-app"></a>

This guide will cover setting up the macOS app. It's their lead platform and is the most up-to-date. These instructions may or may not work for the Windows version. If you use 1Password 6 without a 1Password.com account, make note of this.

1. Download and install the 1Password macOS app.
2. Launch the app.
3. Click "Sign in to your 1Password account" button. If there is no such button please follow the instructions for updating 1Password.

Now you'll need the **Emergency Kit** PDF that 1Password told you to save when you registered your **Teams** account. Note: Store the Emergency Kit safely. Store a copy of the Emergency Kit on a USB flash drive or print a copy and store it in a vault at home or safe deposit box — somewhere not online or accessible by anyone other than yourself.

If you saved it as a digital PDF file:

1. Open the PDF file
2. Click **Scan QR Code**
3. Drag the scanner window over the QR code on the PDF sheet

If you printed the PDF:

1. Click **Sign In Manually**
2. For **Team URL** enter IllumiDesk**.1password.com**
3. For **Account Key** enter the Account Key from your Emergency Kit
4. For **Email Address** enter your `@`IllumiDesk`.com` email
5. For **Master Password** enter the password to your **Teams** account \(_not_ the password you created above when you chose "I'm a new user"\)

After the Team is added, you should see some notifications about vaults being added to 1Password. By default you'll have the **Private** vault, but may have access to others. It should be part of your onboarding process to be granted access to the **Team** vault, so it might not appear straight away. If in doubt, get in touch with the person responsible for onboarding you to make sure you're granted access.

#### Adding the IllumiDesk Team to a 1Password account-less installation <a id="adding-the-gitlab-team-to-a-1password-account-less-installation"></a>

If you already have a non-account based license for 1Password, you can still add the IllumiDesk Team to your current account, but there are a few peculiarities:

1. The Master Password you create for your new IllumiDesk Team account is distinct from your current local vault Master Password, but you will still be able to access all vaults in the macOS app, local and IllumiDesk, with your existing local vault password.
2. You will _not_ be able to log into 1Password.com using your local Master Password. If you choose to set up 1Password this way, please do print out your IllumiDesk  account recovery sheet with your new Master Password and store it somewhere secure, because you'll need it to access your team account online or recover the account, even if you use your local Master Password in day-to-day usage. IllumiDesk cannot recover your account if your account-specific Master Password is lost.
3. It is possible to set up your IllumiDesk  account with any of your email aliases, but each can only be used one time. People Ops Specialists and security will need to set it up as an additional account, so coordinate with them.

#### Updating 1Password to support the Teams feature <a id="updating-1password-to-support-the-teams-feature"></a>

_Read this section only if you could not follow the instructions in "Adding the_ IllumiDesk _Team to a 1Password app" section._

1. At the prompt, choose "I'm a new user". _Note:_ This is one source of confusion. "I created my Teams account, I'm not new!" Just go with it.
2. Enter a master password, confirmation, and hint. This can \(and should\) be different from the password you used for our **Teams** account. This password gates access to your **local, private** Vault on your computer and/or phone.
3. Skip over the remaining dialogs \(syncing, newsletter, etc.\)
4. You should now have an empty vault called **Primary**.

Because the Teams feature is not available in your current version of 1Password, we need to update the app to the latest version:

1. Go to **Preferences**
2. Go to **Updates**
3. Click **Check Now**
4. Install the update and relaunch
5. After relaunch, go to **Preferences** again
6. Go to **Accounts**
7. Click the **+** icon

#### Vaults <a id="vaults"></a>

Click the **Vault Selector** in the upper-left corner of the window:

**Team** is a vault that everyone on the IllumiDesk Teams account has access to, both read and write.

**Private** is your _hosted, private_ vault that is part of the IllumiDesk 1Password for Teams account. Since the Private vault is part of the IllumiDesk  Teams account, it should be thought of as company property \(like the @IllumiDesk.com email account\), however the vault _can not_ be viewed by anyone else on the team, including admins. If you choose to store truly personal information in the Private vault, it opens up the possibility that you would be separated from this information if you offboard. Such truly personal information is therefore better to store in your **Primary** vault, which is associated with you instead of with the IllumiDesk Teams account, assuming that you added an individual account.

#### Browser Extension <a id="browser-extension"></a>

It can be confusing having 1Password's browser extension and Okta's browser plugin working at the same time. It is not recommended to install both the 1Password browser plugin and Okta's browser plugin on the same browser.

Go to Browser extensions and install the extension for whatever browser you're using. You _should not_ need a beta version here.

With the extension installed, you should be able to go to a site that has credentials stored in our Team vault and log in:

![Mailchimp Login](https://about.gitlab.com/handbook/security/1password-login.gif)

If you don't see the site listed in the results window, make sure you're using the correct vault:

![Vault switching](https://about.gitlab.com/handbook/security/1password-vault-change.gif)

#### Saving Logins <a id="saving-logins"></a>

When 1Password detects a login form submission, it may ask if you want to save the login with a dialog like this:

![Save login](https://about.gitlab.com/handbook/security/1password-save-login.png)

If you do want to save it, make sure the appropriate **Vault** is selected first.

#### Several accounts and unlocking the app <a id="several-accounts-and-unlocking-the-app"></a>

Please refer to 1Password FAQ.

If you are planning to use both the IllumiDesk team account and a separate individual account you should first add your separate individual account to the app first \(Preferences &gt; Accounts\). By doing this you will be able to unlock the 1Password app using the Master Password of the individual account.

If you were using 1Password before joining IllumiDesk, and you receive a prompt titled **Migrate To Account**, choose **I'll move later**. There is no harm in doing this, and it is easy to move items between vaults.

#### 1Password for your private passwords <a id="1password-for-your-private-passwords"></a>

You are encouraged to use 1Password for your private passwords, not related to your work at IllumiDesk. This makes it less likely for a security breach to occur. You can purchase a standalone license or start an individual subscription. While under the IllumiDesk team subscription, it is also possible to create and use a 'Private' vault \(same features of a standalone license, without the cost, but you will lose access if you go through offboarding\).

Please bear in mind that if you decide to purchase a standalone license or create a personal local vault, your data is stored only in a local folder on your computer. You can optionally sync this folder to Dropbox or iCloud \(if you are using a Mac/iOS\) to make it available on your phone's 1Password app, or on another computer.

Signing up for a subscription seems to be the solution now recommended by AgileBits \(the company behind 1Password\).

To create a personal local vault:

1. Go to **Preferences**
2. Go to **Advanced**
3. Under **Local Vaults**, check **Allow creation of vaults outside of 1Password accounts**
4. Enter your Master Password
5. A new local vault \(**Primary**\) is created outside the IllumiDesk team account
6. If you want to set up sync for your new local vault, go to **Preferences &gt; Sync**

#### Two Factor Authentication and Time-based One Time Passwords <a id="two-factor-authentication-and-time-based-one-time-passwords"></a>

All IllumiDesk team-members should use two factor authentication \(2FA\) whenever possible.

1Password provides an alternative solution that does not require using your smartphone: 1Password Time-based One Time Passwords \(TOTP\). 2FA codes are displayed directly in the 1Password app running on your laptop \(Note: this can not be set up via 1Password browser extension or 1Password web app\).

1Password TOTP is compatible with Okta, as it uses the same algorithm as Google Authenticator.

To enable TOTP for a saved account:

1. Open 1Password app
2. Go to the item for which you want to set up TOTP
3. Click **Edit** in the bottom right corner
4. Add a new field ![Add new field](https://about.gitlab.com/handbook/security/1password-add-new-field.png)
5. Click the field type dropdown \(it offers a "Text field" by default\) ![Field type dropdown](https://about.gitlab.com/handbook/security/1password-select-field-type.png)
6. Select **One-Time Password** ![One-time password field type](https://about.gitlab.com/handbook/security/1password-totp.png)
7. Click QR code icon that appeared
8. Scan QR code using the transparent window
9. Click **Save**
10. 2FA code should be displayed now

Please refer to demo video 1password TOPT setup

Please refer to the 1Password blog for more information on how TOTP works.

If scanning the QR code using the "transparent window" with the 1Password Mac app fails on a recent macOS, please consider using the 1Password iOS app instead. This mechanism works the same way, and supports Touch ID to login.

While the above 1Password default recommendation applies to all IllumiDesk team-members, there are alternative, although more complex solutions that can also be used. Google Authentication is a TOTP solution that can be used to store tokens, for those who want to have separate application for password storage and token storage. However, be aware that using two applications is more complex, and not necessary. If unsure which mechanism to use, we recommend using 1Password as a TOTP for 2FA.

Follow this guideline when getting a new mobile device, if you are using Google Authenticator as a TOTP mechanism.

**Setting Up 1Password TOTP for Your** IllumiDesk **Google Account**

1. Navigate to myaccount.google.com.
2. In the left-side menu, select "Security".
3. Under "Signing into Google", click on the option for 2-Factor Authentication.
4. Click "Get Started"
5. Enter your password to log in to your account. If you are unable to do this and Google says it is because the account requires 2FA, contact the security team and ask them to make an exception for your account.
6. Once successfully logged in, on the following page select "Choose another option" and then select "text message or voice call" from the dropdown menu.
7. Enter your mobile phone number and select your preferred method \(text or call\), and then click "Next".
8. Enter the code that you receive and click "Next".
9. On the following page, click "Turn On". Now 2FA is enabled for your Google account.
10. On the following page, scroll down to the section titled, "Set up alternative second step". From this list, select "Authenticator app" setup.
11. This will present a QR code. Open the 1Password desktop or mobile app, and navigate to your IllumiDesk email/Google login. Select edit.
12. On the edit page, select "Add new section" and title it One-time password \(or something else of your choosing\), and then select "Add new field", and choose "One-Time Password" from the dropdown menu.
13. Tap or click the small QR code that appears next to your newly created field. A QR scanner will open up. Use the scanner to read the QR code that Google is presenting \(from step 11\).
14. Tap or click Done within 1Password to save the edits. Keep 1Password open.
15. Within your Google settings, click "Next". Now enter the six-digit code that has appeared in the One-time password field that you have just sent up in 1Password. Once the code is entered, click "Verify". Google should present a "Done!" message. You have now set up TOPT for your Google account! Nice work.

#### Example Usage <a id="example-usage"></a>

This is an example of how Robert, one of our developers, uses 1Password:

> Once you fully commit to using 1Password to manage all of your security information, it really does make life easier.
>
> I memorize one strong password and let the app generate everything else. Every site I use has a unique password that I can't compromise because I don't even know it, and a hacked site can't compromise it because the password is never re-used on another site.
>
> I store my shipping and credit card info in 1Password and use the browser extension to quickly fill out shipping and billing information on shopping sites.
>
> I store my passport data, along with a digital scan, in 1Password; driver's license info and scan; insurance info; software license keys; any important information that needs to be secure but still easily accessible when I need it, from anywhere. I sync my personal vault to my personal iCloud so it's available on my phone, tablet, laptop, and desktop.
>
> Even my 1Password for Teams account information is stored in my personal **Primary** vault, with the Emergency Kit PDF as a secure attachment:
>
> ![Teams Login](https://about.gitlab.com/handbook/security/1password-teams-login.png)
>
> I have no idea what the password is. I've never actually typed it. And that's the idea.

#### Traveling with 1Password <a id="travel-mode"></a>

When traveling with a device that has access to the IllumiDesk 1Password vaults, be sure to enable Travel Mode in 1Password. Travel Mode removes copies of any 1Password vaults that are not tagged as "safe for travel" from your mobile devices. None of the IllumiDesk team vaults are marked as safe for travel so you will need to either create a dedicated travel vault or mark your Private vault as safe for travel.

Once you have enabled Travel Mode open 1Password on each device you will be taking with you so that it can sync with 1Password.com and remove any vaults that cannot be used while traveling.

For more information on Travel Mode and how it works, see the AgileBits blog.

### Security Awareness Training <a id="security-awareness-training"></a>

The IllumiDesk Security Training is IllumiDesk's security awareness presentation for new hires and annual training requirements. The training is originally part of the onboarding process, and needs to be completed by every new hire. We are trying to make it fun, engaging and not time-consuming.

The training is being actively developed by IllumiDesk Security's Security Operations team. The goal of the training is to:

1. Make all IllumiDesk team-members aware of the IllumiDesk Security team, and familiarize them with our efforts, team structure, and people.
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
3. Email by sending an email to security-training@IllumiDesk.com.

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

### Using the panic email address <a id="panic-email"></a>

IllumiDesk provides a `panic@`IllumiDesk`.com` email address for team members to use in situations that require an immediate security response. Should a team member lose a device such as a thumb drive, YubiKey, mobile phone, tablet, laptop, etc. that contains their credentials or other IllumiDesk-sensitive data they should send an email to `panic@`IllumiDesk`.com` right away. When the production and security teams receive an email sent to this address it will be handled immediately. Using this address provides an excellent way to limit the damage caused by a loss of one of these devices.

#### Checklist for when `panic` is triggered <a id="checklist-for-when-panic-is-triggered"></a>

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

