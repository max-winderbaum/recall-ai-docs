---
title: "Zoom FAQMoon (Dark Mode)Sun (Light Mode)"
description: "Frequently asked questions about Zoom bots."
source_file: "docs/zoom-faq.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:47:11.860Z"
api_parameters_count: "0"
---
## What if Zoom returns an internal error?

[](#what-if-zoom-returns-an-internal-error)

On rare occasions, your bot may fail to enter a call with a `zoom_internal_error` [sub code](/docs/sub-codes.md).

Unfortunately this means something went wrong on Zoom's end, and we have limited visibility into the underlying error. We do our best to handle these errors internally through retries but on rare occasions this error can cause a bot to fail.

If you're seeing this error recur for a certain situation or user, please let us know and we can raise the issue with Zoom.

## What happens if there is a password on the Zoom meeting?

[](#what-happens-if-there-is-a-password-on-the-zoom-meeting)

If there is a password on the meeting, it should be embedded in the meeting URL as a query parameter by default. For example, a meeting URL with an embedded password might look like this: [https://zoom.us/j/123?pwd=abc](https://zoom.us/j/123?pwd=abc). Everything after the `pwd=`in the URL is the password, which the bot will use to join the call.

If the password is not in the query parameter, the bot will not be able to join the call.

## Does the bot need to be let in every time?

[](#does-the-bot-need-to-be-let-in-every-time)

The bot will go into the waiting room only if there is a waiting room enabled.

Think about the bot just like a normal participant. If there's a waiting room enabled, then it will go into the waiting room with other participants.

If there is no waiting room enabled, then it will skip the waiting room and join the meeting directly, just like other participants.

## Are Zoomgov URLs supported?

[](#are-zoomgov-urls-supported)

We currently don't have support for Zoomgov URLs, but if this is a requirement for your use case, please reach out to our team.

## Why isn't my bot sending chat messages?

[](#why-isnt-my-bot-sending-chat-messages)

If the chat messages sent by your bot aren't showing up, it's likely a problem with your Zoom configuration. Please ensure that "Continuous Meeting Chat" is enabled on your Zoom account.

![](https://files.readme.io/743c501a76963f60eabad93a13bef499c43bac7a3c72028a8b11433222505581-CleanShot_2024-09-13_at_13.24.41.png)
