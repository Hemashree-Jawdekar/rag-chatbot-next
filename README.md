🚀 RAG Chatbot – PDF-Powered Question Answering

Next.js + Google Gemini + Vector Search

A lightweight Retrieval-Augmented Generation (RAG) system built with Next.js App Router, Google Gemini API, and a simple in-memory vector store.
Users can upload PDFs → extract text → embed → store → chat with an AI assistant that answers questions from your documents.

🔗 Live Demo

👉 Hosted on Vercel:

https://your-vercel-link.vercel.app

📘 Project Overview

This application lets users:

📄 Upload PDF documents

🧵 Extract text using pdf-parse

🧠 Generate vector embeddings using Google Gemini Embeddings

📚 Store chunks & embeddings in a lightweight vector store

💬 Chat with an AI assistant using retrieval + Gemini

🔍 Perform semantic similarity search (cosine similarity)

🧩 Architecture
1. Ingestion Flow (Upload PDF)

User uploads PDF to /api/upload

Extract text via pdf-parse

Split text into chunks

Generate embeddings with:

models/embedding-001


Save {chunk, embedding} pairs in local vector store

2. Retrieval Flow (Chat)

User sends a query

Embed query using Gemini embeddings

Compare query vector with stored vectors → cosine similarity

Select top-K most relevant chunks

Send them to Gemini model:

gemini-2.5-flash


Generate a grounded, contextual answer

🏗️ Tech Stack
Function	Tech
Frontend	Next.js 14 (App Router)
PDF Extraction	pdf-parse
Embedding Model	Gemini models/embedding-001
Chat Model	Gemini gemini-1.5-flash
Vector Storage	In-memory cosine similarity
Runtime	Node.js
📦 Installation & Setup
1. Clone the Repo
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>

2. Install Dependencies
npm install

3. Environment Variables

Create .env.local in your project root:

GEMINI_API_KEY=your_google_api_key_here


Get your key from:
🔗 https://aistudio.google.com/app/apikey

4. Start Dev Server
npm run dev


Your app runs at:
👉 http://localhost:3000

📂 Folder Structure
app/
 ├─ api/
 │   ├─ upload/route.js   → PDF upload & embedding
 │   └─ chat/route.js     → Chat endpoint
lib/
 ├─ pdf.js                → PDF extraction helper
 ├─ embedding.js          → Gemini embedding generator
 ├─ chunk.js              → Text splitter
 └─ vectorStore.js        → Local vector DB
components/
 └─ ChatUI.jsx            → Chat UI
public/
 └─ screenshots/          → Images for README
README.md

🖼️ Screenshots & Demo
Upload Screen

Chat Screen

Demo GIF

(Add your actual files inside public/screenshots/)

📝 Important Notes

Vector store is in-memory → resets after server restart

Upload supports multi-PDF indexing

Retrieval uses cosine similarity

For production, you can switch to:

Pinecone

Supabase Vector

ChromaDB

pgvector

🚀 Future Improvements

Persistent vector database

UI streaming responses

PDF multi-page summarization

User auth + personal document stores
