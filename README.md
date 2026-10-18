# Awesome-Data-Analysis-Manipulation

## Top Data Analysis & Manipulation Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on Data Preparation, Transformation Pipelines & In-Memory Analytics*  

**Last updated: October 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Data Analysis & Manipulation**. These tools enable analysts and engineers to clean, transform, join, and aggregate datasets—from visual ETL platforms that replace hand-coded scripts to in-process engines that process hundreds of millions of rows on a single machine without a cluster.



**Examples** include Alteryx, KNIME, Dataiku, Trifacta, Talend, RapidMiner, Databricks, AWS Glue DataBrew, Tableau Prep, and Paxata (the category leaders).



**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, visual data preparation, and open analytical engines—ideal for data analysts, analytics engineers, and organizations seeking transparent, vendor-independent data manipulation.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **Alteryx**  

  The enterprise standard for visual data preparation and analytics. Features **drag-and-drop workflow builder**, **hundreds of pre-built tools**, **spatial analytics**, and **predictive modeling**. **The benchmark that open-source alternatives like Loomflow and Amphi explicitly target** . Pricing starts around **$5,000/year per user**—a barrier that has driven significant migration to open-source tools.



- **KNIME**  

  Open-core analytics platform with visual workflows and a free desktop version. **The most accessible commercial-adjacent option**—the free tier is genuinely usable, with paid server and team features. Features **extensive node library**, **integration with Python/R/JavaScript**, and **database connectivity**.



- **Dataiku**  

  Enterprise AI and analytics platform with visual data preparation, machine learning, and deployment. Features **no-code, low-code, and full-code interfaces** in one platform.



- **Trifacta (Alteryx)**  

  Cloud data preparation platform acquired by Alteryx. Features **machine-learning-assisted wrangling**, **visual transformation suggestions**, and **integration with major cloud warehouses**.



- **Talend**  

  Enterprise data integration and transformation platform. Features **visual ETL/ELT**, **data quality**, and **API services**. **The enterprise standard for data integration pipelines**.



- **RapidMiner**  

  Data science platform with visual workflows for data preparation, modeling, and deployment.



- **Databricks**  

  Lakehouse platform built on Apache Spark. Features **notebooks**, **SQL analytics**, **Delta Lake**, and **MLflow**. **The enterprise standard for large-scale data engineering and ML**—but overkill for the "medium data" problems most teams actually have .



- **AWS Glue DataBrew**  

  Visual data preparation service on AWS. Features **250+ pre-built transformations**, **data profiling**, and **integration with Glue and S3**.



- **Tableau Prep**  

  Visual data preparation tool integrated with Tableau. Features **visual workflow builder**, **data profiling**, and **direct connection to Tableau Desktop**.



- **Paxata (Workday)**  

  Self-service data preparation platform acquired by Workday. Features **visual transformation**, **data quality**, and **collaboration**.



## Open-Source GitHub Projects



- **[Pandas](https://github.com/pandas-dev/pandas)**  

  **Flexible and powerful data analysis / manipulation library for Python** (BSD-3-Clause) — **the most widely used data manipulation library in the world**. **Key strengths**: **ubiquitous**—every data science tutorial starts with `import pandas as pd`; **rich ecosystem** (scikit-learn, matplotlib, seaborn all accept DataFrames); **full-featured** with merging, joining, grouping, pivoting, and time series . **The critical limitation**: **holds all data in RAM** and is **single-threaded**—a **2.3GB CSV ballooned to 7.2GB in memory** during a benchmark test, causing the OOM killer to terminate the process before completion . **The "Pandas cliff" occurs around tens of gigabytes**—beyond that, it doesn't just slow down, it dies . **Best for**: datasets under 10 million rows, exploration, and any project where the ecosystem's maturity outweighs performance .



- **[Polars](https://github.com/pola-rs/polars)**  

  **Performance-focused, multi-threaded DataFrame library written in Rust** (MIT) — **the modern Pandas replacement for large data**. **Key advantages**: **lazy evaluation** (builds query plans, applies predicate pushdown, eliminates unused columns before execution), **Apache Arrow columnar format**, **multi-threaded by default**, and **streaming execution** for out-of-core processing . **Benchmark**: the same 2.3GB CSV that crashed Pandas completed in **8.7 seconds with 1.8GB peak memory**—**60% less memory and zero crashes** . **On the 1 Billion Row Challenge**, Polars finished in **5.04 seconds** vs. Pandas' **4 minutes 28 seconds** . **Requires strict schema definitions** but rewards with predictable performance . **Best for**: production ETL, datasets that don't fit in RAM, and any Python data workload where performance matters .



- **[DuckDB](https://github.com/duckdb/duckdb)**  

  **Feature-rich in-process SQL OLAP database** (MIT) — **"SQLite for analytics"** . **Key advantages**: **no external dependencies**, **vectorized SQL queries**, **parallel processing**, **spills to disk automatically when memory pressure rises**, and **queries Parquet/CSV files directly without loading them first** . **Benchmark**: the 2.3GB CSV query completed in **12 milliseconds with 0.4GB peak memory**—**18x less memory than Pandas** . **On the 1 Billion Row Challenge**, DuckDB finished in **5.19 seconds** vs. Pandas' **4 minutes 28 seconds** . **Unlike SQLite (OLTP-optimized), DuckDB is OLAP-optimized**—built for aggregate calculations across large numbers of rows . **Best for**: analytical scans, joins, and aggregations on local files; SQL-heavy workflows; and any "medium data" problem where a cluster is overkill .



- **[Loomflow](https://github.com/cardchase/loomflow)**  

  **Self-hosted, lightweight, visual ETL platform inspired by Alteryx** (open-source) — **the open-source Alteryx alternative** . **Features**: **Alteryx-inspired configuration panels** with spreadsheet-like tabular grids for managing hundreds of columns, **tool containers** for grouping and bypassing logic, **multi-rule sorting and summarization** powered by a **native Polars backend**, **semantic type profiling** (detects `currency_usd`, `percentage`, `email` and propagates metadata through the DAG), **agent-ready architecture** (export workflows to YAML for AI orchestration), **Gemini AI node** for extracting data from text/images/video/audio, **built-in Python IDE** with column-aware autocompletion, **multi-tabbed workspaces** for parallel DAGs, **flexible I/O** (CSV, Excel, Word, PDF, SQLite, Access), and **global cloud integrations** (Google Cloud, OAuth) . **The most feature-complete open-source visual ETL platform available**.



- **[Amphi](https://github.com/amphi-ai/amphi)**  

  **Free and source-available visual data transformation tool based on Python** (open-source) — **the low-code tool that generates native Python code** . **Key differentiator**: **generates pandas and DuckDB code that you can export and run anywhere**—unlike Alteryx or KNIME, Amphi doesn't lock workflows into a proprietary format. **Supports any Python library** and **custom code integration directly into the pipeline**. **Available as standalone app or JupyterLab extension** . **Best for**: teams wanting visual building without sacrificing code portability.



- **[OpenRefine](https://github.com/OpenRefine/OpenRefine)**  

  **Free and open-source data cleaning tool** (BSD-3-Clause) — **the original data wrangling tool** . **Runs as a local web application**—data never leaves your machine. **Supports CSV, Excel, JSON, and more**. Features **GREL (General Refine Expression Language)** for programmatic transformations, **faceted browsing** for exploring data, **clustering algorithms** for finding near-duplicate values, and **reconciliation** against external knowledge bases . **Best for**: cleaning messy spreadsheets and exploring unfamiliar datasets.



- **[Ibis](https://github.com/ibis-project/ibis)**  

  **Python data-frame interface that works on top of any backend** (Apache-2.0) — **write once, run anywhere** . **Supports BigQuery, MySQL, PostgreSQL, pandas, DuckDB, ClickHouse, PySpark, Snowflake, SQLite, and more**. **Can use both its own object-oriented interface (similar to pandas) and standard SQL interchangeably** . **Best for**: teams that want a consistent Python API across multiple data backends without rewriting pipelines.



- **[dbt (data build tool)](https://github.com/dbt-labs/dbt-core)**  

  **Command-line tool for the transform step of ELT** (Apache-2.0) — **the analytics engineering standard** . **Sits on top of a data warehouse**, managing data modeling, testing, and documentation in a predefined workflow. **Data manipulation via SQL with Jinja templating** . **The de facto standard for warehouse-native transformations**.



- **[tidysheet](https://pypi.org/project/tidysheet/)**  

  **Local-first data profiling and cleaning with reproducible, exportable pipelines** (open-source) — **the reproducible cleaning tool** . **Point it at a messy CSV/Excel/Parquet/JSON file**: it profiles the data, proposes a cleaning pipeline you review as plain YAML, runs it on **DuckDB**, and exports the whole thing as **standalone pandas, Polars, or SQL code you own**. **Data never leaves your machine**. **`infer` command reverse-engineers a pipeline from a hand-edited Excel file**—clean however you like, then let tidysheet reproduce the steps . **Best for**: teams wanting auditable, reproducible cleaning pipelines.



- **[Hermes](https://pypi.org/project/hermes-plt/)**  

  **Pipeline layer around existing data tools** (open-source) — **the provenance-first data framework** . **Designed to work with Pandas, Polars, PyArrow, DuckDB, NumPy, Parquet, SQL databases, and ML frameworks**—not replace them. **Features**: **entity resolution** (connect `Apple Inc.`, `Apple Computer Inc.`, and `AAPL` to a canonical entity), **dataset versioning** (`snapshot()`, `version()`, `diff()`), **provenance tracking** (every dataset answers "where did this come from?"), and **lineage recording** . **Local-first**—`pip install hermes-plt` and start working immediately, no cloud account required . **Best for**: teams needing auditable, reproducible data pipelines with lineage.



### Additional Strong Open-Source Options



- **[Modin](https://github.com/modin-project/modin)** — Drop-in Pandas replacement that scales to multiple cores and clusters (Apache-2.0) . **Change the import statement, keep your code**  . **Best for**: existing Pandas codebases needing speed without rewrites.

- **[Fugue](https://github.com/fugue-project/fugue)** — Unified interface for distributed computing (Apache-2.0) . **Execute Python, pandas, and SQL code on Spark and Dask with minimal rewrites**—switch engines by changing one variable  . **Best for**: teams wanting portability across compute engines.

- **[Daft](https://github.com/Eventual-Inc/Daft)** — Distributed DataFrame for Python and Rust (Apache-2.0) . **Polars-like expressiveness with Spark-like distribution**  .

- **[Great Expectations](https://github.com/great-expectations/great_expectations)** — Data quality and testing framework (Apache-2.0) . **The standard for pipeline validation**  .

- **[Datasette](https://github.com/simonw/datasette)** — Low-code tool for exploring and publishing data (Apache-2.0) . **The fastest way to explore a SQLite database**  .

- Community **n8n** workflows for data pipeline orchestration and transformation alerting.



**Frameworks for building custom systems**: Combine **Polars** for high-performance DataFrame operations with **DuckDB** for SQL-heavy analytics, **Loomflow** or **Amphi** for visual pipeline building, **dbt** for warehouse transformations, and **Hermes** for provenance and lineage—creating a comprehensive data analysis and manipulation stack that handles everything from exploration to production.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Data analysis tools handling enterprise data must comply with data protection regulations (GDPR, CCPA, etc.) and implement appropriate access controls.

- **The "Big Data" myth drives unnecessary complexity.** Telemetry from Amazon Redshift's fleet shows **94.7% of tables are under 100 GB** and **86.9% of queries scan 80 GB or less** . **Most organizations face "Medium Data" problems**—tens to hundreds of gigabytes—that **single-machine tools like Polars and DuckDB handle easily** without a distributed cluster .

- **Pandas has a hard ceiling.** It **holds all data in RAM** and is **single-threaded**—a 2.3GB CSV balloons to 7.2GB in memory and crashes . **On the 1 Billion Row Challenge**, Pandas took **4 minutes 28 seconds** vs. Polars' **5.04 seconds** and DuckDB's **5.19 seconds** . **Migrate when you hit the cliff**—don't wait for an OOM kill in production.

- **Polars vs. DuckDB: the choice depends on your interface preference.** **Polars** for a **Pythonic DataFrame API** that feels like a faster Pandas . **DuckDB** for **SQL-native workflows** and querying files directly without loading them first . **Both spill to disk automatically and parallelize across cores**—the difference is ergonomic, not architectural .

- **Visual ETL is no longer a commercial-only category.** **Loomflow** provides **Alteryx-inspired configuration panels** with a **Polars backend** and **agent-ready YAML export** . **Amphi** generates **native pandas and DuckDB code you can export and run anywhere** . **The visual builder no longer means vendor lock-in.**

- **Self-hosted open-source solutions require proper memory management, schema validation, and pipeline testing.** **Use engines that spill automatically**—hand-rolling chunked joins in Pandas is **5-50x slower and far more fragile** than declarative SQL or Polars expressions . **Reach for hand-rolling only when no engine fits the workload** .



---



**Made for data analysts, analytics engineers, and organizations building transparent data manipulation solutions.**  

Let's make Data Analysis & Manipulation more open, data-driven, and performant.
