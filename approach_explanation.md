# Approach Explanation

## Objective
To build a generic document intelligence system that extracts and prioritizes relevant sections from a variety of documents, customized for a given persona and task.

## Methodology

### 1. Document Parsing
The system parses structured text (headings, summaries) from each document. Due to the constraint of CPU-only and sub-1GB runtime, we use heuristic-based parsing for titles and section headers.

### 2. Persona & Job Alignment
Each persona is associated with a concrete job-to-be-done. The system cross-references section titles and content for semantic overlap with job keywords like "methodology", "financials", "reaction mechanisms".

### 3. Importance Ranking
Sections are ranked using:
- Relevance to persona keywords
- Structural position (executive summaries ranked higher)
- Explicit mentions of core concepts (e.g., R&D, Arrhenius, Benchmarks)

### 4. Sub-Section Refinement
From key sections, concise summaries are extracted by filtering for definitions, metrics, named concepts, and practical summaries.

## Adaptability
This approach is domain-agnostic, works on varied document types (academic, financial, educational), and provides robust summaries even without access to model-based NLP tools.

## Output
The final output includes structured JSON with metadata, extracted sections, and refined sub-section summaries. All processing fits within the 60s CPU-only constraint.