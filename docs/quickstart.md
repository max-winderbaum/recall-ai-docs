---
title: "Quickstart: Record a meeting using a botMoon (Dark Mode)Sun (Light Mode)"
description: "Learn how to send a bot to a meeting and retrieve the recording."
source_file: "docs/quickstart.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:15.538Z"
api_parameters_count: "0"
---
# 1\. Initial setup

[](#1-initial-setup)

Create an API Key in the [Recall dashboard](https://api.recall.ai/dashboard/apikeys/). This will be used for API authentication.

# 2\. Create a meeting

[](#2-create-a-meeting)

We recommend using Google Meet for this quickstart. You can create one quickly by navigating to [meet.new](https://meet.new). After you create the meeting, stay in the meeting you created, and save the meeting URL for the next step.

# 3\. Send a bot to the meeting

[](#3-send-a-bot-to-the-meeting)

Use the [Create Bot](/reference/bot_create.md) endpoint to send a bot to a meeting.
- Swap the `$RECALLAI_API_KEY` placeholder in `Authorization` with your API key
- Swap the `$RECALLAI_REGION` placeholder with the region associated with your Recall account (e.g. `us-west-2`, `us-east-1`, `eu-central-1`, or `ap-northeast-1`)
- Swap the placeholder in `$MEETING_URL` with the meeting URL from the previous step.

cURL

```
curl -X POST https://$RECALLAI_REGION.recall.ai/api/v1/bot \
    -H 'Authorization: Token $RECALLAI_API_KEY' \
    -H 'Content-Type: application/json' \
    -d '
    {
      "meeting_url": "$MEETING_URL",
      "bot_name": "My Bot",
      "recording_config": {"transcript": {"provider": {"meeting_captions": {}}}
    }'

```

The response will include a **Bot ID** (in `id`). Save it for the next few steps.
If everything works, the command-line displays a response in the following shape.

JSON

```
{
  "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "meeting_url": "string",
  "bot_name": "Meeting Notetaker",
  "join_at": "2024-12-21T02:59:30.044Z",
  "recording_config": {
    "video_mixed_mp4": {
      "metadata": {}
    },
    "participant_events": {
      "metadata": {}
    },
    "meeting_metadata": {
      "metadata": {}
    },
    "transcript": {
      "provider": {
        "meeting_captions": {}
      }
    },
    "realtime_endpoints": [],
    "video_mixed_layout": "speaker_view",
    "video_mixed_participant_video_when_screenshare": "overlap",
    "start_recording_on": "participant_join",
    "include_bot_in_recording": {
      "audio": false
    },
    "metadata": {},
    "audio_mixed_raw": null,
  },
  "status_changes": [],
  ...
}

```

# 4\. Talk for a little bit

[](#4-talk-for-a-little-bit)

While you and the bot are in the meeting, make sure to turn on your video or talk for a little bit. This way, there will be actual content in the video recording the bot produces for you to look at after.

# 5\. End the meeting

[](#5-end-the-meeting)

Once you feel like there is enough content in the meeting, end the meeting. The bot will automatically leave.

# 6\. Wait for `done`

[](#6-wait-for-done)

Once the meeting is done, Recall begins processing the video recording. This typically takes less than 10 seconds no matter the length of the meeting.

When the recording is ready to be downloaded, the bot status changes to `done`.

The best way to retrieve this is via **webhooks**. See the [Webhook Overview](/reference/webhooks-overview.md) for details.

If you can't use webhooks for some reason, you can manually **poll** [Retrieve Bot](/reference/bot_retrieve.md) to see the bot status.

# 7\. Retrieve the recording

[](#7-retrieve-the-recording)

To retrieve the recording the bot created, use the [Retrieve Bot](/reference/bot_retrieve.md) endpoint.
- Swap the `$RECALLAI_API_KEY` placeholder in `Authorization` with your API key
- Swap the `$RECALLAI_REGION` placeholder with the region associated with your Recall account (e.g. `us-west-2`, `us-east-1`, `eu-central-1`, or `ap-northeast-1`)
- Swap the Bot ID with the id you saved in Step 3.

cURL

```
curl -X GET https://$RECALLAI_REGION.recall.ai/api/v1/bot/$BOT_ID \
	-H 'Authorization: Token $RECALLAI_API_KEY'

```

The response will contain a lot of data about the meeting, but for now we'll focus on retrieving the mp4 recording. The `recordings` array in the response will contain a list of the recordings associated with this bot. In this case there's just one recording.

The mp4 recording itself is located in the `video_mixed` object in the `media_shortcuts` field of the recording object. In the `data` field, you'll see a `download_url`. Copy and paste this URL into your web browser to view.

JSON

```
{
  "id": "95db53d7-47f6-4d49-be61-dd4481038958",
  ...,
  "recording": "824ad909-8736-4bb1-92d8-1639aa297cd2",
  "recordings": [
    {
      "id": "824ad909-8736-4bb1-92d8-1639aa297cd2",
      ...
      "media_shortcuts": {
        "video_mixed": {
          "data": {
            "download_url": "https://recallai-production-bot-data.s3.amazonaws.com/_workspace-8ef4bed2-e139-4449-af6a-e26d2d231555/recordings/824ad909-8736-4bb1-92d8-1639aa297cd2/video_mixed/39718d95-a981-450e-b16c-170b9b153d9c/bot/95db53d7-47f6-4d49-be61-dd4481038958/AROA3Z2PRSQAET6FSC3NG%3Ai-0d05e48eb769f7e40/video.mp4?AWSAccessKeyId=ASIA3Z2PRSQAP7V2VTVW&Signature=1qwkdS2KLwxKxjkbqk9fma5lb%2F8%3D&x-amz-security-token=IQoJb3JpZ2luX2VjEKT%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLWVhc3QtMSJIMEYCIQC01t0cqG%2BJ%2BaXuQliX6hx3ilkkq5kA7cze1y4MEDrgzgIhAO8zSkOKHBa0GsZufper%2FgO%2FJzp4C%2BUqR1o6DXv4YfNpKroFCE0QABoMODExMzc4Nzc1MDQwIgySUiwgZFsPTUKB8MAqlwXPG%2BVAI41s3Ag1SJsLPP5vX8IGxpgE2sT4pj3Z%2B8GnzRdfQCtWYl9ZUbzQ%2FPgAzl7MZfgtKcZ8Sn8qttsGbQIdx3McIqr1XaV7MxibaRETywjeaQGeEFDZQNbSjvvw7zsryRAcB5FKY8ZaTTrbnyrRwSq%2BPTovOh98DNzXteNDNvh6azntys7HcuTfUHrRmp%2FgmmFGIRCdU96x1qvmdqvIJKprWpVuoAmdGVtHR6ArtVtBdxKC%2BjUSivXOdlSkYNTJ0wYXyMmMRLYzNezDEIqrHNahsz%2BcnNfP01rFLlhIfP64gWUgGWMrQb%2FY4q7stPUBTPq2MQDdNC0tE2zHyb1XYzcS0vvpyen8GfUwK5SQhwzmCYEaq648%2FUPvLVR6Akd1CpByAE6zjVFB7G5mwCWoC02Mmua8%2F9t1vToSHB7JWwBdNtwua4glUJ01kzjqkFdACzlJB31FpUSpxkwSPl1Vi1v%2FQa4jvcdm0DtPA6%2B1%2BAI98ddx81WjLkgePqwlEIcH7rNTIlZLElIzjesNGWIFFMSazm1PuntVv9LnWtUttHWmVjlF%2FCyZYF2pevbnaKw%2FmKqWPUT0U92RjrFvaPyZmJ1YQZcOzTg1t8VdeKwMqj5pX2mfAD2MPPZAk5rDGMhjitBKYPnNy%2FP31HsUDuxwKjyoKrI4QelcYUTcAgIT2%2FQUIaBZ%2Bc90hUt7cS9qk8hQzKKZfQuM%2FhTiCGcBS5CE8KBPd9QUtucTYKzzW3e0%2FlYG3u8ha2gBqmR%2FN8%2FiiT0ewVZaFeoDttjnZ1ySN21hLqIxvh%2Fn4rcPn%2FooRjlHOjbrrkX5q%2Bw2eVhOxby0E%2BDqk6HXTHBfC7xlLQI9vCDP3Rc045qaPbToTLYXafExMTdpDVzLGaEwweedugY6sAEebI5sdpC9i3I0wJL%2BYPHKQz9MJzjPc88cN4%2FtHT5XEhQJMCXeakGl3Gbgu%2F1G9dGX%2FtlVwUVZjABUKCNt32RzDbfKQgHa28dgkphubSlA7SxKIObbIJm3o3xJuV%2Fp93qHFK%2FgyWQ9w5CoqPFJJZuMEYyoZZLyhip8su%2Bdnp9eveV7qkHYLFEec4BVu54yImfqf5kYVWumGM8WMcFuuwsE4GuSuRFSeatxXInJs6JBEg%3D%3D&Expires=1732766680"
          },
          "format": "mp4",
          ...
        },
        ...
      }
    }
  ]
}

```

Recall deletes the recording files after 7 days, indicated by `expires_at` on the recording.

In practice, you should download the recording and upload to your own servers right after you receive the `bot.done` [Bot Webhook](/docs/bot-status-change-events.md).

# 8\. Retrieve the transcript

[](#8-retrieve-the-transcript)

The transcript itself is located in the `transcript` object in the `media_shortcuts` field of the recording object. In the `data` field, you'll see a `download_url`. Copy and paste this URL into your web browser to view.

JSON

```
{
  "id": "95db53d7-47f6-4d49-be61-dd4481038958",
  ...,
  "recording": "824ad909-8736-4bb1-92d8-1639aa297cd2",
  "recordings": [
    {
      "id": "824ad909-8736-4bb1-92d8-1639aa297cd2",
      ...
      "media_shortcuts": {
        "transcript": {
          "data": {
            "download_url": "..."
          },
          ...
        },
        ...
      }
    }
  ]
}

```

The response will be in [the following format](/docs/download-schemas#json-transcript-download-url.md)

# Next steps

[](#next-steps)

Now that you have a sense of how to work with Recall's API, here are a few things to try next:

### [Real-time transcription](/reference/real-time-transcription.md)

[](#real-time-transcription)

This will allow your bot to transcribe conversations in real-time, allowing you to react to conversation data as soon as it's spoken.

### [Asynchronous transcription](/reference/asynchronous-transcription.md)

[](#asynchronous-transcription)

This will allow you to transcribe conversations after they've ended.

### [Zoom Setup](/reference/zoom-overview.md)

[](#zoom-setup)

Learn how to start sending bots to Zoom calls!
