## Deduplication methods
![image](https://github.com/iamfabo/dellemc/assets/60046736/c63d1e5c-85c1-463f-a3e6-99905bf0386e)

- When the deduplication occurs close to where the data is created (backup client), it is referred to as [source-based deduplication](https://github.com/iamfabo/dellemc/edit/main/data_protection_and_management/deduplication.md#source-based-deduplication)
- When it occurs near where the data is stored (backup device), it is referred as target-based deduplication. In a [target-based deduplication](), the deduplication can happen in-line or post-process
### Source-based deduplication
![review+MG+5+final-_1](https://github.com/iamfabo/dellemc/assets/60046736/cc3c35c2-0fce-4a84-9c29-fe4bc12b21c7)
- The backup client sends only new, unique segments across the network
- The deduplication server maintains a hash index of the deduplicated data
- The deduplication agent running on the clients checks each file for duplicate content, it creates the hash value for each chunk of the file
- If the chunk has already been backed up, then it won't be sent to the deduplication server by the client, which ensures that the redundant backup data is eliminated at the client

### Target-based deduplication
![review+MG+6+final-_1](https://github.com/iamfabo/dellemc/assets/60046736/1f4751c5-b0e9-483b-a039-61e264c89cca)
- Data is deduplicated at the target
- Client is not affected since deduplication process takes place at target
- Requires much more bandwidth to send data over the network during backup than source-based deduplication backup
- Data is deduplicated at the backup device, either inline or post-process
