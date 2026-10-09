# ForgeFiend: Atlassian Forge Architect Foundation

Build a production-ready Atlassian Forge app, then take it through Marketplace readiness and submission with the [Marketplace Listing MCP Server](https://github.com/wjkennedy/AtlassianMarketplaceMCPServer/tree/main/marketplace-listing-mcp).

This repository provides an agent skill for designing, implementing, and reviewing Forge apps. It establishes the architecture, security, testing, and packaging practices you need before moving into the Marketplace listing workflow.

## From app idea to Marketplace

1. **Design your app.** Choose the Atlassian product surface, interaction model, UI technology, identity model, and storage approach.
2. **Build and validate it.** Implement the app with clear frontend/backend boundaries, minimal permissions, tests, and deployment instructions.
3. **Prepare the listing handoff.** Gather your app identifiers, release evidence, customer-facing documentation, and listing assets.
4. **Connect the Marketplace Listing MCP Server.** Check deployment, distribution, Developer Space publication, and Marketplace discovery; resolve any blockers.
5. **Proceed to submission.** Use the server's controlled release workflow to prepare the listing and explicitly confirm submission for Atlassian review.

**Continue here when your app is ready: [Marketplace Listing MCP Server →](https://github.com/wjkennedy/AtlassianMarketplaceMCPServer/tree/main/marketplace-listing-mcp)**

## Get started

Clone this repository:

```bash
git clone https://github.com/wjkennedy/ForgeFiendCodexSkill.git
```

Make the cloned directory available to your coding agent using its supported local skill installation workflow. [SKILL.md](SKILL.md) is the entry point; keep the `agents/` and `references/` directories with it.

Invoke the skill with a concrete app brief:

```text
Use $atlassian-forge-development-architect-foundation to design and
implement a production-ready Forge app for Jira that helps project
admins review overdue work. Include the manifest, backend resolvers,
UI, permission tests, deployment script, and README. Prepare a
handoff checklist for the Marketplace Listing MCP Server.
```

For an existing app:

```text
Use $atlassian-forge-development-architect-foundation to review this
Forge app for Marketplace readiness. Check its architecture, scopes,
tenant isolation, data lifecycle, tests, and deployment packaging.
Fix the implementation gaps and identify what is still needed for
the Marketplace Listing MCP Server handoff.
```

## What the skill covers

- **Architecture:** UI-driven, event-driven, API-driven, and job-driven apps; product surfaces and module selection.
- **UI:** UI Kit by default, with Custom UI or a hybrid approach when the experience requires it.
- **Backend:** Resolvers for product API access, validation, authentication context, retries, pagination, and mutations.
- **Data and AI:** Storage choices, tenant isolation, incremental ingestion, and asynchronous indexing or embedding work.
- **Security:** Minimal scopes, permission boundaries, admin controls, secret handling, and documented data retention.
- **Delivery:** Resolver and permission tests, mocked Atlassian APIs, deployment scripts, and complete app documentation.

The skill records its runtime and CLI expectations in [SKILL.md](SKILL.md). Check those assumptions against current Forge documentation when preparing a release.

## Prepare your Marketplace handoff

Before moving to the MCP server, assemble the following in your app repository or release documentation:

| Area | Prepare |
| --- | --- |
| App identity | Forge app ID, target product, vendor details, and Marketplace software ID if one already exists. |
| Release | Validated manifest and scopes, build/test results, deployment instructions, and the intended production version. |
| Listing content | App name, summary, description, feature highlights, screenshots, and release notes. |
| Customer information | Support contact, privacy policy, terms of service, and accurate data handling and retention details. |
| Access | Forge CLI authentication and the account access needed to inspect Developer Console and Marketplace state. |

Keep credentials out of source control and handoff documents.

## Continue with the Marketplace Listing MCP Server

Open the [server's setup guide](https://github.com/wjkennedy/AtlassianMarketplaceMCPServer/blob/main/marketplace-listing-mcp/README.md) to install and configure it in your MCP client. Follow that guide for prerequisites, client registration, browser bridge setup, and optional Marketplace REST credentials.

The server checks the manifest, Forge deployment records, distribution state, Developer Space publication state, and whether Marketplace can discover your app and version. It returns evidence and blocking reasons, including checks that are unavailable because an integration or credential is missing.

Start with a readiness assessment:

```text
Use the Marketplace Listing MCP Server to assess this Forge app.
Repository path: /absolute/path/to/my-forge-app
Forge app ID: <my Forge app ID>
Vendor ID: <my Marketplace vendor ID>

Run marketplace_readiness_check, report the evidence and blockers,
and explain what is needed to prepare the listing for review.
```

A successful production deployment is one part of the journey: the server also verifies the distribution and Marketplace discovery steps. Its mutation tools are disabled by default, and deployment, distribution changes, and review submission require explicit confirmation. Submission starts Atlassian's review process; approval remains with Atlassian.

For repeatable release preparation, the server project also documents a `marketplace.json` configuration and a release wrapper. Use its [example configuration](https://github.com/wjkennedy/AtlassianMarketplaceMCPServer/blob/main/marketplace-listing-mcp/marketplace.example.json) as the starting point for your app's listing metadata and document paths.

## Repository guide

| File | Purpose |
| --- | --- |
| [SKILL.md](SKILL.md) | Agent workflow, mandatory constraints, and delivery checklist. |
| [agents/openai.yaml](agents/openai.yaml) | Skill display metadata and default prompt. |
| [references/forge-design-decision-tree.md](references/forge-design-decision-tree.md) | Architecture, UI, identity, and module selection guidance. |
| [references/forge-foundation-rules.md](references/forge-foundation-rules.md) | Foundation doctrine for data, security, and delivery. |
| [references/forge-storage-openapi-v3.json.txt](references/forge-storage-openapi-v3.json.txt) | Storage API reference supplied with the skill. |

**Next step: [prepare your app's Marketplace listing with the MCP server](https://github.com/wjkennedy/AtlassianMarketplaceMCPServer/tree/main/marketplace-listing-mcp).**
