# Muhammad Pandu Dwi Cahyo

<p align="left">
  <a href="https://linkedin.com/in/mpandudc"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="https://mpandudc.com"><img src="https://img.shields.io/badge/Website-mpandudc.com-2ea44f?style=flat&logo=google-chrome&logoColor=white" alt="Website" /></a>
  <a href="mailto:mpandudc@gmail.com"><img src="https://img.shields.io/badge/Email-mpandudc%40gmail.com-blue?style=flat&logo=gmail&logoColor=white" alt="Email" /></a>
</p>

**Data Engineer Supervisor** with 4+ years of experience architecting high-throughput, low-latency streaming pipelines (10K+ RPS) and distributed data platforms in fintech and cryptocurrency (CFX, Pintu). Proven record in leading engineering teams, executing Snowflake/AWS migrations (25% compute cost reduction), and orchestrating Apache Flink, Spark, and Airflow on Kubernetes.

Currently pursuing an **MBA in Business Leadership Executive at SBM ITB** to bridge large-scale distributed data systems with strategic business growth, regulatory compliance, and quantitative product execution.

---

### 🌐 Distributed Systems & Homelab Topology

A hybrid self-hosted private cloud powering autonomous AI agents, quantitative execution engines, local data lakehouse pipelines, and second-brain retrieval:

```mermaid
flowchart TB
    subgraph WAN [Edge & Ingress]
        CF[Cloudflare Edge / Tunnel]
        TS[Tailscale Private Mesh]
    end

    subgraph HOMELAB [Private Infrastructure Node]
        direction TB

        subgraph AI_LAYER [AI Agent & Knowledge Gateway]
            H_ROSTER["Hermes Multi-Agent Hub\n@hermes (Knowledge) | @coder (SRE) | @quant (Trading)"]
            R9["9router LLM Context Gateway"]
            V_MCP["vault-mcp (FastMCP)\nTwo-Tier Hybrid RAG (BGE-M3 + BM25)"]
            NLM_MCP["notebooklm-fastmcp (FastMCP)\nGoogle Master Token & 1-Shot Audio Deep Dive"]
        end

        subgraph QUANT_LAYER [Execution & Workflow Automation]
            CUANTUM["cuantum (Private)\nFastAPI Async + React + CCXT\nBinance/Bitget Bracket Execution"]
            N8N["n8n Automation Engine\nEvent-Driven Webhook Pipelines"]
        end

        subgraph DATA_LAYER [Data Platform & Lakehouse Lab]
            AIRFLOW["Apache Airflow\nBatch Orchestration & Data Pipelines"]
            MINIO["MinIO Object Storage\nS3-Compatible Local Data Lake"]
            DUCKDB["DuckDB & dbt Engine\nIn-Process Analytics & Lake Transformations"]
            PG[(PostgreSQL\nTransactional State & App DB)]
            REDIS[(Redis\nHigh-Throughput Cache & PubSub)]
        end

        subgraph NET_LAYER [Network & DNS Infrastructure]
            ADGUARD["AdGuard Home DNS\n(Tailnet-wide DNS Security)"]
        end
    end

    subgraph EXTERNAL [External Knowledge & Data Providers]
        OBSIDIAN[("Obsidian Vault\nSecond Brain (Local Markdown)")]
        G_NLM[("Google NotebookLM\n1-2M Context Engine")]
        EXCHANGES[("Exchanges API\nBinance / Bitget WebSocket")]
    end

    %% Network Routing
    CF --> CUANTUM
    CF --> R9
    TS --> AI_LAYER
    TS --> DATA_LAYER
    TS --> NET_LAYER

    %% AI & Second Brain Pipeline
    H_ROSTER -->|Context Retrieval| V_MCP
    H_ROSTER -->|Document Grounding| NLM_MCP
    V_MCP <-->|Sub-Second Hybrid Search| OBSIDIAN
    NLM_MCP <-->|Direct Ingest Bypass| G_NLM

    %% Quantitative Trading Pipeline
    H_ROSTER -->|Risk & Strategy Evaluation| CUANTUM
    CUANTUM <-->|Execution State| PG
    CUANTUM <-->|Live Ticker Cache| REDIS
    CUANTUM <-->|Market Data Ingress| EXCHANGES
    N8N -->|Trigger Automation| CUANTUM

    %% Data Engineering Lakehouse Pipeline
    AIRFLOW -->|Orchestrate Ingestion| MINIO
    AIRFLOW -->|Run Transformations| DUCKDB
    DUCKDB <-->|Lakehouse Storage| MINIO
    AIRFLOW -->|Sync Trading History| PG
```

---

### 🚀 Systems & Projects

#### 🤖 AI Engineering & Autonomous Agents
* **[notebooklm-fastmcp](https://github.com/mpandudc/notebooklm-fastmcp)** — Lean FastMCP server for Google NotebookLM. Built for zero-token context offloading, Google Master Token (AAS) auto-reminting, 1-shot audio deep dives, and Obsidian sync.
* **[obsidian-hybrid-rag-mcp](https://github.com/mpandudc/obsidian-hybrid-rag-mcp)** — High-performance MCP server delivering Two-Tier Hybrid RAG (FTS5 BM25 + dense BGE-M3 1024-dim vector + Jina cross-encoder reranking) with sub-second retrieval over private Markdown knowledge bases.

#### 📈 Quantitative Trading & Financial Systems
* **[cuantum](https://github.com/mpandudc/cuantum)** *(Private)* — Self-hosted algorithmic crypto trading signal and order execution platform. Built on FastAPI, SQLAlchemy async, React/TypeScript, and CCXT. Features automated bracket execution and risk management across Binance and Bitget.
* **[duwit](https://github.com/mpandudc/duwit)** — Personal financial analytics engine and expense tracking suite built on Next.js, Drizzle ORM, and automated transaction reconciliation pipelines.

#### 🏗️ Data Engineering & Lakehouse Lab
* **Data Platform Stack** *(Private / Self-Hosted)* — Local lakehouse and data pipeline lab leveraging **Apache Airflow**, **MinIO (S3-compatible object storage)**, and **DuckDB/dbt** to ingest, store, and transform market tickers and trading records into parquet-based analytical layers.

---

### 🛠️ Core Engineering Stack

```
Streaming & Big Data : Apache Flink, Apache Spark, Apache Airflow, Kafka, Apache Hudi, Iceberg, dbt
Storage & Lakehouse  : Snowflake, BigQuery, MinIO, PostgreSQL, DuckDB, TimescaleDB, Redis
Cloud & Distributed  : AWS (EMR, S3, Glue, Lambda, Athena), Kubernetes, Docker, Terraform
Languages            : Python, SQL, C/C++, Rust, Bash
Architecture         : Medallion Architecture, CDC (Debezium/DMS), High-throughput Ingestion (10K+ RPS)
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
