# 🤖 HR Resume Screening AI

An AI-powered resume screener that compares a candidate’s resume (PDF) against a job description and returns a structured hiring analysis — match score, skills found, missing skills, strengths, weaknesses, and a recommendation. Runs entirely locally using **Ollama** (no API keys, no cloud costs) with a **Gradio** web UI.

## How it works

1. The recruiter pastes a **job description** into the UI.
1. They upload a candidate’s **resume as a PDF**.
1. The resume text is extracted using `pdfplumber`.
1. The job description + resume text are combined into a structured prompt and sent to a local LLM (`qwen2.5` via Ollama).
1. The model returns a structured breakdown:
- Candidate Name
- Match Score (out of 100)
- Skills Found
- Missing Skills
- Strengths
- Weaknesses
- Hiring Recommendation

## Tech stack

|Component                                         |Purpose                              |
|--------------------------------------------------|-------------------------------------|
|[Gradio](https://www.gradio.app/)                 |Web UI (`gr.Blocks`)                 |
|[Ollama](https://ollama.com/)                     |Local LLM inference (`qwen2.5` model)|
|[pdfplumber](https://github.com/jsvine/pdfplumber)|Extracting text from resume PDFs     |
|pandas                                            |Data handling                        |

## Prerequisites

- Python 3.10+
- [Ollama](https://ollama.com/download) installed and running locally
- The `qwen2.5` model pulled:
  
  ```bash
  ollama pull qwen2.5
  ```

## Installation

```bash
git clone https://github.com/indtajith20053/hr-resume-screening-ai.git
cd hr-resume-screening-ai
pip install gradio ollama pdfplumber pandas
```

## Usage

The core app currently lives in the notebook `HR_Resume_Screening_AI.ipynb`. Open and run it:

```bash
jupyter notebook HR_Resume_Screening_AI.ipynb
```

Run all cells — the last cell launches the Gradio app (`demo.launch()`) and opens a local URL (e.g. `http://127.0.0.1:7860`) in your browser. From there:

1. Paste the job description into the **Job Description** box.
1. Upload a resume PDF.
1. Click **Analyze Resume**.
1. Read the AI-generated hiring analysis in the output box.

## Project structure

```
hr-resume-screening-ai/
├── HR_Resume_Screening_AI.ipynb   # Main app: PDF extraction + Ollama analysis + Gradio UI
├── main.py                        # Placeholder entry point
├── .gradio/                       # Gradio runtime cache
└── .gitignore
```

## Roadmap ideas

- [ ] Move the notebook logic into `main.py` as a standalone script
- [ ] Batch-screen multiple resumes against one job description
- [ ] Export results to CSV/Excel for HR review
- [ ] Support `.docx` resumes in addition to PDF
- [ ] Add a `requirements.txt`

## License

Add a license of your choice (e.g. MIT) if you plan to share this publicly.
