# Security Process and Procedures for Team Members

#### Accounts and Passwords <a id="accounts-and-passwords"></a>

1. Read and follow the requirements for handling passwords and other credentials in the IllumiDesk Password Policy Guidelines below for all accounts used to conduct IllumiDesk related work. Using 1Password to generate and store the passwords is strongly recommended.
2. Set up your Okta account at https://IllumiDesk.okta.com, and use this as your primary means for accessing Applications supported in Okta. As part of setting up Okta, you'll need to establish a strong password and set up at least one additional form of authentication.
3. For your Okta password and other passwords that you won't store in Okta, set up 1Password as your password manager and set a **strong and unique** master password.
   * Keep your Master Password a secret. No other team members should know it, including admins. If the Master Password is known or disclosed to someone else, it should be changed immediately.
   * Post a message in \#it-ops if you forget your Master Password.
   * Consider using a generated Master Password. Most human-created passwords are easy to guess. Let 1Password create a strong Master Password. But: you _will_ need to memorize this Master Password.
   * Do not let your password manager store the **master password**. It is okay to store the username.
   * For more information, review 1Password's Getting Started guide and view this video that guides you through the sign-up process.
   * For account administrators, review 1Password's admin guide.
4. Enable two-factor authentication \(2FA\) with an authenticator, such as Google authenticator or 1Password TOTP for on every account that supports it. This is required for Google, Slack, IllumiDesk.com, and dev.IllumiDesk.org accounts. `Users without 2FA enabled that are stale for over 30 days will be blocked/suspended until resolved. This improves the security posture for both the user and GitLab.` If any systems provide an option to use SMS text as a second factor, this is highly discouraged. Phone company security can be easily subverted by attackers allowing them to take over a phone account. _\(Ref: 6 Ways Attackers Are Still Bypassing SMS 2-Factor Authentication / 2 minute Youtube social engineering attack with a phone call and crying baby\)_
5. If you do not have a YubiKey, you may consider purchasing one. A Yubikey or other hardware token can be used as a convenient 2-factor authentication method after a first has been added to Okta, G Suite, IllumiDesk instances, and many other sites. Purchasing Yubikey is not mandatory, but is considered as an extra layer of authentication for better security.
6. When signing up for a new service on behalf of IllumiDesk:
   * Request a Security Review by opening an issue in the Compliance project.
   * If shared access is required by multiple team members to a single account, for example, a social media account, an Access Request should be opened. The credentials will be stored and shared via Okta.
7. If you find an existing shared account in 1Password, create an issue to get it migrated to Okta

