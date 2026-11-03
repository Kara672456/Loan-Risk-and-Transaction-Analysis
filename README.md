# Loan Risk and Transaction Analysis of a Czech Bank

End-to-end SQL (MySQL) and Power BI analysis of 682 loans and 1,056,320 transactions from a Czech bank (1993 to 1998).


## Key findings
- Overall default rate: 11.1% (76 of 682 loans; default = loan status B or D).
- Accounts with the lowest balance before the loan defaulted at 19.3%, about 4x the highest-balance group (4.7%).
- Default rates range from 1.6% (North Bohemia) to 15.8% (West Bohemia).
- Defaulted loans were larger (B +54% vs A, D +45% vs C). Client age and district salary did not separate risk.
- Transaction volume grew 45% to 48% a year through 1997, then 13% in 1998, with seasonal spikes in January, June and December.
- Adding one index cut a query on the 1.06M-row transactions table from 4.3 s to 0.14 s (about 31x).

## Tools
MySQL 8.0, MySQL Workbench, Power BI Desktop. SQL techniques: joins, CTEs, NTILE, LAG, window AVG with PARTITION BY, RANK, COALESCE/NULLIF, indexing and EXPLAIN.

## Repository structure
- `sql/`: cleaning checks, loan risk queries, transaction analysis, optimization, Power BI views
- `dashboard/`: Power BI file and screenshots
- `docs/`: full project report (PDF) and ER diagram

## How to reproduce
1. Get the Financial (Berka) dataset from the CTU Prague Relational Dataset Repository (host relational.fel.cvut.cz, schema `financial`, public guest account) and load it into a local MySQL 8.0 database.
2. Run the scripts in `sql/` in order.
3. Open the Power BI file and point it at your local database or the exported CSVs.

## Limitations
Default includes status D (running, client in debt), which is closer to "at risk". 1998 loans were too new to judge. Region is where the account was opened. Several groups are small. Findings are associations, not causes. Data is from the 1990s, amounts in koruna.

## Author
Karan Singh | [LinkedIn](https://linkedin.com/in/karan-singh-data-analyst)
