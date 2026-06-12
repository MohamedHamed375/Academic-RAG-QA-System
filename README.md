# Advanced Academic Lecture Q&A System (RAG)

An advanced, production-quality Retrieval-Augmented Generation (RAG) system built to navigate and query academic lecture materials (PDFs). This project was engineered as part of the **AIE343 Machine Learning for Text Mining** course at **Galala University** (Spring Semester).

The system transitions a basic single-pass prototype into an optimized, robust system utilizing state-of-the-art dense retrieval and low-latency LLM inference on free-tier infrastructure.

---

##  System Architecture & Innovations

The advanced system architecture systematically overcomes standard RAG bottlenecks identified in the baseline prototype through a multi-layered upgrade pipeline:

1. **Sentence-Aware Chunking:** Splits dense PDF text at sentence boundaries into `400-token` windows with a `50-token overlap` to preserve semantic purity and context continuity.
2. **State-of-the-Art Embeddings:** Upgraded to `BAAI/bge-large-en-v1.5` (1024-dim) with hard-negative fine-tuning, achieving high passage retrieval precision.
3. **Optimized Vector Store:** Replaced slow brute-force similarity calculations with a **FAISS IndexFlatIP** for exact inner-product search on L2-normalized vectors.
4. **Two-Stage Retrieval (Reranking):** Integrates a Cross-Encoder (`ms-marco-MiniLM-L-6-v2`) to jointly score top-12 query-chunk pairs, feeding only the highly-precise top-4 chunks to the LLM.
5. **Ultra-Fast Inference:** Migrated to **Llama 3.1 8B-Instruct** hosted via **Groq's LPU** engine, slicing response latency down to `300–800 ms` while improving answer reasoning.
6. **Conversational Continuity:** Implements a rolling context window injected with the last `6 Q&A turns` to seamlessly handle co-references and follow-up prompts.
7. **Interactive Educational Features:** Features an automated Study Notes Generator and an interactive Multiple-Choice Quiz Engine that provides detailed explanations and page-level source attribution.

---

##  Tech Stack

* **Core Language Model:** Llama-3.1-8B via Groq API.
* **Vector Indexing & Retrieval:** FAISS (Facebook AI Similarity Search), SentenceTransformers.
* **Reranking Engine:** Cross-Encoder (MS-MARCO).
* **Interface & Tooling:** Streamlit UI.
* **Environment:** Optimized for Local CPU inference (Embeddings/Reranking) & Free-tier cloud APIs.

---

##  Getting Started

1. Clone the repository:
   ```bash
   git clone [https://github.com/MohamedHamed375/Academic-RAG-QA-System.git](https://github.com/MohamedHamed375/Academic-RAG-QA-System.git)
