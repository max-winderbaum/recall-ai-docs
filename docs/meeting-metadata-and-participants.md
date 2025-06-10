---
title: "Meeting MetadataMoon (Dark Mode)Sun (Light Mode)"
description: "Recall.ai exposes metadata for a given meeting as media object on a recording. Examples of meeting metadata include meeting title and unique identifiers, though the specific metadata available depends on the platform. Configuration To configure a bot to record meeting metadata, provide a meeting_met..."
source_file: "docs/meeting-metadata-and-participants.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:00:11.669Z"
api_parameters_count: "0"
---
Recall.ai exposes metadata for a given meeting as media object on a recording.

Examples of meeting metadata include meeting title and unique identifiers, though the specific metadata available depends on the platform.

# Configuration

[](#configuration)

To configure a bot to record meeting metadata, provide a `meeting_metadata` object in your [Create Bot](/reference/bot_create) request's `recording_config`:

cURL

```
curl --request POST \
     --url https://us-east-1.recall.ai/api/v1/bot/ \
     --header "Authorization: $RECALLAI_API_KEY" \
     --header "accept: application/json" \
     --header "content-type: application/json" \
     --data '
{
  "meeting_url": "https://meet.google.com/gtt-vjsi-jhj",
  "recording_config": {
    "meeting_metadata": {}
  }
}
'

```

# Retrieving Meeting Metadata

[](#retrieving-meeting-metadata)

**Platform Support**

| Platform | Supported? |  |
| --- | --- | --- |
| Zoom | ✅ |  |
| Google Meet | ⚠️ | Only works if:- Bot is signed- Bot is a participant on the calendar event- Calendar event's end time is in the future |
| Microsoft Teams | ❌ |  |
| Cisco Webex | ❌ |  |
| Slack Huddles | ✅ |  |

To retrieve meeting metadata for a recording, you can either:
- Call [Retrieve Bot](/reference/bot_retrieve) and access the metadata in `shortcuts.meeting_metadata.data` in the recording object
- Call [Retrieve Meeting Metadata](/reference/meeting_metadata_retrieve), using the ID of the meeting metadata artifact
- Call [List Meeting Metadata](/reference/meeting_metadata_list), filtering to a specific recording ID



### Google Meets

[](#google-meets)

The Microsoft Teams title will only be populated if the bot is signed in and the bots email on the calendar meeting invite

JSON

```
{
  "data": {
      "title": "John Smith's Personal Meeting Room",
    },
  },
  ...
}

```

### Zoom

[](#zoom)

JSON

```
{
  "data": {
      "title": "John Smith's Personal Meeting Room",
      "zoom_meeting_uuid": "x7OAB2GkQmFZuNhAY+nTNg=="
    },
  },
  ...
}

```

### Slack Huddles

[](#slack-huddles)

JSON

```
{
  "data": {
      "huddle_id": "...",
      "channel_id": "..."
    },
  },
  ...
}

```
