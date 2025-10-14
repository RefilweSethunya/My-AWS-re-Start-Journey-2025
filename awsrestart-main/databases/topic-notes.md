# Database Design Notes

## Concepts Covered
- RDBMS : RDS, Aurora
- NoSQL : DynamoDB, ElastiCache, Neptune, DocumentDB, Keyspaces
- Object Store : S3, Glacier for backups/archives
- Data Warehouse : Redshift, Athena, EMR
- Graphs : Neptune
- Ledger : Quantum Ledger DB
- Time Series : Amazon Timestream
- Data Analytics : Glue, Quicksight

## Diagramming Tools
- dbdiagram.io
- Lucidchart

## Reflection
...

## Exam Essentials
Know the vertical and horizontal scaling options for RDS.<br>You can scale an RDS instance vertically by upgrading to a larger instance class to give it more processing power, memory, or disk or network throughput. You can also select provisioned IOPS SSD storage to ensure your instance always achieves the storage performance it needs. For horizontal scaling of reads, your only option is to use read replicas.<br><br>
Know the vertical and horizontal scaling options for RDS.<br>You can scale an RDS instance vertically by upgrading to a larger instance class to give it more processing power, memory, or disk or network throughput. You can also select provisioned IOPS SSD storage to ensure your instance always achieves the storage performance it needs. For horizontal scaling of reads, your only option is to use read replicas.<br><br>
Know the backup and recovery options for RDS.<br>You can schedule automatic snapshots for your RDS instance to occur daily during a 30-minute backup window of your choice. Backups are retained between 1 day and 35 days. Enabling automatic backups also enables point-in-time recovery, allowing the restoration of a failed database up to 5 minutes prior to failure. Restoring from a snapshot entails creating a new instance from the snapshot. You can also take a manual snapshot at any time.
<br><br>
