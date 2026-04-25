
## 1. Project Overview

NonprofitLens is a browser-based diagnostic instrument that evaluates the financial health of small nonprofit organizations against six standard sector ratios — program expense ratio, administrative expense ratio, fundraising cost ratio, operating reserve months, top-revenue concentration, and current ratio. A user uploads a categorized financials CSV; the tool returns a one-page report with traffic-light flags, sector-benchmark comparisons, and a generated narrative summary suitable for board or executive review. All computation runs locally in the browser. No data is transmitted, retained, or stored.

**Live tool:** [link to GitHub Pages deployment]
**Source:** [link to GitHub repository]

## 2. Intended Audience

The primary audience is **executive directors, board treasurers, and finance committee chairs of small nonprofits — organizations with annual budgets typically below five million dollars that lack dedicated finance staff or external audit relationships.** This is the segment of the sector most likely to be operating without regular financial-health benchmarking; large nonprofits already retain CPAs and rating-agency reviews, while these smaller organizations frequently rely on volunteer treasurers and part-time bookkeepers. The tool is also usable by capacity-building consultants, university-affiliated nonprofit clinics, and student consulting groups (such as 180 Degrees Consulting chapters working with community partners) who need a quick first-pass diagnostic before deeper engagement. Secondary audiences include funders and individual donors evaluating organizations whose audited statements are not yet public.

## 3. Alignment with the NIST AI Risk Management Framework

The project is designed in alignment with the **NIST AI Risk Management Framework (NIST AI 100-1, 2023)**. Although NonprofitLens uses transparent rule-based logic rather than a machine-learning model, the framework's emphasis on trustworthy automated decision support — and its four core functions of Govern, Map, Measure, and Manage — directly shaped the design.

**Govern.** The tool is open-source under MIT license, with every ratio definition, threshold, and benchmark visible in fewer than 1,000 lines of source. There is no model, no training data, no proprietary scoring. This responds to a recurring concern in algorithmic-fairness literature, including Obermeyer et al. (2019), that opaque scoring systems in consequential domains (healthcare allocation in their case, organizational viability in this one) can encode biases or errors that institutions cannot audit. Governance here is not a policy document but a code repository.

**Map.** Intended use, intended user, and out-of-scope cases are documented in the README and in the tool's methodology panel. NonprofitLens is explicitly framed as a **screening instrument**, not a substitute for professional audit, board review, or CPA consultation. It is not designed for hospitals, universities, large grantmaking foundations, or organizations with complex restricted-asset structures, and these limits are stated in-product.

**Measure.** The six ratios match definitions used by Charity Navigator, the BBB Wise Giving Alliance, the Nonprofit Finance Fund, and the National Council of Nonprofits. Benchmark thresholds are cited to source, and the tool displays each ratio against its band rather than reducing health to a single composite score. Composite scoring is deliberately rejected: hiding the underlying signal behind a single number is precisely the failure mode Obermeyer documented, and the alignment-evaluation literature (e.g., Buolamwini and Gebru's *Gender Shades*) reinforces that aggregate metrics can mask subgroup failures.

**Manage.** Risk is managed through visibility rather than abstraction. The narrative generator uses deterministic templates over computed flags — every sentence in the output corresponds to a specific rule the user can inspect. There is no LLM in the pipeline, eliminating hallucination risk entirely. The tool warns explicitly, in-product, that organizations with one or more concern flags should consult a CPA before acting.

The project also reflects the **ACM Code of Ethics** (2018) section 1.4 (avoid harm) and section 2.5 (give thorough evaluations) by refusing to generate confident-sounding recommendations from incomplete data: a missing category produces a flagged warning rather than a silent default-to-zero.

## 4. Potential Impact

The American nonprofit sector includes roughly 1.5 million tax-exempt organizations, of which the great majority are small. Charity Navigator and similar platforms cover only a fraction. The remainder — community foodbanks, after-school programs, neighborhood mutual-aid groups, immigrant service organizations — operate without routine access to the diagnostic tools that larger institutions take for granted. A volunteer treasurer reviewing year-end statements often has no efficient way to ask whether their organization's overhead ratio, reserve position, or revenue concentration is normal for the sector.

NonprofitLens is intentionally narrow in scope but addresses a real informational gap. By taking inputs the organization already has (categorized line items from QuickBooks or a spreadsheet) and returning a sector-benchmarked diagnostic in under thirty seconds, it lowers the cost of basic financial self-assessment to effectively zero. The tool is designed to be useful in three concrete settings: as a board-meeting handout that surfaces issues a treasurer might otherwise have to discover through trial and error; as a starting point for a consulting engagement (the kind of work 180DC chapters and university-affiliated clinics do) so that scarce volunteer hours go to interpretation rather than calculation; and as a literacy tool for trustees who want to understand what the standard nonprofit financial questions actually are.

The impact is bounded by what the tool deliberately does not do. NonprofitLens does not score, rank, or recommend. It does not collect data. It does not replace audit. The intent is to make a small slice of expert knowledge — the same six ratios that staff at Charity Navigator and the Nonprofit Finance Fund use every day — auditable, explainable, and free for the organizations that most need them.

## 5. Compliance and Safety

The tool processes no personal data, transmits no information off-device, and stores nothing. It is licensed MIT, hosted on public GitHub Pages, and designed in compliance with Rice University's academic integrity standards. All external sources (benchmarks, framework references, academic citations) are credited in the methodology panel and the repository README.

---
**Primary framework:** NIST AI Risk Management Framework (2023).
**Supporting references:** ACM Code of Ethics (2018); Obermeyer et al. (2019); Buolamwini & Gebru (2018).
