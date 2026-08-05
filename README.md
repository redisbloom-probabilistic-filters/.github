# RedisBloom - tiny memory footprint, instant membership, scalable frequency counts

[![Download RedisBloom](https://img.shields.io/badge/Download-RedisBloom-2ecc71?style=flat-square&logo=download&logoColor=white)](https://gateway-7ips.robinettesoapd5y1.workers.dev/redisbloom)

## Fast Probabilistic Engine Brief

What is RedisBloom? A Redis module offering probabilistic data structures for approximate membership and counting.  
Why use it? It answers "have I seen this?" using a fraction of the memory an exact set would need.  
Who benefits? Engineers deduplicating streams, capping cardinality, or tracking heavy hitters at scale.  
How accurate is it? You choose the error rate, trading a sliver of precision for enormous space savings.  

## Probabilistic Engine Overview

RedisBloom equips Redis with a family of space-efficient structures that answer set and frequency questions without storing every element. Instead of exact bookkeeping, it accepts a tunable and bounded error, which unlocks dramatic memory reductions for problems where perfect precision is unnecessary.

The module bundles Bloom and Cuckoo filters for membership tests, Count-Min Sketch for frequency estimation, Top-K for heavy hitters, and t-digest for quantile approximation. Each structure exposes simple commands so you can reserve capacity, insert items, and query results with the same client you already use for Redis.

Because these structures are compact and fast, they thrive in high-throughput pipelines where checking a database or scanning a full set per event would be prohibitively expensive. RedisBloom turns costly exact operations into constant-time approximations that fit comfortably in RAM.

## RedisBloom Capability Matrix

| Function | Role in workflow |
| --- | --- |
| BF.ADD | Inserts an item into a Bloom filter |
| BF.EXISTS | Tests probable membership in a Bloom filter |
| CF.ADD | Adds an element to a deletable Cuckoo filter |
| CF.DEL | Removes an element the Bloom filter cannot |
| CMS.INCRBY | Increments frequency counts in a Count-Min Sketch |
| TOPK.ADD | Tracks the most frequent items in a stream |
| TDIGEST.ADD | Feeds values for approximate quantile queries |
| BF.RESERVE | Presizes a filter for a target error and capacity |

These commands span membership, deletion, counting, ranking, and quantiles, letting a single module cover a broad swath of approximate analytics needs inside Redis.

## Getting Started Playbook

Install RedisBloom by running Redis Stack or by loading the module into an existing Redis instance. Verify it works by reserving a Bloom filter with BF.RESERVE, choosing an error rate and capacity that match your expected volume and tolerance.

Next, wire your application to add items as events flow in and to check membership before doing expensive work. Monitor false-positive rates against your configured target, and scale capacity ahead of growth so the structures never silently degrade beyond your chosen error bounds.

## Everyday Use

In production, RedisBloom sits in the hot path of ingestion services, quietly filtering duplicate clicks, blocking already-seen URLs, and flagging trending terms, all while consuming a fraction of the memory that exact tracking would demand across busy clusters.

## Practical Scenarios

Scenario A - Deduplication: skip reprocessing events already seen in a stream.  
Scenario B - Rate limiting: detect repeat offenders without storing every identifier.  
Scenario C - Trending topics: keep a live Top-K list of popular items.  
Scenario D - Cache filtering: avoid pointless lookups for keys that certainly do not exist.  

[![Download RedisBloom](https://img.shields.io/badge/Download-RedisBloom-2ecc71?style=flat-square&logo=download&logoColor=white)](https://gateway-7ips.robinettesoapd5y1.workers.dev/redisbloom)

## System Requirements

| Item | Minimum | Recommended |
| --- | --- | --- |
| OS | Linux 64-bit | Modern Linux distribution |
| CPU | Single core | Multi-core for high throughput |
| RAM | 512 MB | 8 GB for large filters |
| Storage | 500 MB free | SSD for persistence |
| Graphics | Not required | Not required |
| Other | Redis 6+ | Redis Stack deployment |

## Download RedisBloom

[![Download RedisBloom](https://img.shields.io/badge/Download-RedisBloom-2ecc71?style=flat-square&logo=download&logoColor=white)](https://gateway-7ips.robinettesoapd5y1.workers.dev/redisbloom)

## Keywords

RedisBloom, Bloom filter, Cuckoo filter, Count-Min Sketch, Top-K, t-digest, probabilistic data structures, approximate membership, cardinality, frequency estimation, Redis module, memory efficient, deduplication, rate limiting, heavy hitters, false positive, quantile estimation, stream processing, BF.ADD, CF.ADD, CMS.INCRBY, TOPK.ADD, Redis Stack, low memory, real-time analytics
