# SYS.1.01 - Audit Logging



### Control Statement

GitLab logs critical information system activity.

###  Context

Logging is the foundation for a variety of other security controls including monitoring, incident response, and configuration management. Without comprehensive and reliable logs, large parts of our security compliance program wouldn't be possible. This control is left vague by design. As we develop our system maps and inventories this control will likely become a bit more targeted. To start we really want all IllumiDesk teams to enable system-level logging on all production systems.

An auditor will look to validate in-scope systems are generating logs, those logs are collected, retained the required amount of time and utilized to monitor for performance, health, and anomalies. To validate the control is working properly, the auditor should require additional pieces of information to demonstrate audit logging is functioning properly. Those information items include:

* Review of the audit and accountability policy and procedures
* Confirmation that audit events are reviewed and updated on a recurring basis
* Review what should be collected for auditing and cross-reference against what is collected
* Determine what defines a production system to validate the correct systems are being audited
* Confirm log validation processes are working as intended
* Master asset listing to confirm correct systems are being audited
* Log collection process\(es\)

###  Scope

This control applies to all systems within our production environment. The production environment includes all endpoints and cloud assets used in hosting IllumiDesk.com and its subdomains. This may include third-party systems that support the business of IllumiDesk.com.

###  Ownership

Control Owner:

* Infrastructure

Process Owners:

* Security Compliance
* Infrastructure
* Security Operations

###  Guidance

Server configuration standards should have logging information enabled for each type of system. These logs should be retained for one year with 90 days of data immediately available for analysis or in accordance with Record Retention Policy, whichever is longer.

####  Audit Logging Matrix

_Audit Logging Matrix is a modified version of_ NIST 800-92 - Guide to Computer Security Log Management

| Type | Value | Reason\(s\) | Log Example\(s\) |
| :--- | :--- | :--- | :--- |
| General Information | Timestamp | When the event occurred | 2017-07-04\*13:23:55 2019-09-30T19:15:26.309Z Sep 30, 2019 @ 15:15:26.309 |
| Event, Status, and/or error codes | The action taken | Sep 11 09:46:33 sys1 crontab\[20601\]: \(root\) BEGIN EDIT \(root\) Sep 11 09:46:39 sys1 crontab\[20601\]: \(root\) REPLACE \(root\) Sep 11 09:46:39 sys1 crontab\[20601\]: \(root\) END EDIT \(root\) storage.objects.delete v1.compute.instances.delete |  |
| Service/cmd/app name | What tool the actor used | service sshd start |  |
| User or system acct associated with an event \(username, uuid, global UID, API token name, 3rd party\) | Actor | "user\_id":3003042 "username":"jsmith-admin" "TdGZg20BL6pl1duCU2g7" |  |
| Group | What access the actor has | 6007778 |  |
| Device used \(e.g. source and destination IPs, terminal session ID, web browser, device ID, etc.\) | Where the event is originating from or terminates | source IP - 192.168.xxx.174:8080 destination IP - 192.168.xxx.126:53021 device ID - 89ABxDEF-01234567-89ABxDEF |  |
| OS Events | Start-up and shut-down of the system | Unintended or modified system activity | Jun 1 22:20:05 secserv kernel: Kernel logging \(proc\) stopped. Jun 1 22:20:05 secserv kernel: Kernel log daemon terminating. Jun 1 22:20:06 secserv exiting on signal 15 Nov 27 08:05:57 galileo kernel: Kernel logging \(proc\) stopped. Nov 27 08:05:57 galileo kernel: Kernel log daemon terminating. Nov 27 08:05:57 galileo exiting on signal 15 |
| Start-up and shut-down of a service | Unintended or modified service activity | Jan 26 12:22:41 combo xinetd\[2013\]: bind failed \(Address already in use \(errno = 98\)\). service = telnet Jan 26 12:22:41 combo xinetd\[2013\]: Service telnet failed to start and is deactivated. Jan 26 12:22:42 combo spamassassin: spamd startup succeeded Jan 26 12:22:43 combo privoxy: privoxy startup succeeded Jan 26 12:55:20 combo sendmail: sm-client shutdown succeeded |  |
| Network connection changes or failures | Unintended or modified network activity | Jan 26 12:22:03 combo network: Setting network parameters: succeeded |  |
| Changes to, or attempts to change, system security settings and controls | Security settings and controls are modified very rarely | TBD  |  |
| Audit Records | Log-on attempts \(successful or unsuccessful\) | Identify brute force, password spraying | May 21 11:21:03 gitlab.com sshd\[11179\]: \`Accepted password\` for tanuki from 202.91.xxx.210 port 58244 ssh2 Dec 12 21:32:40 gitlab.com sshd\[43456\]: \`Failed password\` for root from 192.168.xxx.174 port37632 ssh2 Jan 22 05:51:12 combo sshd\[24935\]: Failed password for illegal user miha from ::ffff:212.24.173.67 port 55263 ss |
| The function\(s\) performed after logging on \(e.g., reading or updating a critical file, software installation\) | Track all actions taken by actor | Jan 26 12:22:13 combo kernel: audit\(1138278089.855:0\): avc: denied { read write } for pid=1 exe=/sbin/init name=initctl dev=hda2 ino=1031635 scontext=system\_u:system\_r:kernel\_t tcontext=system\_u:object\_r:file\_t tclass=fifo\_file |  |
| File changes\( e.g., name, creation and deletion, integrity\) | Unintended or modified file activity | Sat Feb 3 05:32:20 CST 2007 0 /etc/hosts1308742 fd:00 0100644 0 0 00:00 system\_u:object\_r:etc\_t:s0 |  |
| Data export | Track data exportation against defined baselines | Mon Jun 19 04:44:43 2017 1 10.4.xxx.22 20 /CSV/test1.csv a \_ o r testuser ftp 0 \* c Mon Jun 19 04:51:33 2017 1 10.4.xxx.22 432 /CSV/test4.csv a \_ o r testuser ftp 0 \* c Mon Jun 19 04:57:15 2017 1 10.4.xxx.22 110 /CSV/test14.csv a \_ o r testuser ftp 0 \* c Mon Jun 19 04:57:19 2017 1 10.4.xxx.22 2505 /CSV/master.csv a \_ o r testuser ftp 0 \* c |  |
| Account changes \(e.g., account creation and deletion, account privilege assignment\) | Identify privilege escalation or suspicious accounts | sudo: mike : TTY=pts/2 ; PWD=/home/mike ; USER=root ; COMMAND=/usr/sbin/adduser jim sudo: pam\_unix\(sudo:session\): session opened for user root by mike\(uid=1000\) groupadd\[1731\]: group added to /etc/group: name=jim, GID=1001 groupadd\[1731\]: group added to /etc/gshadow: name=jim groupadd\[1731\]: new group: name=jim, GID=1001 useradd\[1735\]: new user: name=jim, UID=1001, GID=1001, home=/home/jim, shell=/bin/bash passwd\[1742\]: pam\_unix\(passwd:chauthtok\): password changed for jim passwd\[1742\]: gkr-pam: couldn't update the login keyring password: no old password was entered chfn\[1743\]: changed user 'jim' information sudo: pam\_unix\(sudo:session\): session closed for user root |  |
| Successful/failed use of privileged accounts | Unintended privileged account activity | Jan 30 11:25:57 combo sshd\(pam\_unix\)\[3533\]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=mail.fullerproperties.com user=root Jan 23 05:28:18 combo sshd\[28534\]: Failed password for root from ::ffff:62.26.66.134 port 57203 ssh2 |  |
| Database Operations | Direct data changes | Integrity of financial data used in reporting | TBD  |
| ELT job failures | Completeness and accuracy of data being used in financial reporting and operational decision-making | \_Dependent on key financial applications\_ |  |
| Application account information | Successful and failed application authentication attempts | Identify unintended activity | Git-99-sb-gprd sshd 3087 error: Received disconnect from 10.218.xxx.36 port 39772:3: com.jcraft.jsch.JSchException: Auth fail \[preauth\] system.auth gprd git-99-sb-gprd git-99-sb-gprd.c.gitlab-production.internal  2019/10/04 18:06:23 \[error\] 29881\#0: \*319208 connect\(\) to unix:/var/opt/gitlab/gitlab-workhorse/socket failed \(111: Connection refused\) while connecting to upstream, client: 156.160.xxx.190, server: git.kts.io, request: "POST /api/v4/jobs/request HTTP/1.1", upstream: "hxxp://unix:/var/opt/gitlab/gitlab-workhorse/socket:/api/v4/jobs/request", host: "git.kts.io" |
| Application account changes \(e.g., account creation and deletion, account privilege assignment\) | Identify privilege escalation or suspicious accounts | October 06, 2014 11:56: User "Administrator" \(admin@example.com\) was created October 06, 2014 11:56: Documentcloud created a new project "Documentcloud / Underscore" October 06, 2014 11:56: Gitlab Org created a new project "Gitlab Org / Gitlab Ce" October 07, 2014 11:25: User "Claudie Santie" \(santie\_clause@tanuki.co.uk\) was removed October 07, 2014 11:25: Project "project133" was removed |  |
| Use of application privileges | Unintended privileged account activity |  TBD |  |
| Application Operations | Application startup and shutdown | Unintended or modified application activity |  TBD |
| Application failures | Identify brute force, password spraying |  TBD |  |
| Major application configuration changes | Unintended or modified application configuration activity |  TBD |  |
| Application transactions:  – e-mail servers recording the sender, recipients, subject name, and attachment names for each e-mail  – Web servers recording each URL requested and the type of response provided by the server  – business applications recording which financial records were accessed by each user | Capture relevant application transaction data to create baselines for identifying unintended actions | TBD  |  |

###  Additional control information and project tracking

Non-public information relating to this security control as well as links to the work associated with various phases of project work can be found in the Audit Logging control issue.

###  Framework Mapping

* ISO
  * A.12.4.1
* SOC2 CC
  * CC7.2
* NIST 800-53
  * AU-1
  * AU-2
  * AU-9
  * AU-12

