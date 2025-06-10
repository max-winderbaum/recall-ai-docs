---
title: "Pre-Submission Checklist (Legacy)Moon (Dark Mode)Sun (Light Mode)"
description: "Zoom SDK App pre-submission checklist for legacy Recall customers."
source_file: "docs/pre-submission-checklist-legacy.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:00:11.801Z"
api_parameters_count: "0"
---
> **CALLOUT**:

## 🚧

Existing Customers

These checklist items are only for customers using Recall prior to Zoom instating new bot compliance requirements in late 2023. If you were not a Recall customer prior to this, you don't need to worry about the remaining items and can continue to our [Zoom SDK App Submission Guidelines](/docs/zoom-sdk-review-guidelines).

## Have you registered your new Zoom SDK credentials in your **⚠️non production⚠️** Recall.ai workspace?

[](#have-you-registered-your-new-zoom-sdk-credentials-in-your-️non-production️-recallai-workspace)

Zoom will verify that the credentials used by the bot are correct during the review process.

Do not register Zoom SDK credentials that have not been whitelisted or approved in your production Recall account. This is because bots using un-approved credentials are not able to join meetings outside of the app creator's workspace, such as your customers' meetings.

If your Zoom SDK credentials **have** been whitelisted, you **can** put them in your production Recall account. If you are not sure, ask us in our shared Slack channel!

## When you call [Create Bot](/reference/bot_create), are you sending the new Zoom parameters to request permission?

[](#when-you-call-create-bot-are-you-sending-the-new-zoom-parameters-to-request-permission)

1.  You should specify: `zoom.request_recording_permission_on_host_join: true` and `zoom.require_recording_permission: true`
2.  Specifying these parameters triggers the new Zoom recording consent flow, which is required to pass Zoom app review.
3.  If you're using the Recall V1 calendar integration to automatically create bots, please contact us so we can set these parameters for you!

Note that since these parameters are enabled by default for all new Recall accounts, they are *not* displayed in the [Create Bot](/reference/bot_create) endpoint parameters.

**Zoom Parameters**

JSON

```
{
  "zoom": {
    "require_recording_permission": true,
    "request_recording_permission_on_host_join": true
  },
  ...
}

```
