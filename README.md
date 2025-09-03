# FinBot-RAG-API
This project provides a high-performance Retrieval-Augmented Generation (RAG) API built with FastAPI, specifically designed for the financial analysis domain. It ingests dense financial reports in PDF or DOCX format and delivers precise, explainable answers to complex analyst queries in real-time.   
The core of the system is a sophisticated retrieval pipeline featuring the SPLADE sparse retriever and a fine-tuned Mixtral 8x7B model for accurate, context-aware answer generation.  

## Features
Financial Document Processing: Natively extracts and cleans text from complex financial reports in both PDF and DOCX formats.  
Advanced Hybrid Retrieval: Combines SPLADE (sparse) for keyword-aware matching and Sentence-Transformers (dense) for semantic understanding.  
Cross-Encoder Re-ranking: Refines the retrieved results using a cross-encoder model to ensure maximum relevance for complex financial queries.  
Fine-Tuned Generative QA: Utilizes a powerful, instruction-tuned Mixtral 8x7B model to synthesize answers.  
Proven Accuracy: The fine-tuned model achieved a 74.6% F1 score and 612 exact matches out of 1000 validation points.  
Scalable FastAPI Backend: Deployed as a robust and scalable API with a clean, production-ready structure.  

## How It Works  
Document Ingestion: The API fetches a financial report (PDF/DOCX) from a given URL.  
Text Extraction & Chunking: Extracts and cleans text, then splits it into smaller, semantically coherent passages.  
Indexing:  
  A sparse index is created using SPLADE vectors for efficient, term-based retrieval.    
  A dense index is created using Sentence-Transformers for semantic vector search.     
Hybrid Search: For a given query, the system retrieves the top N passages from both the sparse (SPLADE) and dense indices.   
Fusion & Re-ranking: 
  Results from both retrievers are combined.  
  A cross-encoder model re-ranks the fused list to identify the absolute best passages to serve as context.  
Answer Generation: The top-ranked passages and the user's query are passed to the fine-tuned Mixtral 8x7B model, which generates a precise and explainable answer.  
API Response: The final answer is returned in a structured JSON format.  

## Installation
Clone the repository:   
git clone https://github.com/DivyanshKgpian/FinBot-RAG-API.git    
cd FinBot-RAG-API    

## Usage   
Run the API using Uvicorn:   
uvicorn main:app --reload
