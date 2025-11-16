# <img width="45" height="45" alt="image" src="https://github.com/user-attachments/assets/61d576aa-d0d1-4d50-a1a8-d744469e272c" /> Storage Notes

## Primary Storage Types
- Object storage
  e.g AWS S3
- Block storage
  e.g Amazon EBS, Amazon EC2 instance stores and FSx for ONTAP block storage over iSCSI
- File storage
  e.g Amazon EFS, AWS FSx for Windows/OpenZFS

## Use Cases
- S3 for static websites and file backups
- EBS for app data (like databases)
- EFS for shared file access across instances

## Related Concepts
- Amazon Storage Gateway (Tape, Volume, FSx File Gateway or S3 File Gateway)
- AWS Transfer Family

## Reflection
In AWS storage, you trade high CAPEX(on-premises) to pay for only the storage capacity allocated or the storage used. Understanding when to use each service can be determined by a number of considerations: type of access method; patterns of acces; required throughput in MB/sec; required input in IOPS; frequency of access; frequency of update; avaialability and durability constraints etc.

## Exam Essentials
Understand the difference between durability and availability in S3.<br> Durability is the likelihood that an object won’t be lost over the course of a year.<br>Availability is the percentage of time an object will be accessible during the year.
<br><br>
Be able to select the best S3 storage class given cost, compliance, and availability requirements.<br> S3 offers six storage classes. STANDARD has the highest availability at 99.99 percent, replicates objects across at least three zones, and is the most expensive in terms of monthly storage cost per gigabyte. ONEZONE_IA has the lowest availability at 99.5 percent and stores objects in only one zone, and its monthly per-gigabyte storage cost is less than half that of the STANDARD storage class.
<br><br>
Know the different options for getting data into and out of S3.<br> You can upload or download an object by using the S3 service console, by using the AWS CLI, or by directly accessing the object’s URL.<br>AWS Storage Gateway lets your on-premises servers use industry-standard storage protocols such as iSCSI, NFS, and SMB to transfer data to and from S3.<br>AWS Snowball and Snowball Edge allow secure physical transport of data to and from S3.
<br><br>
Understand when to use bucket policies, user policies, and access control lists in S3.<br> Use bucket policies or ACLs to grant anonymous access to objects, such as webpages or images you want made public.<br>Use user policies to grant specific IAM principals in your account access to objects.
<br><br>
Be able to explain the differences between S3 and Glacier.<br> S3 offers highly available, real-time retrieval of objects. Retrieving data from Glacier is a two-step process that requires first requesting an archive using the Expedited, Standard, or Bulk retrieval option and then downloading the archive once the retrieval is complete.
<br><br>
Know how to use encryption, versioning, and object life cycle configurations in S3.<br> S3 offers server-side and client-side encryption to protect objects at rest from unauthorized access.<br>Versioning helps protect against object overwrites and deletions.<br>Object life cycle configurations let you delete objects or move them to different storage classes after they reach a certain age.
<br><br>
Understand the three virtual machine types offered by AWS Storage Gateway.<br> File gateways offer access to S3 via the NFS and SMB storage protocols. Volume gateways and tape gateways offer access via the iSCSI block storage protocol, but tape gateways are specifically designed to work with common backup applications.
