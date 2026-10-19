# Fabric Beacon

**Power BI & Fabric discovery, search, lineage, governance, and Jira-scoped analysis.**

| Resource | Link |
|----------|------|
| **Team guide (browser)** | https://lynarasimha.github.io/Fabric_Beacon/DOCUMENTATION.html (enable Pages: branch **gh-pages**, root) |
| **Product brief** | [PRODUCT-BRIEF.md](./PRODUCT-BRIEF.md) |
| **Leadership doc** | [docs/Fabric-Beacon-Project-Insights.docx](./docs/Fabric-Beacon-Project-Insights.docx) |

## What this repo is

Public **team-facing** home for Fabric Beacon (HTML guide, brief, docs). The **full application** (FastAPI + React, MCP, labels) lives in the engineering monorepo:

`C:\Users\LYal01\ZABC\projects\incubating\pbi-discovery-platform`

(A copy may also exist under `Downloads\pbi-discovery-platform`.)

## Run the app (developers)

```powershell
cd projects\incubating\pbi-discovery-platform
.\start-dev.ps1
```

Open **http://localhost:5173** → **About** → **Setup** → Discovery / Search / Lineage / Governance.

## Docs in this repo

| Path | Purpose |
|------|---------|
| `DOCUMENTATION.html` | Team guide (GitHub Pages) |
| `docs/` | Insights docx, sign-off, naming |
| `scripts/` | Regenerate leadership docx |

Regenerate insights docx:

```powershell
python scripts/generate-fabric-beacon-insights-docx.py
```

## Sibling products

Semantic Scout · Semantic Forge · KPI Forge · Paginate Forge
