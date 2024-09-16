![cloud_tier](https://github.com/user-attachments/assets/cbecf055-bee9-4abe-a35b-0da5de141141)

## General
- The PowerProtect DD system requires a cloud capacity license to use Cloud Tier
- On systems with a dedicated management interface, reserve that interface for system management traffic. You should direct backup and cloud tier data traffic to other interfaces, such as `eth1a`
- Each cloud unit can write to a separate supported cloud provider
- Cleaning of the active tier and the cloud tier takes place separately
- Replicated files are always placed first in the active tier first even when cloud tier is enabled
- Managed through a single namespace
  
## Supported cloud storage services
- Alibaba
- Amazon Web Services
- Elastic Cloud Storage
- Google Cloud Platform
- Microsoft Azure
- Flexible Cloud Tier Provider Framework for S3

## Cloud Tier Benefits
- When files move from the active tier to the cloud tier, PowerProtect DD deduplicates and stores the data in cloud object storage in its native format
- Lower TCO over time for long term retention
- Data is scheduled for movement to the cloud using policies based on the age of the data

## Retention Lock and Encryption
- You must use an encryption license
- You are prompted for the security officer username and password to enable encryption
- PowerProtect DD appliances using DD Retention Lock Compliance do not allow deleting files in the cloud unit
- Files that are under retention lock on the active tier can be moved to the cloud tier
- You can apply DD Retention Lock on files that are already in the cloud tier
- You can recall locked files to the active tier. The recalled files remain locked

## Model Sizing
- Each cloud unit has the maximum capacity of the active tier
- Dell cloud tier can scale up to twice the maximum capacity of the active tier
- The amount of required cloud tier metadata storage is based on the PowerProtect DD model
- Metadata shelves store metadata for both cloud units. The number of metadata shelves you need depends on the cloud unit physical capacity

## Cloud Tier Deduplication
- Each cloud unit has its own segment index and metadata and thus each cloud is a deduplication unit by itself
- Deduplication does not occur across the active tier and cloud tier

## Supported protocols for data movement
- Network File System (NFS) 
- Common Internet File System (CIFS) 
- DDBoost

## Cloud tier migration
- It is possible to migrate the system data from an older appliance that is configured with Dell cloud tier to a newer appliance
- The migration process moves the active tier storage, and the locally stored cloud tier metadata from the existing system to a new system
- During the cloud tier migration, the source system operates in a restricted mode

## Data Movement
- You can schedule the policy to run daily, weekly, or monthly and at a specific time of day
- The system moves files from the active tier to the cloud tier based on the date that the files were last modified
- You can also throttle the number of resources that the process can consume
- Data movement policies can be one of the following:
  - **Age threshold**:\
    If a files placement or modification time is greater than the age range set, it is selected for migration to the cloud tier
  - **Age range**:\
    If a file placement or modification time falls within a certain range, it is selected for migration to the cloud tier
  - **Application defined**:\
    The backup application designates if a file is to be selected for migration to the cloud tier

