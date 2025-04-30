## Minimum intervals to include each query (can be also solved using sweep line)

- sort the events
- for each query in sorted(queries)
- insert into heap those intervals whose start <= current query (interval_len, interval_end)
- after that pop from heap whose interval_end < query
- if heap still contains element then answer will be top of heap
- else answer is -1

## Maximum Number of events that can be attended


## Maximum Profit in job Scheduling (can be solved using dp as well)