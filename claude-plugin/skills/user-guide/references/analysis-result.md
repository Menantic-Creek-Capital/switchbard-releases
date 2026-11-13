# Final worksheet example

[Open the rendered example](examples/analysis-result.html).
This source produces the fixed monthly table in the Analysis case study.
The HTML, styles and query below come from the same file embedded in the guide.

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="color-scheme" content="light dark">
  <meta http-equiv="Content-Security-Policy" content="default-src 'none'; style-src 'unsafe-inline'; base-uri 'none'; form-action 'none'">
  <title>Monthly sales: October and November 2026</title>
  <!--
    Formatted result illustration for the verified Analysis case study.
    This is a presentation of the verified data, not a screenshot of app UI.
    The live run kept the saved name Verification_units_by_region.
    The two raw result rows are 2026-10-01 / 25 and 2026-11-01 / 45.
    Month labels are formatted for readers; values are unchanged.

    Colours come from web/desktop/src/tokens.css. System typography and
    numeric alignment follow the native table; spacing is sized for this
    standalone guide example. No scripts or external resources are loaded.

    Query executed in the verified session:
    SELECT month, SUM(units) AS total_units
    FROM sales
    GROUP BY month
    ORDER BY month ASC;
  -->
  <style>
    :root {
      color-scheme: light dark;
      --bg: #ffffff;
      --fg: #1b1c1e;
      --line: #dcdcd8;
      --muted: #4d5157;
    }
    @media (prefers-color-scheme: dark) {
      :root {
        --bg: #1c2024;
        --fg: #e8eaec;
        --line: #2d3237;
        --muted: #b0b6bd;
      }
    }
    * { box-sizing: border-box; }
    body {
      margin: 0;
      background: var(--bg);
      color: var(--fg);
      font: 16px/1.5 system-ui, sans-serif;
    }
    main {
      max-width: 640px;
      margin: 0 auto;
      padding: 28px 32px 24px;
    }
    header {
      display: flex;
      align-items: baseline;
      justify-content: space-between;
      gap: 16px;
      margin-bottom: 24px;
    }
    h1 {
      margin: 0;
      font-size: 24px;
      line-height: 1.25;
      font-weight: 650;
      letter-spacing: -0.035em;
    }
    .year { color: var(--muted); font-size: 14px; }
    table {
      width: 100%;
      border-collapse: collapse;
      font-variant-numeric: tabular-nums;
    }
    thead th {
      padding: 0 0 12px;
      color: var(--muted);
      font-size: 12px;
      font-weight: 600;
      text-align: left;
    }
    tbody tr { border-top: 1px solid var(--line); }
    tbody th {
      padding: 16px 0;
      font-weight: 500;
      text-align: left;
    }
    td {
      padding: 12px 0 12px 24px;
      font-size: 28px;
      line-height: 1.4;
      font-weight: 600;
      letter-spacing: -0.035em;
    }
    .numeric { text-align: right; }
    footer {
      margin-top: 16px;
      padding-top: 12px;
      border-top: 1px solid var(--line);
      color: var(--muted);
      text-align: right;
      font-size: 12px;
    }
    .visually-hidden {
      position: absolute;
      width: 1px;
      height: 1px;
      padding: 0;
      overflow: hidden;
      clip-path: inset(50%);
      white-space: nowrap;
    }
    @media (max-width: 400px) {
      main { padding: 24px 20px 20px; }
      h1 { font-size: 22px; }
    }
  </style>
</head>
<body>
  <main aria-labelledby="table-title">
    <header>
      <h1 id="table-title">Monthly sales</h1>
      <span class="year">2026</span>
    </header>
    <table>
      <caption class="visually-hidden">Total sales units by month in 2026</caption>
      <thead>
        <tr><th scope="col">Month</th><th scope="col" class="numeric">Units sold</th></tr>
      </thead>
      <tbody>
        <tr><th scope="row"><time datetime="2026-10">October</time></th><td class="numeric">25</td></tr>
        <tr><th scope="row"><time datetime="2026-11">November</time></th><td class="numeric">45</td></tr>
      </tbody>
    </table>
    <footer>Ready for review</footer>
  </main>
</body>
</html>

```
