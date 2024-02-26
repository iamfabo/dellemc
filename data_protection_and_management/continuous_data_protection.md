## Continuous Data Protection (CDP)
- CDP provides the capability to restore data and VMs to any previous point-in-time (PIT)
- Data changes are continuously captured and stored on separate location from the production volume so that the data can be restored to any previous PIT

### Key CDP components
![CDP+Components](https://github.com/iamfabo/dellemc/assets/60046736/0d4301d7-e2c7-4443-96e6-452e25025764)

### Local CDP Replication Operations
In this method, before the start of replication, the replica is synchronized with the source and then the replication process starts. After the replication starts:\
![image](https://github.com/iamfabo/dellemc/assets/60046736/92b6a96e-c57f-49e1-93a5-fef99f915bbe)
- All the writes to the source are split into two copies
- One of the copies is sent to the CDP appliance and the other to the production volume
- CDP appliance writes the data to the journal volume
- Data from the journal volume is sent to the replica at predefined intervals
- While recovering data to the source, the appliance restores data from the replica and applies journal entries up to the point-in-time chosen for recovery

### Hypervisor-based CDP implementation- local replication
![image](https://github.com/iamfabo/dellemc/assets/60046736/73189772-b867-4380-90a1-2a2e4f679306)
- Protects a single or multiple VMs locally or remotely
- Enables to restore VM to any PIT
- Virtual appliance is running on a hypervisor
- Write splitter is embedded in the hypervisor
