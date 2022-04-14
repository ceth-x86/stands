
```
make rm-volumes
docker-compose up
```

Use `8124`, `8125`, `8126` ports for shards:

```sql
CREATE DATABASE IF NOT EXISTS billing;

CREATE TABLE IF NOT EXISTS billing.transactions(
    timestamp DateTime,
    currency String,
    value Float64)
ENGINE = ReplicatedMergeTree('/clickhouse/tables/{shard}/billing.transactions', '{replica}')
PARTITION BY currency
ORDER BY timestamp;
```

Use `8123` for master:

```sql
CREATE DATABASE IF NOT EXISTS billing;

CREATE TABLE IF NOT EXISTS billing.transactions(
    timestamp DateTime,
    currency String,
    value Float64)
ENGINE = Distributed(example_cluster, billing, transactions, rand());
```
