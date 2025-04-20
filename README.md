# Retrieval Augmented Generation
One of the most powerful applications enabled by LLMs is sophisticated question-answering (Q&A) chatbots. These are applications that can answer questions about specific source information. These applications use a technique known as retrieval-augmented generation (RAG). RAG is a technique for augmenting LLM knowledge with additional data, which can be your own data.

LLMs can reason about wide-ranging topics, but their knowledge is limited to public data up to the specific point in time that they were trained. If you want to build AI applications that can reason about private data or data introduced after a model’s cut-off date, you must augment the knowledge of the model with the specific information that it needs. The process of bringing and inserting the appropriate information into the model prompt is known as RAG.

LangChain has several components that are designed to help build Q&A applications and RAG applications, more generally.

Let's move forward to the architecture of a **RAG** 😃.

## RAG Architecture
A typical RAG has two main components
1) Indexing - It is a pipeline for ingesting and indexing data.
2) Retrieval And Generation - The RAG chaintakes the user query as an input(which happens at runtime) and then retrieves the data from the index and then passes the input to the model.

Let's Look at some examples:  
