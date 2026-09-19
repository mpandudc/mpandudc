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
flowchart TB
    subgraph INGRESS [Ingress & Private Mesh]
        direction LR
        CF[Cloudflare Tunnel]
        TS[Tailscale Mesh]
        DNS[AdGuard Home DNS]
    end

    subgraph SOURCES [Data Ingestion Sources]
        direction LR
        subgraph CLOUD_FEEDS [External Market & Financial Feeds]
            direction TB
            EX_BINANCE[Binance API / WS]
            EX_BITGET[Bitget CCXT / WS]
            EX_YFINANCE[Yahoo Finance & Macro]
            EX_IDX[IDX Financial Reports]
        end
        subgraph CLOUD_EDGE [Cloud Edge: Vercel Serverless]
            direction TB
            DUWIT[duwit Web & API]
            DUWIT_DB[(Vercel Postgres)]
            DUWIT <--> DUWIT_DB
        end
    end

    subgraph HOMESERVER [Local Infrastructure & Execution]
        direction TB

        subgraph APPS_OPS [Operational Trading Engine & State]
            direction TB
            CUANTUM[cuantum Trading Engine]
            N8N[n8n Automations]
            PG[(PostgreSQL 16 Operational)]
            REDIS[(Redis 7 State Cache)]

            CUANTUM <--> PG
            CUANTUM <--> REDIS
            N8N --> CUANTUM
        end

        subgraph DATA_PLATFORM [Self-Hosted Streaming & Lakehouse Platform]
            direction TB
            
            subgraph INGESTION_BUS [Ingestion & CDC Transport]
                direction LR
                DEBEZIUM[Debezium CDC Engine<br/>PostgreSQL Logical Replication WAL]
                REDPANDA[Redpanda Cluster<br/>High-Throughput C++ Broker]
                DEBEZIUM -->|Stream Avro / JSON Mutation Events| REDPANDA
            end

            FLINK[Apache Flink<br/>Event-Time Streaming Engine]
            AIRFLOW[Apache Airflow<br/>Batch DAG Orchestrator]
            
            subgraph STORAGE_LAYER [Storage & Lake]
                direction LR
                MINIO[(MinIO Object Lake<br/>Parquet & Delta Tables)]
                CLICKHOUSE[(ClickHouse OLAP<br/>Columnar Analytics Warehouse)]
            end

            SPARK[Apache Spark on K8s<br/>Distributed Batch Compute & ML]
            DBT[dbt Core<br/>dbt-clickhouse Model Compiler]
            METABASE[Metabase BI<br/>Operational Analytics Dashboards]

            %% Streaming Pipeline
            REDPANDA -->|Event Streams| FLINK
            FLINK -->|Real-Time Analytics Marts| CLICKHOUSE
            FLINK -->|Raw Event Bronze Sink| MINIO

            %% Batch Orchestration & Processing
            AIRFLOW -->|Schedule Batch & ML Runs| SPARK
            AIRFLOW -->|Trigger Mart Transformations| DBT
            SPARK <-->|Read / Write Delta Format| MINIO
            SPARK -.->|Load Enriched Parquet| CLICKHOUSE

            %% Transformation & Serving
            DBT -->|Materialize Staging & Marts| CLICKHOUSE
            CLICKHOUSE -->|Sub-Second SQL Queries| METABASE
        end

        subgraph AI_KNOWLEDGE [Autonomous Systems & Knowledge Hub]
            direction TB
            HERMES[Hermes Multi-Agent Runtime]
            ROUTER[Context & Model Gateway]
            VAULT_MCP[vault-mcp Server]
            NLM_MCP[notebooklm-fastmcp Server]
            PROXMOX_MCP[proxmox-homelab-mcp Server]
            OBSIDIAN[(Obsidian Second Brain)]
            NLM_ENGINE[(NotebookLM Long-Context Engine)]
            PVE_HOST[(Proxmox VE Cluster & LXCs)]

            HERMES --> ROUTER
            HERMES --> VAULT_MCP
            HERMES --> NLM_MCP
            HERMES --> PROXMOX_MCP
            VAULT_MCP <-->|Two-Tier Hybrid Search| OBSIDIAN
            NLM_MCP <-->|Direct Ingest & Podcast Gen| NLM_ENGINE
            PROXMOX_MCP <-->|LXC Lifecycle, Snapshots & Stats| PVE_HOST
            HERMES -.->|Risk Evaluation & Execution Rules| CUANTUM
        end
    end

    %% Ingestion into Broker & Apps
    PG -.->|Logical WAL Log Decoding| DEBEZIUM
    DUWIT_DB -.->|Edge Webhook / Change Feed| REDPANDA
    CLOUD_FEEDS -->|Tickers, Order Books & Filings| REDPANDA
    CLOUD_FEEDS -->|Direct Price Feeds & Trade Orders| CUANTUM

    %% Ingress Connections
    CF -->|Public Web Access| CUANTUM
    CF -->|Gateway Access| ROUTER
    TS -->|Private Tailnet Mesh| HOMESERVER
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
