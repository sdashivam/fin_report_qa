# 📊 Financial Report RAG QA System

A production-oriented Retrieval-Augmented Generation (RAG) application that extracts insights from financial reports (PDFs) and answers user queries using LLMs.

---

# 🚀 Overview

This project enables users to:

* Upload financial reports (annual reports, 10-K, etc.)
* Ask natural language questions
* Get grounded, context-aware answers

It uses a **RAG pipeline** combining:

* Document parsing
* Vector search
* Large Language Models (LLMs)

---

# 🧠 Architecture

## 🔹 Query Flow

```
User (Streamlit UI)
        ↓
FastAPI Backend
        ↓
Embedding Model
        ↓
Vector Database (Top-K Retrieval)
        ↓
LLM (Answer Generation)
        ↓
Response to User
```

## 🔹 Ingestion Flow

```
PDF Upload
   ↓
Text Extraction
   ↓
Chunking
   ↓
Embeddings
   ↓
Vector Database Storage
```

---

# 🧩 Tech Stack

| Layer      | Technology                            |
| ---------- | ------------------------------------- |
| Frontend   | Streamlit                             |
| Backend    | FastAPI                               |
| LLM        | Vertex AI (Gemini) / OpenAI           |
| Embeddings | Vertex AI                             |
| Vector DB  | Vertex AI Vector Search / FAISS (dev) |
| Storage    | GCS / Local                           |
| Parsing    | PyMuPDF                               |
| Deployment | Docker                                |
| CI/CD      | GitHub Actions                        |

---

# 📁 Project Structure

```
rag-finance-app/
│
├── backend/
│   ├── main.py
│   ├── rag/
│   │   ├── pipeline.py
│   │   ├── retriever.py
│   │   └── generator.py
│   ├── ingestion/
│   │   └── ingest.py
│
├── frontend/
│   └── app.py
│
├── docker-compose.yml
├── requirements.txt
└── README.md
```

---

# ⚙️ Setup & Installation

## 1. Clone the Repository

```
git clone <your-repo-url>
cd rag-finance-app
```

---

## 2. Create Environment Variables

Create a `.env` file:

```
OPENAI_API_KEY=your_api_key
```

---

## 3. Run with Docker

```
docker-compose up --build
```

---

## 🌐 Access the Application

* Frontend: http://localhost:8501
* Backend: http://localhost:8000

---

# 📄 Data Ingestion

To ingest a financial report:

1. Place your PDF inside a data folder
2. Run ingestion script:

```
python backend/ingestion/ingest.py
```

> ⚠️ Note: Update the script to point to your PDF file path.

---

# 💬 Usage

1. Open the Streamlit UI
2. Enter a financial query, e.g.:

   * "What is the total revenue?"
   * "Summarize the risk factors"
3. View the generated answer

---

# 🔧 Configuration

You can modify:

* Chunk size in ingestion pipeline
* Number of retrieved documents (`top_k`)
* LLM model and temperature
* Embedding model

---

# 🚀 Deployment

## Build Docker Image

```
docker build -t rag-finance-app .
```

## Push to Registry

```
docker push <your-image>
```

## Deploy

* Vertex AI / Cloud Run (recommended)
* Any container platform

---

# 🔁 CI/CD (GitHub Actions)

Basic pipeline:

* Build Docker image
* Push to container registry
* Deploy to cloud

---

# ⚠️ Limitations

* Basic chunking (can be improved)
* No table-aware extraction yet
* In-memory vector store (dev only)
* No authentication

---

# 🔮 Future Improvements

* Section-aware chunking (MD&A, balance sheet, etc.)
* Table extraction → structured data
* Source citations with page numbers
* Multi-document comparison
* Evaluation metrics (RAG quality)

---

# 🧭 Notes

* Financial documents are complex → parsing quality is critical
* RAG performance depends more on data processing than model choice
* Use metadata filtering for better accuracy

---

# 📜 License

MIT License

---

# 🤝 Contribution

Contributions are welcome! Feel free to open issues or submit pull requests.

---

# 📬 Contact

For questions or improvements, reach out or open an issue in the repository.
