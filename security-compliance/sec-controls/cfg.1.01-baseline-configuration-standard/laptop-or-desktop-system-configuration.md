# Laptop or Desktop System configuration

## Laptop or Desktop System Configuration

{% hint style="info" %}
The following instructions are for Apple \(MacBook, MacBook Pro or MacBook Air\) users. All IllumiDesk collaborators use MacBooks.
{% endhint %}

1. Set up **full disk encryption** with FileVault \(for details, refer to Apple Support\)
2. Set up a screen saver with **password lock** on your laptop with a timeout of 5 minutes or less.
3. Never leave your unlocked computer **unattended**. Activate the screensaver, lock the desktop, or close the lid.
4. For backups on macOS follow this tutorial: How to use Time Machine
5. If you backup your computer make sure the backup drive is encrypted and use a strong password.
6. Purchase \(if necessary\) and install security related software.
7. Little Snitch is an excellent personal firewall solution for macOS. Recommended to monitor application network communications.
8. An anti-virus/anti-malware program such as McAfee or Norton.
9. Refer to Why We Don't Have A Corporate VPN for more information about personal VPN usage at IllumiDesk 
10. Do not allow your web browser \(e.g. Chrome, Safari, Firefox\) to store passwords when prompted. This presents an unnecessary risk and is redundant.
11. Do not install software with many known security vulnerabilities. At this point IllumiDesk's vendor security review scope does not include services individually deployed on endpoint devices. After a decision regarding deployment of an endpoint management solution is made the process will be redesigned accordingly and services, where applicable, will be retroactively reviewed. Please ensure you continue to follow the requirements defined in the acceptable use policy.
12. Enable automatic software updates for security patches. On macOS, this is found under "System Preferences" -&gt; "Software Update", "Automatically keep my Mac up to date".
13. Enable your system's built in firewall. In macOS, this can be found in `System Settings` -&gt; `Security & Privacy` under the `Firewall` tab. It is recommended to select "Block all incoming connections"; however, if choosing not to block all incoming traffic, apply the following configuration \(see screenshot\):
    * Deselect "Automatically allow downloaded signed software to receive incoming messages"
    * Select "Enable stealth mode"

![macOS Firewall Settings](https://about.gitlab.com/handbook/security/macos_firewall_settings.png)

## Other Services/Devices

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

