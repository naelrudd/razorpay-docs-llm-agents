# Razorpay docs — LLM mirror

Machine-readable mirror of [official docs](https://razorpay.com/docs/llms.txt) as plain Markdown, organized 1:1 by URL path, for LLM ingestion, RAG, and knowledge graphs.

## Quick start

- `llms.txt` — official link index
- `llms-full.txt` — entire corpus in one file (2238 pages)
- `INDEX.md` — every page with its first heading

Point an LLM at `llms-full.txt`, or feed `INDEX.md` for discovery.

## Rebuild from local corpus

```bash
llms-mirror full   # regenerate llms-full.txt
llms-mirror index  # regenerate README.md / INDEX.md
```
