# Product naming — Fabric Beacon (v1)

## Recommended public name

| Field | Value |
|-------|--------|
| **Product name** | **Fabric Beacon** |
| **Subtitle** | Power BI & Fabric catalog discovery, documentation, and Jira-scoped analysis |
| **Repo slug (unchanged)** | `pbi-discovery-platform` |
| **MCP companion** | Beacon MCP (`pbi-discovery/mcp-server/`) |
| **Legacy internal** | PBI Discovery Platform |

**Why “Fabric Beacon” (vs Catalog Beacon):** Signals Microsoft Fabric + Power BI together; “beacon” = find the right report, model, and ticket scope quickly without opening ten admin portals.

**Alternatives** (same portfolio style): Catalog Beacon, Fabric Atlas, Power Compass — see history in git if needed.

## Display override (optional)

Non-secret UI label only (not required for onboarding):

```env
# frontend/.env.local (optional)
VITE_PRODUCT_NAME=Fabric Beacon
```

Default in code is already **Fabric Beacon** when this is unset.

## Sibling products

| Name | Role |
|------|------|
| Paginate Forge | Paginated RDL build & validate |
| Release Orchestrator | PIC / release workflow |
| Lake Lanes | PBIP → lakehouse migration |
| Label Relay | Jira label workers (operators; excluded from clean copy) |
