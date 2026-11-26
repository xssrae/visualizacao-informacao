# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

University deliverable (Visualização da Informação, prof. Ismar Frango): three Plotly charts of different course units, all over one real dataset — Kaggle "E-commerce Orders and Customer Analytics" (1,200 orders, 2023-01 to 2025-06; `data/ecommerce/ecommerce_orders_dataset.csv`, a real Excel (xlsx) file despite the `.csv` extension). The whole deliverable is a single notebook, `projeto_visualizacao_ecommerce.ipynb`; there is no package, test suite or build. Notebook prose and chart labels are in Brazilian Portuguese — keep it that way. Deadline: 2026-12-01 23:59 (Brasília). Delivery = 1 code file + 1 PDF (dataset link, video link ≤5 min, the three charts), no zip.

`projeto_visualizacao_usd_brl.ipynb` + `data/USD_BRL_hist.csv` is the previous USD/BRL version, kept only as a fallback; it is not the deliverable.

## Commands

Use the local virtualenv (Windows):

```bash
.venv/Scripts/python.exe -m jupyter lab projeto_visualizacao_ecommerce.ipynb
.venv/Scripts/python.exe -m jupyter nbconvert --to notebook --execute projeto_visualizacao_ecommerce.ipynb --output projeto_visualizacao_ecommerce_executado.ipynb
```

Dependencies: `pandas`, `plotly`, `nbformat`, `openpyxl`, plus Jupyter (and `kaggle` CLI to re-download the data). `*_executado.ipynb` output is gitignored. The notebook reads the data by relative path, so run it from the repo root.

Kaggle access: the token lives in the user env var `KAGGLE_API_TOKEN` (never write it into files). `.mcp.json` configures the Kaggle MCP server using that variable. Re-download: `kaggle datasets download hammadansari7/e-commerce-orders-and-customer-analytics-dataset -p data/ecommerce --unzip`.

## Architecture

The notebook is a linear pipeline; the three plots form one narrative ("where does revenue come from, how does it evolve, how much of it materializes?"). "Receita" = sum of `TotalPrice` over all orders, including cancelled/returned; the dataset gives no currency.

1. **Load/prepare cell** — `pd.read_excel`, adds Portuguese label columns `status`, `pagamento`, `produto` mapped from `OrderStatus`, `PaymentMethod`, `Product`.
2. **Plot 1 – bar** (descriptive statistics): revenue per product, ticket médio and order count in hover.
3. **Plot 2 – line** (temporal): monthly revenue plus 3-month rolling mean, with a range slider.
4. **Plot 3 – sunburst** (hierarchical): `status > pagamento > produto`, sized by `TotalPrice`, colored by status.
5. **Conclusion cell** — hard-coded figures (revenue 1.26M; Cadeira 195.6k ≈ Impressora 195.6k lead, Celular last at 151.7k; peak 2024-06 = 68.1k, trough 2023-04 = 27.8k; delivered+shipped 38.6% of revenue, cancelled+returned 41.1%, pending 20.3%). The data is close to uniformly random, so differences are small; don't overstate them. If data or charts change, re-verify these numbers.

Broader context and decisions live outside the repo in the vault `C:\Projetos\segundo-cerebro\03 Areas\Faculdade\` (per README).
