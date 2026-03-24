# ChatVector-AI Development Roadmap

This document outlines the current development focus and future direction of the ChatVector-AI project. It is intended for contributors to quickly understand priorities and pick up tasks.

---

## ✅ Phase 1: Stabilize & Optimize Core Engine (Complete)

Phase 1 focused on hardening the RAG backend for reliability, observability, and performance. All core work is shipped.

**What shipped:**

- Ingestion pipeline robustness and error handling
- Async/batch processing foundations
- Embedding queue for production scaling
- Centralized retry utility
- Advanced logging and request ID middleware
- Chunk metadata, chunk tuning, and source citation support
- Real system metrics on /status endpoint
- Terminology standardized to "ingestion" throughout
- POST /chat migrated to JSON request body
- LLM error handling with distinct error classification
- Upload pipeline refactored into dedicated service layer

---

## 🚀 Phase 2: Enhance Developer Experience (Current)

### 🔧 Backend

| Issue                                                                                                         | Description                                                                                          | Skill Level  |
| ------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ------------ |
| [#123 Redis-Backed Durable Ingestion Queue](https://github.com/chatvector-ai/chatvector-ai/issues/123)        | Replace in-memory queue with Redis for job durability, multi-worker support, and DLQ visibility      | Advanced     |
| [#124 Observability & Structured Log Shipping](https://github.com/chatvector-ai/chatvector-ai/issues/124)     | Wire log shipping to DataDog/Splunk/ELK; add LLM and embedding health checks to /status              | Intermediate |
| [#125 Advanced Chunking Strategies](https://github.com/chatvector-ai/chatvector-ai/issues/125)                | Introduce configurable chunking strategies (fixed, paragraph, semantic) to improve retrieval quality | Intermediate |
| [#126 Query Transformations](https://github.com/chatvector-ai/chatvector-ai/issues/126)                       | Add a query transformation layer (rewrite, expand, stepback) between user input and vector search    | Intermediate |
| [#127 Prompt Tuning & System Prompt Configuration](https://github.com/chatvector-ai/chatvector-ai/issues/127) | Externalize system prompt and LLM parameters for adopter customization                               | Intermediate |
| [#128 Python Client SDK](https://github.com/chatvector-ai/chatvector-ai/issues/128)                           | Lightweight Python SDK wrapping core API endpoints with consistent error handling                    | Advanced     |
| [#129 Deployment Improvements](https://github.com/chatvector-ai/chatvector-ai/issues/129)                     | Production Compose config, GitHub Actions CI pipeline, and deployment documentation                  | Intermediate |

### 🎨 Frontend

| Issue                                                                                               | Description                                                                      | Skill Level  |
| --------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | ------------ |
| [#5 Add Document Upload to Chat Page](https://github.com/chatvector-ai/chatvector-ai/issues/5)      | Upload component with file selection, progress tracking, and backend integration | Intermediate |
| [#8 Connect Chat Interface to Backend API](https://github.com/chatvector-ai/chatvector-ai/issues/8) | Wire chat input to POST /chat using doc_id from upload — blocked by #5           | Intermediate |

---

## 🏗 Phase 3: Scale & Specialize (Later)

Focus: Production-ready document intelligence platform.

- **Authentication & multi-tenancy** — gate all endpoints including /queue/stats; add tenant model across upload, chat, and queue
- **Specialized pipelines** — legal, academic, or code document handling
- **Ecosystem growth** — community integrations, example applications
- **Frontend maturity** — full documentation site with live API explorer and community showcase gallery

---

## 📌 Notes

- Issue status (blocked, in progress, etc.) is visible when you click through to GitHub.
- This roadmap provides a quick overview; click any link for full issue details.
