# Data Classification Policy

Data classification provides a way to categorize organizational data based on levels of sensitivity. The purpose of this policy is to establish a framework for classifying data based on its sensitivity, value and criticality to the organization. By understanding what data types are available, classification and access levels, you can map the appropriate access/protection of the data. This ensures that sensitive corporate and customer data can be secured appropriately.

## Scope

The IllumiDesk Data Classification Policy applies to all data handled, managed, stored, or transmitted by IllumiDesk and IllumiDesk team members, including that which is submitted to IllumiDesk Support as part of a support request.

## Roles and Responsibilities

Everyone at IllumiDesk is responsible to review, adhere to and handle data according to the classification levels below. The Data Classification Index \(internal only\) provides a list of various types of data and their classification level. If you cannot identify the data element or are uncertain of the risk associated with the data and how it should be classified and handled, please contact The Compliance Team.

## Definitions

* Personally Identifiable Information \(PII\) has been defined per GDPR Requirements

## Data Classification levels

### RED

Restricted and must remain confidential. This is our most sensitive data and access to it should be considered privileged. Exposure of this data to unauthorized parties could cause extreme loss to IllumiDesk and/or its customers. In the gravest scenario, exposure of this data could trigger or cause a business extinction event.

**Examples:** See Data Classification Index

**Access:** Requests should be reviewed based on the principle of "need-to-know" and approved by the appropriate data owner. Once approved, access should be logged and monitored. Additional security measures should be put in place to ensure immediate response to access that seems unexpected or inappropriate. These measures should include a formalized and documented review of access on a recurring basis, during which appropriateness of access and access entitlements are recertified. Strong access controls should be put in place to ensure that this type of data is not publicly exposed.

Vendor and/or contractor access is not permitted without formal approval and verification that they have signed an approved confidentiality agreement or non-disclosure agreement.

Systems, applications and/or integrations containing Red information must have a DPIA on file.

**Reproduction:** Do not reproduce or share Red information in an application lacking the appropriate level of security. Never share in a public forum.

### ORANGE

Data and information that should not be made generally available. Unauthorized access or disclosure could cause significant or financial material loss, risk of harm to IllumiDesk if exposed to unauthorized parties, break contractual obligations, and/or adversely impact IllumiDesk, its partners, employees, and customers.

**Examples:** See Data Classification Index

**Access** Access to this data must be approved by the appropriate owner prior to being granted, and once provisioned, access should be logged and monitored. Strong access controls should be put in place to ensure that this type of data is not publicly exposed.

Access to ORANGE data is limited to those with a business need-to-know, including third parties and customers, as defined by IllumiDesk Security.

Third party access to confidential information is granted only on a need to know basis and providing appropriate confidentiality agreement or non-disclosure agreement is in place.

**Reproduction:** May be reproduced for Internal Use only.

**Distribution/Disclosure:** May be sent internally on a need to know basis, but discretion should be used. May not be sent over a public network unless encrypted. Must use the standard IllumiDesk email statement regarding sensitive information. Information must be encrypted or otherwise electronically protected when sent to a recipient outside the company. Must be encrypted or otherwise protected when stored and not in use on a laptop or portable device. Documents and computer screens should be positioned to prevent inadvertent disclosure of information. “Orange” markings should be applied to all presentation materials to identify sensitive information.

**Storage/Disposal:** Electronic storage requires access controls, access control lists, and directory as well as file permissions, and other protection mechanisms. Information must be encrypted if necessary to store on publicly accessible systems. Electronic storage media must be irretrievably erased, degaussed and/or disposed of in a secure fashion. When information is no longer valid or necessary, it should be completely and permanently destroyed in accordance with the Record Retention Policy.

### YELLOW

Non-public data that is not classified as ORANGE or RED. Disclosure of this data could violate privacy policies, minimal risk of harm and/or adversely impact IllumiDesk, its partners, employees, and customers.

**Examples:** See Data Classification Index

**Access:** Access to this data should be approved prior to being provisioned and should be logged. Strong access controls should be put in place to ensure that this type of data is not publicly exposed.

Access to YELLOW data is limited to those with a business need-to-know, including third parties and customers, as defined by IllumiDesk Security.

**Reproduction:** May be reproduced for internal use only. May be distributed to vendors and contractors on a need-to-know basis.

**Distribution/Disclosure:** Whenever possible, do not leave screens unattended or unsecured in public locations. Conversations must be limited to other IllumiDesk employees or individuals covered by a non-disclosure agreement. Appropriate care must be taken to prevent disclosure or theft.

**Storage/Disposal:** Normal deletion commands or utilities with operating systems are sufficient for online files. When information is no longer valid or necessary, it should be completely and permanently destroyed. Basic access controls must be configured on the device\(s\) storing such information

### GREEN

Data and information that are publicly shareable, and do not expose IllumiDesk or its partners to any harm are classified as Green.

Public Information requires no special handling.

### Credentials and access tokens are classified at the same level as the data they protect

Credentials such as passwords, encryption keys, and session cookies derive their importance from the data they protect. For example, authentication cookies for IllumiDesk.com super users are classified as RED because anyone who gains access to them will have access to customer content, which is RED data.

### Systems must be protected at a level appropriate for the volume of data they process. <a id="systems-must-be-protected-at-a-level-appropriate-for-the-volume-of-data-they-process"></a>

A system that processes a single data element at a time still processes many over time and must therefore be protected at a level appropriate for systems processing bulk data.

Typically only client applications are considered to be handling "A single customer's" data. Data on hosts/services is typically always "more than one customer". \(example of hosts running "client applications" would likely be runner hosts\)

### Combinations of data types may result in a higher classification level <a id="combinations-of-data-types-may-result-in-a-higher-classification-level"></a>

An example of this would be a single customer's encrypted content \(ORANGE\) that is stored on the same system as a IllumiDesk employee'ss credentials \(ORANGE\). If this user has permission to access to secrets that decrypt the customer's encrypted content, this elevates the classification \(to RED\).

## Labeling

There is currently no requirement to label data according to this policy however labels are encouraged. By labeling data according to classification level, individuals can quickly refer to this policy for proper handing.

Issues that are confidential must be marked accordingly per our Communication Handbook Page

## Customer Responsibilities

Customers are responsible to identify and classify their own data. IllumiDesk handles confidential customer information internally according to our `non disclosure obligations` written in our Mutual Non Disclosure Agreement.

