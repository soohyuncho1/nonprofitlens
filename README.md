# NonprofitLens

**A transparent financial diagnostic instrument for small nonprofit organizations.**

NonprofitLens is a single-page web tool that takes a categorized financials CSV and returns a one-page diagnostic across six standard nonprofit financial-health ratios. Everything runs in the browser. No accounts, no data transmission, no model.

Built for DSCI 305 (Data Across Domains), Rice University, Spring 2026, in alignment with the NIST AI Risk Management Framework (2023).

---

## Live Tool

Open `index.html` in any modern browser, or visit the deployed version at `https://[your-username].github.io/nonprofitlens/`.

## What It Does

Compute and benchmark six nonprofit financial-health ratios:

| Ratio | What it measures | Healthy threshold |
|---|---|---|
| Program Expense Ratio | Share of spending on mission programs | ≥ 75% |
| Administrative Expense Ratio | Share of spending on management | ≤ 15% |
| Fundraising Cost Ratio | Cost per dollar of contributions raised | ≤ 10% |
| Operating Reserve | Months of expenses covered by unrestricted reserves | ≥ 6 months |
| Top Revenue Concentration | Share from largest revenue source | ≤ 40% |
| Current Ratio | Current assets ÷ current liabilities | ≥ 1.5x |

Each ratio is flagged green (Healthy), yellow (Watch), or red (Concern), with sector benchmarks shown alongside. A generated narrative summary identifies strengths, watch areas, and concerns.

## How to Use

1. Open the tool in your browser.
2. Click **Try with sample data** to see how a finished report looks, or
3. Click **Download CSV template** to get the expected format, fill it in with your organization's numbers, and upload it via **Upload financials CSV**.
4. Review the report. Print or save as PDF if needed.

## CSV Format

Two columns: `category` and `amount`. Recognized categories:

- `program_expense`
- `admin_expense`
- `fundraising_expense`
- `contributions`
- `grants`
- `earned_revenue`
- `other_revenue`
- `unrestricted_net_assets`
- `current_assets`
- `current_liabilities`

Amounts in dollars (no currency symbols required, but tolerated). See `sample_data.csv` for a working example.

## What It Doesn't Do

NonprofitLens is a screening tool, not an audit replacement. It does not:

- Score or rank organizations against each other
- Substitute for CPA review, board oversight, or formal audit
- Apply to organizations with complex restricted-asset structures (hospitals, universities, large foundations)
- Collect or transmit any data — files are read entirely client-side

If your organization shows one or more concern flags, consult a CPA or qualified nonprofit finance advisor before making consequential decisions.

## Methodology and Sources

Ratio definitions and benchmark thresholds are drawn from:

- Charity Navigator Encompass Rating financial methodology
- BBB Wise Giving Alliance Standards for Charity Accountability
- Nonprofit Finance Fund operating reserve guidance
- National Council of Nonprofits financial-health indicators

All thresholds and computation logic are visible in `index.html`. The narrative generator uses deterministic rule-based templates — there is no machine-learning model, no LLM, and no external API call.

## Ethical Framework

Designed in alignment with the **NIST AI Risk Management Framework** (NIST AI 100-1, 2023). See `PROJECT_BRIEF.md` for the full alignment writeup covering the framework's four core functions: Govern, Map, Measure, Manage.

## Repository Contents

```
nonprofitlens/
├── index.html         The complete application (HTML + CSS + JS in one file)
├── sample_data.csv    Sample categorized financials for testing
├── PROJECT_BRIEF.md   Audience, ethical alignment, and impact writeup
└── README.md          This file
```

## Local Development

No build step required. Clone the repo and open `index.html` in a browser:

```bash
git clone https://github.com/[your-username]/nonprofitlens.git
cd nonprofitlens
open index.html
```

External dependencies are loaded from CDNs at runtime: Google Fonts (Fraunces, Geist, JetBrains Mono) and PapaParse (CSV parser).

## Deployment to GitHub Pages

1. Push this repository to GitHub as a public repo.
2. Go to **Settings → Pages**.
3. Under **Source**, select branch `main` (or `master`) and folder `/ (root)`.
4. Click **Save**. Your site will be live at `https://[your-username].github.io/[repo-name]/` within a minute or two.

## License

MIT License. See source for full terms.

## Citation

If you use NonprofitLens in research or coursework, please cite:

> Soohyun [Last name]. 2026. "NonprofitLens: A Transparent Financial Diagnostic Instrument for Small Nonprofits." DSCI 305 Final Project, Rice University.

## References

- National Institute of Standards and Technology. 2023. *Artificial Intelligence Risk Management Framework (AI RMF 1.0)*. NIST AI 100-1. https://doi.org/10.6028/NIST.AI.100-1
- Obermeyer, Ziad, Brian Powers, Christine Vogeli, and Sendhil Mullainathan. 2019. "Dissecting Racial Bias in an Algorithm Used to Manage the Health of Populations." *Science* 366(6464): 447–453. https://doi.org/10.1126/science.aax2342
- Buolamwini, Joy, and Timnit Gebru. 2018. "Gender Shades: Intersectional Accuracy Disparities in Commercial Gender Classification." *Proceedings of Machine Learning Research* 81: 1–15.
- Association for Computing Machinery. 2018. *ACM Code of Ethics and Professional Conduct*. https://www.acm.org/code-of-ethics
