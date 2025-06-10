---
title: "Bot FundamentalsMoon (Dark Mode)Sun (Light Mode)"
description: "Scheduled vs. Ad Hoc Bots There are two different ways of using bots: Ad Hoc (\"On-demand\") bots - Bot joins call immediately. Very occasionally, the call to Create Bot may return a HTTP 507 . In this rare case, you can retry the call to Create Bot. Scheduled bots - Bot is scheduled to join a call in..."
source_file: "docs/bot-fundamentals.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:14.734Z"
api_parameters_count: "0"
---
# Scheduled vs. Ad Hoc Bots

[](#scheduled-vs-ad-hoc-bots)

There are two different ways of using bots:

1.  Ad Hoc ("On-demand") bots - Bot joins call immediately. Very occasionally, the call to [Create Bot](/reference/bot_create.md) may return a [HTTP 507](https://recallai.readme.io/reference/errors#adhoc-bot-pool-errors). In this rare case, you can retry the call to Create Bot.
2.  Scheduled bots - Bot is scheduled to join a call in the future, and is guaranteed to join.

**We highly recommend you use scheduled bots whenever possible.**

To use scheduled bots, you can either:

1.  Specify the `join_at` parameter in the [Create Bot](https://recallai.readme.io/reference/bot_create) endpoint at least 10 minutes in advance
2.  Use our [calendar integration](calendar-integration).

> **CALLOUT**:

## 📘

Scheduling bots for the future using `join_at`

The `join_at` parameter allows you to schedule bots for the future, and you may be wondering if there are limitations or best practices.

In general, we recommend you to schedule a bot **as soon as you know about the meeting, and there is no limit how far into the future you can schedule bots.**

# Send Bots to Meetings

[](#send-bots-to-meetings)

There are a few different ways to send a bot to a meeting in Recall.

Depending on your app's requirements and use case, you'll likely want to use a combination of these options.

## Calling the Create Bot endpoint directly

[](#calling-the-create-bot-endpoint-directly)

This is the most manual way to send a bot to a meeting, where you simply call the [Create Bot](/reference/bot_create.md) endpoint directly.

While it's the easiest to get started with and the most flexible, there may be a better way to create bots depending on your use case.

## Automatically schedule bots to calendar events

[](#automatically-schedule-bots-to-calendar-events)

The Recall calendar integration allow you to automatically schedule bots to send your users' calendar events, keeping scheduled bots in sync with any calendar changes.

For more information, check out our getting started guide [here](calendar-integration).

## Adding a bot email address to the meeting event

[](#adding-a-bot-email-address-to-the-meeting-event)

Another benefit of the Recall calendar integration is that it enables your users to add bots to meetings through inviting an email, just like you would any other participant.

To enable this flow, see [these instructions](calendar-integration-faq#how-do-i-add-a-bot-to-a-calendar-event-via-email).
