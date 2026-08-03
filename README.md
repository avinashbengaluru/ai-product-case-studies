# Avinash Bengaluru

**Product engineer building AI-assisted operations systems and decision analytics.**

I design end-to-end tools where messy real-world data (invoices, stickers, billing strings) becomes reliable catalog matches, stock movements, and clerk-ready workflows — with AI used as a controlled last mile, not a black box.

---

## What I build

| Pillar | Focus |
| --- | --- |
| **AI systems** | Local-first resolution cascades, LLM fallbacks with human confirm, OCR → structured extract |
| **Analytics** | Match rates, stock drawdown integrity, exception queues, operational cycle time |
| **Product engineering** | Mobile + web ops apps, APIs, inventory lots (FEFO), invoice processing |

Private production systems stay private. This repo is the **public case-study layer**: clerk before/after, architecture, and impact — no secrets, no customer data, no proprietary catalogs.

---

## Case studies

1. **[AI catalog findability](./case-studies/01-ai-catalog-findability.md)** — **Before:** hunt & retype every invoice line. **After:** auto-match most lines; clerks only confirm exceptions.
2. **[Scan → invoice → stock](./case-studies/02-scan-to-invoice-stock.md)** — **Before:** pick from shelf, rebuild the bill at the desk. **After:** scan with the **phone camera only** (no external gun); process draws down the right lots (FEFO).

---

## How I use AI (working principles)

- **Rules and indexes first.** Exact aliases and deterministic matchers own the easy majority.
- **Models for ambiguity.** LLMs propose structured candidates; clerks confirm before durable writes.
- **Measure the system.** Hit rate, suggestion quality, and time-to-confirm beat demo screenshots.
- **No secret prompts as portfolio.** Patterns and diagrams ship publicly; production prompts, keys, and datasets do not.

---

## Stack (representative)

`TypeScript` · `Next.js` · `Flutter` · `Firestore` · Vision OCR · LLM orchestration · inventory / invoice domain modeling

---

## Contact

- GitHub: [avinashbengaluru](https://github.com/avinashbengaluru)

---

*Screenshots in the case studies use blurred UI / synthetic data. Figures are illustrative of architecture and outcomes, not production exports.*
