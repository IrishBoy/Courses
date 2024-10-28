In the context of storing data in a computer system, this means that the data survives after the process with which it was created has ended. In other words, for a data store to be considered persistent, it must write to non-volatile storage.

### **Which data stores provide persistence?**

If you need persistence in your data store, then you need to also understand the four main design approaches that a data store can take and how (or if) these designs provide persistence:

- Pure in-memory, no persistence at all, such as memcached or Scalaris
- In-memory with periodic snapshots, such as Oracle Coherence or Redis
- Disk-based with update-in-place writes, such as MySQL ISAM or MongoDB
- Commitlog-based, such as all traditional OLTP databases (Oracle, SQL Server, etc.)

In-memory approaches can achieve blazing speed, but at the cost of being limited to a relatively small data set. Most workloads have relatively small "hot" (active) subset of their total data; systems that require the whole dataset to fit in memory rather than just the active part are fine for caches but a bad fit for most other applications. Because the data is in memory only, it will not survive process termination. Therefore these types of data stores are not considered persistent.