# nlp-text-mapping-pilot

# NLP & AI for Consumer Insight: Feasibility Pilot

This repository contains a fast-tracked prototype designed to map unstructured, qualitative consumer feedback into structured, decision-ready domain descriptors. 

The goal of this pilot is to demonstrate a workflow that reduces manual coding time for R&D screening decisions while maintaining high semantic accuracy.

## Theoretical Framework & Methodology
To map free-text consumer responses to a fixed set of descriptors when exact terms are not present, this pipeline avoids rigid keyword matching and instead utilizes a **semantic embedding approach**.

### 1. Latent Semantic Space & Text Embeddings
* Qualitative consumer phrases (e.g., "feels like a grease slick") and the domain lexicon (e.g., "Oily") are converted into dense mathematical vectors using a pre-trained **Transformer model** (such as a lightweight BERT or RoBERTa variant like `all-MiniLM-L6-v2`).
* This projects both the consumer language and the target industry lexicon into the same *latent semantic space*, where words with similar contextual meanings sit close together.

### 2. Nearest-Neighbor Retrieval via Cosine Similarity
* Because exact keywords may be missing, the pipeline calculates the **Cosine Similarity** (the angular distance) between the consumer text vector and all available descriptor vectors in the lexicon.
* The system retrieves the "nearest neighbor"—the descriptor with the highest similarity score—assigning the text to its closest logical domain classification.

### 3. Validation & Robustness Testing Framework
To ensure this AI workflow is reliable for industry stakeholders, the project incorporates:
* **Phrase Sensitivity Testing:** Evaluating if the model consistently maps different surface-level phrases (synonyms, slang) to the correct underlying lexicon term.
* **Confidence Thresholds:** Flagging ambiguous or low-similarity mappings for human review to mitigate error modes.
