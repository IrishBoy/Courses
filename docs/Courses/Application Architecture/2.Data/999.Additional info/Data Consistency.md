In distributed systems, data is replicated across multiple nodes, requiring synchronization to maintain consistency. **Quorum consensus** ensures consistency for both read and write operations by defining specific thresholds for acknowledgments. Let’s clarify some key terms:

- **N**: The total number of replicas.
- **W**: The write quorum size. A write operation is considered successful only when acknowledgments are received from at least **W** replicas.
- **R**: The read quorum size. A read operation is successful when responses are received from at least **R** replicas.

### Example
![[Data Consistency.svg]]

In the example shown **N = 3** (replicas).

- **W = 1** does not mean data is written to only one server. Data is still replicated across all servers (**s0**, **s1**, and **s2**). However, the coordinator only needs one acknowledgment to mark the write operation as successful. For instance, if **s1** sends an acknowledgment, the coordinator does not need to wait for responses from **s0** or **s2**.

The **coordinator**, acting as a proxy between the client and the nodes, manages these quorum checks.

### Tradeoff: Latency vs. Consistency

The configuration of **N**, **W**, and **R** represents a tradeoff between operation speed and consistency:

- If **W = 1** or **R = 1**, operations complete quickly because the coordinator only waits for a response from one replica.
- If **W > 1** or **R > 1**, better consistency is achieved, but latency increases as the coordinator waits for responses from more replicas.

### Ensuring Strong Consistency

If **W + R > N**, the system guarantees strong consistency. This is because there will always be at least one replica with the latest data to ensure consistency.

### Common Configurations

Depending on use cases, different configurations of **N**, **W**, and **R** are used:

1. **Fast Read**:
    
    - **R = 1**, **W = N**
    - Data is written to all replicas, but reads return quickly by querying only one replica.
2. **Fast Write**:
    
    - **W = 1**, **R = N**
    - Writes require only one acknowledgment, but reads query all replicas for consistency.
3. **Strong Consistency**:
    
    - **W + R > N** (e.g., **N = 3, W = R = 2**)
    - Ensures there is at least one replica with the latest data in overlap between read and write quorums.
4. **Weaker Consistency**:
    
    - **W + R ≤ N**
    - Strong consistency is not guaranteed.

By tuning **N**, **W**, and **R**, systems can be optimized for desired levels of latency, throughput, and consistency based on specific requirements.