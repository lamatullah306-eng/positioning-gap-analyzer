# Positioning Gap Analyzer

A browser-based tool that turns competitor messaging, pricing and a weighted scorecard into **metrics, white-space themes and ranked marketing moves**. No install, no backend, no API key: open `index.html`.

> Built by Amatullah Lokhandwala as a product-marketing portfolio project. Sample data uses fictional brands.

## The problem it solves
Early-stage and D2C teams often know *who* their competitors are but not *where the positioning gaps are*. This tool makes that comparison structured and repeatable: which claims are crowded, which are unowned, where the brand is under-proving, and whether price matches quality.

## What you get
| Output | What it tells you |
|---|---|
| Messaging map (heatmap) | Which of 10 themes each brand talks about, and who owns each theme |
| White-space detection | Themes no brand uses, which are candidate positioning angles |
| Distinctiveness score (0-100) | How different a brand's message mix is from the rest of the market |
| Proof density | Numbers, reviews, certifications per 100 words of copy |
| Tone and readability | Emotive vs rational share, Flesch reading ease, call-to-action count |
| Weighted scorecard | Brand score from user-defined factors and weights, plus gaps vs the best rival |
| Price index and value ratio | Price vs market average, and score per unit of price |
| Price vs quality map | Scatter of price against score, with market-average lines |
| Priority moves | Insights typed as threat / opportunity / strength / watch, ranked by impact, each with evidence and an action |
| Voice of customer | Paste public reviews per brand: sentiment, most-praised theme, top complaint topic, and a say-vs-hear table (Aligned / Untapped praise / Unproven claim / Contradicted) |
| Competitor weak spots | Complaint topics that dominate a rival's reviews but not yours, surfaced as attack angles |
| Editable keyword lists | Add, rename or remove message themes and complaint topics to fit any category |
| Summary and draft positioning angle | One-paragraph readout plus a fill-in-the-blank positioning statement built from an unclaimed or owned theme |
| Export / import | Markdown report, JSON data (re-importable), print to PDF; light and dark themes; works on phones |

## How to use
1. Open `index.html` (or host it on GitHub Pages).
2. Add your brand and 2-6 competitors. Paste each one's website or ad copy and a typical price.
3. Score each brand 1-5 on the factors that matter in your category and weight them.
4. Read the headline metrics and the top 3 priority moves, then export the report.

## Method (and limits)
- **Themes:** keyword stems per theme are matched against the pasted copy and normalised per 100 words. A brand "owns" a theme at ≥1.0 mentions and ≥1.5× the next brand. A theme is "white space" if no brand is above 0.8.
- **Distinctiveness:** 1 − cosine similarity between a brand's theme vector and the average of the others, scaled to 100.
- **Score:** Σ(score × weight) ÷ Σ(weight) ÷ 5 × 100.
- **Value ratio:** score ÷ (price index ÷ 100).
- **Review sentiment:** each review is scored (positive words − negative words) ÷ total, with simple negation handling ("not good" flips). A theme's customer share is the % of reviews that mention it. Complaint topics only count in reviews that are not clearly positive. Brands need 5+ reviews to feed insights.
- **Limits:** the analysis reflects what brands *say*, not what customers believe. Scores are your judgement and keyword matching misses context and sarcasm. Validate findings with reviews, ad libraries and customer interviews before acting.

## Case study (add yours here)
Run it on a real category and write up:
1. **Context:** category, who you compared and why
2. **Finding:** the 2-3 sharpest insights, with screenshots
3. **Decision:** what you would do, and how you'd measure it
4. **Result / next test:** the experiment you'd run next

## Roadmap ideas
- Fetch copy from URLs and use an LLM for theme extraction
- LLM-based theme and sentiment extraction for higher accuracy
- Trend tracking over time (re-run monthly and compare)

## Tech
Vanilla HTML, CSS and JavaScript in one file. Data is kept in your browser's localStorage only.
