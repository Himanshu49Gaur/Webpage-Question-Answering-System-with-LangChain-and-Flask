# Webpage-Question-Answering-System-with-LangChain-and-Flask
This project demonstrates a simple Flask API that fetches a webpage, processes the content into text chunks, generates embeddings for those chunks using Hugging Face models, stores them in a FAISS vector store, and enables querying through a question-answering (QA) system powered by LangChain.

## Requirements

- Python 3.13 or later
- Install the necessary dependencies with `pip`:

```bash
pip install -r requirements.txt
```

Setup
Hugging Face API Key: You will need a Hugging Face API key to generate embeddings from the model all-MiniLM-L6-v2 (or another model of your choice). Replace the HEADERS in the script with your personal API key.

Web Scraping URL: The URL in the script ("https://brainlox.com/courses/category/technical") is the webpage that will be scraped. You can change this to any URL you'd like to scrape and extract data from.

Vector Store: The embeddings are saved in a local FAISS vector store (vector_store). This allows you to store and query the processed data efficiently.

How It Works
1. Fetch Webpage Content
The script uses requests to fetch a webpage with the given URL. It also sets a custom User-Agent header to identify the bot.

2. Extract Data
Using BeautifulSoup, the text content of the webpage is extracted.

3. Process Data
The extracted text is split into chunks using LangChain's RecursiveCharacterTextSplitter to make it manageable for generating embeddings.

4. Generate Embeddings
The text chunks are passed to the Hugging Face API for generating embeddings using the all-MiniLM-L6-v2 model.

5. Store Embeddings
The embeddings are stored in a local FAISS vector store (vector_store) for efficient searching.

6. Load Vector Store
The vector store is loaded, and it is used to retrieve documents relevant to a query.

7. Question Answering Chain
A question-answering (QA) chain is created using Hugging Face's distilbert-base-uncased-distilled-squad model. The QA chain uses the vector store to retrieve relevant documents and generate answers based on them.
