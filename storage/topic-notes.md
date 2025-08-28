# Storage Notes

## Primary Storage Types
- Object storage
  AWS S3
- Block storage
  Amazon EBS, Amazon EC2 instance stores and FSx for ONTAP block storage over iSCSI
- File storage
  Amazon EFS, AWS FSx for Windows/OpenZFS

## Use Cases
- S3 for static websites and file backups
- EBS for app data (like databases)
- EFS for shared file access across instances

## Related Concepts
- Amazon Storage Gateway (Tape, Volume, FSx File Gateway or S3 File Gateway)
- AWS Transfer Family

## Reflection
In AWS storage, you trade high CAPEX(on-premises) to pay for only the storage capacity allocated or the storage used. Understanding when to use each service can be determined by a number of considerations: type of access method; patterns of acces; required throughput in MB/sec; required input in IOPS; frequency of access; frequency of update; avaialability and durability constraints etc.
