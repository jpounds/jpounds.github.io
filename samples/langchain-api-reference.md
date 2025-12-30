# LangChain Mini API Reference

## TextLoader
Loads documents from a file.

```python
from langchain.document_loaders import TextLoader
loader = TextLoader("docs/sample.txt")
docs = loader.load()
```

## CharacterTextSplitter
Splits text into smaller chunks for embeddings.

```python
from langchain.text_splitter import CharacterTextSplitter
splitter = CharacterTextSplitter(chunk_size=1000, chunk_overlap=100)
chunks = splitter.split_documents(docs)
```
## OpenAIEmbeddings
```python
from langchain.embeddings.openai import OpenAIEmbeddings
embeddings = OpenAIEmbeddings()
```

## FAISS
```python
from langchain.vectorstores import FAISS
vectorstore = FAISS.from_documents(chunks, embeddings)
retriever = vectorstore.as_retriever(search_type="similarity", k=5)
```
## RetrievalQA
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

## ChatOpenAI
```python
from langchain.chat_models import ChatOpenAI
llm = ChatOpenAI(temperature=0)
```
