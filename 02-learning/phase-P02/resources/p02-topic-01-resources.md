# P02 · Topic 1: Vector DB Architecture (pgvector Deep Dive)
**Phase:** P02 RAG Deep Dive
**Status:** Reference material — use AFTER completing Topic 1 learning
**Last Updated:** 2026-06-10
**Rule:** Generated after topic completed. Web-fetched for freshness.

---

## 🗺️ The Map (Quick Recap)

```
SEARCH TYPES — Know all three:
Exact scan  → no index, compares EVERY row, 100% recall, O(n), dies at scale
HNSW ★      → graph layers, airport-hub routing, ~97-99% recall, O(log n), RAG DEFAULT
IVFFlat     → k-means buckets, scan nearest buckets only, ~90-95% recall, low RAM
```

**The three knobs (which one, what cost):**
```
m=16               → connections/node     → BUILD-TIME → change = FULL REINDEX
ef_construction=64 → build effort (AOT)   → BUILD-TIME → change = FULL REINDEX
ef_search=40→100   → query candidate list → QUERY-TIME → one line, instant, FREE
                     SET hnsw.ef_search = 100;  (recall ~95%→99% for +3ms)
```

**Debug order — "right doc sometimes missing" (memorize):**
```
1. Raise ef_search (free, instant)
2. Isolate the layer: SET LOCAL enable_indexscan = off → force exact scan
   Found? → index recall problem. Still missing? → embedding meaning gap.
3. Embedding gap → hybrid search / chunking / reranking (T2-T5)
4. Rebuild m/ef_construction = LAST resort (hours of compute @ 2M vectors)
```

**Invisible bug:** operator class MUST match query operator.
`vector_cosine_ops` ↔ `<=>`. Mismatch = index silently ignored, full scan, zero error.

**Capacity math:**
```
1536 dims × 4 bytes ≈ 7 KB/vector all-in (HNSW overhead included)
400k chunks (10k docs)   → ~3 GB    → pgvector laughs
4M chunks (100k docs)    → ~32 GB   → pgvector fine
40M chunks (1M docs)     → ~300 GB  → possible, painful
400M+                    → ~1 TB+   → Qdrant/Pinecone territory
Index spills to disk → 5ms becomes 200ms → CLIFF, not slope.
```

**ArNir status:** HNSW deployed (m=16, ef_construction=64, vector_cosine_ops)
on 35 vectors = future infrastructure. Does nothing measurable today;
mandatory at enterprise scale. Operator class matches `<=>` — correct by design.

---

## 📰 Blog / Article

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **pgvector Official README — Index Reference** | [github.com/pgvector/pgvector](https://github.com/pgvector/pgvector) | • Canonical source: exact scan = default (perfect recall), index = approximate trade • HNSW builds fine on empty table (no training step) — IVFFlat cannot • `SET LOCAL hnsw.ef_search = 100` inside transaction = per-query tuning • Best for: bookmark as THE reference for every pgvector decision |
| 2 | **The Ultimate Guide to Using pgvector (millions of rows)** | [medium.com](https://medium.com/@intuitivedl/the-ultimate-guide-to-using-pgvector-76239864bbfb) | • Real benchmark: HNSW query ~2s on millions of rows vs full-scan minutes • Gotcha: CROSS JOIN breaks HNSW index → silent full-table scan • pgvector 0.8.0 `hnsw.iterative_scan` fixes filtered-search recall loss • Best for: production patterns beyond hello-world demos |
| 3 | **HNSW Indexes with Postgres and pgvector — Crunchy Data** | [crunchydata.com](https://www.crunchydata.com/blog/hnsw-indexes-with-postgres-and-pgvector) | • Raising m/ef_construction slows builds drastically, often without query gains • `SET hnsw.ef_search` session vs `SET LOCAL` transaction scoping • Don't throw away IVFFlat — still wins specific RAM-constrained cases • Best for: understanding build-time vs query-time cost split |
| 4 | **Optimize pgvector Search — Neon Docs** | [neon.com](https://neon.com/docs/ai/ai-vector-search-optimization) | • Sequential vs HNSW vs IVFFlat benchmarks side by side • m guidance: start 12-48 range; default 16 fits most RAG workloads • Recall defined properly: relevant retrieved / total relevant • Best for: explaining recall to a client in one paragraph |

---

## 🎥 YouTube Video / Long Read

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **Accelerate HNSW with pgvector on Aurora/RDS — AWS** | [aws.amazon.com](https://aws.amazon.com/blogs/database/accelerate-hnsw-indexing-and-searching-with-pgvector-on-amazon-aurora-postgresql-compatible-edition-and-amazon-rds-for-postgresql/) | • AWS-grade tuning: maintenance_work_mem must fit graph for fast builds • Confirms m=16 / ef_construction=64 as production defaults • ef_search = primary recall lever; m/ef_construction = secondary • Best for: enterprise client conversations (AWS = credibility anchor) |

---

## 📱 Quick Reference

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **Tuning Approximate Indexes in pgvector — CodeSignal** | [codesignal.com](https://codesignal.com/learn/courses/indexing-optimization-and-scaling-pgvector/lessons/tuning-and-running-queries-with-approximate-indexes-in-pgvector) | • Two knobs to remember: `ivfflat.probes` and `hnsw.ef_search` • Constraint: ef_search >= k (requested results) • Hands-on exercises for both index types • Best for: 15-min practice session before client audit |

---

## 🏢 Vendor Decision Table (2026 landscape)

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **pgvector vs Pinecone vs Qdrant vs Weaviate — Production** | [kalviumlabs.ai](https://www.kalviumlabs.ai/blog/vector-databases-compared-pgvector-pinecone-qdrant-weaviate/) | • 45-80ms pgvector latency invisible inside 2s LLM response — DB ≠ bottleneck • Migration cost real: re-embed/export, rebuild index (2-4 hrs @ 1M), rewrite filter syntax • Qdrant wins selective metadata filtering; Weaviate wins multi-modal • Best for: the "should we migrate?" client conversation |
| 2 | **100M Vector Benchmark — 4-way Comparison** | [tensoria.fr](https://tensoria.fr/en/blog/vector-database-comparison) | • Verdict: "Start with pgvector. Migrate when you have a MEASURED reason." • Vector store = least interesting problem; chunking/eval matter more • Hybrid search core requirement → Qdrant/Weaviate from day one • Best for: consultant positioning — measure first, migrate second |
| 3 | **pgvector vs Pinecone vs Qdrant 2026 Benchmarks** | [vecstore.app](https://vecstore.app/blog/vector-database-performance-compared) | • Real numbers: pgvector HNSW 5-8ms; embedding generation 90ms = actual bottleneck • Pinecone does NOT expose HNSW tuning — recall is whatever they chose • Qdrant filtered search = best-in-class; Milvus = billion-vector scale • Best for: hard numbers in proposals |

---

## 🏢 Real Business Use Cases

| Scenario | Decision | Why |
|----------|----------|-----|
| Legal firm, 200k contracts | pgvector + HNSW, ef_search=100 | Missed clause = liability → recall first; scale fits Postgres |
| Startup demo → production | pgvector v1, ship in 2 weeks | Migrate only on measured latency pain, not anticipation |
| E-commerce search-as-you-type | Qdrant | Vector query IS the user-visible step; <10ms matters |
| Budget VPS 8GB, 2M vectors, stable corpus | IVFFlat | ~3× less RAM; data stable = clusters won't go stale |
| Client adds 500k docs over 6 months on IVFFlat | Switch to HNSW | Stale clusters = silent recall drop 93%→78% |
| Multi-region consumer AI, billions of vectors | Pinecone / Milvus | Beyond Postgres expertise ceiling |

---

## 💡 ArNir-Specific Notes

```
DEPLOYED THIS TOPIC (commit 43f7dc7):
✅ HNSW index: vector_cosine_ops, m=16, ef_construction=64
✅ Operator match verified: cosine_ops ↔ <=> in RetrievalService SQL
✅ 3-layer config: PlatformSettings DB → appsettings → constants
✅ VectorDbContextFactory (IDesignTimeDbContextFactory) for EF CLI migrations

KNOWN STATE:
- 35 vectors today → index = future infrastructure (correct move)
- Score threshold, hybrid weights, context caps now admin-tunable live

WATCH FOR:
- Document-scope filter (WHERE DocumentId IN ...) + HNSW = filtered-search
  recall loss → pgvector 0.8.0 iterative_scan if it bites
- ef_search default 40 → raise to 100 when corpus grows past ~100k chunks
```

---

## ✅ After Reading Checklist

- [ ] Can explain exact vs HNSW vs IVFFlat in one sentence each
- [ ] Know which knob is build-time (m, ef_construction) vs query-time (ef_search)
- [ ] Can run the isolate-the-layer diagnostic (enable_indexscan = off)
- [ ] Know the operator-class invisible bug (cosine_ops ↔ <=>)
- [ ] Can do RAM math: 7 KB/vector → docs → chunks → GB
- [ ] Know pgvector ceiling (~10-50M vectors) and migration triggers
- [ ] Memorized 3 consultant pitches (see consultant card)
- [ ] Know IVFFlat's two gotchas: empty-table build + stale clusters

---

## 🔗 Related

- Previous Phase: `02-learning/phase-P01/resources/p01-topic-05-resources.md`
- Next: `p02-topic-02-resources.md` (Chunking Strategies)
- Consultant card: `02-learning/phase-P02/consultant-cards/p02-topic-01-consultant-card.png`
- Mind map: `02-learning/phase-P02/mindmaps/p02-topic-01-mindmap.png`
- ADR: `00-system/decisions/ADR-0005-resource-format.md`, `ADR-0009-consultant-cards.md`
