# Agentic Architect Challenge

**A Python-based AI application featuring three intelligent agents powered by the Anthropic Claude API.**

This project demonstrates three practical AI workflows: customer support email automation, intelligent web scraping and summarization, and document-based question answering with conversation memory and tool usage.

## Overview

The Agentic Architect Challenge consists of three independent AI components designed to handle different tasks.

| Component                       | Description                                                                                          |
| ------------------------------- | ---------------------------------------------------------------------------------------------------- |
| **Part 1: Support Email Agent** | Classifies customer emails, detects escalation cases and drafts responses using a knowledge base.    |
| **Part 2: Web Scraper**         | Extracts and cleans webpage content, processes long pages in chunks and generates concise summaries. |
| **Part 3: Document Agent**      | Answers document-related questions, maintains conversation memory and uses a calculator when needed. |

All three components use Python and integrate with the Anthropic Claude API through a shared language-model module.

## System Architecture

The application follows a modular architecture in which each component handles a separate task while sharing common AI functionality.

**Architecture components:**

* **User Input:** Customer emails, website URLs, questions and documents.
* **Part 1:** Customer support classification, escalation and response drafting.
* **Part 2:** Web content extraction, cleaning, chunking and summarization.
* **Part 3:** Document retrieval, conversation memory and calculator functionality.
* **Shared AI Layer:** Python modules and the Anthropic Claude API integration.
* **Validated Outputs:** Draft responses, concise summaries and document-grounded answers.

## Features

### Part 1: Customer Support Email Agent

* **Email classification:** Categorizes messages into Billing, Technical, Feedback and Other.
* **Escalation detection:** Identifies emails that require human review, including data loss, service outages, security breaches and customers with more than three contacts in seven days.
* **Knowledge-based drafting:** Uses the support knowledge base to generate relevant draft responses.
* **Hallucination prevention:** Avoids inventing unsupported refund information.
* **Human oversight:** Escalation cases are identified before a response is drafted.

### Part 2: Intelligent Web Scraper

* **URL validation:** Checks that the provided URL uses HTTP or HTTPS.
* **Web extraction:** Retrieves webpage content using HTTP requests and Beautiful Soup.
* **Content cleaning:** Removes unnecessary HTML elements and website clutter.
* **Text chunking:** Splits long content into manageable chunks for processing.
* **AI summarization:** Uses Claude to summarize extracted content.
* **Length control:** Applies a word-limit guardrail to keep summaries concise.

### Part 3: Document Q&A Agent

* **Document retrieval:** Finds relevant content from the provided sample document.
* **Contextual answers:** Uses retrieved information to answer user questions.
* **Conversation memory:** Retains relevant conversational context.
* **Calculator tool:** Performs supported arithmetic calculations when required.
* **Grounded responses:** Instructs the model to avoid inventing answers unsupported by the document.

## Technology Stack

| Technology           | Purpose                               |
| -------------------- | ------------------------------------- |
| Python               | Core application development          |
| Anthropic Claude API | Language understanding and generation |
| Beautiful Soup       | HTML parsing and content extraction   |
| Requests             | HTTP requests for webpage retrieval   |
| python-dotenv        | Environment variable management       |
| Pytest               | Automated testing                     |

## Project Structure

```text
agentic_architect_challenge_claude/
│
├── app/
│   ├── llm.py
│   ├── support.py
│   ├── scraper.py
│   ├── document_agent.py
│   └── demo.py
│
├── data/
│   ├── sample_document.txt
│   └── support_kb.txt
│
├── tests/
│   ├── test_support.py
│   ├── test_scraper.py
│   └── test_document_agent.py
│
├── .env.example
├── .gitignore
├── pytest.ini
├── requirements.txt
├── README.md
└── system_architecture.pdf
```

## Installation

### 1. Clone the repository

```bash
git clone rvmiill
cd agentic_architect_challenge_claude
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

### 3. Activate the virtual environment

**Windows PowerShell:**

```powershell
.venv\Scripts\Activate.ps1
```

### 4. Install dependencies

```bash
pip install -r requirements.txt
```

## Configuration

Create a `.env` file in the project root using `.env.example` as a template.

Configure the following variables:

```env
ANTHROPIC_API_KEY=your_api_key_here
CLAUDE_MODEL=claude-haiku-4-5
```

Replace `your_api_key_here` with your Anthropic API key.

**Security:** Never commit your `.env` file or expose your API key in your GitHub repository.

## Usage

### Run the demonstration

```bash
python -m app.demo
```

This runs the project's demonstration workflow.

### Run the web scraper

```bash
python -m app.scraper https://example.com
```

Replace the example URL with the website you want to scrape.

### Run the automated tests

```bash
python -m pytest -v
```

## Testing

The project includes **20 automated tests** covering the three main components.

| Test module              | Coverage                                                     |
| ------------------------ | ------------------------------------------------------------ |
| `test_support.py`        | Email classification, escalation and contact history         |
| `test_scraper.py`        | URL validation, HTML extraction, chunking and summary limits |
| `test_document_agent.py` | Document retrieval, conversation memory and calculator usage |
| **Total**                | **20 tests**                                                 |

Run all tests with:

```bash
python -m pytest -v
```

## Design Decisions

**1. Modular architecture**

Each component is implemented separately, making the application easier to maintain, test and extend.

**2. Shared language-model integration**

A shared LLM module centralizes communication with the Anthropic Claude API, reducing duplicated integration code.

**3. Rule-based safeguards**

Explicit rules handle important escalation conditions, URL validation and output length limits rather than relying entirely on AI-generated decisions.

**4. Chunking for long content**

The scraper divides lengthy webpage content into smaller sections before summarization to make processing more manageable.

**5. Human oversight**

Sensitive customer support cases are flagged for escalation rather than automatically drafting a response.

## Limitations

* Email classification and escalation use predefined rules and may not recognize every possible wording.
* The scraper does not execute JavaScript-rendered webpages.
* Document retrieval uses a simple approach rather than a vector database.
* Calculator support is restricted to supported arithmetic expressions.
* The application is a prototype and has not been deployed as a production service.

## Future Improvements

* Introduce more advanced semantic email classification.
* Add retries, structured logging and monitoring.
* Support JavaScript-rendered webpages.
* Implement vector-based document retrieval.
* Expand automated testing with additional real-world scenarios.
* Add a web interface for interacting with all three agents.

---

**Author:** Ramil Chupov

**Project:** Agentic Architect Challenge
