# Aura: The SEC Filing Analyst AI

**Aura (Analytical Unified Reasoning & Awareness Engine)** is an open-source platform that uses a hybrid AI architecture to intelligently structure, analyze, and reason about corporate SEC filings. It transforms dense, thousand-page documents into actionable insights.

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
![Project Status](https://img.shields.io/badge/status-in%20development-yellow)
![Python Version](https://img.shields.io/badge/python-3.9+-blue.svg)

---

### The Vision: Beyond Simple Search

Financial analysts spend countless hours manually parsing 10-K and 10-Q filings to find critical data points. This process is slow, prone to error, and a major cause of analyst burnout.

Aura is designed to solve this problem by acting as an AI-powered junior analyst. It goes beyond simple keyword search and summarization to perform a deep, structured analysis of the document's content, risk factors, and underlying narrative.

**[This is where you will add a GIF of the final application in action. It's the most important visual element. Use a tool like Giphy Capture, LiceCap, or ScreenToGif to record your screen.]**

![Aura Demo GIF](https://your-gif-host.com/aura_demo.gif)

---

### Technical Architecture

Aura employs a sophisticated, modular architecture that combines classical AI models with modern Large Language Models (LLMs) and a robust deployment stack.

```mermaid
graph TD
    A[User Request] --> B{Nginx Web Server};
    B --> C{Streamlit App};
    C --> D{Aura Engine};

    subgraph Aura Engine
        D -- asks question --> E[RAG Module];
        D -- requests analysis --> F[Bayesian Reasoning Module];
    end

    subgraph Data Pipeline (Offline Process)
        G[SEC EDGAR API] -- downloads HTML --> H{HMM Structuring Engine};
        H -- outputs structured JSON --> I[RAG Ingestion];
        I -- creates embeddings --> J[(Vector Database)];
    end

    E -- retrieves context --> J;
    F -- gets evidence --> E;
```

### Key Modules

*   **HMM Structuring Engine:** Uses a Hidden Markov Model (HMM) to intelligently parse the unstructured HTML of a filing into clean, labeled sections (e.g., `Item 1A. Risk Factors`), overcoming inconsistent formatting.
*   **RAG Knowledge Core:** Implements a Retrieval-Augmented Generation (RAG) pipeline. It converts the structured text into vector embeddings and stores them in a ChromaDB vector store for fast, semantic search.
*   **Bayesian Reasoning Engine:** Models financial concepts (Market Risk, Operational Risk, etc.) in a Bayesian Network. It uses the RAG module to find evidence in the text, then performs probabilistic inference to calculate an overall company risk score.

---

### Features

*   **Interactive Q&A:** Ask complex, natural language questions about the filing and get sourced answers.
*   **Automated Risk Report:** Generate a high-level risk assessment with a single click, showing the key factors contributing to the score.
*   **[Future] Conceptual Navigator:** An interactive graph visualization to discover hidden relationships between concepts, people, and projects within the document.

---

### Tech Stack

| Category      | Technology                                    |
|---------------|-----------------------------------------------|
| **AI/ML**     | `hmmlearn`, `pgmpy`, `sentence-transformers`, `scikit-learn` |
| **Backend**     | `Python 3.9+`, `ChromaDB`, `OpenAI API`       |
| **Frontend**    | `Streamlit`                                   |
| **Deployment**  | `Nginx`, `Gunicorn`, `Systemd`, `Ubuntu Server` |

---

### Live Demo

**[Once Day 8 is complete, you will put the live URL here.]**

**URL:** `https://your-aura-domain.com`

---

### Installation & Usage

Follow these steps to run Aura on your own machine.

**Prerequisites:**
*   Python 3.9+
*   An OpenAI API Key (or other LLM provider)

**1. Clone the repository:**
```bash
git clone https://github.com/your-username/aura-sec-analyzer.git
cd aura-sec-analyzer
```

**2. Set up the environment:**
```bash
# Create and activate a virtual environment
python3 -m venv venv
source venv/bin/activate

# Install all dependencies
pip install -r requirements.txt
```

**3. Configure your API Key:**
```bash
# Create a .env file from the example
cp .env.example .env

# Edit the .env file and add your OpenAI API key
nano .env
```

**4. Run the Data Pipeline:**
*(This only needs to be done once per company you want to analyze)*
```bash
# This script fetches the filing, parses it, and ingests it into the vector store
python scripts/run_full_pipeline.py --ticker AAPL
```

**5. Launch the Web Application:**
```bash
streamlit run app.py
```

Open your browser and navigate to `http://localhost:8501`.

---

### Project Roadmap

This project is currently in active development. Future plans include:

- [ ] **Module 4: The A* Knowledge Navigator:** Implementing the graph-based conceptual search.
- [ ] **Support for More Document Types:** Adding support for earnings call transcripts and proxy statements.
- [ ] **REST API:** Building a dedicated FastAPI backend to allow other applications to consume Aura's analysis.
- [ ] **Advanced Caching:** Implementing a caching layer (e.g., Redis) to speed up repeated queries.

---

## License

This project is licensed under the **Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License**. See the `LICENSE` file for details.

For inquiries about commercial licensing, please contact **[Your Name or Your Email]**.
