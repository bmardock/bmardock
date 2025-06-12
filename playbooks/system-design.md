# System Design Guide

*A concise, reusable checklist for tackling any large‑scale system design question.*

### 1. Clarify Requirements

* Ask questions to nail the exact scope (e.g. for a Twitter‑like service: post tweets, follow users, timeline display?).
* Identify must‑have vs. nice‑to‑have features **before** moving on.

### 2. Define System Interface

* Draft the external APIs with parameters and return types.
* Example (Twitter):

  ```
  POST /tweet            # postTweet(user_id, content, ...)
  GET  /timeline/:userId # generateTimeline(user_id, ...)
  POST /favorite         # markTweetFavorite(user_id, tweet_id, ...)
  ```

### 3. Back‑of‑the‑Envelope Estimation

* Ballpark QPS, storage, and bandwidth needs.
* Guides scaling, partitioning, load balancing, and caching decisions.

### 4. Define the Data Model

* List core entities and their attributes; sketch an ER diagram.
* Choose storage tech (RDBMS vs. NoSQL) and object storage for media.

### 5. High‑Level Design

* Draw a 5‑6 box diagram of core components (LB, app servers, DB, cache, media store).
* Separate read‑heavy traffic from write‑heavy if needed.

### 6. Detailed Design & Trade‑offs

* Dive into each component; discuss alternative approaches and trade‑offs.
* Consider data partitioning, hot‑user mitigation, cache layers, load balancing.

### 7. Identify & Resolve Bottlenecks

* Spot single points of failure; plan replication and failover.
* Define monitoring and alerting for critical components.

---

**Pro Tip:** After each step, *pause and verify* the previous assumptions still hold. Iteration beats perfection.
