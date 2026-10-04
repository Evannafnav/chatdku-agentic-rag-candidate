# Evaluation protocol and experiment log

Use **only authorized documents** in `local_docs/`, outside version control. Create a balanced question set: English and Chinese, lexical and paraphrased questions, multi-page questions, and unanswerable prompts. Annotate expected document/page before looking at outputs. Keep the same corpus, split, and retrieval `k=5` across configurations.

| Run | Date | Machine/GPU | LLM server + model/revision | Embedding/revision | Language counts | Hit@5 | Answer correct / N | Claim support / N | Median latency | Failures |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Pending | — | — | — | — | — | — | — | — | — | Local model unavailable in this workspace |

For each case, save: question, expected document/page, retrieved keys, final answer, displayed citations, correctness judgment, whether the cited passage supports each factual claim, refusal on unanswerable cases, and wall-clock latency. Have a second reader adjudicate ambiguous support where possible. Do not infer LLM quality from retrieval hit@5 alone.

## Verified so far

- `python -m compileall -q src tests`: pass in Python 3.12.14.
- In-memory keyword example: `library midnight` retrieves `guide.pdf:p3:c1`; CJK tokenization retrieves `图书馆` from `图书馆开放`.
- These are code smoke checks, **not** empirical cross-model results or successful local-LLM hosting.
