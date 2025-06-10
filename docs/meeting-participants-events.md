---
title: "Meeting Participants & EventsMoon (Dark Mode)Sun (Light Mode)"
description: "Most recordings typically have associated meeting participants and participant events. Recall.ai's API exposes these through a variety of endpoints outlined below. Participants Recall.ai records and exposes participants for recordings automatically, so no configuration is needed. Retrieving Particip..."
source_file: "docs/meeting-participants-events.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:47:11.295Z"
api_parameters_count: "0"
---
Most recordings typically have associated meeting participants and participant events. Recall.ai's API exposes these through a variety of endpoints outlined below.

# Participants

[](#participants)
- * *

Recall.ai records and exposes participants for recordings automatically, so no configuration is needed.

## Retrieving Participants

[](#retrieving-participants)

The response schema can be found at [Participants Download Schema](/docs/download-urls#json-participant-download-url.md).

### Retrieve participants for a bot

[](#retrieve-participants-for-a-bot)

After calling the [Retrieve Bot](/reference/bot_retrieve.md) endpoint, the `recordings` in the response will contain a `media_shortcuts` object.

In this object, you can download the participants by accessing the `participant_events.data.participants_download_url`:

```
{
  "recordings": [
    {
      "id": "a5437136-4b69-429a-9e0c-cd388fd8fee6",
      ...
      "participant_events": {
        "id": "a7ae9238-0e2d-40f2-8480-8e9c0cf3af6c",
        "data": {
          "participants_download_url": "https://us-east-1.recall.ai/api/v1/download/participants?token=eyJpZCI6ImE3YWU5MjM4LTBlMmQtNDBmMi04NDgwLThlOWMwY2YzYWY2YyJ9%3A1tOqjv%3AapjfmYtSltJrroNgtl0RORSrwP-Q03ErOq7VymGbwuY",
          ...
        }
      },
    }
  ],
  ...
]

```

### Retrieve participants for a recording

[](#retrieve-participants-for-a-recording)

To retrieve a given recording's list of participants, you can call the [List Participant Events](/reference/participant_events_list.md) endpoint, using the bot's corresponding recording ID:

cURL

```
curl --request GET \
     --url https://us-east-1.recall.ai/api/v1/participant_events?recording_id=RECORDING_ID \
     --header "Authorization: $RECALLAI_API_KEY" \
     --header "accept: application/json"

```

*Example Response:*

JSON

```
{
  "next": "...", // URL pre-filled with params/cursor value to fetch the next page
  "previous": "...",
  "results": [
    {
      id: "...",
      // ...
      data: {
	      participant_events_download_url: '...',
				speaker_timeline_download_url: '...',
				participants_download_url: '...'
      }
    }
  ]
}

```

Then you can query the `participants_download_url` and you will receive the data in JSON format as seen in [this schema](/docs/download-schemas#json-participant-download-url.md)

# Participant Events

[](#participant-events)
- * *

Recall.ai exposes participant events as an artifact of a recording.

## Configuration

[](#configuration)

To configure a bot to record participant events, no configuration is needed, since the default is to generate this artifact.

You can also explicitly set this by providing an `participant_events` object in your [Create Bot](/reference/bot_create.md) request's `recording_config`:

CSS

```
curl --request POST \
     --url https://us-east-1.recall.ai/api/v1/bot/ \
		 --header "authorization: $RECALLAI_API_KEY"
     --header "accept: application/json" \
     --header "content-type: application/json" \
     --data '
{
  "meeting_url": "https://meet.google.com/ggt-kpdk-mrj",
  "recording_config": {
    "participant_events": {}
  }
}
'

```

## Retrieving Events

[](#retrieving-events)

To retrieve a bot's participant events, you can call the [Retrieve Bot](/reference/bot_retrieve.md) and access the `media_shorcuts.participant_events.data.participant_events_download_url` in the recording object.

The response schema can be found [Download URL Schemas: Participant Events](/docs/download-urls#json-participant-event-download-url.md).

To retrieve all participant events for a specific **recording**, use the [List Participant Events](/reference/participant_events_list.md) endpoint while specifying a `recording_id`:

```
curl --request GET \
     --url 'https://us-east-1.recall.ai/api/v1/participant_events/?recording_id={RECORDING_ID}' \
     --header "Authorization: $RECALLAI_API_KEY" \
     --header "accept: application/json"

```

*Example response*

JSON

```
{
  "next": "...",
  "previous": "...",
  "results": [
    {
      "id": "9aa74189-92d0-410a-b247-4239e42c2465",
      "recording_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "created_at": "2024-12-01T21:29:51.019Z",
      "status": {
        "code": "string",
        "sub_code": "string",
        "updated_at": "2024-12-01T21:29:51.019Z"
      },
      "metadata": {},
      "data": {
        "participant_events_download_url": "https://...",
        "speaker_timeline_download_url": "https://...",
        "participants_download_url": "https://..."
      }
    }
  ]
}

```

The `data.download_url` will be populated with a pre-signed URL where you can download the entire artifact's contents.



# FAQ

[](#faq)
- * *

## Can I get participant emails from the bot?

[](#can-i-get-participant-emails-from-the-bot)

Meeting platforms don't expose participant emails for security reasons, so bots aren't able to capture participant emails just by being present in the call.

To map participants to their corresponding email addresses, you can use the [Recall Calendar Integration](/docs/calendar-integration.md), or implement a calendar integration of your own.
