---
title: "Teams Blacklisted Tenant IDsMoon (Dark Mode)Sun (Light Mode)"
description: "Microsoft Teams has certain tenants that do not allow bots to join their calls. If you attempt to create a bot for a Microsoft Teams meeting hosted by a blacklisted tenant, you'll receive a 400 error with the following message: Tenant is blacklisted. More info: https://docs.recall.ai/docs/teams-blac..."
source_file: "docs/teams-blacklisted-tenant-ids.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:47:11.748Z"
api_parameters_count: "0"
---
Microsoft Teams has certain tenants that do not allow bots to join their calls.

If you attempt to create a bot for a Microsoft Teams meeting hosted by a blacklisted tenant, you'll receive a `400` error with the following message:

```
Tenant is blacklisted. More info: https://docs.recall.ai/docs/teams-blacklisted-tenant-ids

```

Since these tenants have banned all bots from joining their calls, there is no workaround for this.
