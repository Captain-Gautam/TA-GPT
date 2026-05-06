# TA-GPT: MultiPDF Chat App

> **Publication:** A research paper based on this project is available on [Zenodo](https://zenodo.org/records/10005991).
> **Tutorial:** The tutorial for the baseline project can be found on [YouTube](https://youtu.be/dXxQ0LR-3Hg).

## Introduction

---

TA-GPT is a Python application built with Streamlit and LangChain that allows you to chat with multiple PDF documents. You can ask questions about the PDFs using natural language, and the application will provide relevant responses based on the content of the documents. This app utilizes OpenAI's Large Language Models (or optionally HuggingFace models) and FAISS vectorstore to generate accurate answers to your queries. Please note that the app will only respond to questions related to the loaded PDFs.

## How It Works

---

![MultiPDF Chat App Diagram](./docs/PDF-LangChain.jpg)

The application follows these steps to provide responses to your questions:

1. **PDF Loading**: The app reads multiple PDF documents and extracts their text content using `PyPDF2`.
2. **Text Chunking**: The extracted text is divided into smaller chunks using LangChain's `CharacterTextSplitter`.
3. **Vector Store & Embeddings**: The application utilizes `OpenAIEmbeddings` to generate vector representations of the text chunks and stores them using `FAISS`.
4. **Similarity Matching**: When you ask a question, the app compares it with the text chunks and identifies the most semantically similar ones.
5. **Response Generation**: The selected chunks are passed to the `ChatOpenAI` language model along with the chat history (via `ConversationBufferMemory`), which generates a response based on the relevant context.

## Dependencies and Installation

---

To install TA-GPT, please follow these steps:

1. Clone the repository to your local machine.
2. Install the required dependencies by running the following command:

   ```bash
   pip install -r requirements.txt
   ```
3. Obtain an API key from OpenAI and add it to the `.env` file in the project directory.

   ```env
   OPENAI_API_KEY=your_secret_api_key
   ```

   *(Optional)* If you plan to use HuggingFace embeddings or models, you can also add your HuggingFace API key:

   ```env
   HUGGINGFACEHUB_API_TOKEN=your_huggingface_api_token
   ```

## Usage

---

To use TA-GPT, follow these steps:

1. Ensure that you have installed the required dependencies and added your API keys to the `.env` file.
2. Run the Streamlit application by executing the following command:

   ```bash
   streamlit run app.py
   ```
3. The application will launch in your default web browser, displaying the user interface.
4. Open the sidebar, load multiple PDF documents into the app, and click on **Process**.
5. Ask questions in natural language about the loaded PDFs using the main chat interface!

## Research & Publication

---

A research paper detailing the methodology and applications of this project has been formally published.
The full publication can be accessed here: **[https://zenodo.org/records/10005991](https://zenodo.org/records/10005991)**.

## License

---

The TA-GPT app is released under the [MIT License](https://opensource.org/licenses/MIT).
