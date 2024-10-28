**Atomicity**

All the writes in a transaction are executed as a single unit and cannot be divided into smaller parts. If any error occurs during the transaction, all changes are undone, ensuring that either all the writes are applied or none at all. This is why atomicity is often described as "all or nothing."

**Consistency**

In this context, consistency refers to maintaining the integrity of the database by ensuring that all data adheres to the predefined rules and constraints. Unlike the CAP theorem's concept of consistency, which focuses on reading the latest write or returning an error, here it means that every transaction must leave the database in a valid state.

**Isolation**

When multiple transactions are running concurrently, isolation ensures that the operations of one transaction do not interfere with another. The strictest form of isolation is "serializability," where each transaction behaves as though it is the only one being processed. Although serializability is difficult to achieve in practice, more relaxed isolation levels are commonly used.

**Durability**

Once a transaction is successfully committed, the data is guaranteed to be stored permanently, even in the event of a system failure. In distributed systems, durability often involves replicating the data across multiple nodes to ensure it remains intact.