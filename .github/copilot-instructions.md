### Purpose

This file guides AI coding agents (Copilot-style) so they can be quickly productive in this repository: a short, notebook-based Microsoft Fabric / Spark data-engineering exercise.

### Big picture
- **Repo type:** single exercise repository with a Jupyter notebook (`prueba_tecnica_fabric_spark_sql.ipynb`) and example CSV datasets under `data/`.
- **Data flow:** CSV files in `data/` -> loaded by the notebook into Spark (temporary views/tables) -> SQL and DataFrame transforms produce Bronze/Silver-style outputs inside the notebook.
- **Primary goals:** implement SQL challenges with `spark.sql` and Spark DataFrame challenges (PySpark API); follow Medallion layering and produce clear notebook cell outputs.

### Key files / dirs (examples)
- `prueba_tecnica_fabric_spark_sql.ipynb`: main entry — contains TODO cells for answers.
- `data/products.csv`, `data/stores.csv`, `data/sales.csv`, `data/inventory.csv`: canonical input tables; columns documented in `README.md` (e.g., `product_id`, `sale_date`, `unit_price`).

### Project-specific conventions (do this here)
- Use `spark.sql(...)` for the SQL block challenges and the PySpark DataFrame API for Spark challenges — the notebook intentionally separates them.
- Keep column names exactly as in the CSVs (`product_id`, `store_id`, `sale_date`, `quantity`, `unit_price`, `stock`, etc.) to avoid unexpected join failures.
- Favor explicit aliases in SQL (e.g., `SELECT s.store_id AS sid, p.product_id AS pid`) and descriptive column names in DataFrames.
- Follow the Medallion idea: treat intermediate results as Bronze/Silver steps inside the notebook (clear comments and a small SQL/View name indicating layer).

### Developer workflows (how to run / test locally)
- Recommended: open the notebook in an environment with Spark available (Microsoft Fabric Notebooks, Databricks, or local PySpark).
- Minimal local quickstart (PowerShell):
  - `python -m venv .venv; .\.venv\Scripts\Activate.ps1; pip install pyspark notebook pandas`
  - `jupyter notebook` and open `prueba_tecnica_fabric_spark_sql.ipynb`
- When targeting Databricks/Fabric, load the notebook into the workspace and run cells — the README notes these supported runtimes.

### Patterns to follow when editing the notebook
- Do not change input CSV filenames or their schema unless explicitly needed; prefer deriving new columns instead.
- Write compact, testable SQL/DataFrame cells; after a transform, produce a small sample `show()` or `display()` output in the same cell to verify correctness.
- For SQL tasks: create temporary views with meaningful names (e.g., `CREATE OR REPLACE TEMP VIEW sales_raw AS SELECT * FROM ...`) before subsequent queries.

### Integration points & external dependencies
- Inputs are static CSVs under `data/` — there are no network calls or external DB connections in this repo.
- The README documents the required runtime: Python 3 and Spark (Fabric, Databricks, or local PySpark).

### What to commit / deliver
- Commit the completed notebook with answers in-place. Keep outputs visible so reviewers can follow results.
- Avoid large binary artifacts outside the notebook (no additional datasets expected).

### Examples (how to reference the repo content)
- SQL challenge example: run `spark.sql("SELECT product_id, SUM(quantity) AS total_qty FROM sales GROUP BY product_id")` in a notebook cell.
- DataFrame example: `sales_df.groupBy('product_id').agg(F.sum('quantity').alias('total_qty'))` then `sales_df.show(10)`.

### If uncertain
- Prefer minimal-invasive changes: add new cells, create temp views, and comment choices in the notebook markdown.
- Ask the repository owner when in doubt about altering dataset schema or adding persistent outputs.

---
If you want changes (tone, length, or more examples), tell me which sections to expand or clarify and I will update this file.
