# 📄 AI Document Assistant

An AI-powered PDF analysis application built with **Google Gemini, Gradio, and Google Colab**. Upload a PDF to generate executive summaries, extract key insights, ask questions about the document, search for specific text, and create study materials and downloadable reports.

## ✨ Features

* **📑 PDF Text Extraction** — Extract readable text from PDF documents and view document statistics.
* **📝 Executive Summary** — Generate structured summaries covering main topics, key findings, important details, and intended audience.
* **🔑 Key Insights** — Extract important points, concepts, dates, numbers, named entities, and recommendations.
* **💬 Ask Your PDF** — Ask questions and receive answers grounded in relevant document excerpts.
* **🔍 Document Search** — Search for exact words or phrases and view matching text with page numbers.
* **🎓 Study Helper** — Generate revision questions, short-answer quizzes, and discussion prompts.
* **🕘 Question History** — Review questions and answers from the current session.
* **📥 Downloadable PDF Report** — Create a formatted report from previously generated analyses.
* **⚡ Response Caching** — Reuse cached AI responses to reduce repeated API requests.
* **🔄 Model Fallback** — Try alternative configured Gemini models when a model is unavailable.
* **🛡️ API Error Handling** — Display helpful messages for missing API keys, quota limits, and unavailable models.
* **🔐 Secure API Key Handling** — Read the Gemini API key from Google Colab Secrets instead of displaying it in the application interface.

## 🛠️ Tech Stack

* **Language:** Python
* **AI Model:** Google Gemini
* **AI SDK:** Google Gen AI SDK
* **User Interface:** Gradio
* **PDF Processing:** pypdf
* **PDF Report Generation:** ReportLab
* **Development Environment:** Google Colab

## 🚀 Getting Started

### Option 1: Run in Google Colab

This is the recommended way to run the project.

**1. Open the notebook**

Open `AI_Document_Assistant.ipynb` in Google Colab.

**2. Create a Gemini API key**

Get an API key from [Google AI Studio](https://aistudio.google.com/).

**3. Configure Google Colab Secrets**

* Open the **Secrets** panel in Colab.
* Create a secret named `gen`.
* Paste your API key into the secret's value field.
* Enable notebook access for the secret.

**4. Run the application**

Run the notebook cell containing the application code. Wait for the dependencies to install and the Gradio interface to launch.

**5. Upload a PDF**

Upload a text-based PDF and click **Load Document**. You can then generate summaries, extract insights, ask questions, search the document, create study questions, and download a report.

## 💻 Running Locally

The application currently uses Google Colab Secrets to retrieve the Gemini API key. To run it locally, adapt the key-loading section to use an environment variable.

For example:

```python
import os
from google import genai

GEMINI_API_KEY = os.environ.get("GEMINI_API_KEY")

if not GEMINI_API_KEY:
    raise ValueError("Please configure the GEMINI_API_KEY environment variable.")

client = genai.Client(api_key=GEMINI_API_KEY)
```

Install the required packages:

```bash
pip install -U gradio pypdf google-genai reportlab
```

Save the application as a Python file, apply the local API-key configuration, and run it with Python. The `google.colab.userdata` import and Colab-specific secret access must be adapted for local execution.

## 📖 How to Use

1. Upload a PDF document.
2. Click **Load Document** to extract its text.
3. Review the document statistics and text preview.
4. Open the **Summary** tab to generate an executive summary.
5. Open **Key Insights** to extract important concepts and findings.
6. Use **Ask PDF** to ask questions about the document.
7. Use **Search** to find exact words or phrases.
8. Open **Study Helper** to generate revision and discussion questions.
9. Visit **History** to review questions and answers.
10. Open **Report** to create a downloadable PDF from analyses already generated.

## 🔒 API Key Security

The application retrieves its Gemini API key from Google Colab Secrets using the secret name `gen`.

* Do not hardcode your API key in the source code.
* Do not upload API keys or other credentials to GitHub.
* Do not share screenshots containing secret values.
* If an API key is accidentally exposed, revoke it and generate a replacement.

## ⚠️ Limitations

* **Scanned PDFs:** The current version extracts selectable text. Image-only PDFs require OCR, which is not included.
* **API Quotas:** Gemini requests may fail when usage limits are reached.
* **Model Availability:** Configured Gemini models may not be available to every API project or region.
* **Large Documents:** AI analysis uses limited portions of extracted document text, so some content in very large PDFs may not be included.
* **Answer Accuracy:** Responses depend on the extracted text and may occasionally be incomplete or incorrect. Verify important information against the original document.
* **Page Retrieval:** Question answering uses keyword-frequency scoring to select relevant pages, which may not always identify the best excerpts.
* **Session Storage:** Application state and cached responses are maintained in memory for the current running session and are not a persistent database.

## 🔮 Future Improvements

* OCR support for scanned PDFs.
* Improved semantic search and document retrieval.
* Support for multiple PDF documents.
* More advanced study tools and answer explanations.
* Export options for summaries and study materials.
* Improved document chunking for large PDFs.
* Persistent storage for chat history and saved analyses.

## 👨‍💻 Project Overview

This project demonstrates how generative AI can be combined with PDF processing and an interactive web interface to make document analysis, information retrieval, and study preparation easier.

Built with Python, Google Gemini, Gradio, and Google Colab.
