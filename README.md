# Muhammad Pandu Dwi Cahyo

<p align="left">
  <a href="https://linkedin.com/in/mpandudc"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="https://mpandudc.com"><img src="https://img.shields.io/badge/Website-mpandudc.com-2ea44f?style=flat&logo=google-chrome&logoColor=white" alt="Website" /></a>
  <a href="mailto:mpandudc@gmail.com"><img src="https://img.shields.io/badge/Email-mpandudc%40gmail.com-blue?style=flat&logo=gmail&logoColor=white" alt="Email" /></a>
</p>

**Data Engineer Supervisor** with 4+ years of experience architecting high-throughput, low-latency streaming pipelines (10K+ RPS) and distributed data platforms in fintech and cryptocurrency (CFX, Pintu). Proven record in leading engineering teams, executing Snowflake/AWS migrations (25% compute cost reduction), and orchestrating Apache Flink, Spark, and Airflow on Kubernetes.

Currently pursuing an **MBA in Business Leadership Executive at SBM ITB** to bridge large-scale distributed data systems with strategic business growth, regulatory compliance, and quantitative product execution.

---

### 🌐 Homelab & Autonomous Systems Topology

A high-availability, self-hosted homelab environment (Intel i5-8500T 6C / 32GB RAM Proxmox node) running a hybrid multi-agent AI framework, algorithmic trading execution engine, and second-brain retrieval pipelines:

```mermaid
flowchart TB
    subgraph WAN [Secure Ingress & Edge]
        CF[Cloudflare Edge / Tunnel]
        TS[Tailscale Mesh Network]
    end

    subgraph PROXMOX [Proxmox VE Node - homelab]
        direction TB

        subgraph LXC_INGEST [LXC 203: AI Engine & Knowledge Gateway]
            H_GATEWAY["Hermes Agent Runtime\n(Multi-Agent Daemon)"]
            H_ROSTER["Agent Roster:\n@hermes (Knowledge) | @coder (SRE) | @quant (Trading)"]
            R9["9router LLM Gateway"]
            V_MCP["vault-mcp (FastMCP)\nTwo-Tier Hybrid RAG (BGE-M3 + BM25)"]
            NLM_MCP["notebooklm-fastmcp (FastMCP)\nGoogle Master Token & 1-Shot Audio Deep Dive"]
        end

        subgraph LXC_EXEC [LXC 201: Quantitative Trading & Automation]
            CUANTUM["cuantum (Private)\nFastAPI Async + React + CCXT\nBinance/Bitget Bracket Execution"]
            N8N["n8n Automation Engine\nWorkflow & Webhook Pipelines"]
        end

        subgraph LXC_STORAGE [LXC 205: State & Persistence Engine]
            PG[(PostgreSQL 16\nTrading Ledger & State)]
            REDIS[(Redis 7\nCache & PubSub)]
        end

        subgraph LXC_NET [LXC 204 & 206: Dev & Network Core]
            ADGUARD["AdGuard Home DNS\n(Tailnet-wide DNS Filter)"]
            DE_LAB["Data Engineering Lab\n(Docker, Python 3.12, uv)"]
        end
    end

    subgraph STORAGE_EXT [External Knowledge & Data Lakes]
        OBSIDIAN[("Obsidian Vault\nSecond Brain (Local Markdown)")]
        G_NLM[("Google NotebookLM\n1-2M Context Engine")]
        EXCHANGES[("Exchanges API\nBinance / Bitget WebSocket")]
    end

    %% Ingress Routes
    CF --> CUANTUM
    CF --> R9
    TS --> LXC_INGEST
    TS --> LXC_STORAGE
    TS --> ADGUARD

    %% Interconnects
    H_GATEWAY --- H_ROSTER
    H_ROSTER -->|Query Context| V_MCP
    H_ROSTER -->|Document Grounding| NLM_MCP
    V_MCP <-->|Sub-second Rerank| OBSIDIAN
    NLM_MCP <-->|Zero-Token Bypass| G_NLM
    
    H_ROSTER -->|Strategy Evaluation| CUANTUM
    CUANTUM <-->|Order & Balance State| PG
    CUANTUM <-->|Live Ticker Cache| REDIS
    CUANTUM <-->|Real-time Execution| EXCHANGES
    N8N -->|Trigger Automation| CUANTUM
```

---

### 🚀 Ecosystem & Featured Systems

#### 🤖 AI Engineering & Autonomous Agents
* **[notebooklm-fastmcp](https://github.com/mpandudc/notebooklm-fastmcp)** — Lean FastMCP server for Google NotebookLM. Engineered for zero-token context offloading, Google Master Token (AAS) auto-reminting, 1-shot audio podcast generation, and Obsidian sync.
* **[obsidian-hybrid-rag-mcp](https://github.com/mpandudc/obsidian-hybrid-rag-mcp)** — High-performance MCP server delivering Two-Tier Hybrid RAG (FTS5 BM25 + dense BGE-M3 1024-dim vector + Jina cross-encoder reranking) with sub-second retrieval over private Markdown knowledge bases.

#### 📈 Quantitative Trading & Financial Systems
* **[cuantum](https://github.com/mpandudc/cuantum)** *(Private)* — Self-hosted algorithmic crypto trading signal and order execution platform. Built on FastAPI, SQLAlchemy async, React/TypeScript, and CCXT. Features automated bracket execution and risk management across Binance and Bitget.
* **[duwit](https://github.com/mpandudc/duwit)** — Modern personal financial analytics engine and expense tracking suite built on Next.js, Drizzle ORM, and automated transaction reconciliation pipelines.

---

### 🛠️ Core Engineering Stack

```
Streaming & Big Data : Apache Flink, Apache Spark, Apache Airflow, Kafka, Apache Hudi, Iceberg
Data Warehouses      : Snowflake, BigQuery, PostgreSQL, TimescaleDB, Redis
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
