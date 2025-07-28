# 🤖 Round 1B Submission – Persona-Driven Document Intelligence

## 🧠 Challenge Theme: “Connect What Matters — For the User Who Matters”

### 🎯 Goal
Build a **generic document analysis system** that extracts and prioritizes the most relevant sections from a set of PDF documents based on:
- A defined **persona** (e.g., student, analyst, researcher)
- A specific **job-to-be-done** (e.g., summarize, analyze, prepare, review)

---

## 📂 Project Structure

round1b_submission/
│
├── challenge1b_output.json # Final output JSON per spec
├── approach_explanation.md # Explanation of methodology and design
│
├── input_pdfs/ # Input document set (3–10 PDFs)
│ ├── test_case_1_academic_research.pdf
│ ├── test_case_2_business_analysis.pdf
│ └── Reaction_Kinetics_Study_Guide.pdf
│
└── output/ # (Optional) Intermediate summaries / logs

yaml
Copy
Edit

---

## 🧾 Input Specification

- **Documents**: 3–10 domain PDFs (research papers, financial reports, educational chapters, etc.)
- **Persona**: Describes role, expertise, focus (e.g., "Undergraduate Chemistry Student")
- **Job-to-be-done**: A goal the persona wants to achieve (e.g., "Identify key concepts for exam preparation")

---

## ✅ Output JSON Format

```json
{
  "metadata": {
    "input_documents": ["file1.pdf", "file2.pdf", ...],
    "persona": {
      "role": "Undergraduate Chemistry Student",
      "job_to_be_done": "Identify key concepts and mechanisms for exam preparation on reaction kinetics"
    },
    "processing_timestamp": "2025-07-28T12:00:00Z"
  },
  "extracted_sections": [
    {
      "document": "Reaction_Kinetics_Study_Guide.pdf",
      "page_number": 1,
      "section_title": "Rate Laws and Rate Expressions",
      "importance_rank": 1
    }
  ],
  "sub_section_analysis": [
    {
      "document": "Reaction_Kinetics_Study_Guide.pdf",
      "refined_text": "Rate laws describe how the rate depends on concentration. First-order: rate ∝ [A], Zero-order: rate is constant.",
      "page_number": 1
    }
  ]
}
⚙️ Execution Environment
✅ CPU-only (no GPU required)

✅ Model size ≤ 1GB (if used)

✅ No internet access during execution

✅ Must process 3–5 documents in ≤ 60 seconds

🧠 Methodology (See approach_explanation.md)
Text Extraction: Parse and clean text using PyMuPDF or PDFMiner

Section Relevance Ranking: Based on:

Keyword matching with job description

Title prominence (H1 > H2 > H3)

Semantic overlap (optional model under 1GB)

Subsection Summarization: Extract concise, topic-relevant definitions or mechanisms

Metadata Logging: Add persona, document list, and timestamp for traceability

🧪 Test Cases Included
Test Case 1: Academic Research
Documents: 4 papers on GNNs for drug discovery

Persona: PhD Researcher in Computational Biology

Job: Literature review focusing on methodologies, datasets, benchmarks

Test Case 2: Business Analysis
Documents: 3 tech company annual reports (2022–2024)

Persona: Investment Analyst

Job: Analyze revenue trends, R&D, market strategy

Test Case 3: Educational Content ✅ (Active)
Documents: 5 organic chemistry textbook chapters

Persona: Undergraduate Chemistry Student

Job: Identify key concepts and mechanisms for exam preparation

🧾 Deliverables
challenge1b_output.json

approach_explanation.md

Folder: input_pdfs/ (contains 3 PDFs)

(Optional): Dockerfile and script for automated batch processing

📥 How to Run (If Using Docker)
bash
Copy
Edit
docker build -t persona-doc-analyst .
docker run --rm -v $(pwd)/input:/app/input -v $(pwd)/output:/app/output --network none persona-doc-ana
