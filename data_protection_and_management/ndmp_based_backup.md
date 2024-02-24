## NDMP-based backup
![image](https://github.com/iamfabo/dellemc/assets/60046736/998d4e10-4ff1-4387-881c-e99702b32f52)

Network Data Management Protocol (NDMP) is an open standard TCP/IP-based protocol specifically designed for a backup in a NAS environment

- Data can be backed up using NDMP regardless of the OS
- Backup data is sent directly from NAS to the backup device
- No longer necessary to transport data through application servers
- Backs up and restores data while preserving security attributes of file system (NFS and CIFS)

The key components of an NDMP infrastructure are **NDMP client** and **NDMP server**
- The NDMP server has two components- data server and media server

The backup operation occurs as follows:
- Backup server uses NDMP client and instructs the NAS head to start the backup
- The NAS head uses its data server to read the data from the storage
- The NAS head then uses its media server to send the data read by the data server to the backup device
