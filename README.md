# Affinity Answers: Technical Assignment

Three short tasks completed as part of a job application to Affinity Answers.

| Task | File | What it does |
|---|---|---|
| 1. Address validation | `task1.ipynb` | Extracts the 6-digit PIN code from an Indian address and checks it against India Post's public PIN-code API (`api.postalpincode.in`), comparing the returned post-office details with the address |
| 2. SQL on a public database | `Task2.txt` | Queries on the public Rfam MySQL database: finding a species' taxonomy ID, identifying the join keys between `taxonomy`, `rfamseq` and `family`, the longest rice (*Oryza*) sequence, and paginating families with long maximum sequence lengths |
| 3. Shell data extraction | `Task3.txt` | A bash script that downloads AMFI's daily mutual-fund NAV file and extracts scheme name and asset value into a TSV, with a note on TSV vs JSON |

## Notes

- **Task 1:** the notebook calls the API with certificate verification turned off, which produces an `InsecureRequestWarning`. In
  production, keep verification on.
- **Task 3:** the script splits fields with `tr` but then indexes `$fields` as if it were a bash array, so it won't extract the right
  columns as written. `awk -F';' '{print $4 "\t" $5}' NAVAll.txt` does the extraction in one line.
