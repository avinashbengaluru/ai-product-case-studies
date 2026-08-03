# Avinash Bengaluru

**Product engineer building AI-native operations apps and decision analytics.**

I ship full-stack products where AI is not a demo chat window — it runs through **document understanding, catalog construction, invoice matching, and clerk exception queues**. Private production systems stay private; this repo is the public writeup layer.

---

## Where AI actually shows up

| Layer | What AI does | What stays deterministic |
| --- | --- | --- |
| **Document intake** | Vision OCR + LLM turns PDF/image invoices into structured line items (qty, batch, expiry, descriptions) | Schema validation, clerk edit table |
| **Catalog building** | LLMs design variant matrices from messy billing strings + manufacturer docs; map strings onto real SKUs without Cartesian explosion | Stock ledger gates, pack rules, human publish |
| **Research assist** | Web/doc retrieval + Vision OCR on price lists/IFUs → structured catalog specs | Source citations, clerk acceptance |
| **Invoice matching** | LLM proposes variants only when local aliases/rules miss | Exact/alias/fuzzy first; confirm before write |
| **Ops UX** | Statused suggestions (`MATCHED` / `SUGGEST` / `NEW`) so AI is an exception queue | Durable IDs, FEFO stock, mobile scan |

**Principle:** spend model budget on ambiguity. Already-known billing strings and product-label scans should not call a model.

---

## What I build

| Pillar | Focus |
| --- | --- |
| **AI systems** | Multi-step LLM pipelines, OCR→JSON extract, catalog architect + mapper flows, measured fallbacks |
| **Analytics** | Match rates, model-vs-local mix, stock drawdown integrity, cycle time |
| **Product engineering** | Flutter + Next.js ops apps, APIs, inventory lots (FEFO), invoice processing |

---

## Selected product builds

1. **[Smart Invoice Matching](./case-studies/01-smart-invoice-matching.md)** — OCR + LLM extract, local-first resolve, AI suggestions on misses, AI-assisted catalog that makes matching possible.
2. **[Scan → invoice → stock](./case-studies/02-scan-to-invoice-stock.md)** — Phone-only sales capture (no external POS); product-label scan → draft → FEFO. Powered by the same AI-built catalog + match graph.

---

## How I use AI (working principles)

- **Several model jobs, not one chat.** Extract ≠ architect catalog ≠ map aliases ≠ suggest a miss — separate contracts, separate evals.
- **Rules and indexes first.** Exact aliases own the easy majority; models handle the long tail.
- **Human confirm on durable writes.** Suggestions are cheap; wrong stock links are not.
- **Budget the model.** Per-family / per-bill spend caps; stop calling once local hit rate is healthy.
- **No secret prompts in public.** Patterns and outcomes ship; keys, prompts, and customer data do not.

---

## Stack (representative)

`TypeScript` · `Next.js` · `Flutter` · `Firestore` · Google Vision OCR · LLM orchestration (incl. frontier models such as Grok) · catalog / inventory domain modeling

---

## Contact

- GitHub: [avinashbengaluru](https://github.com/avinashbengaluru)

---

*Images are synthetic mockups. Figures illustrate architecture and clerk impact — not production exports.*
