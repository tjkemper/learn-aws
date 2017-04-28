# EBS
* Elastic Block Store
* Instance storage is ephemeral.  EBS is persistent (off instance) storage.

### General
* Persistent block level storage volumes for EC2 instances
* Each volume is replicated within an AZ
* Exists separately from life of EC2 instance
* By default, EBS volumes detach from terminated instances
  * They remain attached during stop-start cycle
* Data persists until volume is deleted


### Security & Encryption
* Overwritten with zeroes before going to another account
* Encrypt data
  * Manually
  * Using a volume encrypted by Amazon
* Amazon EBS encryption
  * 256-bit Advanced Encryption Standard algorithms (AES-256)
  * Amazon managed key infrastructure
* Encryption is supported for all EBS types
* Same IOPS performance whether encrypted or not

### Snapshots
* Stored in S3
* Allows us to create a new EBS volume (with snapshot data) in any AZ of same region
* Incremental
* **EBS volumes specific to AZ**
* **EBS Snapshots specific to Region** (can copy between regions)
* Only blocks changed since last snapshot are saved
  * Time taken to restore snapshot to EBS volume is the same for all snapshots
  * Deleting a snapshot only deletes changed data
* Use cases
  * Create multiple volumes with same data
  * Increase size of volume
  * Change type of volume???????????????????????????????????????????????????????????????????????????????????????????????????
  * Move volumes between AZ
* Lazy loading: can use a snapshot immediately (without waiting for all data to transfer)
* Sharing Snapshots (private to account by default)
  * with team members
  * AWS community

##### [Snapshot of RAID array](https://aws.amazon.com/cn/premiumsupport/knowledge-center/snapshot-ebs-raid-array/)
* Freeze file system
* Unmount RAID array
* Stop instance

### [Volume Types](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html)
* General Types
  * SSD
  * HDD
* Types
  * General Purpose - SSD backed burstable to 3000 IOPS
  * Provisioned IOPS - SSD backed 4000 IOPS consistently
  * Throughput optimized HDD (st1)
  * Cold HDD (sc1)
  * Magnetic - 40-200 IOPS
* Use cases for each type???

### [RAID](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/raid-config.html)
* **RAID 0**: When *IO performance* is more important than *fault tolerance*
* **RAID 1**: When *fault tolerance* is more important than *IO performance*
* **RAID 5 and RAID 6**: *Not recommended*
