# Semantic Spotter: RAG System in Insurance Domain

## 📌 Background  
This project demonstrates how to **build a Retrieval-Augmented Generation (RAG) system** in the insurance domain using [LangChain](https://python.langchain.com/docs/introduction/).  

---

## 🎯 Problem Statement  
The objective is to design a **robust generative search system** capable of accurately answering queries from a set of insurance policy documents.  

---

## 📂 Documents  
Policy documents are located in the [Policy Documents](./Policy+Documents) directory.  

---

## 🛠️ Approach  

**LangChain Framework**  
LangChain is a powerful framework that simplifies building **LLM-powered applications**. It provides:  

- **Components** → Modular abstractions (Models, Embeddings, Retrievers, Agents, etc.)  
- **Use-Case Specific Chains** → Ready-made customizable workflows  
- **Core Building Blocks**:  
  - *Model I/O*: LLMs, prompts, output parsers  
  - *Retrieval*: Loaders, transformers, embeddings, vector stores  
  - *Chains*: Sequences of LLM calls  
  - *Memory*: Persisting application state  
  - *Agents*: Decision-making for tool usage  
  - *Callbacks*: Logging & monitoring  

LangChain’s **composition & modularity** allow quick development of complex and personalized applications.  

---

## 🏗️ System Layers  

1. **Reading & Processing PDFs** → [PyPDFDirectoryLoader](https://python.langchain.com/api_reference/community/document_loaders/langchain_community.document_loaders.pdf.PyPDFDirectoryLoader.html)  
2. **Document Chunking** → [RecursiveCharacterTextSplitter](https://python.langchain.com/docs/how_to/recursive_text_splitter/)  
3. **Generating Embeddings** → [OpenAIEmbeddings](https://python.langchain.com/docs/integrations/text_embedding/openai/)  
4. **Storing in ChromaDB** → [CacheBackedEmbeddings](https://python.langchain.com/api_reference/langchain/embeddings/langchain.embeddings.cache.CacheBackedEmbeddings.html)  
5. **Retrievers** → [VectorStoreRetriever](https://python.langchain.com/api_reference/core/vectorstores/langchain_core.vectorstores.base.VectorStoreRetriever.html)  
6. **Re-Ranking** → [HuggingFaceCrossEncoder](https://python.langchain.com/api_reference/community/cross_encoders/langchain_community.cross_encoders.huggingface.HuggingFaceCrossEncoder.html) (`BAAI/bge-reranker-base`)  
7. **Chains** → Prompt from LangChain Hub: `rlm/rag-promp`  

---

## 🖥️ System Architecture  

### High-Level Flow  
1. Load policy PDFs  
2. Split text into chunks  
3. Generate embeddings  
4. Store embeddings in ChromaDB  
5. Retrieve relevant chunks for queries  
6. Re-rank results using Cross-Encoder  
7. Answer queries with RAG Chain  

### Architecture Diagrams  
![Architecture 1](./images/arch1.png)  
![Architecture 2](./images/arch2.png)  

---

## 📋 Prerequisites  

- Python 3.7+  
- `langchain==0.3.13`  
- OpenAI API Key (stored in **OpenAI_API_Key.txt**)  

---

## 🚀 How to Run  

1. Clone the repository:  
   ```bash
   git clone https://github.com/Sravansanka/semantic-spotter.git
   ```  

2. Open the [Jupyter Notebook](https://github.com/Sravansanka/semantic-spotter/blob/main/semantic-spotter-langchain-notebook.ipynb).  

3. Run all cells to execute the pipeline.  

---

## ✅ Summary  
This project leverages **LangChain + ChromaDB + OpenAI Embeddings + HuggingFace Cross Encoder** to build a scalable **insurance policy RAG system**.  
