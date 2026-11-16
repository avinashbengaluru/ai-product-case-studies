# Avinash Immaneni (`avinashbengaluru`)

**AI Agent & Data Systems Engineer · Open-Weight LLM Pipelines · Senior Data Scientist**

I build full-stack systems where AI is not a demo chat wrapper — it runs through **autonomous, tool-using agents, open-weight models (`Gemma 4` & `Gemma 2B LoRA`), dual-reader OCR pipelines, edge database routing (`~25 ms/line`), and reversible audit queues**.

I built **BillMiner** to turn **Tally Prime (a desktop Legacy ERP and book keeping system** communicating via `XML over HTTP :9000`) into an LLM-powered distribution and automated book keeping workflow across ~13,000 messy stock items — without changing how bookkeepers and accountants work in Tally.

> **Core Theme:** *XML in, intelligence out.* Spend model budget only on ambiguity: offload known lookups to ~25 ms edge databases at $0 token cost, replace expensive frontier APIs with open-weight models (`Gemma 4` + `Gemma 2B LoRA`), and let deterministic arithmetic checks decide when models disagree.

---

## Where AI Agents & Open-Weight Models Actually Run in BillMiner

| Layer | What AI Agents & Open-Weight Models Do | Deterministic Guardrails & Cost Controls |
| --- | --- | --- |
| **1. Dual-Reader Purchase Bill Scanner (`92%` / `291/317` bills)** | Custom **Vision OCR + rule-based table layout reader** runs in parallel with **LlamaParse ("OCRia-1")**; **Gemma 4** matches lines to Tally items & catalogue cards | **Arithmetic decides the winner:** line items must sum to the bill's printed taxable total (**12/12** match in regression); per-supplier notes re-verified by math |
| **2. Nightly Self-Learning & Catalogue Repair Agents** | Nightly **Cloudflare cron** diffs raw scans against posted Tally vouchers to learn supplier aliases/rules; scheduled **Claude cloud agent** audits bills and repairs catalogue cards | Fragment guards prevent learning from bad OCR substrings; every agent edit hits **audited, state-logged endpoints** with 1-click undo |
| **3. Edge Seller Detect (`~25 ms/line`) & LoRA Judge** | Maps WhatsApp (**81% top-1, 98% top-3**), Gmail (**75% top-1, 89% top-3**), and handwritten lists to Tally items; fine-tuned **Gemma 2B LoRA** judge (in progress) ranks top-5 candidates | **Cloudflare Workers + D1 / KV** handle fast lookup in ~25 ms at $0 model cost using per-item "defining words"; offers top-3 picker when unsure |
| **4. "Rao" (Retrieval Augmented Outvoicing Agent)** | In-workspace invoicing chat agent that puts pasted/photographed customer orders **straight onto the live bill** with inline variant pickers, or drafts GST-inclusive price quotes | Never overwrites active bills during price-reply mode; shows customer's original words above each matched Tally name |
| **5. "Nothing Is Lost" Catalogue & Web Research Agent** | Reorganized **~13,000 Tally names** (~9,600 sold) into **Product Families → Variants** using manufacturer PDFs + **Brave Search + LLM web reader** | **Move, never delete** (full pre/post set verification; **3,256 never-billed dead names** audited); shelf unknowns routed to mobile staff micro-questions (**22% of gaps solved**) |
| **6. Paisa-Exact Tally XML & Storefront** | Non-generative house-style product imagery pipeline at **~$0.007/image** (top 85 pages covering 70% of sales prioritized); read-only Gmail draft worker | Custom **TDL** reports export ≤500 KB queued jobs with isolated date variables; outbound XML matches Tally's **per-line half-up paisa GST rounding** & rebuilt **GSTR-1** |

---

## Selected Product & Architecture Case Studies

1. **[Smart Invoice Matching & Dual-Reader Bill Scanner](./case-studies/01-smart-invoice-matching.md)** — Dual-reader OCR (Vision layout reader + LlamaParse reconciled by arithmetic), open-weight **Gemma 4** matching (**291/317 real bills**), nightly Cloudflare cron self-learning loop, and ~13,000-item catalogue reconstruction.
2. **[Scan → Invoice → Stock & Edge Operations](./case-studies/02-scan-to-invoice-stock.md)** — Phone-only unit label capture, **~25 ms/line** Cloudflare D1 edge resolution, **Rao (Retrieval Augmented Outvoicing)**, and paisa-exact Tally XML voucher sync.
3. **[Open-Weight LLMs, AI Agent Architecture & Cost Engineering](./case-studies/03-open-weight-agents-and-cost-engineering.md)** — How we migrated from expensive commercial frontier APIs to **Gemma 4** in production, built a **Gemma 2B LoRA** ranking judge, designed 4 bounded production AI agents, and cut storefront image costs to **~$0.007/photo**.

---

## How I Build Production AI Systems (Working Principles)

- **Open-weight models for high-frequency production.** Prototype on frontier APIs if needed, then move volume workloads to open-weight models (**Gemma 4**) and compact LoRA judges (**Gemma 2B LoRA**) to eliminate rate limits and per-token cost spikes.
- **Checks beat model confidence.** Never trust a model's self-reported confidence score when you can check the math (e.g., extracted line items must sum to the printed taxable total).
- **Zero-token edge lookups first.** Known aliases and defining words resolve at the edge in **~25 ms** on Cloudflare Workers + D1; save model compute for genuine ambiguity.
- **Agents need reversible, audited tools.** Autonomous agents (like our nightly catalogue-repair routine) must write through state-logged endpoints where every change records its before/after state and can be undone.
- **Nothing from the system of record is ever lost.** Legacy ERP names are moved, never deleted, and every outbound voucher matches Tally's per-line paisa GST rounding.

---

## Tech Stack (BillMiner Production)

| Area | Tools |
| --- | --- |
| **Open-Weight & Cloud AI / OCR** | **Gemma 4** (production matching), **Gemma 2B LoRA** (fine-tuning judge), **Claude Agents** (scheduled audited cloud routines), **Google Cloud Vision**, **LlamaParse ("OCRia-1")**, **Brave Search API** |
| **Edge & Data Layer** | **Cloudflare Workers** (bill reader, seller detect, quoting, nightly learning cron), **Cloudflare D1 (SQLite)**, **Cloudflare KV**, **Cloud Firestore**, **Firebase Storage** |
| **Legacy ERP & Book Keeping** | **Tally Prime Legacy ERP** (`XML over HTTP :9000`, custom **TDL** reports ≤500 KB/job, bidirectional XML voucher sync agent) |
| **Web App & Agent Surfaces** | **Next.js / React / TypeScript**, **Tailwind CSS**, **shadcn/ui**, **Firebase App Hosting & Auth**, **Rao** in-screen invoicing agent, Gmail read-only draft agent, WhatsApp intake |

---

## Links & Contact

- **Interactive BillMiner Deck:** [billbuddy-deck.vercel.app](https://billbuddy-deck.vercel.app)
- **Engineering Portfolio:** [avinashbengaluru.github.io/portfolio/portfolio.html](https://avinashbengaluru.github.io/portfolio/portfolio.html)
- **GitHub:** [avinashbengaluru](https://github.com/avinashbengaluru)
- **LinkedIn:** [Avinash Immaneni](https://www.linkedin.com/in/avinash-immaneni-912763150/)
