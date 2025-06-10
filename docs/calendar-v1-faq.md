---
title: "Calendar V1 FAQMoon (Dark Mode)Sun (Light Mode)"
description: "Calendar V1 FAQ"
source_file: "docs/calendar-v1-faq.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:47:10.804Z"
api_parameters_count: "0"
---
## When do I have to call the Refresh Calendar Meetings endpoint?

[](#when-do-i-have-to-call-the-refresh-calendar-meetings-endpoint)

When you update calendar preferences or a calendar event, you don't need to manually call the [Refresh Calendar Meetings](https://recallai.readme.io/reference/calendar_meetings_refresh_create) endpoint. Recall handles updating any relevant bots when changes are made to these.

## Linking bots to calendar user/meetings

[](#linking-bots-to-calendar-usermeetings)

Bots scheduled via the calendar integration produce the status change events. On receiving these events, one common requirement is to link the bot back to a specific calendar meeting/user. Below are the steps for the same

1.  Fetch bot data via [Retrieve Bot](/reference/bot_retrieve.md) endpoint using `bot_id` from the event payload

2.  The `calendar_meetings` array will contain all the meeting instances which were recorded by this specific bot. Use `calendar_user.external_id` to fetch [Get Calendar Auth Token](/reference/calendar_authenticate_create.md).

3.  Use the auth token to fetch details for the meeting object via [Retrieve Calendar Meeting](/reference/calendar_meetings_retrieve.md) endpoint.


## How to detect if a user connected their calendar successfully or not ? OAuth callbacks are redirected to Recall's server.

[](#how-to-detect-if-a-user-connected-their-calendar-successfully-or-not--oauth-callbacks-are-redirected-to-recalls-server)

When [building the oAuth URL](/reference/calendar-v1-google-calendar.md), you can add `success_url` and/or `error_url` to the pass through `state` object. Recall will redirect the user to these depending on a successful/unsuccessful connection attempt. The query parameters attached to these are preserved allowing you to pass user context in these.

## What's the best way to allow users to disable a single calendar integration? [Delete Calendar User](/reference/calendar_user_destroy.md) disconnects all calendars.

[](#whats-the-best-way-to-allow-users-to-disable-a-single-calendar-integration-delete-calendar-user-disconnects-all-calendars)

To disconnect a specific calendar platform, you can use the [Disconnect Calendar Platform](/reference/calendar_user_disconnect_create.md) endpoint.

## What is `REACT_APP_AUTH_URL` in the [demo app source code](https://github.com/recallai/calendar-integration-demo/tree/master/v1-demo) ?

[](#what-is-react_app_auth_url-in-the-demo-app-source-code-)

The [Calendar Integration V1 APIs](/reference/calendar-v1-integration-guide.md) are designed to be directly integrated into the client. Due to this, there is need on your end to setup a server endpoint which token exchange (by calling the [https://recallai.readme.io/reference/calendar\_authenticate\_create](https://recallai.readme.io/reference/calendar_authenticate_create) endpoint on Recall's server). This needs to be a server endpoint to avoid exposing your Recall API Key on the client. The `REACT_APP_AUTH_URL` variable should contain the value for the endpoint. The demo code includes a [Cloudflare worker](https://github.com/recallai/calendar-integration-demo/tree/master/v1-demo/worker) to allow setting this up on your end without having to deploy a new endpoint on your backend.

## Can I connect two Google Calendars to the same user?

[](#can-i-connect-two-google-calendars-to-the-same-user)

The same calendar user cannot have multiple Google calendars (or multiple Microsoft calendars) connected to them. The latest connection will clear out bots and calendar data for any previous connections.

The same user **can** have one Google and one Microsoft calendar connected.

## What happens to scheduled bots when a user changes their recording preferences?

[](#what-happens-to-scheduled-bots-when-a-user-changes-their-recording-preferences)

If a user updates their recording preferences to include fewer meetings, the calendar v1 integration will automatically remove scheduled bots from any upcoming meetings that no longer match the new preferences.

# Common Errors

[](#common-errors)
- * *

## **Refresh token missing from OAuth response**

[](#refresh-token-missing-from-oauth-response)

`Calendar connection failed! (reason: refresh_token missing from oAuth response)`

There are a couple of cases related to the setup of [Microsoft Outlook Calendar Setup](/reference/calendar-v1-microsoft-outlook.md) which can lead to the above error.

1.  Incorrect/Misconfigured OAuth [credentials in dashboard](https://api.recall.ai/dashboard/platforms/microsoft) - `client id, client secret` (verify steps 3, 5, 6).
2.  `Supported Account Type` not set to **Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)** (step 1). For this step, if you've already created an app registration without Multitenant support, we recommend to create a new registration from scratch as updating the existing one can still lead to above error.

Incase neither of the above help, please try connecting the same calendar account on [the demo app here](https://recall-calendar-integration.pages.dev/) and report the error to us in Slack.

## Invalid Recall calendar auth token supplied

[](#invalid-recall-calendar-auth-token-supplied)

`Calendar connection failed! (Invalid ‘recall_calendar_auth_token’ supplied)`

This error occurs for one of two reasons:
- The auth token supplied is invalid: Either the token is invalid and couldn't be decoded
- The auth token has expired: Tokens have an expiry of 24h.
