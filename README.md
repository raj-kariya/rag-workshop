# Retrieval Augmented Generation
One of the most powerful applications enabled by LLMs is sophisticated question-answering (Q&A) chatbots. These are applications that can answer questions about specific source information. These applications use a technique known as retrieval-augmented generation (RAG). RAG is a technique for augmenting LLM knowledge with additional data, which can be your own data.

LLMs can reason about wide-ranging topics, but their knowledge is limited to public data up to the specific point in time that they were trained. If you want to build AI applications that can reason about private data or data introduced after a model’s cut-off date, you must augment the knowledge of the model with the specific information that it needs. The process of bringing and inserting the appropriate information into the model prompt is known as RAG.

LangChain has several components that are designed to help build Q&A applications and RAG applications, more generally.

Let's move forward to the architecture of a **RAG** 😃.

## RAG Architecture
A typical RAG has two main components
1) Indexing - It is a pipeline for ingesting and indexing data.
2) Retrieval And Generation - The RAG chaintakes the user query as an input(which happens at runtime) and then retrieves the data from the index and then passes the input to the model.

Let's Understand both the components in detail:  

 **Indexing**
1. Load: First, you must load your data. This is done with [DocumentLoaders](https://python.langchain.com/docs/modules/data_connection/document_loaders/).

2. Split: [Text splitters](https://python.langchain.com/docs/modules/data_connection/document_transformers/) break large `Documents` into smaller chunks. This is useful both for indexing data and for passing it into a model because large chunks are harder to search and won’t fit in a model’s finite context window.

3. Store: You need somewhere to store and index your splits so that they can later be searched. This is often done using a [VectorStore](https://python.langchain.com/docs/modules/data_connection/vectorstores/) and [Embeddings](https://python.langchain.com/docs/modules/data_connection/text_embedding/) model.

<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/WEE3pjeJvSZP0R7UL7CYTA.png" width="50%" alt="indexing"/> <br>
<span style="font-size: 10px;">[source](https://python.langchain.com/docs/use_cases/question_answering/)</span>


- **Retrieval and generation**
1. Retrieve: Given a user input, relevant splits are retrieved from storage using a retriever.
2. Generate: A ChatModel / LLM produces an answer using a prompt that includes the question and the retrieved data.

<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/SwPO26VeaC8VTZwtmWh5TQ.png" width="50%" alt="retrieval"/> <br>
<span style="font-size: 10px;">[source](https://python.langchain.com/docs/use_cases/question_answering/)</span>


## PreProcessing

- Loading the documents in txt format. Example loading company policies for this project.

## Splitting Docs into chunks
`LangChain` is used to split the document and create chunks. It helps you divide a long story (document) into smaller parts, which are called `chunks`, so that it's easier to handle. 

For the splitting process, the goal is to ensure that each segment is as extensive as if you were to count to a certain number of characters and meet the split separator. This certain number is called `chunk size`. Let's set 1000 as the chunk size in this project. Though the chunk size is 1000, the splitting is happening randomly. This is an issue with LangChain. `CharacterTextSplitter` uses `\n\n` as the default split separator. You can change it by adding the `separator` parameter in the `CharacterTextSplitter` function; for example, `separator="\n"`.

## Embedding and storing
This step is the `embed` and `store` processes in `Indexing`. <br>
<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/u_oJz3v2cSR_lr0YvU6PaA.png" width="50%" alt="split"/>

In this step, you're taking the pieces of the story, your "chunks," converting the text into numbers, and making them easier for your computer to understand and remember by using a process called "embedding." Think of embedding like giving each chunk its own special code. This code helps the computer quickly find and recognize each chunk later on. 

You do this embedding process during a phase called "Indexing." The reason why is to make sure that when you need to find specific information or details within your larger document, the computer can do so swiftly and accurately.

# Project - Summarize private documents using RAG, LangChain, and LLMs
I am beginning my journey with Summarize Private Documents Using RAG, LangChain, and LLMs project in which I learned how to load documents and then split and embed private documents for efficient processing. This foundational project introduces secure document summarization using advanced LLMs and demonstrates how to create a chatbot capable of retrieving key information while maintaining data privacy. Here I used Use Llama 3.3 (on IBM watsonx.ai), LangChain, and RAG to enable LLMs to retrieve information from our own private document.
