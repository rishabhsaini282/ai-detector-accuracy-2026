# Data: AI Detector Accuracy Benchmarks

## File: `detector-accuracy-benchmarks.csv`

This file contains structured accuracy, false-positive, and pricing data for 8 major AI content detectors as of mid-2026. Each row represents one tool.

---

## Column Definitions

| Column | What it contains |
|---|---|
| `tool` | Product name |
| `vendor_accuracy_claim_pct` | The accuracy figure the vendor markets on their homepage or in press materials |
| `independent_accuracy_raw_ai_pct` | Accuracy on unedited AI output from major models (GPT-4/5, Claude, Gemini), from independent testing |
| `independent_accuracy_edited_ai_pct` | Accuracy on AI text that has been lightly edited (synonym swaps, minor restructuring) — how most people actually use AI |
| `independent_accuracy_humanized_ai_pct` | Accuracy on AI text after passing through a humanizer tool (e.g., QuillBot, Undetectable AI, Phrasly) |
| `false_positive_rate_vendor_pct` | The false positive rate the vendor claims — how often the tool incorrectly flags human-written text as AI |
| `false_positive_rate_independent_pct` | The false positive rate found in independent benchmarks; often substantially higher than vendor claim |
| `false_positive_rate_esl_writers_note` | Notes on false positive rates specifically for non-native English speakers (a critical fairness dimension) |
| `pricing_free_tier` | Free tier availability and limits |
| `pricing_paid_tier` | Approximate paid plan pricing as of mid-2026 (verify with vendors — pricing changes frequently) |
| `recommended_primary_use_case` | Context where this tool is most defensible |
| `avoid_for` | Contexts where this tool's risk profile makes it inappropriate |
| `humanizer_resistance` | How well the tool maintains accuracy against content processed through humanizer tools |
| `independent_study_sources` | Key sources for the independent figures cited |
| `notes` | Additional context — quirks, recent changes, known limitations |

---

## Methodology Notes

**"Independent" means:** Studies not commissioned by or controlled by the tool vendor. Vendor-commissioned meta-analyses (like Originality.ai's 14-study aggregation) are not treated as fully independent, though they are noted because even vendor-favorable meta-analyses tend to show results far below homepage marketing claims.

**Why vendor claims differ from independent results:** Vendors measure accuracy on their own test sets, using the kinds of AI text and human text they selected. These sets are not representative of real-world usage. Independent benchmarks use varied content types, recent model outputs, and — critically — include non-native English writers, neurodivergent writers, and technical/STEM writing, all of which elevate false positive rates significantly.

**What "humanized" means in this data:** AI text that has been processed through a dedicated bypass tool (e.g., QuillBot's paraphraser, Undetectable AI, Walter Writes, Phrasly) at least once — or three passes in the Axis Intelligence March 2026 testing that found no tool consistently identified humanized content.

**Pricing caveat:** Subscription pricing in this space changes frequently. Verify current pricing on each vendor's site. Credit-based pricing (Originality.ai) can become significantly more expensive than flat-rate plans at high volume.

---

## Primary Sources for This Data

- 2026 Stanford Human-Centered AI report on AI detection performance across major models
- University of Chicago study on detector behavior on short-form content
- University of Maryland independent verification of Pangram Labs accuracy claims
- RAID Benchmark — University of Pennsylvania
- February 2026 paper in the International Journal for Educational Integrity (Springer): evaluation of Originality.ai and Turnitin across 192 texts
- Weber-Wulff et al. study (widely cited independent AI detection research)
- Scribbr 2026 benchmark (Originality.ai overall accuracy: 76%)
- Supwriter 2026 benchmark (Sapling FPR: 28%; ZeroGPT FPR: 14–33%; editing impact on detection rates)
- Humanize AI Pro independent review (early 2026)
- Fritz.ai independent benchmark (early 2026)
- Axis Intelligence, March 2026 (humanizer arms race testing)
- PCWorld independent GPTZero test (accuracy: 62%)
- Washington Post study (Turnitin false positive rate on specific content types)
- Common Sense Media reporting on demographic disparities in AI plagiarism accusations
- Stanford Liang study 2026 follow-up (TOEFL essays: 61.3% FPR for Chinese students vs. 5.1% for US students)
- Hands-on testing and editorial analysis documented at [aicheckerdetector.com](https://aicheckerdetector.com/)

---

## Contributing Corrections

If you have more recent benchmark data, pricing updates, or coverage of tools not listed here, open a PR or issue. Include a link to the source study or benchmark.
