## Cache Evictions Runbook (Redis/Memcached)

- Symptom: elevated latency + "OOM" or evicted_keys > baseline
- Check metrics: memory_used_bytes, evicted_keys, hit_ratio
- Actions:
  1) Raise maxmemory or lower eviction rate by increasing capacity
  2) Set eviction policy to allkeys-lru for mixed workloads
  3) Add per-tenant TTLs; purge keys > size threshold
  4) For EKS: ensure pod requests/limits keep margin to avoid OOMKill
- Post-mortem note: record spike window and top keys if available
