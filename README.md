# Wise

API connector for [Wise](https://wise.com) (formerly TransferWise), an international money transfer and multi-currency account platform. This connector provides access to profiles, transfers, and recipient account data.

## What is this?

This is a **connector** -- a configuration that defines how to authenticate with Wise and what data endpoints are available for reading and writing. It does not move data by itself. Instead, it is used by the [Analitiq](https://analitiq-app.com) data integration platform or the open-source `analitiq-core` engine to set up data pipelines.

## How to use this connector

There are two ways to use this connector:

### Option 1 -- Analitiq Cloud (no setup required)

All connectors from this registry are automatically available on [analitiq-app.com](https://analitiq-app.com). Simply log in, select the connector, and follow the on-screen instructions to connect your account.

### Option 2 -- Open Source (self-hosted)

All connectors are open source and free to use. To get started:

1. Clone the [analitiq-core](https://github.com/analitiq-core) repository
2. Install the Claude plugin `analitiq-plugin-dataflow`
3. Launch Claude in the root directory of `analitiq-core`
4. Tell it: *"I need to move data from X to Y"*

The `analitiq-plugin-dataflow` plugin will automatically fetch the required connectors from the [Analitiq Skill Registry](https://github.com/analitiq-skill-registry) and set up the data flow pipeline for you.

## Prerequisites

- A Wise account (personal or business)
- A Personal API Token generated from your Wise account settings

## Authentication

Wise uses a **Personal API Token** (Bearer token) for authentication. This is a deprecated auth method -- Wise is migrating to OAuth2 + mTLS -- but tokens continue to work as of March 2026.

### How to get your credentials

1. Log in to your account at [wise.com](https://wise.com)
2. Navigate to **Your Account > Integrations and Tools > API tokens**
3. Click **Add new token**
4. Select the permissions you need (read-only is recommended for data extraction)
5. Copy the generated token -- it will not be shown again

After connecting, you will be asked to select a **profile** (personal or business). Most API endpoints require a profile ID.

## Available Endpoints

The table below lists all data endpoints defined by this connector. Each endpoint represents a resource you can read from or write to.

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/v1/profiles` | GET | List user profiles (personal and/or business) |
| `/v1/transfers` | GET | List transfers for a profile |
| `/v1/accounts` | GET | List recipient (beneficiary) accounts for a profile |

## Limitations

- **Rate limits** -- The API allows 1000 requests per 60 seconds
- **Deprecated auth** -- The Personal API Token method is deprecated. Wise is migrating to OAuth2 + mTLS. Monitor the [Wise migration guide](https://docs.wise.com/guides/developer/auth-and-security) for updates
- **Profile required** -- Most endpoints require a `profile_id`, obtained via the post-auth profile selection step
- **Sandbox** -- A sandbox environment is available at `https://api.wise-sandbox.com` for testing with test credentials

## For AI agents

This connector includes `CLAUDE.md` and `AGENTS.md` files -- machine-readable references used by AI agents and agentic frameworks. They document authentication types, available endpoints, post-auth steps, and any caveats for programmatic use. Both files are kept identical -- `CLAUDE.md` is for Claude Code, `AGENTS.md` is for other agent frameworks.

## Create a connector to any system

You can create a new connector to any API or database using Claude and the Analitiq connector builder plugin:

1. Install [Claude Code](https://claude.ai/code)
2. Install the connector builder plugin:
   ```
   claude plugin add analitiq-skill-registry/analitiq-plugin-connector-builder
   ```
3. Launch Claude and say: *"I want to create a connector for [system name]"*
4. The plugin will interview you about the system, research its API documentation, and generate the full connector with all required files

No coding required -- the plugin handles authentication research, endpoint schema generation, and file creation automatically.

![Example of Claude building a connector](media/example_1.png)

## Contributing

All connectors in this registry are community-maintained and live at [github.com/analitiq-skill-registry](https://github.com/analitiq-skill-registry). To add new endpoints or improve an existing connector, install the [connector builder plugin](https://github.com/analitiq-skill-registry/analitiq-plugin-connector-builder) and follow its instructions.

## Links

- [Wise API Documentation](https://docs.wise.com/api-docs/api-reference)
- [Wise Auth & Security Guide](https://docs.wise.com/guides/developer/auth-and-security)
- [Analitiq Cloud](https://analitiq-app.com)
- [Analitiq Core (open source)](https://github.com/analitiq-core)
