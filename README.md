# RAG-Gemini

# RAG-Based Query Answering with Gemini API

This project implements a Retrieval-Augmented Generation (RAG) system using Google's Gemini API. The goal is to provide accurate and contextually relevant answers by combining a pre-trained language model with custom prompts that ensure the model only considers relevant queries and ignores irrelevant ones.

## Overview

The RAG system is designed to enhance the capabilities of large language models by retrieving relevant passages from a database before generating answers. This approach leverages both the generative power of the model and the specificity of the retrieval system to provide more accurate and context-aware responses.

## Features

- **Custom Prompts:** The prompts are customized to instruct the model to focus on relevant data and ignore irrelevant queries.
- **Gemini API Integration:** Uses the Gemini API to access Google's state-of-the-art language models.
- **ChromaDB Integration:** Persistent storage and retrieval of relevant passages from a collection stored in ChromaDB.
- **Modular Design:** The project is structured to allow easy customization and extension.

## Prerequisites

- Python 3.8 or later
- Google Gemini API access
- ChromaDB for managing and querying your document collections

## Installation

1. **Clone the repository:**
   ```bash
   https://github.com/avirooppal/RAG-Gemini.git
   cd RAG-gemini
   ```

2. **Install required Python packages:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables:**

   - Create a `.env` file in the root directory of the project and add your Gemini API key:

     ```bash
     GEMINI_API_KEY=your_gemini_api_key_here
     ```

4. **Prepare the ChromaDB Collection:**
   - Populate your ChromaDB collection with relevant data passages using your own script or tools.

## Usage

### Loading ChromaDB Collection

Load your ChromaDB collection, which contains the documents you wish to retrieve passages from:

```python
db = load_chroma_collection(path="/path/to/db_chroma/", name="rag_experiment")
```

### Custom Prompt Generation

Create a custom prompt to ensure the language model focuses only on relevant data:

```python
def make_rag_prompt(query, relevant_passage):
    prompt = f"""
    You are an expert AI designed to answer queries strictly based on the provided information.
    Ignore irrelevant or out-of-context queries and only respond based on the following passage:
    {relevant_passage}
    
    Question: {query}
    Answer:
    """
    return prompt
```

### Generate an Answer

Using the RAG system, generate an answer based on the query:

```python
query = "The implementation of RAG"
answer = generate_answer(db, query=query)
print(answer)
```

### Example Output

```text
Question: The implementation of RAG
Answer: Retrieval-Augmented Generation (RAG) is a technique that combines retrieval-based approaches with generative models...
```

## Customization

### Modify the Prompt

To change the behavior of the language model, you can customize the `make_rag_prompt` function to tailor the responses to your specific needs.

### Extend the Retrieval System

You can enhance the retrieval system by modifying the `get_relevant_passage` function, which determines how relevant passages are fetched from the ChromaDB.

## Contact

For questions or inquiries, please reach out to avirooppal42@gmail.com.
