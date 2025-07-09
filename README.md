##Multimodal AI Agent with Llama 3.2
Overview
This project implements a multimodal AI system that enables users to interact with complex document and visual data through natural language. It combines the power of Llama-3.2-3B (Small Language Model) and Llama-3.2-11B-Vision (Vision Language Model) to intelligently process, index, and respond to queries across diverse data formats.

Using a combination of modern AI tools and infrastructure, this system extracts information from PDFs, PowerPoint presentations, images, and text files, then indexes that data for semantic search and contextual Q&A via a conversational chat interface.

Technologies Used
Llama 3.2-3B and Llama 3.2-11B-Vision – For natural language and image understanding

LlamaIndex – Document ingestion, parsing, orchestration, and query routing

Hugging Face Transformers – Model inference

Google DePlot + NVIDIA NIM Microservices – For chart and graph understanding

Milvus – GPU-accelerated vector database for scalable semantic search

Streamlit – Interactive front-end chat interface

Features
Multi-format Document Processing: Supports PDFs, PPTs, images, and text files

Language & Vision Understanding: Image descriptions, text summaries, and chart comprehension

Advanced Indexing: Vector embeddings stored in Milvus for efficient similarity search

Interactive Q&A Chat Interface: Query your documents like a conversation

GPU-Acceleration Ready: Leveraging NVIDIA GPUs for high-performance inference and search

Setup Instructions
1. Clone the Repository
bash
Copy
Edit
git clone https://github.com/shadaab123/Multimodal-RAG.git
cd Multimodal-RAG
2. Install Dependencies
bash
Copy
Edit
pip install -r requirements.txt
3. Set NVIDIA API Key
bash
Copy
Edit
export NVIDIA_API_KEY="your-api-key-here"
Get your API key from build.nvidia.com

4. Start Milvus (GPU-enabled vector DB)
Follow the official guide: Install Milvus Standalone (GPU)

bash
Copy
Edit
sudo docker compose up -d
Running the Application
Make sure the Milvus container is running:

bash
Copy
Edit
docker ps
Start the app:

bash
Copy
Edit
streamlit run app.py
Open the URL shown in your terminal to access the app

Upload files or specify a folder path, then click Process Files or Process Directory

Use the chat interface to interact with your documents

File Structure
bash
Copy
Edit
.
├── app.py                    # Main Streamlit application
├── document_processors.py    # PDF, PPT, and image processors
├── utils.py                  # API interactions, image utilities
├── requirements.txt          # Project dependencies
└── vectorstore/              # Auto-generated Milvus collection data
GPU Acceleration
To use GPU-accelerated search in Milvus, ensure:

You’re using a system with an NVIDIA GPU

The GPU-enabled Milvus Docker container is installed

Milvus configuration in app.py specifies the GPU ID:

python
Copy
Edit
vector_store = MilvusVectorStore(
    host="127.0.0.1",
    port=19530,
    dim=1024,
    collection_name="your_collection_name",
    gpu_id=0  # Replace with your GPU ID
)
