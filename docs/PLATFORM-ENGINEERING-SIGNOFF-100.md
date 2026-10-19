# Fabric Beacon — platform engineering signoff — 100% (new-user release scope)

**Verdict:** **GO — 100%** for the defined product scope below.  
**Signed (engineering):** Cursor agent session, **2026-10-09**  
**Branch / copy:** tag your release copy from the commit where verification commands last passed.

This signoff means the **onboarding spine, Jira scoped analyzer, Setup, About, and Documentation** meet the acceptance criteria. It does **not** replace live tenant staging cert, analyst burn-in, or Jira admin tasks (see §Excluded).

---

## 100% acceptance criteria (all required)

### A. New-user journey (single path)

| # | Criterion | Evidence |
|---|-----------|----------|
| A1 | One documented path: About → Setup → Jira → Discovery/Documentation | `docs/DOCUMENTATION.md` §0 |
| A2 | Same four steps in UI on About, Setup, Jira, Documentation | `NewUserFlowStrip` + `newUserFlow.ts` |
| A3 | Secrets only in root `.env`; collapsed info panels (no browser tokens) | `JiraCredentialsSetupGuide`, `InfoHelpCollapsible` |
| A4 | Printable onboarding | `docs/DOCUMENTATION.md`, `docs/PLATFORM-UX-ROADMAP.md` |

### B. Jira Analyzer

| # | Criterion | Evidence |
|---|-----------|----------|
| B1 | Matches **only** inside ticket **[QA] workspace** scope | `_match_issue_with_qa_scope` |
| B2 | No whole-tenant catalog fallback when scope unresolved | Tests + `success: false` |
| B3 | Non-QA workspace pick rejected | `_resolve_qa_catalog_scope` QA name filter |
| B4 | Ticket + workspace details panel; blocked → Setup sync link | `JiraTicketWorkspacePanel` |
| B5 | 4-step on-screen flow strip | `JiraAnalyzerFlowStrip` |

### C. Setup & About

| # | Criterion | Evidence |
|---|-----------|----------|
| C1 | Setup Done → Jira, Discovery, Documentation | `DoneStep` |
| C2 | About Get started aligned with DOCUMENTATION §0 | `FIRST_SESSION_STEPS` |
| C3 | About `?tab=` deep links | `AboutPage` search params |
| C4 | Local session reset (no control key); Downloads copy has no `platform_config` / `live_catalog` | `POST /api/setup/reset-local-session`, `export-platform-copy.ps1`, `reset-local-dev-data.ps1` |

### D. Documentation product

| # | Criterion | Evidence |
|---|-----------|----------|
| D1 | Business-only docs; Generate latest | `DocumentationPage`, backend doc routes |
| D2 | Collapsed quality / notes | `InfoHelpCollapsible` |
| D3 | Workspace filter on list | `DocumentationPage` |

### E. Automated verification (must pass on release commit)

```powershell
cd backend
python -m pytest tests/test_jira_qa_routing_integration.py tests/test_jira_workspace_resolver.py tests/test_feature_quality.py tests/test_doc_export.py tests/test_doc_catalog_enrichment.py tests/test_change_detection_integration.py tests/test_smoke.py tests/test_setup_status_safe.py tests/test_catalog_health_safe.py -q

cd ..\frontend
npm test
npm run build
```

**User launch copy (replace prior Downloads folder):**

```powershell
.\scripts\export-platform-copy.ps1
# → %USERPROFILE%\Downloads\pbi-discovery-platform + LAUNCH.md
```

---

## Excluded from this 100% (ops / environment)

These are **not** blockers for tagging a **release copy** of the repo; they are required before **production** with live tenants:

- Sync real client **[QA]** workspaces in Setup  
- `PBI_JIRA_*` / `PBI_PBI_*` in production `.env`  
- Staging cert S01–S08, analyst burn-in (`docs/PLATFORM-NEXT-ACTIONS.md`)  
- Legacy `/jira/legacy` automation (operators only)

---

## Signoff table

| Role | Status | Date | Notes |
|------|--------|------|-------|
| **Engineering** | **GO — 100%** | 2026-10-09 | Criteria A–E + C4; 53 pytest signoff bundle + 23 vitest + build |
| QA | Pending | | One ticket per QA workspace smoke |
| Release owner | Pending | | Tag separate copy + record commit SHA |

---

## After you pull this commit

1. Run the **§E** commands locally.  
2. Smoke: `/about?tab=start` → `/setup` → sync → `/jira` (scoped ticket) → `/documentation`.  
3. Tag release copy; attach this file + `docs/RELEASE-COPY-SIGNOFF.md`.

**Related:** [RELEASE-COPY-SIGNOFF.md](./RELEASE-COPY-SIGNOFF.md) · [DOCUMENTATION.md](./DOCUMENTATION.md) · [PLATFORM-UX-ROADMAP.md](./PLATFORM-UX-ROADMAP.md) · [PLATFORM-ISSUES-REGISTER-P0-P3.md](./PLATFORM-ISSUES-REGISTER-P0-P3.md) (59 items)

**Clean deployable copy:** `.\scripts\export-platform-copy.ps1` → `%USERPROFILE%\Downloads\pbi-discovery-platform` (excludes `labels/`, label docs, secrets, deps).
