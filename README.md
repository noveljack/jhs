# jhs (public runner)

GitHub Actions runner for the **private** `noveljack/screener` repo. This repo
contains **workflows only** — no business logic.

Each workflow:

1. Checks out the private `screener` repo using a Personal Access Token
   (`secrets.SCREENER_PAT`) against `vars.SCREENER_REPO` (e.g. `noveljack/screener`).
2. Sets up Python 3.11 (and Node 20 for the dashboard build).
3. Installs dependencies (`pip install -r requirements.txt`).
4. Runs the pipeline dispatch entrypoint: `python ci.py <mode> [shard]`.

Secrets and variables are injected into each job as two JSON blobs, `CTX`
(secrets) and `VARS` (variables), exactly as in `noveljack/jhms`.

See `.github/workflows/` for the individual pipelines and the repository
settings for the required secrets + variables (documented in the project setup
notes).
