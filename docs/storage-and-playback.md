---
title: "Storage and PlaybackMoon (Dark Mode)Sun (Light Mode)"
description: "All bots follow Recall's data retention policy."
source_file: "docs/storage-and-playback.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:00:12.101Z"
api_parameters_count: "0"
---
By default, all media associated with a recording is retained for 7 days following the end of a call, after which it's deleted **permanently**.

This data can also be deleted at any point by calling [Delete Bot Media](/reference/bot_delete_media_create) or [Delete Recording](/reference/recording_destroy).

# Recording Media

[](#recording-media)

**Media** refers to:
- Recording
- Transcript
- Speaker timeline
- Participant metadata (who joined, left, timestamps)
- Meeting metadata (e.g. Meeting title)
- Video files, audio files, and any other media
- Bot screenshots
- Debug data

*Note: Deleting bot media through the API does not delete logs. Log files will be automatically deleted after the 7 day retention period.*

> **CALLOUT**:

## 📘

Custom metadata and the meeting URL are not deleted upon media expiration/deletion for a bot.

# Custom Storage Duration

[](#custom-storage-duration)

Recall supports specifying custom retention for the recordings captured by a bot via the `recording_config.retention` field in [Create Bot](/reference/bot_create) request. Two retention types are supported

1.  **Timed**
    Allows you to specify a custom retention duration in hours via the required `hours` property (e.g., hours: 72 for 3 days). The recording will expire after the specified number of hours from creation.
    ```
    {
      "type": "timed",
      "hours": <NUMBER_OF_HOURS_TO_RETAIN>
    }

    ```

2.  **Forever**
    The recording will never expire and will be retained indefinitely unless explicitly deleted.
    ```
    {
      "type": "forever"
    }

    ```


## Pricing

[](#pricing)

Recall provides 7 days of free recording retention. After that, additional retention is charged at:

> **$0.05 per hour of recording retained for 30 days**
> (Equivalent to $0.0000694 per hour of recording retained)

For e.g If you retain a 1-hour recording for 30 additional days, the total cost is:
`$0.0000694 × 1 recording hour × 720 hours (30 days) = $0.05`

If you have any questions regarding the pricing, please reach out to us in Slack for more information.

# Media Expiration

[](#media-expiration)

The media expiration date for a given recording can be found in the `expires_at` field of the [Recording](/reference/recording_retrieve):

```
{
  "id": "a5437136-4b69-429a-9e0c-cd388fd8fee6",
  "expires_at": "2024-12-27T00:07:47.409813Z",
  ...
}

```

## The `recording.deleted` Webhook

[](#the-recordingdeleted-webhook)

When a recording reaches its expiration date and is deleted, you will receive a `recording.deleted` [Status Change Webhook](/docs/status-change-webhooks) to notify you of this.

## Manually deleting media

[](#manually-deleting-media)

You can also delete a recording's media at any point through the API by calling the [Delete Recording](/reference/recording_destroy) endpoint.



# Encryption

[](#encryption)

Bot data is encrypted at rest in our database for additional security. For additional information on how data is secured, please visit our [security portal](https://security.recall.ai).



# Transcription Partners

[](#transcription-partners)

## Gladia

[](#gladia)

For customers using Gladia through Recall's account (and *not* their own Gladia API key), there is zero-data retention on Gladia's servers.
