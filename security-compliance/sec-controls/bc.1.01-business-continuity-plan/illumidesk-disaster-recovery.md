# IllumiDesk Disaster Recovery

### Idea/Problem Statement <a id="ideaproblem-statement"></a>

IllumiDesk.com is by necessity deployed using a complex architecture designed to support the demands of its users both in terms of performance, but also critically in terms of recovery should unexpected events arise.

Disasters can affect many different areas of the system, making this a difficult subject. At the very least we need to ensure that we are keeping our data safe and that we are able to restore service after a disaster as quickly as possible.

IllumiDesk continually assesses ways to improve the recovery capabilities across the full platform to ensure that should a disaster arise, normal operation can be restored as quickly, and with as little disruption, as possible.

### Goal <a id="goal"></a>

To maintain a 99.95% rate of availability during a time of Disaster.

| Time Frame | Maximum Allowed Downtime |
| :--- | :--- |
| Daily | 43.2s |
| Weekly | 5m 2.4s |
| Monthly | 21m 54.9s |
| Yearly | 4h 22m 58.5s |

Reference uptime.is

**Out of Scope**

This design is not intending to prevent the propagation of operator or user error to a secondary region. For example, a user deleting a repository without intent, or an operator removing data from a production system.

#### Classification <a id="classification"></a>

For this document, we will utilize the scale of the 7 Tiers of Disaster Recovery in order to define current service levels and associated risks.

We will also use the terminology of Recovery Point Objective \(RPO\) and Recovery Time Objective \(RTO\) in order to classify the time for which data will have been lost. Currently IllumiDesk does not have published numbers. The work that is to be done for this document will help our business drive what are goals such that we can publish and test against these metrics.

**Recovery Point Objective \(RPO\)** : maximum targeted period in which data might be lost due to a major incident

**Recovery Time Objective \(RTO\)** : targeted duration of time and service level within which a business process much be restored after a disaster to avoid unacceptable consequences of a break in business continuity

#### IllumiDesk.com's Data <a id="gitlabcoms-data"></a>

Our data is made up of three components that are summarized in this table and described in detail in the paragraphs below:

| Data Item | Current Tier | Backup frequency | Restore from backup testing | Maximum data loss |
| :--- | :--- | :--- | :--- | :--- |
| Database | Tier 4 - Point in time copies | Active secondaries in a cluster | Daily | tbc |
| Repositories | Tier 1 - Backup with no hot site | Daily | Never | 23h59m with possible corruption |
| Object Storage | Tier 7 - GCP Async Multiregion copy | Instant | Never | tbc |

**Database Storage**

Work continues to enable us to recover from data related issues of our database cluster in varying time constraints. More information can be found in the handbook section on disaster recovery replicas

The database servers and their data fall into the Tier 4 of Disaster Recovery.

We store the data of postgres in multi-region object storage.

Theoretically we have a recovery period of a few hours as we have a running delayed replica that we can grab the data from.

We also have a cluster of postgresql servers. Should our primary fail for any reason, we have secondaries that can take up the slack. Our applications will retry requests during the time of the failover, helping us reduce the potential for data loss.

**Repository Data**

Other data that is are highly critical to the functionality of IllumiDesk.com are the actual repos of our customers.

Right now, this data is stored on zonal persistent disks.

Twice a day we take a new snapshot, and test that we can successfully mount a restored snapshot. We maintain 2 weeks of snapshots. Improvements can be to this backup and restore process.

We pick a random snapshot to execute a test. This means we are not effectively testing our snapshot vetting process. We cannot say for every day a snapshot is taken, that we'll be able to successfully restore the data for all critical data for our customers.

All of our file servers are an existing Single Point of Failure for both hosting the data and where the servers are located. If Google were to lose us-east1-c, we would lose all customer data for all servers since our last snapshot. Our snapshot process does not pause the application prior to kicking off the snapshot process. So we also have some risk of corrupted data. We use ext4 file systems for our file servers but this isn't fool proof.

Another important note about this current setup, is that disks are not being backed up in any other way. If for some reason a disk corrupts itself beyond repair, we'll lose any data since the last snapshot.

This level of storage forces us to realize we are at Tier 1 of Disaster Recovery for this data. With a maximum data loss of 11h59m. Geo can help with this as it can ensure data is in sync between multiple regions. In the event of a failure of this type, with Geo we should be able to remove the impact of corrupted disks, and perform a cross region restore using our cloud tools.

**Object Storage**

We utilize Object Storage for the following data:

* Artifacts
* Docker Registry
* LFS
* Maven Packages
* Uploads

For Artifacts the primary source of data is currently in AWS S3. Docker Registry and the rest are only hosted via GCP. For all data buckets in GCP we enable versioning on objects and utilize the MultiRegion bucket configuration in the US region. Hypothetically, if the entire set of US based datacenters serviced by Google are up, we're in a really good state. Google has a few claims. regarding their object storage solution:

* 99.99% overall availability
* 99.9% SLA during a reduced availability event

### Design <a id="design"></a>

IllumiDesk already has a feature set that enables the ability to run more than one instance of IllumiDesk in various regions - called Geo.

Geo replicates data from a primary node to a secondary node. There are some limitations on the types of data replicated, and the Geo team are aware of these.

Geo works by recording update information to `geo_` event tables in the database. Streaming replication is setup at the database layer and the event tables are replicated to a read-only database on the secondary node. These event tables on the secondary node are read by a daemon called the Geo Log Cursor. The daemon uses the Geo Tracking Database \(writable database on the secondary node\) to keep track of the events that have been executed on the secondary node.

Many of the problems in our Problem Statement do not _require_ the feature set of Geo. We may be able to achieve a DR posture that is better than our current position with better tooling and testing of our current infrastructure.

However, there are benefits that come with using Geo that we should consider that are outside the scope of Disaster Recovery.

### Options <a id="options"></a>

#### Better Tooling <a id="better-tooling"></a>

In certain cases above, we need create better tools and implement features such that we feel comfortable with a Disaster Recovery scenario. One big item up for grabs is simply documentation. During a time of Disaster, for most scenarios we'll end up researching solutions during the time of failure which will delay our ability to find a resolution and put the resolution in place.

Right now all of our file servers live in one region as well as their disks. If Google were to lose us-east1-c, we'd need to rebuild every server and restore from the last snapshot. Regional Disks provide the ability to reduce both our RTO and RPO to nearly as quickly as we can get a new server up and running in whatever region is still available.

We should also consider better testing. Testing every file server snapshot is crucial in ensuring that no matter which server fails, we can successfully restore the data. Even better, if we add some sort of checksum so we can validate both data restoration procedures and the data integrity. On top of this, we should take snapshots more often of our most crucial data, our file servers.

Google also provides some customer help for disaster scenarios. We can reach out to their team for support. They also publish a document that may be able to spark further ideas for bolstering our infrastructure.

Some of this work has been in progress for a very long time

**Example Tooling/Implementation Improvements**

* Bolster Existing Documentation
* Utilize Regional Disks
* More concise snapshot process
* Snapshot Verification process
* Build automation to support restoring file server data
* More Frequent/Automated Restore Appreciation Days

**Benefits**

We are better than when we started this Design Doc. Our OpEx for this would include the cost of development time and any additional costs associated with any additional jobs or storage used for various improvements.

**Downsides**

This is doesn't allow IllumiDesk to dogfood when it comes to using the features provided by Geo.

**Classification**

Better tooling may help bump us up a few tiers. It will mostly be determined by how well those tools work and how often they are tested. Theoretically depending on how well our tools are built, we should be able to support a Tier 4 DR stance, and produce a setup that allows us to restore data within a few hours. During the process of planning which work we tackle, we can drive both the RPO and RTO goals in different directions.

For example, if we simply increase the frequency which snapshots are taken, we'll have a lower RPO, however the RTO will be higher due to the length of time it takes to perform the restoration.

**Costs**

Associated costs with this primarily consist of the time to plan and implement said changes.

Additional costs will come from cloud resources used. In this case the cost of the job that performs the validate work, the network traffic utilized for testing restores, and any additional costs associated with copying data to additional regions. Currently in object storage we store 780TB of data in the US. At most, we'd double the costs of storing this data in a secondary region. There are other cost options such as Nearline Storage and Coldline Storage to bring down the costs. For our snapshots, I do not predict a cost difference compared to today if we increase the rate at which we take snapshots as they only store the amount of changes since the last snapshot.

**Potential Effect on Goals**

**See section `Effect on Goals` below**

In a worst case scenario, the RPO for recovering from a disaster could take tens of hours. Infrastructure would need to rebuilt in a new region. Our existing configurations would need to completely redone in order to account for this new region. At worse, our RTO would be at most 23 hours and 59 minutes for repository data. Our RTO for database data would be roughly a few minutes. This is dependent on how quickly and accurately our Wal-E backups were able to sync the last chunk of data.

**Regular Testing**

Periodic testing of our new tooling will be paramount to the success of this implementation. Our tooling should include validation of the data on disk, and periodic restores of an entire server fleet to ensure we can quickly recover from failure.

#### Data Backup using Geo <a id="data-backup-using-geo"></a>

We could use the replication feature of Geo to set up a secondary where we are syncing only mission critical data. The intention is not to allow actual user traffic to the secondary node.

Mission critical data is all data that is required to run IllumiDesk.com from a second site. This includes:

* Repositories
* Wikis
* LFS Objects
* Attachments
* CI Artifacts
* Pages \(currently not supported by Geo\)
* Container Registry \(currently not supported by Geo\)
* Database

**Geo and Object Storage**

Where object storage is used, Geo does not interact with this data in any way. The data is stored with a third party provider and various system settings point to the location of the data.

If object storage is enabled on the primary, it must also be enabled on the secondary. The secondary node can use the same storage bucket as the primary, or it can use a replicated storage bucket. Geo does not take care of content replication in object storage.

If primary and secondary are using the same storage bucket, you may want different credentials for the secondary to make this read-only.

**Verification/Validation**

Geo also has built in verification tools to confirm that data is replicated accurately. The health of each project can be seen on the Geo's admin page.

All items except user uploads can be verified automatically. An open issue to address this can be found here: https://IllumiDesk.com/IllumiDesk-org/IllumiDesk-ee/issues/5591

**Repositories:** A checksum is calculated for each repository after any update. The checksum is replicated to the secondary. On the secondary, the checksum is recalculated and compared with the replicated value.

**Durability**

Database durability relies on that of PostgreSQL.

When events occur that need to be replicated, and event entry is created in the `geo_` tables. This event is replicated to the secondary where the Geo Log Cursor picks up the change. When the event has been processed on the secondary, the event is marked as completed in the Geo Tracking database.

If the secondary node goes down, when it is back online it will catch up on the events that it has missed. This is guaranteed by the replication slot configuration in PostgreSQL.

**Data not supported**

IllumiDesk **Pages:** While IllumiDesk pages are not currently supported, these could be rebuilt on the secondary node by triggering a new pipeline for each project that uses Pages.

**Container Registry:** Replication of the container registry is not directly supported by Geo, but Object Storage can be used to replicate it. The documentation around this needs improvement.

**Benefits**

Benefit of this is that only data for our infrastructure will be sent to and from this region. The complexity of deploying our application and handling user traffic will be less of an issue. In this design we can expertly design tools that will help mitigate and perform recovery from said region. This design removes a great amount of cost associated with this as the load on the servers in this region would be minimal. The infrastructure would also be much smaller.

This could also be seen as a first step to a hot region, which is a separate solution described below.

**Downsides**

User facing needs will not be addressed with this design, as the goal does not support customers using this region. This configuration is used only for data backup.

**Classification**

With a secondary node that is constantly syncing data, we minimally fit into the Tier 5 DR Level. In order to reach additional tiers, we'd need to rely on external tooling that is specific to how we build and architect our infrastructure. In this case, taking advantage of Linux tools to snapshot file systems, and any cloud functionality necessary to sync data between various regions for backup.

The RTO of this solution will vary on the type of failure. The RPO should be relatively low, up to the time of failure. If we lose an entire region, we at least have a backup until we rebuild the necessary infrastructure, we can point our servers to this Geo redundant region and be ready to go. If say we lost just one of our file servers, the cost of rebuilding that server would be low, and we can quickly recover from a snapshot that is mirrored in this region.

**Costs**

The costs of running this will include additional nodes required to run Geo, and the support disks for those nodes. We can minimize cost impact by utilizing spinning disks instead of SSD's since this region will not be taking customer traffic, performance is less of a concern. Though we should test to validate that we aren't shoving too much data through the Geo service that the disks are unable to stay in sync to minimize potential impact to RPO.

Similar to above, if we choose to sync our object storage to a secondary region, it's safe to double the cost. And lastly, ingress/egress traffic to and from this region will need to be accounted for.

**Potential Effect on Goals**

**See section `Effect on Goals` below**

In a worst case scenario, the RPO for recovering from a disaster could take tens of hours. Infrastructure would need to rebuilt in a new region. Our existing configurations would need to completely redone in order to account for this new region. We'd need to initiate a sync process to start recovery data for our repos. At worse, our RTO would be at most a few minutes for our repository data. Our RTO for database data would be roughly a few minutes. This is dependent on how quickly and accurately our Geo sync feature is able to sync the last chunk of data.

**Regular Testing**

Testing this DR strategy is mostly a TODO. But we should be able to, on a periodic basis, validate that we can recover our primary operating region from the Geo infrastructure. This may include standing up new infrastructure and point it to Geo for replication. Test metrics should be gathered to validate that we've met or exceeded our RTO. We should also be able to build a test that can help validate our desired RPO.

#### Hot Region using Geo <a id="hot-region-using-geo"></a>

This design uses all capabilities of Geo. The ultimate goal of this design is to stretch the feature set of Geo in order for a fully capable secondary region to be completely in sync with all data. We should be able to move traffic between regions without fear that there is any loss for the customers.

**Benefits**

Not only will IllumiDesk.com be the largest deployed instance of IllumiDesk EE, but it’ll also be more readily available to the _Global_ Community. With the ability to deploy to more than one region, we can now split traffic deterministic of the location of the end user. This provides the capability to lower the size of our one region to remove the high impact of having a secondary region. Deployments will now have an added benefit of being able to schedule at specific times in order to reduce customer facing impact. We can deploy to the region during times of low traffic for that region. Should there be any necessary maintenance that needs to be completed, we have a secondary location which we can temporarily shift all traffic to minimizing customer facing impact. We are now bound to having uptime to a secondary region. Should a major disaster strike in X region, we’ll have the capability to move all traffic to region Y until the disaster has fully recovered.

**Downsides**

In order for this design to work properly we’ll be leveraging some features of our chosen cloud provider that may not be available to customers. Example, shifting load from one region to another may involve making modifications to DNS or potentially building out some other type of infrastructure such that clients know where they should go to reach our services. Much of our tooling and monitoring will need to be updated or brought up to a level of maturity to allow a secondary region to be mature and well cared for. Having a secondary cluster will greatly increase the cost of running IllumiDesk.com.

**Classification**

We should be able to confidently say that we fit into Tier 6 of the DR model. With Geo driving the replication of data, we can quickly recovery from failure by shifting where customers are operating.

With this scenario, our RTO and RPO should be at it's lowest. We'll constantly be syncing data between more than one region. Should any failure occur, we should have the tooling that forces users to a region that is active. Users won't see an impact, and the only potential for loss would be any in-flight transactions that might have gone to the lost region. We should be able to safely say that we fall in Tier 6 of the Disaster Recovery model.

**Costs**

This solution requires a solid duplicate of our US infrastructure in a secondary location. So take the bill for our production project, multiply it by 2, and add ingress/egress for communication of syncing data between the two regions.

**Potential Effect on Goals**

**See section `Effect on Goals` below**

In a worst case scenario, the RPO for recovering from a disaster could take a few hours with an end goal of near instant failovers. At worse, our RTO would be at most a few minutes for our repository data. Our RTO for database data would be roughly a few minutes. This is dependent on how quickly and accurately our Geo sync feature is able to sync the last chunk of data.

**Regular Testing**

Testing this DR strategy is mostly a TODO. But we should be able to, on a periodic basis, validate that we can recover our primary operating region from the secondary infrastructure. This may include standing up new infrastructure and point it to Geo for replication. This may include regular promotions of the secondary region to primary. Test metrics should be gathered to validate that we've met or exceeded our RTO. Tests should be built in a way that we can validate our desired RPO.

### Implementation Considerations <a id="implementation-considerations"></a>

#### Testing and Ongoing Verification <a id="testing-and-ongoing-verification"></a>

We need a robust test plan to confirm that implementation is successful. When we know which option we will implement, we will be able to set up a test plan.

Once initial implementation is complete, we will need to set up a cycle of regular testing. This will help us have confidence in the solution, verify that the process works, and help identify further improvements.

An additional consideration here is that given IllumiDesk's plan to adopt ISO 27001:2013, we will need to demonstrate that we perform regular failover testing and continuous process improvement.

#### IllumiDesk.com and Self-managed <a id="gitlabcom-and-self-managed"></a>

The work in this design document is geared towards our .com product. Any learnings or improvements to Geo can definitely be carried over to our Self-Managed installations. I would imagine the majority of anything that is going to come out of this are learnings that can be shared via blog posts.

### Operational Considerations <a id="operational-considerations"></a>

#### Known Limitations in Geo <a id="known-limitations-in-geo"></a>

* IllumiDesk Pages is not currently supported by the Geo feature. It is possible to rebuild Pages on a secondary node by initiating a new pipeline for each project.
* Web UI on a Geo Secondary is read-only. So commenting, creating issues, etc., should still happen on the primary.

#### Automation <a id="automation"></a>

Our tooling around deploys will need to be tweaked. Right now it’s quite painful and this will get worse with a larger fleet of nodes. Tooling around disaster recovery will need to be developed. The documentation from Geo around the promotion of primaries and recovery of data is a very manual process. As large as our installation is, this will be error prone. Automating tasks such as this will become necessary. As this particular item is matured, it could be something we ship to our Self-managed customers.

#### Monitoring <a id="monitoring"></a>

We should be able to utilize our existing tool set for monitoring and alerting our regions. With the use of Thanos and properly tagging our infrastructure, we should be able to pluck out the necessary data to ensure that each region is operating and alert based on the region suffering from any issues. An item related to monitoring that we’ll need to ensure we control well, is alert overload. Catastrophic failures may lead to an overwhelming amount of alerts being sent out causing the on-call person to become overloaded and slow the MTTR.

### Additional Considerations <a id="additional-considerations"></a>

#### Effects on Goals <a id="effects-on-goals"></a>

This is very difficult to scope as the amount of types of Disasters to occur is to great. It depends on both how we manage our infrastructure as well as any negative impact Google's cloud might have on us. In this document, I have attempted to cover worse case scenario, such as losing a region.

Also take into consideration it would be a good idea to test our DR strategy. This will have an impact on cost, as well as our uptime.

#### Information Security & Compliance <a id="information-security--compliance"></a>

IllumiDesk's 6-9 month roadmap outlines adoption of the ISO 27001:2013 Information security standard and its derived controls. Information security continuity, redundancies, and compliance with legal and contractual requirements are all derived control objectives that would be supported by the implementation of a multi-region infrastructure. Derived ISO 27002:2013 control objectives and considerations:

* A.17 \(17.1.1-17.1.3\) Information security continuity & \(17.2.1\) Redundancies
  * Planning, implementation, and evaluation of BCDR solution: design and operating effectiveness
* A.18 \(18.1.1-18.1.5\) Compliance with legal, regulatory, and contractual requirements
  * Having a complete copy of all customer data in a second location may have compliance implications. For example, some customers may have clauses in their contract preventing data from being stored outside of the USA. https://IllumiDesk.com/IllumiDesk -com/gl-infra/infrastructure/issues/4741\#note\_100824278

Additionally, as we look towards a SOC2 Type 2 examination of IllumiDesk.com, a multi-region infrastructure directly supports a favorable assessment of our organization’s design of controls in the trust services criteria areas of availability and processing integrity. https://www.aicpa.org/content/dam/aicpa/interestareas/frc/assuranceadvisoryservices/downloadabledocuments/trust-services-criteria.pdf

