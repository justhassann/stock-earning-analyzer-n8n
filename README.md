# AI-Powered RAG Workflow For Stock Earnings Report Analysis

This workflow provides a powerful RAG (Retrieval-Augmented Generation) pipeline for analyzing dense financial documents like stock earnings reports. It allows a user to upload a report (e.g., a PDF), which is then processed, vectorized, and stored in a knowledge base. You can then ask specific questions about the report, such as "What were the main drivers of revenue growth?" or "Summarize the key risks mentioned by the management," and receive AI-generated answers based directly on the document's content.

## Overview

Analyzing quarterly earnings reports is a critical but time-consuming task for investors and financial analysts. These documents are often long and filled with complex information. This automation streamlines the process by creating an AI-powered assistant that can read and understand the report for you, enabling you to extract key insights in seconds.

## Features

* **Document Ingestion:** Can be configured to work with PDFs, text files, or URLs.
* **Text Processing:** Intelligently chunks the document into smaller, digestible pieces for accurate embedding.
* **Vector Storage:** Stores the vectorized content in a vector database (e.g., Pinecone, Qdrant), creating a searchable knowledge base for each report.
* **Conversational Q&A:** Uses an AI Agent to provide a chat interface where you can ask detailed questions about the financial data, management's commentary, and future outlook.
* **Source-Grounded Answers:** The RAG architecture ensures that the AI's answers are based on the information contained within the earnings report, minimizing hallucinations.

## How It Works

This workflow is typically divided into two main parts:

1.  **Indexing the Report:**
    * The workflow is triggered, receiving the earnings report file or URL.
    * The document's text is extracted.
    * The text is split into smaller, semantically meaningful chunks.
    * An embedding model (e.g., from OpenAI) converts each chunk into a vector.
    * These vectors are stored in a vector database.

2.  **Querying the Data:**
    * A chat trigger receives a user's question (e.g., "What was the net income for this quarter?").
    * The user's question is embedded into a vector.
    * This vector is used to perform a similarity search in the vector database, retrieving the most relevant chunks from the earnings report.
    * The original question and the retrieved text chunks are passed to a Large Language Model (LLM).
    * The LLM synthesizes the information to generate a comprehensive answer.

## Technologies Used

* n8n
* An embedding model (e.g., OpenAI, Cohere)
* A vector database (e.g., Pinecone, Qdrant, Supabase)
* A Large Language Model (e.g., GPT-4o, Claude 3)

## Setup & Configuration

1.  **Vector Database:** Set up your chosen vector database and create an index/collection for the reports. Add your credentials in n8n.
2.  **AI Provider Credentials:** Add your API key for your chosen embedding model and LLM provider (e.g., OpenAI).
3.  **Document Source:** Configure the initial node to receive the document you want to analyze. This can be a `Webhook` node to receive a file upload, a `Read From File` node, or an `HTTP Request` node to download a report from a URL.

## How to Use

1.  First, run the indexing part of the workflow to process and store a new earnings report.
2.  Once indexed, use the chat interface to ask questions about the report.
3.  The AI agent will retrieve the relevant information and provide a detailed answer.

This tool can dramatically accelerate financial research and due diligence. [book a chat here😁](https://cal.com/closegem/coffee-chat)
