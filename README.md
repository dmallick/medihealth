# medihealth

Built with AI power to diagnose disease

## Overview

**medihealth** is an AI-powered medical chatbot that leverages document retrieval and large language models to answer user questions based on your own medical data. It uses Pinecone for vector storage, Hugging Face for embeddings, and supports both OpenAI and Google Gemini models for chat.

## Features

- Upload and index your own medical documents (PDFs).
- Semantic search over your documents using Pinecone.
- Chatbot interface powered by Google Gemini (default) or OpenAI GPT models.
- Web interface built with Flask and Bootstrap.

## Project Structure

```
.
├── app.py                # Main Flask app and chatbot logic
├── store_index.py        # Script to index documents into Pinecone
├── src/
│   ├── helpers.py        # PDF loading, text splitting, embedding helpers
│   ├── prompt.py         # Prompt templates
├── templates/
│   └── chat.html         # Chatbot web UI
├── static/
│   └── style.css         # UI styles
├── requirements.txt      # Python dependencies
├── .env                  # API keys and environment variables
├── README.md
└── ...
```

## Setup

1. **Clone the repository**  
   ```sh
   git clone <repo-url>
   cd medihealth
   ```

2. **Create and activate a virtual environment**  
   ```sh
   python3 -m venv medihealthenv
   source medihealthenv/bin/activate
   ```

3. **Install dependencies**  
   ```sh
   pip install -r requirements.txt
   ```

4. **Set up your `.env` file**  
   Create a `.env` file in the root directory with the following keys:
   ```
   PINECONE_API_KEY=your-pinecone-api-key
   GOOGLE_API_KEY=your-google-api-key
   # OPENAI_API_KEY=your-openai-api-key (optional)
   ```

5. **Index your documents**  
   Place your PDFs in the `data/` directory and run:
   ```sh
   python store_index.py
   ```

6. **Run the app**  
   ```sh
   python app.py
   ```
   The chatbot will be available at [http://localhost:8080](http://localhost:8080).

## Usage

- Open your browser and go to [http://localhost:8080](http://localhost:8080).
- Ask questions in natural language; the chatbot will answer using your indexed documents.

## Customization

- **Change the LLM**:  
  By default, the app uses Google Gemini (`gemini-2.0-flash`). To use OpenAI GPT, uncomment and configure the relevant lines in [`app.py`](app.py).
- **Modify prompts**:  
  Edit prompt templates in [`src/prompt.py`](src/prompt.py).

## Dependencies

See [requirements.txt](requirements.txt) for the full list.

## License