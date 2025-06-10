---
title: "Sending Chat MessagesMoon (Dark Mode)Sun (Light Mode)"
description: "Platform Support Platform Available Supported Recipients Limitations Zoom ✅ everyone , host , everyone_except_host 4096 character limit Google Meet ✅ everyone 500 character limit Microsoft Teams ✅ everyone 4096 character limit Slack Huddles ✅ everyone Cisco Webex ❌ 📘 Note about Microsoft Teams: The..."
source_file: "docs/chat-messages.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:14.966Z"
api_parameters_count: "0"
---
# Platform Support

[](#platform-support)

| Platform | Available | Supported Recipients | Limitations |
| --- | --- | --- | --- |
| Zoom | ✅ | everyone, host, everyone_except_host | 4096 character limit |
| Google Meet | ✅ | everyone | 500 character limit |
| Microsoft Teams | ✅ | everyone | 4096 character limit |
| Slack Huddles | ✅ | everyone |  |
| Cisco Webex | ❌ |  |  |

> **CALLOUT**:

## 📘

Note about Microsoft Teams

The Teams chat window may not be available for bots by default, due to the organization's settings.

For bots to be able to send chat messages in Teams calls, they must have access to the chat. To have access to the chat, one of two things must happen:

1.  The tenant has configured their meeting chat settings to allow **anyone** to chat.
2.  The tenant allows authenticated users to chat **and** you're using [Signed-In Microsoft Teams Bots](/docs/microsoft-teams-bot-login.md).

# How to send chat messages

[](#how-to-send-chat-messages)

There are two ways to have bots send chat messages:

1.  **Providing an automatic chat configuration when [Creating a Bot](/reference/bot_create.md)**
2.  **Calling the [Send Chat Message](/reference/bot_send_chat_message_create.md) endpoint**

## Providing an automatic chat configuration

[](#providing-an-automatic-chat-configuration)
- * *

When creating a bot, you can provide a `chat` object in the [Create Bot](/reference/bot_create.md) request body with two parameters that act as hooks for automatically sending chat messages:
- `on_bot_join`
- `on_participant_join`

*Note that you can provide one without the other, or both if you prefer.*

### **Send a message when the bot joins: `chat.on_bot_join`**

[](#send-a-message-when-the-bot-joins-chaton_bot_join)

| Parameter | Value | Description |
| --- | --- | --- |
| send_to | Zoom: "host" | "everyone" |"everyone_except_host"Meet: "everyone"Teams: "everyone" | Who the message will be sent to. |
| message | string | The message content to send. |

### **Send a message when a participant joins the call: `chat.on_participant_join`**

[](#send-a-message-when-a-participant-joins-the-call-chaton_participant_join)

| Parameter | Value | Description |
| --- | --- | --- |
| exclude_host | boolean | Whether or not to trigger this message when the host joins. |
| message | string | The message content to send. |

## Using the Send Chat Messages endpoint

[](#using-the-send-chat-messages-endpoint)
- * *

For more control over when bots send chat messages, Recall also provides an [endpoint](/reference/bot_send_chat_message_create.md) to send chat messages.

Keep in mind that this endpoint has the same [platform limitations](#platform-limitations) outlined above.

### Send a chat message to a specific participant (Zoom only)

[](#send-a-chat-message-to-a-specific-participant-zoom-only)

Using the [Send Chat Message](/reference/bot_send_chat_message_create.md) endpoint also has the benefit of being able to send chat messages as DM's to specific participants.

**Example: Send a message via DM to a specific Zoom participant**

1.  First, you need the ID of the participant you'd like to send the DM to. For example, you can get this from the `meeting_participants` array in the [Retrieve Bot](/reference/bot_retrieve.md) response:

    JSON

    ```
    "meeting_participants": [
          {
            "id": 16778240,
            "name": "John Doe",
            "events": [
              {
                "code": "join",
                "created_at": "2024-03-26T20:10:56.499605Z"
              }
            ],
            "is_host": true,
            "platform": "desktop",
    				...
          },
          ...
        ],

    ```

2.  Now, to send a DM to John Doe, I can use his ID when calling [Send Chat Message](/reference/bot_send_chat_message_create.md):

    cURL

    ```
    curl --request POST \
         --url https://us-east-1.recall.ai/api/v1/bot/3487f343-7ba6-4fe1-9462-08638b2ee51f/send_chat_message/ \
         --header 'Authorization: {TOKEN}' \
         --header 'accept: application/json' \
         --header 'content-type: application/json' \
         --data '
    {
      "to": "16778240",
      "message": "Hello! I am a virtual meeting assistant that will be taking notes during this call."
    }
    '

    ```

3.  The participant will then receive the message as a DM:

    ![](https://files.readme.io/5bfa387-CleanShot_2024-03-26_at_13.16.49.png)




## Sending formatted chat messages

[](#sending-formatted-chat-messages)
- * *

Teams supports sending hyperlinks in the chat using the following format: `<a href="https://example.com/">Example</a>`

Formatted chat messages are not supported for other meeting platforms at this time.
