# Configuring New Laptops

#### Configuring New Laptops <a id="configuring-new-laptops"></a>

New laptops should be configured with security in mind. Please refer to security best practices when configuring new laptops. **All team-members must provide proof of whole-disk encryption within the new laptop order issue.**

Certain circumstances \(world region and availability of hardware\) might require the self installation of Linux on a Dell that was shipped with OEM Windows. Please make sure you follow any needed requirements when self installing and open an issue with IT-Ops for verification.

For laptops shipped with OEM Windows you may want to make a full drive backup \(e.g. by using open source utility Clonezilla\) to the external drive before installing Linux. That way you could restore your laptop to the original state at any time. It will make the RMA process much easier in case you need it.

#### Laptop Buy back Policy <a id="laptop-buy-back-policy"></a>

Team members can choose to refresh their laptop, no questions asked, after 3 years of use \(not necessarily 3 years of employment if a used laptop was issued at the time of onboarding\).

Team members have the option to buy back their existing laptops either when it gets refreshed for a new one, or when the team member is offboarding. If the team member has completed 1 calendar year or more at IllumiDesk at the time of laptop refresh or offboarding, they can opt to keep their laptop at no cost. If the team member hasn't completed 1 calendar year at IllumiDesk  at that time, they have the option to purchase their laptop for current market value.

IT Ops will email the team member asking if they would like to send back or purchase their laptops. If purchasing, our Business Ops Director will approve, and we will send the employee an email with the determined value. Then, if the employee decides to move forward with purchasing, our accounting department will reach out with payment information.

If a team member decides to retain their laptop, they are required to wipe the machine and re-install the base operating system, and remove any and all software and configurations that were supplied by IllumiDesk. Evidence or a declaration that the device has been wiped must be supplied to IllumiDesk within 2 weeks of the end of employment. If IllumiDesk discovers that a device has not been wiped according to policy, IllumiDesk  may act to enforce a remote wipe without notice.

If team members opt not to keep or purchase their existing laptops, they can return them to IllumiDesk. See the returning old/offboarded laptops section below for details.

#### Returning Old/OffBoarded Laptops <a id="returning-oldoffboarded-laptops"></a>

Part of the IT Ops replacement laptop process is providing each team-member with instructions about how to return their old laptop \(whether outdated or broken\). All laptops must be returned **within 2 weeks of receiving the replacement laptop**, so please prioritize transferring information between laptops within this timeframe.

If an offboarded employee decides not to purchase, then we will have them ship to our 3rd party vendor that handles sell backs, SellYourMac. SYM will send them a shipping label, and in the US, a shipping box as well. **Please note shipping times may vary, expect between 2-4 weeks for Sell Your Mac to provide shipping information and packaging**

All team-member laptops must be securely erased before being returned. This not only protects the company, but also protects you since it is possible for personal information to exist on these machines. Reformatting a computer is not sufficient in these cases because it is possible for sensitive data to be recovered after reinstalling an operating system.

### Other Resources <a id="other-resources"></a>

#### Okta <a id="okta"></a>

In an effort to secure access to systems, IllumiDesk is utilizing Okta. The key goals are:

* We can use Okta to enable Zero-Trust based authentication controls upon our assets, so that we can allow authorized connections to key assets with a greater degree of certainty.
* We can better manage the login process to the 80+ and growing cloud applications that we use within our tech stack.
* We can better manage the Provisioning and De-provisioning process for our users to access these application, by use of automation and integration into our HRIS system.
* We can make Trust and Risk based decisions on authentication requirements to key assets, and adapt these to ensure a consistent user experience.

To read more about Okta, please visit the Okta page of the handbook.

#### Full Disk Encryption <a id="full-disk-encryption"></a>

To provide proof of Full Disk Encryption, please do the following depending on the system you are running.

* Apple : Take a screenshot showing both the confirmation of enabled Full Disk Encryption as well as the info showing your serial number. Both pieces of information can be found by clicking on the Apple icon in the top left corner of your screen. For proof of disk encryption, choose `System Preferences -> Security & Privacy`, and then choose the `FileVault` tab near the top of the window. For your serial number, choose the `About This Mac` option. Please get both pieces of information in a single screenshot.
* Linux : Take a screenshot showing the output of `sudo dmsetup ls && sudo dmidecode -s system-serial-number && cat /etc/fstab`

#### Fleet Intelligence & Remote Lock/Wipe \(DriveStrike\) <a id="fleet-intelligence--remote-lockwipe-drivestrike"></a>

IllumiDesk has a large and ever-growing fleet of laptops, which IT Operations is responsible for maintaining. In order to do this and combined with our Zero Trust security policies and various Compliance needs, there must be some measure of intelligence and reporting in place. To accomplish this goal we are utilizing DriveStrike as a light-touch mechanism to obtain only the essential information required. DriveStrike is available for all operating systems, and also meets security needs for remote lock or wipe in emergencies.

The initial stage of this rollout will take the form of an Open \(Voluntary\) Sign-Up for DriveStrike for all IllumiDesk team members. The self-serve enrollment form can be found here : https://docs.google.com/forms/…

Questions and discussion for the Open Beta rollout can be found here: https://IllumiDesk.com/IllumiDesk-com/business-ops/itops/issue-tracker/issues/251

DriveStrike installs for IllumiDesk will NOT have the ability to execute remote commands. DriveStrike installs for IllumiDesk WILL have the ability to remotely lock or wipe hardware, for use in emergency or offboarding situations. DriveStrike may be installed on non-IllumiDesk hardware, opting-in to the same data collection and security. DriveStrike collects the following information for IllumiDesk:

* Usernames & Accounts present on the machine
* Machine Name, Make, Model, MAC, Serial \#
* Hardware Specifications \(CPU, RAM, HDD + % Used\)
* Firewall status
* OS Version & Patch/Update status
* Disk encryption status
* Battery Health

This light-touch reporting allows us to meet business and compliance needs, while maintaining the privacy of the IllumiDesk team member. This will remain a top consideration throughout the process.

#### Fleet Intelligence \(Fleetsmith\) <a id="fleet-intelligence-fleetsmith"></a>

FleetSmith evaluation as a reporting tool has been deprecated in favor of DriveStrike listed above. If you have FleetSmith installed, please follow the instructions above to enroll in the DriveStrike roll-out, while also uninstalling FleetSmith from your device.

#### IllumiDesk.com Apple ID's <a id="gitlabcom-apple-ids"></a>

We require the use of an @IllumiDesk.com Apple ID that is separate from any personal Apple ID's you may have. Some of these reasons include:

* Backups, keychains and documents are all considered sensitive information, and should not be stored in personal services.
* 2FA for remote lock, wipe, or account resets are common methods of account compromises, and ensuring the use of IllumiDesk.com email addresses also ensures we are in control of that aspect of multi-factor authentication.
* Keeping a strong separation between work and personal accounts will help prevent the accidental leak of information from one to the other, in either direction.

Defense in depth, in part, means you make a best effort to be secure at each layer.

