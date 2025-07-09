# Multimodal AI Agent with Llama 3.2

## **Overview**

This project implements a **multimodal AI system** that enables users to interact with complex document and visual data through natural language. It combines the power of **Llama-3.2-3B** (Small Language Model) and **Llama-3.2-11B-Vision** (Vision Language Model) to intelligently process, index, and respond to queries across diverse data formats.

Using a combination of modern AI tools and infrastructure, this system extracts information from **PDFs, PowerPoint presentations, images, and text files**, then indexes that data for **semantic search and contextual Q\&A** via a conversational chat interface.

---

## **Technologies Used**

* **Llama 3.2-3B and Llama 3.2-11B-Vision** – Natural language and image understanding
* **LlamaIndex** – Document ingestion, parsing, orchestration, and query routing
* **Hugging Face Transformers** – Model inference
* **Google DePlot + NVIDIA NIM Microservices** – Chart and graph understanding
* **Milvus** – GPU-accelerated vector database for scalable semantic search
* **Streamlit** – Interactive front-end chat interface

---

## **Features**

* **Multi-format Document Processing**: Supports PDFs, PPTs, images, and text files
* **Language & Vision Understanding**: Image descriptions, text summaries, and chart comprehension
* **Advanced Indexing**: Vector embeddings stored in Milvus for efficient similarity search
* **Interactive Q\&A Chat Interface**: Query your documents conversationally
* **GPU-Acceleration Ready**: Leverages NVIDIA GPUs for high-performance inference and search

---

## **Setup Instructions**

### **1. Clone the Repository**

```bash
git clone https://github.com/shadaab123/Multimodal-RAG.git
cd Multimodal-RAG
```

### **2. Install Dependencies**

```bash
pip install -r requirements.txt
```

### **3. Set NVIDIA API Key**

```bash
export NVIDIA_API_KEY="your-api-key-here"
```

> You can get your API key from [build.nvidia.com](https://build.nvidia.com)

### **4. Start Milvus (GPU-enabled vector DB)**

Follow the official guide: [Install Milvus Standalone (GPU)](https://milvus.io/docs/install_standalone-docker-compose-gpu.md)

```bash
sudo docker compose up -d
```

---

## **Running the Application**

### **1. Ensure Milvus is Running**

```bash
docker ps
```

### **2. Start the App**

```bash
streamlit run app.py
```

### **3. Using the Interface**

* Open the URL shown in your terminal
* Upload files or specify a folder path
* Click **Process Files** or **Process Directory**
* Use the chat interface to ask questions

---

## **File Structure**

```bash
.
├── app.py                    # Main Streamlit application  
├── document_processors.py    # PDF, PPT, and image processors  
├── utils.py                  # API interactions, image utilities  
├── requirements.txt          # Project dependencies  
└── vectorstore/              # Auto-generated Milvus collection data  
```

---

## **GPU Acceleration**

To enable GPU-accelerated search in Milvus:

* Ensure your system has an **NVIDIA GPU**
* Use the **GPU-enabled Milvus Docker container**
* Update Milvus configuration in `app.py`:

```python
vector_store = MilvusVectorStore(
    host="127.0.0.1",
    port=19530,
    dim=1024,
    collection_name="your_collection_name",
    gpu_id=0  # Replace with your GPU ID
)
```

