### Features

| **Dell PowerProtect Data Manager Features**                  | **Description**                                                                                                                                                                                                                                                                                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Centralized protection                                       | The centralized protection policy manages the entire life cycle of the protected data, and the monitoring is through the PowerProtect Data Manager                                                                                                                                                                             |
| Self-Service protection                                      | You can run the self-service protection manually. PowerProtect Data Manager manages and monitors other backup-related tasks, such as PowerProtect DD user and storage unit                                                                                                                                                     |
| Crash Consistent protection                                  | The crash consistent protection policy captures all the virtual machine disks simultaneously and creates an image-level backup of the virtual machines                                                                                                                                                                         |
| Application-aware protection                                 | The application-aware protection policy creates a virtual SQL server application-consistent backup with transaction log protection and truncation                                                                                                                                                                              |
| Mission-critical applications and modern workloads           | PowerProtect Data Manager supports the Kubernetes cluster, network attached storage (NAS), Oracle database, SAP HANA database, Microsoft SQL and Exchange database, VMware virtual machine, and Windows and Linux file systems protection                                                                                      |
| Discover assets automatically                                | PowerProtect Data Manager can automatically discover any new assets, such as Kubernetes namespace, Oracle database, SAP HANA database, Microsoft SQL and Exchange database, and virtual machine                                                                                                                                |
| PowerProtect DD and DD Virtual Edition as protection storage | PowerProtect Data Manager supports PowerProtect DD appliances, PowerProtect DD Virtual Edition, PowerProtect DD Management Center (DDMC), and DDMC Smart Scale system pool as protection storage                                                                                                                               |
| Application direct workloads                                 | Application direct enables database owners to back up and restore directly from native database applications to PowerProtect DD series appliances while PowerProtect Data Manager enables oversight and governance
| VM direct workloads                                          | PowerProtect Data Manager integrates with the VM direct engine to improve the backup performance and reduce network bandwidth utilization during VMware virtual machine backups                                                                                                                                                |
| SaaS-based and native reporting engine                       | Integrated with CloudIQ, PowerProtect Data Manager presents an aggregated view of data protection within the customers' environment across all sites and supported systems PowerProtect Data Manager comes with a native reporting engine and report browser                                                                  |
| In-Cloud workloads protection                                | PowerProtect Data Manager can be deployed in Amazon AWS, Microsoft Azure, Google Cloud Platform (GCP), and Oracle Cloud VMware Solution (OCVS) to protect the in-cloud workloads                                                                                                                                               |

#### Health

- PowerProtect Data Manager automatically performs a health check every two minutes
- Resolved issues are automatically removed during the next health check

#### Copy Management
![image](https://github.com/user-attachments/assets/c72b0465-b5c2-4de5-8615-4b017755e93d)
The Copy Management option allows PowerProtect Data Manager administrators to view and manage all backup copies at a single glance.

Copy Management feature supports the following use cases:

- View detailed information of backup copies on a single page
- Edit backup retention periods for one or more backup copies
- Delete one or more backup copies from the protection storage
- Remove one or more backup copy records from the PowerProtect Data Manager database, but keep the backup copies in the protection storage
- Locate specific backup copies through the advanced search and filters

The Copy Management option allows PowerProtect Data Manager administrators to view and manage all backup copies at a single glance.

Copy Management feature supports the following use cases:

- View detailed information of backup copies on a single page
- Edit backup retention periods for one or more backup copies
- Delete one or more backup copies from the protection storage
- Remove one or more backup copy records from the PowerProtect Data Manager database, but keep the backup copies in the protection storage
- Locate specific backup copies through the advanced search and filters

### Protection Engines
![image](https://github.com/user-attachments/assets/6eb6c722-db56-422d-b83e-cad5e8781bd3)

The VM Direct Protection Engine, formerly VM Proxy or vProxy, leverages the VMware vStorage API for Data Protection (VADP). It's deployment as a virtual appliance in the VMware vSphere environment is to perform the virtual machine snapshot backups and then move the backup data to a PowerProtect DD appliance.

PowerProtect Data Manager supports the following types of protection engines:

| **Protection Engine Types**     | Description                                                                                                                                                                                                                                                                                                                                                            |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Embedded VM Direct Engine       | - Embedded VM Direct Engine is an integrated vProxy in the PowerProtect Data Manager<br>- Can be used in small environments that do not utilize concurrent VM backups and Hot Add transport mode                                                                                                                                |
| External VM Direct Engine       | - Designed for large environments that require concurrent VM backups and NAS protection<br>- External VM Direct Engine is configured on the ESXi hosts in the environment |
| Transparent Snapshot Data Mover | - Uses the vSphere API for I/O (VAIO) Filtering framework<br>- TSDM's deployment in the VMware ESXi infrastructure through a vSphere Installation Bundle (VIB)<br>- Creates consistent VM backup copies and writes the copies to the protection storage like the PowerProtect DD series                                         |

The PowerProtect VM Direct Engines support the following three transport modes:
- Hot Add
- NBD
- Hot Add with fallback to NBD

PPDM manages the TSDM component by using the VIB from Dell Technologies. You can install this component dynamically as part of the integration of PowerProtect Data Manager which requires the protection of VMs using transparent snapshots. The APIs being used are supported in VMware ESXi 7.0 U3 and later.
