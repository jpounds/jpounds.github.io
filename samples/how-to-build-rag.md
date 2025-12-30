# How to Build a Simple RAG Application with LangChain

## Overview
This guide explains how to build a basic Retrieval-Augmented Generation (RAG) application using LangChain.  
RAG allows your AI to answer questions using external documents or data sources.

## Prerequisites
- Python 3.10+
- Basic knowledge of LLMs
- Installed `langchain` and `openai` Python packages

## Architecture Overview
A simple RAG pipeline consists of:
1. **Document loading** – Import your text data
2. **Embeddings & Vector Store** – Convert text to embeddings for retrieval
3. **Retriever** – Find relevant documents based on a query
4. **LLM** – Generate answers using retrieved content

## Step-by-Step Guide

### 1. Load Documents
```python
from langchain.text_splitter import CharacterTextSplitter
from langchain.document_loaders import TextLoader

loader = TextLoader("docs/sample.txt")
documents = loader.load()
splitter = CharacterTextSplitter(chunk_size=1000, chunk_overlap=100)
texts = splitter.split_documents(documents)

```

### 2. Create Embeddings & Vector Store
```python
from langchain.embeddings.openai import OpenAIEmbeddings
from langchain.vectorstores import FAISS

embeddings = OpenAIEmbeddings()
vectorstore = FAISS.from_documents(texts, embeddings)
```

### 3. Set Up Retriever 
```python
retriever = vectorstore.as_retriever(search_type="similarity", k=5)
```

### 4. Query the LLM 
```python
from langchain.chains import RetrievalQA
from langchain.chat_models import ChatOpenAI

qa_chain = RetrievalQA.from_chain_type(
    llm=ChatOpenAI(temperature=0),
    retriever=retriever
)

query = "What is Retrieval-Augmented Generation?"
answer = qa_chain.run(query)
print(answer)
```



