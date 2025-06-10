---
title: "API ErrorsMoon (Dark Mode)Sun (Light Mode)"
description: "API Error Codes Recall's API uses the following HTTP codes: Error Code Meaning 200 OK -- Everything worked as expected. 201 Bot created successfully. 400 There was something wrong with your request. Check the response body for a detailed error message. For the error message reference, go here . 401 ..."
source_file: "reference/errors.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:57:09.382Z"
api_parameters_count: "0"
---
API Error Codes Recall's API uses the following HTTP codes: Error Code Meaning 200 OK -- Everything worked as expected. 201 Bot created successfully. 400 There was something wrong with your request. Check the response body for a detailed error message. For the error message reference, go here . 401 ...

# API Error Codes

[](#api-error-codes)

Recall's API uses the following HTTP codes:

| Error Code | Meaning |
| --- | --- |
| 200 | OK -- Everything worked as expected. |
| 201 | Bot created successfully. |
| 400 | There was something wrong with your request. Check the response body for a detailed error message. For the error message reference, go here. |
| 401 | Unauthorized -- No valid API key provided. |
| 402 | (Self-serve customers) Insufficient credit balance -- Top up balance in the dashboard. |
| 403 | Request Blocked -- Our WAF blocked your request due to an issue with your payload. |
| 405 | Method is not allowed for the endpoint -- if calling DELETE, the bot has already been dispatched. |
| 409 | Conflict -- please retry with exponential backoff (see Scheduling Guide and Idempotency) |
| 429 | Too many requests: Retry after the duration specified in the returned Retry-After header (Retry-After: <delay-seconds>). |
| 502 | Our servers have dropped the request due to high load -- please retry. |
| 503 | Our servers have dropped the request due to high load -- please retry. |
| 504 | Our servers have dropped the request due to high load -- please retry. |
| 507 | Out of adhoc bots -- Please retry in 30 seconds. |

## Adhoc Bot Pool Errors

[](#adhoc-bot-pool-errors)

An HTTP 507 error occurs when you are trying to create an "adhoc bot", and no bots are available in the "adhoc bot pool". Adhoc bots are bots that are created without specifying a join time in advance. They join the call immediately, and are claimed from a pool of idle bots that we scale predictively based off of expected load.

Sometimes many bots are requested at once, which depletes the idle bot pool. Any attempts to create an adhoc bot at this point will result in a HTTP 507 error, until new bots are automatically launched to replenish the pool.

This replenishment results in new bots being available within a few seconds to a minute or two, so if you receive the HTTP 507 error you should retry the request every 30 seconds.

You can avoid the HTTP 507 error entirely by using [scheduled bots](https://recallai.readme.io/reference/best-practices#scheduling-bots). These are bots that have a join time specified in advance, either through the `create_bot.join_at` parameter or by using the Recall.ai calendar integration. When you create a scheduled bot, we launch and reserve a bot specifically for you, which guarantees that it will join the call at the indicated time.

## 400 Error Message Reference

[](#400-error-message-reference)

| Code | Response Body | Description |
| --- | --- | --- |
| teams_blacklisted_tenant |  | Microsoft Teams has certain tenants that do not allow bots to join their calls. This error occurs when you attempt to create a bot for a meeting hosted by one of these tenants. |
|  | Cannot validate partial without join call task | This typically happens when Update Scheduled Bot is called on a bot that was already sent to a call. You can verify a scheduled bot was already sent to a call when you receive the joining_call webhook event. |
| update_bot_failed | Not enough time to launch new bot | This typically happens when Update Scheduled Bot is called with an updated join_at too close to the present (>6 minutes). There is a minimum amount of time it takes for us to launch a scheduled bot, and we cannot update a scheduled bot's join_at too close to the present for that reason. |
| cannot_command_completed_bot | Cannot send a command to a bot which has completed(is shutting/has shut down/has errored). | This error occurs when a bot is shutting down, has shut down, or has errored, and you call an endpoint that requires the bot to be in the call - for instance, Remove Bot From Call. |
| cannot_command_unstarted_bot | Cannot send a command to a bot which has not been started. | This occurs when you call an endpoint that requires the bot to be in a call while the bot has already been terminated - for instance, Remove Bot From Call. |

## Fatal Errors

[](#fatal-errors)

When you get a [Bot Status Change Webhook Event](/docs/bot-status-change-events.md) from a bot with status `fatal`, you can check the `data.status.sub_code` field to get a description of the error. The complete list for possible `sub_code` can be found here [Bot Error Codes](/docs/sub-codes#fatal-sub-codes.md)

## 403 Request Blocked

[](#403-request-blocked)

Our WAF may block your request if the payload is flagged as potentially malicious or malformed.

In this case, the HTML body in the response will look something like this:

html

```
<BODY>
    <H1>403 ERROR</H1>
    <H2>The request could not be satisfied.</H2>
    <HR noshade size="1px">
    Request blocked.
    We can't connect to the server for this app or website at this time. There might be too much traffic or a
    configuration error. Try again later, or contact the app or website owner.
		...
</BODY>

```

Common scenarios include:
- Providing a `localhost` URL in the payload
- Providing a body (including a null body) in a GET request
- [Table of Contents](#)
- -   [API Error Codes](#api-error-codes)
- [Adhoc Bot Pool Errors](#adhoc-bot-pool-errors)
- [400 Error Message Reference](#400-error-message-reference)
- [Fatal Errors](#fatal-errors)
- [403 Request Blocked](#403-request-blocked)
