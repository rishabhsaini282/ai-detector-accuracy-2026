# AI Content Detector Cheatsheet — 2026 Edition

Quick reference for understanding how AI detectors work, when they fail, and how to pick the right one.

---

## 1. The Two Core Signals Every Detector Measures

### Perplexity
Measures how **predictable** the text is to a language model.

- **Low perplexity** → text is predictable → likely AI (AI models choose the statistically most probable next word at each step)
- **High perplexity** → text surprises the model → more likely human
- **What raises perplexity artificially:** humanizer tools, QuillBot, paraphrasing apps

### Burstiness
Measures **variation in sentence length and structure**.

- **Low burstiness** → uniform sentence lengths → likely AI
- **High burstiness** → alternating long/short sentences → more likely human
- **What flattens burstiness:** grammar checkers (Grammarly), structured rubric-following writing, professional legal/scientific style

**Key insight:** Both signals are exploitable. A humanizer tool injects high perplexity and high burstiness on purpose. This is why detectors fail on humanized content.

---

## 2. What Breaks Detectors (Accuracy Killers)

| Factor | Impact |
|---|---|
| Light editing of AI text (synonyms, restructuring) | Detection drops 15–25 percentage points |
| Heavy editing of AI text (significant rewrite + original ideas added) | Detection drops 30–45 percentage points |
| 1 pass through a quality humanizer | Most detectors fail |
| 3 passes through a humanizer | No major detector consistently identifies AI origin (Axis Intelligence, March 2026) |
| Text under 300 words | Accuracy collapses for all tools; all vendors quietly acknowledge this |
| Non-native English writing (human) | False positive risk spikes dramatically |
| Structured/rubric-following writing style | False positive risk elevated |
| Technical, legal, or scientific prose | False positive risk elevated |
| Grammarly or QuillBot paraphrase on human text | Can cause a false positive |

---

## 3. Accuracy Reality Check

| Content Type | Best Detector Accuracy (Independent Testing) |
|---|---|
| Raw, unedited AI (GPT-4/5) | 85–99% |
| Lightly edited AI | 55–75% |
| Heavily edited AI | 50–65% |
| Humanized AI (3 passes) | <18% (most tools); ~97% (Pangram only) |
| Short text (<300 words) | Unreliable |

**No tool exceeded 80% overall accuracy in 2026 Scribbr or Supwriter independent benchmarks.**

Vendor claims vs. reality:

| Tool | Claims | Independent Finds |
|---|---|---|
| Winston AI | 99.98% | Not independently replicated |
| Originality.ai | 99% | 76–79% |
| GPTZero | 99% | 62% (PCWorld) |

---

## 4. False Positive Rates at a Glance

| Tool | FPR (Independent) | Safe for High-Stakes? |
|---|---|---|
| Pangram Labs | 0.01% (1 in 10,000) | Yes (only tool with external academic validation) |
| Turnitin | 1–7% (controlled); field rate higher | With caution; requires human review |
| Copyleaks | 1–5% | Yes, especially for multilingual contexts |
| GPTZero | 1–18% (varies by writer demographics) | As a first-pass signal only |
| Originality.ai | 14–28% (independent) | Not for education; publisher workflows only |
| ZeroGPT | 14–33% | No |
| Sapling | 28% | No |

**1% FPR on a class of 100 students = at least 1 wrongful accusation per assignment.**
**0.01% FPR on a class of 100 students = 1 wrongful accusation per 100 assignments.**

---

## 5. Tool Selection Decision Tree

```
START: Why do you need an AI detector?
│
├── To screen student work / academic integrity
│   │
│   ├── Primary concern = avoiding wrongful accusations
│   │   └── → Pangram Labs (0.01% FPR, independently verified)
│   │
│   ├── Multilingual or ESL classroom
│   │   └── → Copyleaks (1–5% FPR; strongest multilingual support)
│   │
│   ├── Already paying for Turnitin
│   │   └── → Use Turnitin AI Detection with caution + human review step
│   │
│   └── Individual teacher, free budget
│       └── → GPTZero (best free option; low FPR relative to free tools)
│
├── To verify freelancer / contractor output
│   └── → Originality.ai (aggressive detection; higher FPR acceptable when
│           no misconduct accusation is involved — just a content quality check)
│
├── Enterprise content team at scale
│   └── → Evaluate Originality.ai or Content at Scale API; test false positive
│           rate against YOUR content type before committing
│
└── Legal, compliance, or audit context
    └── → Pangram Labs + mandatory human review layer
        (Only tool with open-source, auditable methodology via EditLens)
```

---

## 6. Demographic Risk Checklist

Before deploying any AI detector in an accountability context, verify:

- [ ] Has the tool been tested on your specific student/writer population (ESL, STEM, humanities)?
- [ ] Stanford Liang 2026 follow-up: TOEFL essays by Chinese students had 61.3% FPR vs. 5.1% for US students on the same tools
- [ ] Do you have an appeal process for flagged individuals?
- [ ] Is the detector output being treated as a signal (triggers investigation) or a verdict?
- [ ] Have you reviewed the vendor's FERPA / GDPR data processing agreement?
- [ ] Is there a human review step required before any formal accusation?
- [ ] Are instructors trained to contextualize scores, not just read them?

**If any box is unchecked, you are not ready to use these tools in an accountability context.**

---

## 7. What Pangram Labs Does Differently (As of June 2026)

- **EditLens classifier** (ICLR 2026; open-sourced) — methodology is publicly auditable
- **Four-tier classification** (introduced in Pangram 3.0, December 2025): Fully AI / Mostly AI / Lightly AI-assisted / Human. Other tools return a single percentage; Pangram returns a category.
- **Segment-level analysis** — highlights which passages within a document are suspicious, not just the overall score
- **Independent academic validation** — University of Chicago + University of Maryland; no other major competitor has equivalent external peer review
- **Humanizer resistance** — ~97% accuracy against QuillBot-paraphrased content (GPTZero: ~18% on the same content)
- **Price** — $20/month (paid); 5 free checks/day (free tier)

---

## 8. Key Terms Glossary

| Term | Definition |
|---|---|
| Perplexity | How unpredictable the text is to a language model; AI text has characteristically low perplexity |
| Burstiness | Variation in sentence length and complexity; AI text tends toward low burstiness |
| False positive | Detector says AI; text was actually human-written. The error that causes wrongful accusations. |
| False negative | Detector says human; text was actually AI-generated. The error that misses cheating. |
| Humanizer | A tool (e.g., Undetectable AI, Phrasly, Walter Writes) that rewrites AI text to defeat detectors |
| EditLens | Pangram Labs' proprietary open-source classifier; presented at ICLR 2026 |
| RAID Benchmark | University of Pennsylvania benchmark measuring how detectors perform when false positive rates are constrained |
| FERPA | US federal law protecting student educational records; governs what vendors can do with submitted essays |
| EU AI Act Art. 50 | Requires high-risk AI systems to retain logs for 6+ months |

---

*Last updated: June 2026 | Source articles: [aicheckerdetector.com](https://aicheckerdetector.com/) | Corrections: open an issue or PR*
