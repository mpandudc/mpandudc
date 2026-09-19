# Muhammad Pandu Dwi Cahyo

<p align="left">
  <a href="https://linkedin.com/in/mpandudc"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="https://mpandudc.com"><img src="https://img.shields.io/badge/Website-mpandudc.com-2ea44f?style=flat&logo=google-chrome&logoColor=white" alt="Website" /></a>
  <a href="mailto:mpandudc%40gmail.com"><img src="https://img.shields.io/badge/Email-mpandudc%40gmail.com-blue?style=flat&logo=gmail&logoColor=white" alt="Email" /></a>
</p>

Data Engineer Supervisor focused on high-throughput streaming pipelines (10K+ RPS) and distributed analytical platforms in fintech/crypto (CFX, Pintu). Experienced in production Flink, Spark on K8s, Airflow orchestration, and Snowflake/AWS infrastructure.

MBA Candidate in Business Leadership Executive at SBM ITB. B.Eng. in Computer Engineering from Universitas Brawijaya (Cum Laude, 3.93/4.00).

---

### Personal Homeserver & Distributed Systems Architecture

```mermaid
flowchart TD
    %% ==========================================
    %% LEVEL 1: EXTERNAL FEEDS & INGRESS
    %% ==========================================
    subgraph S_EXT ["Level 1: Ingress, External Feeds & Mesh"]
        direction TB
        subgraph S_INGRESS ["Public Ingress, DNS & Private Mesh"]
            direction LR
            CF["Cloudflare Tunnel<br/>(Edge SSL Ingress)"]
            DNS["AdGuard Home DNS<br/>(Network-Wide Filter)"]
            TS["Tailscale Private Mesh<br/>(WireGuard CGNAT)"]
            CF --- DNS --- TS
        end
        subgraph S_FEEDS ["External Market Feeds & Edge Services"]
            direction LR
            FEEDS_CRYPTO["Binance & Bitget<br/>(CCXT / WebSocket)"]
            FEEDS_MACRO["Yahoo Finance & IDX<br/>(Macro & Financial Reports)"]
            DUWIT["duwit Edge Service<br/>(Vercel + Postgres)"]
            FEEDS_CRYPTO --- FEEDS_MACRO --- DUWIT
        end
    end

    %% ==========================================
    %% LEVEL 2: TRADING, CORE APPS & OBSERVABILITY
    %% ==========================================
    subgraph S_CORE ["Level 2: Core Homelab Services & Observability"]
        direction LR

        subgraph COL_TRADING ["Operational Trading & Utility"]
            direction TB
            CUANTUM["cuantum Trading Engine<br/>(FastAPI + React Vite)"]
            N8N["n8n Workflow Automations"]
            PAIRDROP["PairDrop Web P2P Transfer"]
            PG[("PostgreSQL Operational DB")]
            REDIS[("Redis State Cache")]

            CUANTUM <--> PG
            CUANTUM <--> REDIS
            N8N --> CUANTUM
            PAIRDROP
        end

        subgraph COL_OBS ["Observability & Telemetry"]
            direction TB
            MONITOR_LXC[("Telemetry Hub")]
            PROM["Prometheus Metrics Scraper"]
            GRAF["Grafana Dashboards"]
            CADV["cAdvisor Container Metrics"]
            KUMA["Uptime Kuma Health Checker"]
            DISCORD["Discord Sentinel Bot<br/>(#server-status)"]

            MONITOR_LXC --> PROM
            MONITOR_LXC --> GRAF
            MONITOR_LXC --> CADV
            MONITOR_LXC --> KUMA
            MONITOR_LXC --> DISCORD
            CADV --> PROM
            PROM --> GRAF
        end
    end

    %% ==========================================
    %% LEVEL 3: DATA PLATFORM & LAKEHOUSE
    %% ==========================================
    subgraph S_DATA ["Level 3: Self-Hosted Streaming & Lakehouse Platform"]
        direction TB

        subgraph DP_INGEST ["1. Ingestion & CDC Transport Layer"]
            direction LR
            DEBEZIUM["Debezium CDC Engine<br/>(PostgreSQL WAL Replication)"]
            REDPANDA["Redpanda Cluster<br/>(High-Throughput C++ Broker)"]
            DEBEZIUM -->|Stream Mutation Events| REDPANDA
        end

        subgraph DP_STREAM ["2. Stream Processing & Lake Storage Sinks"]
            direction LR
            FLINK["Apache Flink<br/>(Event-Time Stream Engine)"]
            MINIO[("MinIO Object Lake<br/>(Parquet & Delta Format)")]
            REDPANDA -->|Event Streams| FLINK
            FLINK -->|Raw Bronze Sink| MINIO
        end

        subgraph DP_WAREHOUSE ["3. Distributed Compute, Transformation & BI Marts"]
            direction TB
            subgraph COMPUTE_ROW ["Batch & Storage Engines"]
                direction LR
                SPARK["Apache Spark on K8s<br/>(Batch Compute & ML)"]
                AIRFLOW["Apache Airflow<br/>(Batch DAG Orchestrator)"]
                CLICKHOUSE[("ClickHouse OLAP<br/>(Columnar Warehouse)")]
                DBT["dbt Core Compiler<br/>(Data Modeling)"]
                METABASE["Metabase BI<br/>(Analytics Dashboards)"]
            end

            AIRFLOW -->|Schedule Runs| SPARK
            AIRFLOW -->|Trigger Models| DBT
            SPARK <-->|Read / Write Delta Format| MINIO
            SPARK -.->|Load Enriched Parquet| CLICKHOUSE
            FLINK -->|Real-Time Aggregates| CLICKHOUSE
            DBT -->|Materialize Marts| CLICKHOUSE
            CLICKHOUSE -->|Sub-Second Queries| METABASE
        end
    end

    %% ==========================================
    %% LEVEL 4: AI RUNTIME & MCP ECOSYSTEM
    %% ==========================================
    subgraph S_AI ["Level 4: Autonomous Systems, Second Brain & Workstation Remote"]
        direction LR

        subgraph COL_AGENT ["Hermes Multi-Agent Stack"]
            direction TB
            HERMES["Hermes Agent Runtime<br/>(@hermes, @coder, @quant)"]
            ROUTER["9router Context Gateway"]
            OBSIDIAN[("Obsidian Second Brain<br/>(Hybrid Knowledge Graph)")]
            NLM_ENGINE[("NotebookLM Engine<br/>(Google Gemini Long-Context)")]
            PVE_API[("Proxmox VE Host<br/>(Intel i5, 32GB RAM)")]

            HERMES --> ROUTER
            HERMES -.->|Risk Rules & Signal Eval| CUANTUM
        end

        subgraph COL_MCP ["FastMCP Tools & Workstation Control"]
            direction TB
            VAULT_MCP["vault-mcp Server<br/>(Two-Tier Hybrid BM25 + Vector)"]
            NLM_MCP["notebooklm-fastmcp Server<br/>(Direct Ingest & Studio Audio)"]
            PROXMOX_MCP["proxmox-homelab-mcp Server<br/>(Lifecycle, Snapshots & Stats)"]
            WORKSTATION_MCP["workstation-remote-mcp Server<br/>(WoL, SSH & Power Control)"]
            MPDC_PC["MPDC-PC Workstation<br/>(Windows 11, CUDA/RTX)"]

            HERMES --> VAULT_MCP <--> OBSIDIAN
            HERMES --> NLM_MCP <--> NLM_ENGINE
            HERMES --> PROXMOX_MCP <--> PVE_API
            HERMES --> WORKSTATION_MCP <-->|WoL & Power API| MPDC_PC
        end
    end

    %% ==========================================
    %% CROSS-TIER DATA & INGRESS FLOWS
    %% ==========================================
    FEEDS_CRYPTO -->|Direct Price Feeds & Trade Orders| CUANTUM
    FEEDS_CRYPTO -->|Market Tickers & Order Books| REDPANDA
    DUWIT -.->|Webhook Sync / Change Feed| REDPANDA
    PG -.->|Logical WAL Replication| DEBEZIUM
    PVE_API -.->|Node Exporter Hardware Metrics| PROM
    CF -->|Public Routing| CUANTUM
    CF -->|Public Routing| PAIRDROP
    CF -->|Public Routing| GRAF
    CF -->|Public Routing| ROUTER
    TS -->|Private Tailnet Mesh| S_CORE
    TS -->|Private Tailnet Mesh| MPDC_PC
```

---

### Systems & Projects

#### Streaming & Lakehouse
* **Self-Hosted Data Platform** — 100% on-premise, containerized lakehouse and columnar analytics engine:
  * **Event Streaming & Ingestion**: **Debezium CDC Engine** (capturing PostgreSQL logical WAL mutation logs without query overhead) and **Redpanda** (low-latency C++ event broker ingesting CDC streams, Vercel edge syncs, and multi-venue market feeds: Binance, Bitget, Yahoo Finance, and IDX), orchestrated by **Apache Airflow**.
  * **Stream Processing**: **Apache Flink** (stateful event-time surveillance, rolling window aggregations, and sub-second sinks into ClickHouse and MinIO).
  * **Storage & Batch Lakehouse**: **MinIO** (S3-compatible local lakehouse) and **Apache Spark on K8s** (distributed feature transformations and Delta Lake table ACID format).
  * **OLAP Analytics & dbt Modeling**: **ClickHouse** (high-concurrency columnar analytics warehouse) transformed via **dbt Core** (`dbt-clickhouse` adapter) for automated staging, intermediate metrics, and dimensional data marts.
  * **BI & Serving**: **Metabase** (sub-second SQL dashboards for trading performance and operational metrics).
* **[flink-market-surveillance](https://github.com/mpandudc/flink-market-surveillance)** — Event-time market surveillance, wash-trading pattern detection, and deterministic replay harness built with Apache Flink and Kafka.
* **[spark-delta-lakehouse](https://github.com/mpandudc/spark-delta-lakehouse)** — Spark Structured Streaming with Delta Lakehouse Medallion architecture and ACID transactions.
* **[streaming-ml-features](https://github.com/mpandudc/streaming-ml-features)** — Streaming ML feature store parity engine ensuring zero-drift between online and offline feature generation.
* **[flink-vs-spark-benchmark](https://github.com/mpandudc/flink-vs-spark-benchmark)** — Benchmark comparing throughput, backpressure handling, and event-time latency between Apache Flink and Spark Structured Streaming.

#### AI Systems & Agent Tooling
* **[workstation-remote-mcp](https://github.com/mpandudc/workstation-remote-mcp)** — FastMCP server for Windows workstation automation via Wake-on-LAN and unattended SSH. Remote power standby, session locking, CPU/RAM telemetry, and runaway process termination.
* **[proxmox-homelab-mcp](https://github.com/mpandudc/proxmox-homelab-mcp)** — FastMCP server for Proxmox VE & Homelab cluster ops. Direct LXC container lifecycle (`start`/`stop`/`reboot`), point-in-time snapshots, service health inspection, and Tailscale mesh status.
* **[notebooklm-fastmcp](https://github.com/mpandudc/notebooklm-fastmcp)** — FastMCP server for Google NotebookLM. Direct-path ingestion (zero chat token consumption), Google Master Token auto-reminting, 1-shot audio deep dives, and Obsidian note generation.
* **[obsidian-hybrid-rag-mcp](https://github.com/mpandudc/obsidian-hybrid-rag-mcp)** — MCP server for Obsidian Second Brain. Two-Tier Hybrid RAG (FTS5 BM25 + dense BGE-M3 vector + Jina cross-encoder reranking) with in-memory caching.

#### Trading & Applications
* **[cuantum](https://github.com/mpandudc/cuantum)** *(Private)* — Algorithmic multi-venue trading and market analytics engine:
  * **Exchange Execution**: Native spot & perpetual futures execution via **Binance** and **Bitget** (CCXT async integration with automated bracket orders and dynamic position sizing).
  * **Market & Alternative Data Ingestion**: Real-time ticker and orderbook streaming into Redpanda/Flink, combined with macro, index, and equity financial history feeds from **Yahoo Finance** and **IDX (Indonesia Stock Exchange)** financial disclosure filings.
  * **State & Reliability**: FastAPI backend, PostgreSQL 16 (transactional ledger), and Redis 7 (in-memory pub/sub & candle caching).
* **[duwit](https://github.com/mpandudc/duwit)** — Financial tracking and analytics app built with Next.js and Drizzle ORM. Fully serverless stack deployed on **Vercel** (Frontend, Serverless Route Handlers, and Vercel Postgres) with automated transaction reconciliation pipelines.

---

### Tech Stack

```
Streaming & Big Data : Apache Flink, Apache Spark, Redpanda, Debezium CDC, Apache Airflow, Kafka, Delta Lake, dbt Core
Storage & Lakehouse  : ClickHouse, MinIO, PostgreSQL 16, DuckDB, TimescaleDB, Redis 7
Data Modeling        : dbt-clickhouse, Medallion Architecture, Dimensional Modeling (Star Schema)
Market & Feeds       : Binance WS/REST, Bitget CCXT, Yahoo Finance, IDX Financial Reports
BI & Serving         : Metabase, Grafana
Cloud & Infra        : AWS (EMR, S3, Glue, Lambda, Athena), Kubernetes, Docker, Vercel, Terraform
Languages            : Python, SQL, TypeScript, C/C++, Rust, Bash
Architecture         : CDC (Debezium/DMS), Streaming ML Parity, High-throughput (10K+ RPS)
```

---

### Education

* **MBA in Business Leadership Executive** — School of Business and Management, Institut Teknologi Bandung (SBM ITB)
* **B.Eng. in Computer Engineering** — Universitas Brawijaya *(Cum Laude, CGPA 3.93/4.00)*
