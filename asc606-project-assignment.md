# ASC 606 Contract Obligation Extractor — One-Week Student Project

**Course:** Advanced Financial Reporting — AI Applications
**Due:** End of Week 7 (Friday, 11:59 PM)
**Format:** Individual submission

---

## Overview

You will build a working AI-powered tool that reads a contract and extracts its ASC 606 performance obligations into a clean, readable interface. This is a scoped component of *Provenance*, a professional-grade revenue recognition application — your output will be benchmarked directly against it.

The goal is not to write perfect code. The goal is to demonstrate that you understand *why* revenue is recognized the way it is, and to show that understanding through a tool that works.

---

## Learning Objectives

By completing this project you will be able to:

1. Map contract language to ASC 606 Step 2 (identify performance obligations) and Step 5 (recognize revenue)
2. Distinguish between the four recognition methods and articulate the reasoning behind each
3. Use a large language model (LLM) as an accounting reasoning engine, not just a text summarizer
4. Present structured financial data in a form a non-technical reviewer can read and verify

---

## What You Are Building

A single-user web or desktop application (any language or framework) that does the following:

**Input** — Accept a contract as either a PDF file upload or pasted text.

**Processing** — Send the contract to an LLM of your choice (GPT-4, Claude, Gemini, or equivalent). Prompt the LLM to extract each performance obligation.

**Output** — Display the results on screen in a structured, human-readable format. No raw JSON, no terminal output. A reviewer must be able to read it without technical knowledge.

For each performance obligation identified, your tool must surface:

| Field | Description |
|---|---|
| **Obligation Name** | Plain-language description of the distinct good or service |
| **Recognition Method** | One of the four methods listed below |
| **Reasoning** | One or two sentences explaining *why* that method applies |
| **Allocated Transaction Price** | Dollar amount or percentage allocated to this obligation |
| **Start Date / End Date** | Performance period, if determinable from the contract |

**Recognition methods in scope:**

- **Time-elapsed** — Straight-line over the service period; customer simultaneously receives and consumes the benefit
- **Cost-to-cost** — Input method; revenue recognized proportional to costs incurred relative to total estimated costs
- **Milestone** — Output method; revenue recognized when a defined contractual milestone is achieved
- **Point-in-time** — Control transfers at a discrete moment (delivery, acceptance, or title passage)

**Out of scope for this project:** Variable consideration, contract modifications, licenses, financing components, and principal/agent questions. Keep it simple.

---

## Sample Contracts

Use at least one real contract and one synthetic contract in your testing and submission.

**Real contracts (SEC EDGAR):**
- Salesforce 10-K: search EDGAR for `CRM` → any annual filing → *Exhibit 10* subscription agreements
- Oracle Cloud Services Agreement: search EDGAR for `ORCL` → master service agreement exhibits
- Any SaaS or professional services contract filed as a material exhibit (Form 8-K, Item 1.01)

**Synthetic contracts provided:**
- [synthetic-saas-contract.txt](https://github.com/bashiraziz/asc606-assignment/blob/main/synthetic-saas-contract.txt) — A 3-obligation SaaS deal: platform subscription, implementation services, and post-go-live support. Total contract value USD 264,000.
- [synthetic-construction-contract.txt](https://github.com/bashiraziz/asc606-assignment/blob/main/synthetic-construction-contract.txt) — A 2-obligation EPC contract: lump-sum construction works and a commissioning milestone. Total contract value USD 52,000,000.

Both files are plain text and can be uploaded directly into your tool or pasted as input. The answer key for each contract will be released on the course portal after the submission deadline.

---

## Deliverables

Submit a single ZIP file containing:

1. **Source code** — All files needed to run the application locally
2. **README** — Setup instructions (how to install dependencies, where to put an API key, how to run)
3. **`reasoning.md`** — A one-page narrative explaining: (a) how you structured your LLM prompt, (b) one obligation where the method choice was not obvious and how you resolved it, and (c) one limitation of your current approach
4. **Two screenshots** — One showing extraction from a real contract, one from a synthetic contract
5. **`contracts/`** folder — The actual contract files you used in your screenshots

Do not submit API keys. Use environment variables.

---

## Grading Rubric

| Criterion | Weight | 4 — Exceeds | 3 — Meets | 2 — Partial | 1 — Insufficient |
|---|---|---|---|---|---|
| **ASC 606 Reasoning** | 35% | Method choices are correct and reasoning is specific to the contract language, not generic | Most methods are correct; reasoning references the contract | Some methods correct; reasoning is generic or missing for some | Methods incorrect or reasoning absent |
| **Extraction Accuracy** | 25% | All obligations extracted; amounts and dates match the contract | Minor omissions; no material errors | Key obligations present but fields incomplete | Obligations missing or materially wrong |
| **UI Readability** | 20% | Output is clear, well-organized, and requires no explanation to read | Output is readable; minor layout issues | Output requires interpretation; some raw data visible | Raw JSON or terminal output presented as the UI |
| **Code Quality** | 10% | Code is organized, variables are named clearly, no dead code | Code works and is readable with minor issues | Code works but is difficult to follow | Code does not run or is substantially broken |
| **Documentation** | 10% | README enables a classmate to run the app in under five minutes; `reasoning.md` is substantive | README is complete; `reasoning.md` addresses all three prompts | README has gaps; `reasoning.md` is thin | README missing or `reasoning.md` absent |

**Benchmark:** Your extraction results for the synthetic contracts will be compared against the Provenance application output. Exact match is not required — *reasoned differences that you can defend in* `reasoning.md` *are acceptable.*

---

## Submission Checklist

Before submitting, confirm each item:

- [ ] Application runs from a clean install using only the README instructions
- [ ] No API keys are hardcoded in source files
- [ ] Both a real and a synthetic contract have been tested
- [ ] Every extracted obligation shows a method *and* a written reason
- [ ] UI displays results on screen — no JSON, no terminal
- [ ] `reasoning.md` addresses prompt design, one ambiguous obligation, and one limitation
- [ ] Two screenshots are included and match the contracts in the `contracts/` folder
- [ ] ZIP file is under 25 MB (do not include `node_modules`, `.venv`, or model weight files)

---

*Questions: post to the Week 7 discussion board. Do not email API key issues — that is a setup problem, not a grading problem.*
