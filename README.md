# Muhammad Pandu Dwi Cahyo

<p align="left">
  <a href="https://linkedin.com/in/mpandudc"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="https://mpandudc.com"><img src="https://img.shields.io/badge/Website-mpandudc.com-2ea44f?style=flat&logo=google-chrome&logoColor=white" alt="Website" /></a>
  <a href="mailto:mpandudc@gmail.com"><img src="https://img.shields.io/badge/Email-mpandudc%40gmail.com-blue?style=flat&logo=gmail&logoColor=white" alt="Email" /></a>
</p>

**Data Engineer Supervisor** with 4+ years of experience architecting high-throughput, low-latency streaming pipelines (10K+ RPS) and distributed data platforms in fintech and cryptocurrency (CFX, Pintu). Proven record in leading engineering teams, executing Snowflake/AWS migrations (25% compute cost reduction), and orchestrating Apache Flink, Spark, and Airflow on Kubernetes.

Currently pursuing an **MBA in Business Leadership Executive at SBM ITB** to bridge large-scale distributed data systems with strategic business growth, regulatory compliance, and quantitative product execution.

---

### 🌐 Distributed Systems & Infrastructure Topology

A hybrid private cloud architecture powering autonomous multi-agent systems, quantitative execution engines, distributed streaming analytics, and local lakehouse pipelines:

```mermaid
flowchart TB
    subgraph WAN [Edge & Ingress]
        CF[Cloudflare Edge / Tunnel]
        TS[Tailscale Private Mesh]
    end

    subgraph CLOUD_NODE [Private Infrastructure Node]
        direction TB

        subgraph AI_LAYER [AI Agent & Knowledge Gateway]
            H_ROSTER["Multi-Agent Runtime\n(Specialized Profiles & Autonomous Task Loops)"]
            R9["Context & Model Gateway\n(Adaptive Routing & Fallbacks)"]
            V_MCP["Second-Brain FastMCP\n(Hybrid RAG: Vector + Full-Text Search)"]
            NLM_MCP["Research FastMCP\n(Long-Context Offloading & Zero-Token Bypass)"]
        end

        subgraph QUANT_LAYER [Execution & Workflow Automation]
            CUANTUM["Algorithmic Execution Platform\n(Bracket Orders & Position Sizing Engine)"]
            N8N["Event Automation Engine\n(Webhooks & Operational Triggers)"]
        end

        subgraph DATA_LAYER [Data Platform & Lakehouse Lab]
            STREAM_PIPE["Real-time Streaming Engine\n(Event-Time Processing & Market Surveillance)"]
            AIRFLOW["Batch Orchestrator\n(Scheduled Ingestion & Lake DAGs)"]
            MINIO["Local Object Lakehouse\n(S3-Compatible Storage)"]
            LAKE_ENGINE["In-Process Analytics\n(Parquet & Analytical Transformations)"]
            PG[(Transactional Database\nLedger & State Persistence)]
            REDIS[(In-Memory Data Store\nTicker Cache & PubSub)]
        end

        subgraph NET_LAYER [Network & DNS Infrastructure]
            ADGUARD["Network DNS Resolver\n(Tailnet DNS Security & Policy Filter)"]
        end
    end

    subgraph EXTERNAL [External Knowledge & Data Providers]
        OBSIDIAN[("Knowledge Vault\nSecond Brain (Local Markdown)")]
        G_NLM[("Long-Context Engine\n1-2M Document Offload")]
        EXCHANGES[("Exchange WebSocket / REST\nMarket Feeds & Execution")]
    end

    %% Network Routing
    CF --> CUANTUM
    CF --> R9
    TS --> AI_LAYER
    TS --> DATA_LAYER
    TS --> NET_LAYER

    %% AI Pipeline
    H_ROSTER -->|Context Retrieval| V_MCP
    H_ROSTER -->|Document Grounding| NLM_MCP
    V_MCP <-->|Sub-Second Hybrid Search| OBSIDIAN
    NLM_MCP <-->|Direct Ingest Bypass| G_NLM

    %% Trading Pipeline
    H_ROSTER -->|Risk & Strategy Evaluation| CUANTUM
    CUANTUM <-->|Execution State| PG
    CUANTUM <-->|Live Cache| REDIS
    CUANTUM <-->|Market Data Ingress| EXCHANGES
    N8N -->|Trigger Automation| CUANTUM

    %% Data Lakehouse Pipeline
    AIRFLOW -->|Orchestrate Ingestion| MINIO
    STREAM_PIPE -->|Stream Micro-batches| MINIO
    AIRFLOW -->|Run Transformations| LAKE_ENGINE
    LAKE_ENGINE <-->|Storage Engine| MINIO
    AIRFLOW -->|Sync Reconciled Records| PG
```

---

### 🚀 Systems & Projects

#### 🤖 AI Engineering & Autonomous Agents
* **[notebooklm-fastmcp](https://github.com/mpandudc/notebooklm-fastmcp)** — Lean FastMCP server for Google NotebookLM. Built for zero-token context offloading, Google Master Token (AAS) auto-reminting, 1-shot audio deep dives, and Obsidian sync.
* **[obsidian-hybrid-rag-mcp](https://github.com/mpandudc/obsidian-hybrid-rag-mcp)** — High-performance MCP server delivering Two-Tier Hybrid RAG (FTS5 BM25 + dense BGE-M3 1024-dim vector + Jina cross-encoder reranking) with sub-second retrieval over private Markdown knowledge bases.

#### 📊 Real-Time Streaming & Lakehouse Systems
* **[flink-market-surveillance](https://github.com/mpandudc/flink-market-surveillance)** — Event-time market surveillance, wash-trading pattern detection, and deterministic replay harness built on Apache Flink and Kafka.
* **[spark-delta-lakehouse](https://github.com/mpandudc/spark-delta-lakehouse)** — Replay-safe Spark Structured Streaming and Delta Lakehouse implementation using ACID transactions and Medallion architecture.
* **[streaming-ml-features](https://github.com/mpandudc/streaming-ml-features)** — Online and offline streaming ML feature store parity system ensuring zero-drift feature computation and backfill replay.
* **[flink-vs-spark-benchmark](https://github.com/mpandudc/flink-vs-spark-benchmark)** — Reproducible, fair streaming benchmark comparing throughput, backpressure handling, and end-to-end event-time latency between Apache Flink and Spark Structured Streaming.
* **Data Platform Lab** *(Private / Self-Hosted)* — Local lakehouse orchestrating **Apache Airflow**, **MinIO**, and **DuckDB/dbt** to ingest, store, and transform market tickers into partitioned analytical layers.

#### 📈 Quantitative Trading & Financial Systems
* **[cuantum](https://github.com/mpandudc/cuantum)** *(Private)* — Self-hosted algorithmic crypto trading signal and order execution platform. Built on FastAPI, SQLAlchemy async, React/TypeScript, and CCXT. Features automated bracket execution and risk management across Binance and Bitget.
* **[duwit](https://github.com/mpandudc/duwit)** — Personal financial analytics engine and expense tracking suite built on Next.js, Drizzle ORM, and automated transaction reconciliation pipelines.

---

### 🛠️ Core Engineering Stack

```
Streaming & Big Data : Apache Flink, Apache Spark, Apache Airflow, Kafka, Apache Hudi, Delta Lake, dbt
Storage & Lakehouse  : Snowflake, BigQuery, MinIO, PostgreSQL, DuckDB, TimescaleDB, Redis
Cloud & Distributed  : AWS (EMR, S3, Glue, Lambda, Athena), Kubernetes, Docker, Terraform
Languages            : Python, SQL, C/C++, Rust, Bash
Architecture         : Medallion Architecture, CDC (Debezium/DMS), Streaming ML Feature Parity, High-throughput (10K+ RPS)
```

---

### 🎓 Background & Education

* **Master of Business Administration (MBA)** — School of Business and Management, Institut Teknologi Bandung (SBM ITB) *(Business Leadership Executive)*
* **Bachelor of Engineering (B.Eng.) in Computer Engineering** — Universitas Brawijaya *(Cum Laude, CGPA 3.93/4.00)*

---

<p align="left">
  <img src="https://github-readme-stats.vercel.app/api?username=mpandudc&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" height="150" alt="GitHub Stats" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=mpandudc&layout=compact&theme=tokyonight&hide_border=true" height="150" alt="Top Languages" />
</p>
