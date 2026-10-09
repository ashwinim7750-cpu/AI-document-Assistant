# 📄 AI Document Assistant

An AI-powered PDF analysis tool built with **Google Gemini, Python, and Gradio**. Upload a PDF, explore its contents, generate summaries, ask document-grounded questions, and create study materials — all through an interactive web interface.

## ✨ Features

* **📤 PDF Upload & Text Extraction** — Upload a PDF and extract its readable text.
* **📝 Executive Summary** — Generate a concise, professional overview of a document.
* **💡 Key Insights** — Identify important concepts, facts, dates, figures, and requirements.
* **💬 Ask Your PDF** — Ask natural-language questions and receive answers grounded in the document.
* **📍 Page References** — Retrieve relevant PDF pages to help locate supporting information.
* **🔎 Document Search** — Search exact words and phrases with page references.
* **🎓 Study Helper** — Generate revision questions and study prompts from document content.
* **🕘 Conversation History** — Review previous questions and answers during a session.
* **📑 Downloadable Analysis Report** — Generate a PDF report containing document analysis.
* **⚡ Response Caching** — Reuse cached AI responses during a session to reduce duplicate API calls.
* **🔐 Secure API Key Handling** — Read the Gemini API key from Google Colab Secrets instead of displaying an API key field in the interface.
* **⚠️ Error Handling** — Display useful messages for API quota issues and common API-key errors.

## 🛠️ Tech Stack

| Technology        | Purpose                                     |
| ----------------- | ------------------------------------------- |
| Python            | Application logic and document processing   |
| Google Colab      | Development and execution environment       |
| Google Gemini API | AI-powered summaries, insights, and answers |
| Google Gen AI SDK | Communication with Gemini                   |
| Gradio            | Interactive web interface                   |
| PyPDF             | PDF text extraction                         |
| ReportLab         | PDF report generation                       |

## 🚀 Getting Started

### Option 1: Run in Google Colab

**1. Open the notebook**

Open `AI_Document_Assistant.ipynb` in [Google Colab](https://colab.research.google.com/).

**2. Create a Gemini API key**

Visit [Google AI Studio](https://aistudio.google.com/) and create an API key.

**3. Store the key in Colab Secrets**

In your Colab notebook:

1. Open the **Secrets** panel using the key icon in the sidebar.
2. Add a new secret named `gen`.
3. Paste your Gemini API key into the secret's value field.
4. Enable notebook access for the secret.

The application reads the key using:

```python
GEMINI_API_KEY = userdata.get("gen")
```

**Never paste your actual API key into the notebook, source code, or GitHub repository.**

**4. Run the notebook**

Run the notebook's main code cell using `Shift + Enter`. Wait for the Gradio application link, then open it to access the interface.

### Option 2: Clone the Repository

Replace `YOUR_USERNAME` with your GitHub username.

```bash
git clone https://github.com/YOUR_USERNAME/ai-document-assistant.git
cd ai-document-assistant
pip install -r requirements.txt
```

The current notebook is designed for Google Colab. To run the application locally, adapt the API-key retrieval code to use an environment variable and ensure that the required dependencies are installed.

For example, your local environment can read the key with:

```python
import os

GEMINI_API_KEY = os.environ.get("GEMINI_API_KEY")

if not GEMINI_API_KEY:
    raise ValueError("Set the GEMINI_API_KEY environment variable.")
```

Make sure the application initializes the Gemini client using `GEMINI_API_KEY`. A `requirements.txt` file must also be included in the repository for the installation command above to work.

## 📖 How to Use

1. Launch the application in Google Colab.
2. Upload a text-based PDF document.
3. Click **Load Document**.
4. Choose a feature from the interface:

   * **Summary** — Generate an executive summary.
   * **Key Insights** — Extract important concepts and information.
   * **Ask PDF** — Ask questions about the uploaded document.
   * **Search** — Find exact words or phrases and their page references.
   * **Study Helper** — Generate revision questions and study prompts.
   * **Document Text** — Inspect the extracted PDF text.
   * **History** — Review previous questions and answers.
   * **Report** — Generate and download a PDF analysis report.

## 🔐 Security & API Key Management

The application retrieves the Gemini API key from Google Colab Secrets.

* Never commit API keys or credentials to GitHub.
* Do not hardcode API keys in Python files or notebooks.
* Keep local environment files containing secrets out of version control.
* If a key is exposed, revoke it in Google AI Studio and create a replacement.

Consider adding a `.gitignore` file to prevent accidental commits of sensitive or temporary files.

## ⚠️ Limitations

* **Scanned PDFs:** Image-only documents may require OCR before their text can be processed.
* **API quotas:** Requests depend on Gemini API limits and the account's available quota.
* **Large documents:** Very large PDFs may require chunking or selective text retrieval to control processing costs and token usage.
* **AI accuracy:** Generated answers and summaries may omit details or misinterpret the source. Verify important information against the original document.
* **Page references:** Retrieved page references help locate relevant passages but do not guarantee that every generated claim is supported by those pages.
* **Internet access:** Gemini-powered features require connectivity to the API.

## 🔮 Future Improvements

Potential enhancements include:

* OCR support for scanned PDFs.
* Support for multiple document formats.
* Improved semantic search and retrieval.
* More advanced document comparison.
* Persistent conversation history.
* Export options for Markdown and Word documents.
* More detailed source citations for generated answers.

## 📄 License

This project is intended to be distributed under the **MIT License**. Include a `LICENSE` file containing the MIT License text in the repository before describing the project as officially licensed under it.

## 👩‍💻 Author

Developed as an AI-powered document analysis project using Python, Gemini, and Gradio.

If you find this project useful, consider giving the repository a ⭐ on GitHub.
