---
title: "Recording WebhooksMoon (Dark Mode)Sun (Light Mode)"
description: "Recording Status Webhook This webhook is sent whenever the recording's status is changed and is delivered via Svix to the endpoints configured in your Recall dashboard . { \"event\": \"recording.processing\", // recording.done, recording.failed, recording.deleted \"data\": { \"data\": { \"code\": string, \"sub..."
source_file: "docs/recording-webhooks.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:15.676Z"
api_parameters_count: "0"
---
## Recording Status Webhook

[](#recording-status-webhook)

This webhook is sent whenever the recording's status is changed and is delivered via Svix to the endpoints configured in your [Recall dashboard](https://api.recall.ai/dashboard/webhooks/).

JSON

```
{
  "event": "recording.processing", // recording.done, recording.failed, recording.deleted
  "data": {
    "data": {
      "code": string,
      "sub_code": string | null,
      "updated_at": string
    },
    "recording": {
      "id": string,
      "metadata": object
    },
    "bot": {
      "id": string,
      "metadata": object
    }
  }
}

```

| Event | Description |
| --- | --- |
| recording.processing | The recording has started |
| recording.done | The recording has successfully completed. All data for media objects on the recording is now available |
| recording.failed | The recording failed to be captured. The data.sub_code will contain machine readable code for the failure |
| recording.deleted | The recording has been deleted from Recall systems. |



## Media Object Status Webhook

[](#media-object-status-webhook)

This webhook is sent whenever the media object's status is changed and is delivered via Svix to the endpoints configured in your [Recall dashboard](https://api.recall.ai/dashboard/webhooks/). The following media object are supported
- `participant_events`
- `transcript`
- `video_mixed`
- `video_separate`
- `audio_mixed`
- `audio_separate`
- `meeting_metadata`

Example structure:

JSON

```
{
  "event": "participant_events.processing",
  "data": {
    "data": {
      "code": string,
      "sub_code": string | null,
      "updated_at": string
    },
    "participant_events": {
      "id": string,
      "metadata": object,
    },
    "recording": {
      "id": string,
      "metadata": object
    },
    "bot": {
      "id": string,
      "metadata": object
    }
  }
}

```

| Event | Description |
| --- | --- |
| participant_events.processing | The media object has started capturing |
| participant_events.done | The media object has successfully completed. All data for media objects on the recording is now available |
| participant_events.failed | The media object failed to be captured. The data.sub_code will contain machine readable code for the failure |
| participant_events.deleted | The media object has been deleted from Recall systems. |
