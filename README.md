# The Clarity Engine

The **Clarity Engine** is an enterprise-grade, **100% private, neuro-symbolic RAG (Retrieval-Augmented Generation)** system designed to transform chaotic internal knowledge into a clear, queryable asset.

Built on the principles of the *"Living Brain"* cognitive architecture, it uses a **dual-brain approach**:

### System 1 (Intuitive Brain)
A vector store (**ChromaDB**) for fast, semantic search.

### System 2 (Logical Brain)
A knowledge graph (**Neo4j**) for deep, causal, and relational reasoning.

---

## Key Features

- **100% Private:** Runs entirely on your own infrastructure using Docker. No data ever leaves your control.
- **Dual-Brain RAG:** Goes beyond simple semantic search to understand relationships and causality within your documents.
- **Verifiable Answers:** Can distinguish between factual recall and relational reasoning, providing more trustworthy answers.
- **Powered by a Sovereign Core:** Uses locally-run LLMs via **Ollama**, ensuring data sovereignty.

---

## Getting Started

### Prerequisites

- Docker and Docker Compose  
- Git

---

### Installation & Launch

**1. Clone the repository:**

```bash
git clone https://github.com/your-username/clarity_engine.git
cd clarity_engine
```

**2. Configure your environment:**

Copy the example environment file and set your own secure password for Neo4j.

```bash
cp .env.example .env
# Open .env and change the NEO4J_PASSWORD
```

**3. Launch the engine:**

This command will build the Docker images and start all services. It may take some time on the first run as it downloads Neo4j and Ollama.

```bash
docker-compose up -d --build
```

**4. Pull the LLM models:**

Once the containers are running, pull the necessary models into Ollama.

```bash
docker exec -it clarity_engine_llm ollama pull nomic-embed-text
docker exec -it clarity_engine_llm ollama pull llama3:8b
```

The Clarity Engine is now running! 🎉  
API available at: [http://localhost:8000](http://localhost:8000)

---

## 🧭 How to Use

You can interact with the API using any HTTP client (like **Insomnia**, **Postman**) or by building your own frontend.

### 1. Ingest a Document

**Endpoint:** `POST /api/ingest`  
**Body:** `multipart/form-data` with a `file` key.

### 2. Query Your Knowledge

**Endpoint:** `POST /api/query`  
**Body:** `application/json`

```json
{
  "prompt": "How does component A connect to component B?"
}
```

---

## License

This project is licensed under the AGPL 3.0.

- You are free to use, modify, and distribute this software for internal and non-commercial purposes.

- If you use this software to provide a service over a network, you must also open-source your entire application under the AGPL 3.0.

- For use in a closed-source commercial product, please contact us for a commercial license.

Inspired by the *"The Living Brain"* architecture.
