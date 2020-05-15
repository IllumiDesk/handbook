# IllumiDesk Handbook listing of DR for Databases



### Database: Disaster Recovery <a id="database-disaster-recovery"></a>

This page contains an overview of the disaster recovery strategy we have in place for the PostgreSQL database. In this context, a disaster means losing the main database cluster or parts of it \(a `DROP DATABASE`-type incident\).

The overview here is not complete and is going to be extended soon.

We base our strategy on PostgreSQL's Point-in-Time Recovery \(PITR\) feature.

This means we're shipping daily snapshots and transaction logs \(WAL\) to an external storage \(the archive\). Given a snapshot, we are now able to replay the WAL until a certain point in time is reached \(for example, right before the disaster happened earlier\).

Currently, AWS S3 serves as a storage backend for the PITR archive.

#### Restore testing <a id="restore-testing"></a>

A backup is only worth something if it can be successfully restored in a certain amount of time. In order to monitor the state of backups and measure the expected recovery time \(`DB-DR-TTR`\), we employ a daily process to test the backups.

This process is implemented as a CI pipeline \(see README.md for details\). On a daily schedule, a fresh database GCE instance is created that restores from the latest backup, gets configured as an archive replica that recovers from the WAL archive \(essentially performing PITR\). After this is complete, the restored database is verified.

There is monitoring in place to detect problems with the restore pipeline \(currently using deadmanssnitch.com\). We plan to monitor the time it takes to recover and other metrics soon.

#### Disaster Recovery Replicas <a id="disaster-recovery-replicas"></a>

The backup strategy above is a _cold backup_. In order to restore from a cold backup, we need to retrieve the full backup from a cold storage \(via network\) and perform PITR from it. This can take quite some time considering the amount of data needed to be put on the network.

The current speed of restoring a cold backup from AWS S3 is at about 380 GB per hour \(net size\) for retrieving the base backup. With a database size of currently 2.1 TB, just retrieving the base backup alone takes more than 5 hours already. The PITR phase is generally deemed slower.

We currently aim at a `DB-DR-TTR` of 8 hours to recover from a backup. We're _not there yet_ and as an interim measure, we introduce disaster recovery replicas.

**Delayed Replica**

Another option is to have a replica in place that always lags a few hours behind the production cluster. We call this a _delayed replica_: It is a normal streaming replica but delayed by a few hours. In case disaster strikes, it can be used to quickly perform PITR from the WAL archive. This is much faster than a full restore, because we don't have to fully retrieve a full backup from S3. Additionally, with daily snapshots the latest snapshot is 24 hours \(plus the time it took to capture the snapshot\) old worst-case. A delayed replica is constantly kept at a certain offset with respect to the production cluster and hence does not need to replay too many hours worth of data.

* Production host: `postgres-dr-delayed-01-db-gprd.c.`IllumiDesk`-production.internal`
* Chef role: `gprd-base-db-postgres-delayed`

**Archive Replica**

Another type of replica is an _archive replica_. It's sole purpose is to continuously recover from the WAL archive and hence _test_ the WAL archive. This is necessary because PITR relies on a continuous sequence of WAL that can be applied to a snapshot of the database \(basebackup\). If that sequence is broken for whatever reason, PITR can only recover until this point and no further. We monitor the replication lag of the archive replica. If it falls back too far, there's likely a problem with the WAL archive.

The restore testing pipeline also performs PITR from the WAL archive and thus also would be able to detect \(some\) problems with the archive. However, employing an archive replica that is close to the production cluster helps to detect problems with the archive much faster than with a daily test of a backup. Also, the archive replica has to consume all WAL from the archive - a backup restore is likely to only read a portion of the archive to recover to a certain point in time.

In that sense, there is overlap between functionality of archive and delayed replicas and the restore testing. Together it gives us high confidence in our cold backup and PITR recovery strategy.

* Production host: `postgres-dr-archive-01-db-gprd.c.`IllumiDesk`-production.internal`
* Chef role: `gprd-base-db-postgres-archive`

