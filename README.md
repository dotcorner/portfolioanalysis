# 🌐 Domain Ranker

A lightweight, **client-side** web app that matches your domain portfolio against retail sales data to surface your most commercially valuable domains — no server, no installs, no data ever leaves your machine.

---

## ✨ Features

- **Zero setup** — open `domain-ranker.html` directly in any browser
- **Drag & drop** CSV loading for both your domain portfolio and retail stats
- **Flexible scoring** — choose between exact-match only, all sales columns, or exact + start-match
- **Sortable results table** — click any column header to re-sort live
- **Export to Excel** — generates a two-sheet `.xlsx` workbook (full rankings + summary) named with today's date
- **100% private** — all processing happens in-browser; no data is uploaded anywhere

---

## 📁 Required Input Files

### 1. `RetailStats_YYYYMMDD.csv`
Sales data exported from your retail/registrar source. Expected columns:

| Column | Description |
|---|---|
| `keyword` | The keyword being tracked |
| `exact_sale_count` | Number of exact-match domain sales |
| `start_sale_count` | Sales where keyword appears at the start |
| `end_sale_count` | Sales where keyword appears at the end |
| `middle_sale_count` | Sales where keyword appears in the middle |

### 2. `afternic.csv`
Your domain portfolio exported from Afternic. Expected columns:

| Column | Description |
|---|---|
| `Domain` | Full domain name (e.g. `bestdeals.com`) |
| `TLD` | Top-level domain (e.g. `.com`) |
| `Buy Now Price` | Listed sale price |

---

## 🚀 Usage

1. Download or clone this repository
2. Open `domain-ranker.html` in your browser (Chrome, Firefox, Safari, or Edge)
3. Load your **RetailStats** CSV (drag & drop or click to browse)
4. Load your **Afternic** CSV (drag & drop or click to browse)
5. Adjust settings if needed (score method, minimum keyword length, preview rows)
6. Click **Run Analysis →**
7. Review the ranked results table and click **Export to Excel** to save

---

## ⚙️ Settings

| Setting | Options | Description |
|---|---|---|
| **Score Method** | Exact only / All columns / Exact + Start | Which sale count columns to sum for the score |
| **Min Keyword Length** | Number | Ignore keywords shorter than this (filters noise) |
| **Preview Rows** | Number | How many rows to display in the in-page table |

---

## 📊 How Scoring Works

Each domain name is split into its component words (hyphens, numbers, and separators are used as delimiters). Each word is looked up against the retail stats keyword list. The domain's **Total Sales Score** is the sum of sale counts for all matched keywords, using the selected scoring method.

**Example:**  
Domain: `bestdeals.com` → words: `best`, `deals`  
If `best` has 120 sales and `deals` has 340 sales → Score = **460**

---

## 📤 Export Format

The exported `.xlsx` file contains two sheets:

- **Rankings** — full domain list with scores, matched keywords, TLD, and price
- **Summary** — aggregate stats (total domains, matched domains, top scorers)

File is automatically named `domain-rankings-YYYY-MM-DD.xlsx`.

---

## 🛠️ Tech Stack

- Pure HTML / CSS / JavaScript — no frameworks
- [SheetJS (xlsx)](https://sheetjs.com/) — for Excel export (loaded via CDN)
- No build step required

---

## 📝 License

MIT — free to use, modify, and distribute.
