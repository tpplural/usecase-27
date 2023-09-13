## Trade-off: Data sharing between desktop and cloud
### Shared database

Entries in the table are not correlated, and only list a pro and cons that were defined in the process

|Advantages | Disanvatnages |
| --- | ----------- | 
| Migrating to Citrix Azure VM or Remote Desktop can potentially offer better performance, scalability, and reliability. |Migration Risks: Moving a desktop application to a virtual environment can introduce unforeseen challenges.|
|Restructuring the database for modern needs might lead to better efficiency, data integrity, and easier future enhancements. | Complex Transition: Major restructuring of the database can lead to migration challenges, especially if there's a lot of legacy data.|
| Hosting the database on Azure SQL offers advantages like scalability, backup solutions, replication, and more. | Potential UI/UX Disruptions: While some changes are beneficial, they might disrupt existing users who are accustomed to the current interface.
| Changing the DBIF ensures that the application and database are in harmony, potentially leading to fewer issues in the future. | Cost Implication: Both Citrix and Azure services have associated costs.

### Data sync from on-premise
|Advantages | Disanvatnages |
| --- | ----------- | 
| Minimal Disruption: By keeping the current application as it is, there's less risk of disrupting end-users. |Increased Complexity: Managing synchronization between on-premise and cloud can introduce complexity, especially handling sync failures, conflicts, etc.|
|Simpler Database Changes: Only adding change flags is simpler than a full restructuring.| Latency Issues: Depending on the frequency and volume of sync, there might be delays in data availability or potential data inconsistencies between systems.|
|Flexibility: A new windows service with REST API syncing offers flexibility in managing data transfer to Azure.| Maintenance Overhead: Two systems need maintenance – the on-premise application and the Azure-based sync service.
| Staged Approach: This solution might be seen as a stepping stone to a full migration later, allowing for phased implementation and easier rollback. | Potential Sync Costs: Depending on the volume of data, sync frequency, and network costs, there could be an overhead associated with continuous synchronization.

### Synchronisation of data in the cloud

|Advantages | Disanvatnages |
| --- | ----------- | 
|**Mitigated Connectivity Concerns:** By moving the application to Citrix Azure VM or Remote Desktop, there's less reliance on continuous connectivity for the sync process.|**Potential Complexity:** Introducing background workers can add to the system's complexity.|
|**Scalable Data Sync:** Using background workers (like Azure Functions) can allow for scalable data syncing based on demand.|**Additional Storage Needs:** Like in Option 1, a separate minimal storage for sync state will be needed.|
|**All Benefits of Option 2:** This option inherits the advantages of Option 2 like modern infrastructure and database optimization.|**Migration Effort & Training Needs:** Similar to Option 2, this option will require considerable migration effort and user retraining.|

### Decision

Given the analysis results, it is recommended to pursue storing the data in Azure SQL Database. Having the advantages of cloud solution (managed and scalable service, easier integration with other components) should discount the higher migration effort that is connecetd with scenario 3. That postulate must be confronted with the planned budget and delivery timeline.

 