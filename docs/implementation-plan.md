# Candidate implementation plan

## Focus

The job posting names one AI Engineer role. This submission focuses on the document retrieval, cited answer, and evaluation portion of that role. The full candidate task still requires both search tools, DSPy, local LLM hosting, bilingual interaction, citations, and model comparisons.

## Milestones

1. Confirm the supplied document set and available machine hardware. Select one allowed local LLM serving option.
2. Parse documents page by page, preserving `document_name`, `page_number`, and stable chunk IDs.
3. Build a keyword search tool and a vector search tool with the same result schema.
4. Compose the retrieval and answer steps in DSPy. Cite only retrieved pages; state uncertainty when support is missing.
5. Add a small Chinese/English CLI and a few representative questions.
6. Compare at least two viable LLM or embedding configurations as resources allow; log exact settings and inspect failures.
7. Update the README with commands actually run, dependency versions, evaluation table, limitations, and interview demo steps.

## Evidence to retain

Keep a short experiment log: question, language, expected source, retrieved pages, final answer, citation validity, model configuration, error or observation. Do not claim model results before the experiments are run.
