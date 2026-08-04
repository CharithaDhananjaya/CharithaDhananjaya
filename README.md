<div align="center">

## Hi there 👋

Fullstack Engineer — building cross-platform web and mobile products with a focus on performance, architecture, and product-driven engineering.

![React](https://img.shields.io/badge/React-61DAFB?logo=react&logoColor=black) ![React Native](https://img.shields.io/badge/React%20Native-61DAFB?logo=react&logoColor=black) ![Next.js](https://img.shields.io/badge/Next.js-black?logo=nextdotjs&logoColor=white) [![Astro](https://img.shields.io/badge/Astro-7C3AED?logo=astro&logoColor=white)](https://astro.build) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white) ![GraphQL](https://img.shields.io/badge/GraphQL-E10098?logo=graphql&logoColor=white) ![Node.js](https://img.shields.io/badge/Node.js-339933?logo=nodedotjs&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white) ![Firebase](https://img.shields.io/badge/Firebase-FF6F00?logo=firebase&logoColor=white)
![GCP](https://img.shields.io/badge/GCP-Cloud%20Functions%20%7C%20Pub%2FSub%20%7C%20BigQuery%20%7C%20Firestore-4285F4?logo=googlecloud&logoColor=white) ![AWS](https://img.shields.io/badge/Lambda_%7C_S3_%7C_IAM-FF9900?label=AWS&logo=amazonaws&logoColor=white) ![Vercel](https://img.shields.io/badge/Vercel-000000?logo=vercel&logoColor=white) ![GitHub](https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?logo=githubactions&logoColor=white)
![Gemini AI](https://img.shields.io/badge/Gemini%20AI-4285F4?logo=google&logoColor=white) ![AI SDK](https://img.shields.io/badge/AI%20SDK-000000?logo=vercel&logoColor=white) ![Ollama](https://img.shields.io/badge/Ollama-000000?logo=ollama&logoColor=white) [![Gemma 4](https://img.shields.io/badge/Gemma%204-669DF6?logo=google&logoColor=white)](https://ai.google.dev/gemma)
</div>

---

## 🔨 Current Projects

### 🍪 Pure Cookies — Cookie Consent Platform

Full-stack cookie consent platform with a CDN-first config architecture, a React dashboard for managing consent categories and publishing configs, and a self-contained Shadow DOM widget that integrates on any site with a single script tag.

🔗 Try it live — [https://pure-cookies-web.web.app/en/](https://pure-cookies-web.web.app/en/)

[![Firebase](https://img.shields.io/badge/Firebase-FF6F00?logo=firebase&logoColor=white)](https://firebase.google.com) [![React](https://img.shields.io/badge/React-61DAFB?logo=react&logoColor=black)](https://react.dev) [![Astro](https://img.shields.io/badge/Astro-7C3AED?logo=astro&logoColor=white)](https://astro.build) [![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org) [![Node.js](https://img.shields.io/badge/Node.js-339933?logo=nodedotjs&logoColor=white)](https://nodejs.org)

---

### 📄⚙️ doc-grinder — Local-First Document Grounding Pipeline

Grounded RAG pipeline that extracts structured fields and answers questions with page-level bounding-box citations — every claim traceable to its exact source passage.

The full AI stack runs natively on consumer Apple Silicon hardware (a single Mac mini) via MLX: OCR via **[baidu/Unlimited-OCR](https://github.com/baidu/Unlimited-OCR)** (3B VLM, 4-bit, via **[sahilchachra/unlimited-ocr-4bit-mlx](https://huggingface.co/sahilchachra/unlimited-ocr-4bit-mlx)**), embeddings via **[Qwen3-Embedding-0.6B](https://huggingface.co/Qwen/Qwen3-Embedding-0.6B)** (4-bit DWQ, via **[mlx-community/Qwen3-Embedding-0.6B-4bit-DWQ](https://huggingface.co/mlx-community/Qwen3-Embedding-0.6B-4bit-DWQ)**), and reasoning via **[Qwen3-4B-Instruct-2507](https://huggingface.co/Qwen/Qwen3-4B-Instruct-2507)** (4-bit, via **[mlx-community/Qwen3-4B-Instruct-2507-4bit](https://huggingface.co/mlx-community/Qwen3-4B-Instruct-2507-4bit)**) served through **[vllm-mlx](https://github.com/waybarrios/vllm-mlx)** with constrained JSON-schema decoding.

Zero API cost, no data leaving the device on the default local path — Gemini stays wired in only as an automatic fallback for complex, cross-document reasoning or local outages.

🔗 Try it live — [https://doc-grinder.web.app](https://doc-grinder.web.app)

- **Fully local AI stack, one Mac mini** — OCR, embeddings, and reasoning all run 4-bit quantized on-device: no GPU cluster, no per-token cloud bill
- **High-precision, schema-constrained reasoning** — local answers are constrained to a strict JSON citation schema at decode time: 100% schema validity and 100% fact accuracy on the eval suite, every claim traced to a page and bounding box
- **Hybrid routing with automatic failover** — simple queries answer locally; complex or cross-document queries escalate to Gemini, and a circuit breaker detects a degraded local service and fails over automatically, with full visibility into which backend served each request
- **Hybrid retrieval (RRF)** — over-retrieves on vector similarity, reranks with a fused BM25 + vector-rank signal to cut prefill size without losing citation coverage, on pgvector (HNSW + cosine)
- **Financial & compliance extraction** — structured fields from loan applications, financial statements, KYC/ID documents, and contracts, with exact page + bbox provenance
- **Built-in observability** — a monitoring dashboard tracking token usage, request volume, latency, and success rate across every AI backend, local and cloud, in one place

| Local model                    | Params / Quantization         | Role                                     | Result (Apple Silicon, on-device)          |
| ------------------------------- | ------------------------------ | ----------------------------------------- | -------------------------------------------- |
| Unlimited-OCR                  | 3B VLM, 4-bit MLX              | Extraction — markdown + grounding boxes  | ~8–12 pages/min                              |
| Qwen3-Embedding-0.6B            | 0.6B, 4-bit MLX DWQ             | Embeddings — 1024-dim vectors            | ~300–500 chunks/min                          |
| Qwen3-4B-Instruct-2507          | 4B, 4-bit MLX (via vllm-mlx)    | Reasoning — schema-constrained Q&A       | 100% schema-valid · 100% fact-accurate (eval) |

[![Next.js](https://img.shields.io/badge/Next.js-black?logo=nextdotjs&logoColor=white)](https://nextjs.org) [![Express](https://img.shields.io/badge/Express-000000?logo=express&logoColor=white)](https://expressjs.com) [![PostgreSQL](https://img.shields.io/badge/PostgreSQL%20+%20pgvector-4169E1?logo=postgresql&logoColor=white)](https://www.postgresql.org) [![Gemini](https://img.shields.io/badge/Gemini%203.x-4285F4?logo=google&logoColor=white)](https://ai.google.dev) [![Unlimited-OCR](https://img.shields.io/badge/baidu%2FUnlimited--OCR-000000?logo=github&logoColor=white)](https://github.com/baidu/Unlimited-OCR) [![Qwen3-Embedding](https://img.shields.io/badge/Qwen3--Embedding--0.6B-purple?logo=alibabacloud&logoColor=white)](https://huggingface.co/Qwen/Qwen3-Embedding-0.6B) [![Qwen3-4B-Instruct](https://img.shields.io/badge/Qwen3--4B--Instruct-purple?logo=alibabacloud&logoColor=white)](https://huggingface.co/Qwen/Qwen3-4B-Instruct-2507) [![vllm-mlx](https://img.shields.io/badge/vllm--mlx-black?logoColor=white)](https://github.com/waybarrios/vllm-mlx) [![MLX](https://img.shields.io/badge/MLX-Apple_Silicon-000000?logo=apple&logoColor=white)](https://github.com/ml-explore/mlx) [![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)](https://www.docker.com) [![Turborepo](https://img.shields.io/badge/Turborepo-EF4444?logo=turborepo&logoColor=white)](https://turbo.build)

---

<div align="center">

💼 Let's connect — [linkedin.com/in/charithadhananjaya](https://www.linkedin.com/in/charithadhananjaya/)
2026

</div>
