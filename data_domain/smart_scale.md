## Smart Scale

![smart_scale](https://github.com/user-attachments/assets/2a1072eb-65c6-4d8e-8253-6b6f158fbfab)

Smart Scale allows to manage up to **32** PowerProtect DD appliance in a single system pool under a unified namespace driving down management complexity while increasing storage efficiency.

Supported by:
- DD9900
- DD9400
- DD6900
- DD6400
- DDVE on-premises (vSphere)

## Data Domain Management Center (DDMC)
Smart Scale is orchestrated by the Data Domain Management Center (DDMC), which is deployed as a virtual machine.\
The DDMC configures and controls Smart Scale data movement in the following ways:

- The systems can span across as many as **four pools** in a single data center
- Smart Scale provides up to **48 PB of usable capacity** or over 3 EB logical capacity with typical deduplication rates
- Smart Scale provides an on-demand mobile storage unit (MSU) transfer, sparing the customer from manually rebalancing storage units
- Mobile storage units (MSU) are transportable from one PowerProtect DD system to another within a system pool

![Pasted image 20240604122813](https://github.com/user-attachments/assets/720dc801-320e-4553-9f25-e4e9a0b99196)

> [!IMPORTANT]
> - Smart Scale is deployed through the PowerProtect DD Management Center (DDMC)
> - DDMC operates as the control path for Smart Scale
> - PowerProtect DD systems can belong to only one data center
> - Dell recommends creating no more than four system pools per data center for Smart Scale services
> - The DDOS version must be 7.8 or later, 7.11 or later for DDVE
> - DD Boost must be enabled on the PowerProtect DD systems
> - DDMC manages all mobile storage units (MSU) and all mobile boost users (MBU)
> - A system pool manages available capacity as a group of systems instead of selecting individual PowerProtect DD appliances

## DD Namespace VM
- DDMC deploys the DD Namespace VM (DDNVM)
- The DDNVM is a virtual machine that runs the DD Namespace Redirection Service (DDNRS)
- The DDNRS is used with Smart Scale to manage its credential and backup set databases
- The DD Namespace VM is mostly stateless and is used in the data path for initial connection redirection

![Pasted image 20240604123545](https://github.com/user-attachments/assets/b035221d-2326-40cf-8d74-44f6cb3c98ff)
## Disaster Recovery Restore Operations with Smart Scale

- To perform a DDMC recovery, deploy a new DDMC with the same version and mount the MTree that has the backup on the new DDMC
- Following is a table that explains which recovery operation should be used when experiencing a corrupt or destroyed DDMC instance, or DD Namespace VM (DDNVM), or both:

| DDMC                 | DD Namespace VM (DDNVM) | Solution                                                                                                                |
| -------------------- | ----------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Good                 | Corrupt or destroyed    | Restart DDNVM from vCenter. Redeploy the service from the DDMC UI and sync the data if a restart does not fix the issue |
| Corrupt or destroyed | Good                    | DDMC DR                                                                                                                 |
| Corrupt or destroyed | Corrupt or destroyed    | Recover DDMC from DR backup and redeploy DDNVM from the DDMC UI                                                         |
