# 📝 Jira to FRD Generator

An AI-powered web application that automatically generates a **Functional Requirements Document (FRD)** from a Jira Case ID. It fetches the case summary, description, and attachments — then uses an AI model (OpenAI GPT-4o or Google Gemini) to populate a structured Word document template.

---

## ✨ Features

- 🔗 **Jira Integration** — Fetches case summary, description, and attachments automatically
- 🤖 **AI-Powered** — Uses OpenAI GPT-4o or Google Gemini to generate FRD content
- 📄 **Smart Templating** — Populates the `FRD template.docx` including the Screen Components table
- ⬇️ **One-Click Download** — Download the finished `.docx` file directly from the browser
- 🎨 **Premium UI** — Animated dark-mode interface with glassmorphism and gradient effects

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/jira-frd-generator.git
cd jira-frd-generator
```

### 2. Create a virtual environment & install dependencies
```bash
python3 -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Set up your API Keys
Create a file named `APIKey.env` in the project root (**do not commit this file!**):
```env
JIRA_BASE_URL=https://your-domain.atlassian.net
JIRA_EMAIL=your-email@example.com
JIRA_API_TOKEN=your-jira-api-token
OPENAI_API_KEY=your-openai-api-key        # Optional
GEMINI_API_KEY=your-gemini-api-key        # Optional (free via Google AI Studio)
```

**At least one of `OPENAI_API_KEY` or `GEMINI_API_KEY` is required.**

> 🔑 Get a **Jira API Token**: https://id.atlassian.com/manage-profile/security/api-tokens  
> 🔑 Get a **Gemini API Key** (free): https://aistudio.google.com/app/apikeys

### 4. Run the application
```bash
streamlit run app.py
```
Open your browser at **http://localhost:8501**

---

## 🗂️ Project Structure

```
├── app.py               # Main Streamlit application
├── FRD template.docx    # Word document template (required)
├── requirements.txt     # Python dependencies
├── .gitignore           # Excludes secrets and generated files
├── APIKey.env           # ⚠️ Your credentials (NOT committed to git)
└── README.md            # This file
```

---

## 🧠 How It Works

1. Enter a **Jira Case ID** (e.g., `PROJ-123`) in the web UI
2. The app fetches the case **summary**, **description**, and **attachments** via the Jira REST API
3. An AI model generates structured FRD content mapped to each section of the template
4. The `FRD template.docx` is populated — including filling the **Screen Components table** with AI-identified UI components
5. Download the completed FRD as a `.docx` file

---

## ⚙️ LLM Fallback Logic

The app will try **OpenAI** first. If your quota is exceeded (HTTP 429), it automatically falls back to **Google Gemini** — no manual switching required.

---

## 📋 Requirements

- Python 3.9+
- A valid Jira account with API access
- An OpenAI or Google Gemini API key
