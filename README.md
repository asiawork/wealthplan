# Wealth Plan Portfolio

Slide-style performance summary for the strategic portfolio plans (1–5) and a DIY mix.

## Use
1. Open the page and upload `Model Performance_data.csv` (columns: `Model Name`, `date`, `% Difference in port_value`).
2. The browser remembers the file; upload a newer CSV any time with **อัปเดตไฟล์**.
3. Pick a plan or DIY, adjust weights, and choose the period.

The CSV stays in your browser. It is not uploaded to this repository.

## Files
- `index.html` — the page (calculation engine included)
- `backfill.js` — back-tested history for **FIXEDTDP before 2022-05-03** and **TCT before 2022-09-01** only. Everything after those dates comes from the CSV.
- `fonts/` (optional) — add `BLS-Bold.ttf`, `BLS-Regular.ttf`, `BLS_Text-Regular.ttf`, `BLS_Text-Bold.ttf` to use the company fonts; otherwise Kanit is used.

## Method
- Portfolio: daily-rebalanced fixed weights.
- 1Y rolling return: NAV(d) / NAV(same date 12 months earlier, or nearest earlier) − 1.
- Drawdown / recovery cycles: every day is a possible entry. An entry counts as a cycle when the portfolio falls by at least the threshold within 84 trading days. Drawdown = trough vs entry; recovery = calendar days until back to the entry value. Median uses recovered cycles; Longest is the longest cycle.
- Threshold = Σ weight × model threshold (FIXEDSP 0.05%, FIXEDTDP/FIXEDDP 0.5%, CAA 2%, MAA/AAA/DAA/TCT 4%).
