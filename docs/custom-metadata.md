---
title: "Custom MetadataMoon (Dark Mode)Sun (Light Mode)"
description: "Attach custom metadata to Recall resources"
source_file: "docs/custom-metadata.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:14.982Z"
api_parameters_count: "0"
---
You can attach custom metadata to [Recordings](/docs/recordings-and-media.md), [Media](/docs/recordings-and-media#media.md), and data sources (such as [Bots](/docs/bot-overview.md)) through their corresponding `metadata` field.

Any attached metadata will be present on the corresponding resource when fetched through the API, which can be useful for maintaining relationships with internal data models, or tagging resources with specific pieces of information.

**Example: Tag a Bot's Recording with an internal user ID:**

```
curl --request POST \
     --url https://us-east-1.recall.ai/api/v1/bot/ \
     --header 'Authorization: $RECALLAI_API_KEY' \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
  "recording_config": {
    "metadata": {
      "user_id": "12345"
    }
  }
}
'

```

The `metadata` will be available through the recording's `metadata` field (for instance, when calling [Retrieve Bot](/reference/bot_retrieve.md).

It will also be present when receiving a corresponding webhook. For instance, a Recording status change webhook:

```
{
  "event": "recording.done",
  "data": {
    "recording": {
      "id": string,
      "metadata": {
        "user_id": "12345"
      }
    },
    ...
  }
}

```
