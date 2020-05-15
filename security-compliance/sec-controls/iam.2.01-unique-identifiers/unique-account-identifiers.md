# Unique Account Identifiers

Every service and application must use unique identifiers for user accounts and prevent the re-use of those identifiers.

For example, if a user account is identified with a username, there can only be one account with that username. Accounts may eventually be deleted and that username \(or other unique identifier\) intentionally released for re-use, but that new account may not have the same permissions or access as the first account that was deleted. This doesn't preclude the use of shared accounts \(except where it is strictly forbidden, like in-scope PCI systems\) and applies to both individual and shared accounts. If a shared account is used, that account must have a unique identifier in the same way an individual, non-shared account does.

This is required to allow the actions of any given account to be associated back with that particular account. If two accounts share an identifier, if a malicious action were taken, we'd have no way of identifying which of the two accounts performed that malicious action. It's also important to preserve the confidentiality of information; if access or permission are given to an account, they should only be given to the specific account for which they were intended.

