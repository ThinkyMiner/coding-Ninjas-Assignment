# Multi-Agent Finance Assistant

This project is a multi-source, multi-agent finance assistant designed to deliver spoken market briefs and financial insights. It leverages a microservices architecture and a Streamlit web application for user interaction.

## Features

*   **Multi-Agent System:** Utilizes specialized agents for different tasks like data retrieval, analysis, and voice synthesis.
*   **Microservices Architecture:** Ensures scalability and modularity with services for API interaction, web scraping, data retrieval, language processing, financial analysis, and voice output.
*   **Spoken Market Briefs:** Delivers financial information via synthesized speech.
*   **Streamlit Interface:** Provides an interactive web application for users.
*   **Vector Store Integration:** Manages and retrieves documents/data efficiently using a FAISS vector store.

## Architecture

The application employs a microservices architecture, orchestrated to work in concert. The key components are:

*   **Orchestrator Service:** Coordinates the workflow and communication between all other services.
*   **API Service:** Manages interactions with external APIs (e.g., financial data providers).
*   **Scraping Service:** Retrieves data from web sources.
*   **Retriever Service:** Handles document retrieval and interaction with the vector store (FAISS index and text data).
*   **Language Service:** Provides Natural Language Processing (NLP) capabilities, potentially including language model interactions.
*   **Analysis Service:** Performs financial data analysis and generates insights.
*   **Voice Service:** Converts text-based information into spoken audio output.
*   **Streamlit App:** The user-facing web application built with Streamlit.

## Tech Stack

*   **Backend:** Python, FastAPI (for microservices)
*   **Frontend (Interface):** Streamlit
*   **NLP/AI:** Langchain, Langchain-Google-Genai, Sentence-Transformers, OpenAI Whisper (for STT), gTTS (for TTS)
*   **Data Storage/Retrieval:** FAISS (for vector store)
*   **Web Scraping:** BeautifulSoup4, Requests
*   **Key Libraries:** Uvicorn, Pydub, Alpha Vantage, Langgraph, LXML, python-dotenv.

## Project Structure

```
.
├── agents/               # Core logic for different agents
├── app/                  # Application-specific code (main.py, streamlit_app.py)
├── audio/                # Sample audio files
├── data/                 # Data files, including vector_store
│   └── vector_store/
├── data_ingestion/       # Scripts for populating data (e.g., from SEC)
├── docs/                 # Project documentation
├── services/             # Microservice implementations
├── venv_3_11/            # Python virtual environment (example)
├── .env                  # Environment variables (ports, API keys - create this file)
├── README.md             # This file
├── requirements.txt      # Python dependencies
```

## Setup and Installation

### Prerequisites

*   Python 3.11+
*   An `.env` file for API keys and configurations (see Configuration section)

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd <repository-name>
```

### 2. Create and Configure `.env` File

Create a `.env` file in the project root. This file will store your API keys and service port configurations. Example:

```env
# .env
# API Keys (replace with your actual keys)
ALPHA_VANTAGE_API_KEY=YOUR_ALPHA_VANTAGE_KEY
GOOGLE_API_KEY=YOUR_GOOGLE_AI_STUDIO_KEY
# Add other API keys as needed by your agents/services

# Service Ports (defaults are shown, can be customized)
API_PORT=8000
SCRAPING_SERVICE_PORT=8001
RETRIEVER_SERVICE_PORT=8002
LANGUAGE_SERVICE_PORT=8003
ANALYSIS_SERVICE_PORT=8004
VOICE_SERVICE_PORT=8005
ORCHESTRATOR_SERVICE_PORT=8006
STREAMLIT_PORT=8501 # Default Streamlit port
```
**Important:** Ensure your services and agents are configured to read these environment variables.

### 3. Local Development (Python Virtual Environment)

   a. **Create and activate a virtual environment:**

      ```bash
      python3 -m venv venv
      source venv/bin/activate  # On Windows use `venv\Scripts\activate`
      ```

   b. **Install dependencies:**

      ```bash
      pip install -r requirements.txt
      ```

## Running the Application

### 1. Local Development (after setup)

   a. **Start the microservices:**
      The `app/main.py` script is designed to start all configured microservices.

      ```bash
      python app/main.py
      ```
      This will launch each service defined in `SERVICES_CONFIG` within `app/main.py`. Check the console output for the status of each service and the ports they are running on.

   b. **Run the Streamlit application:**
      In a separate terminal (ensure your virtual environment is activated if not using Docker for Streamlit):

      ```bash
      streamlit run app/streamlit_app.py
      ```
      Or, if you have a top-level `streamlit_app.py` that imports from `app.streamlit_app`:
      ```bash
      streamlit run streamlit_app.py
      ```
      Open your browser and navigate to `http://localhost:8501` (or the port Streamlit indicates).

## Configuration

*   **Environment Variables:** Critical configurations like API keys and service ports are managed via an `.env` file in the project root. See the `.env` example in the Setup section.
*   **Service Endpoints:** The Streamlit app and services need to know the URLs/ports of other services they depend on. This is typically managed via environment variables loaded at runtime.

## Contributing

Contributions are welcome! Please follow these steps:

1.  Fork the repository.
2.  Create a new branch (`git checkout -b feature/your-feature-name`).
3.  Make your changes.
4.  Commit your changes (`git commit -m 'Add some feature'`).
5.  Push to the branch (`git push origin feature/your-feature-name`).
6.  Open a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details (if one exists, otherwise consider adding one).

## Acknowledgements

*   Built by Kartik Sehgal
*   Inspired by various financial tools and AI agent frameworks.

---
*This README is a comprehensive guide. You may need to adjust paths, commands, or configurations based on the exact current state and ongoing development of the project.*


### Local Deployment

1. Clone the repository
2. Install dependencies:
   ```
   pip install -r requirements.txt
   ```
3. Run the main application:
   ```
   python app/main.py
   ```
4. Open the Streamlit app in your browser at http://localhost:8501
