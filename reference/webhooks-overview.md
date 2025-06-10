---
title: "WebhooksMoon (Dark Mode)Sun (Light Mode)"
description: "Overview of Recall webhooks."
source_file: "reference/webhooks-overview.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:15.049Z"
api_parameters_count: "0"
---
Overview of Recall webhooks.

Recall uses webhooks to push data or notify your server when certain events happen.

There are a few different types of webhooks to be aware of. You may find yourself using some, none, or all of these depending on your application and use case.

## Status Changes

[](#status-changes)

These are sent using Svix and can be setup via your [Recall Webhook Dashboard](https://api.recall.ai/dashboard/webhooks/). These include the following
- **[Bot Status Change Events](/docs/bot-status-change-events.md)**
- **[Recording Webhooks](/docs/recording-webhooks.md)**



## Calendar Integration

[](#calendar-integration)

These are sent using Svix and can be setup via your [Recall Webhook Dashboard](https://api.recall.ai/dashboard/webhooks/)
- **[Calendar (V2) Events](/docs/calendar-v2-webhooks.md)**



## Realtime Endpoints

[](#realtime-endpoints)

These are used to deliver data from bots in realtime, these must be configured on a per bot basis via the [Create Bot](/reference/bot_create.md) endpoint. They are not configurable via the Recall webhook dashboard.
- [Realtime Endpoints](/docs/real-time-endpoints.md)
- [Table of Contents](#)
- -   [Status Changes](#status-changes)
- [Calendar Integration](#calendar-integration)
- [Realtime Endpoints](#realtime-endpoints)
