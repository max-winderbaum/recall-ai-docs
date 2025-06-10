---
title: "List Slack TeamsMoon (Dark Mode)Sun (Light Mode)"
description: "List all Slack Team Integrations This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/slack_teams_list.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:15.042Z"
api_parameters_count: "13"
---
## GET https://us-east-1.recall.ai/api/v2/slack-teams/

List all Slack Team Integrations This endpoint is rate limited to: 60 requests per min per workspace

> **CALLOUT**:

## 📘

Relevant Links

[Slack Huddles Overview](/docs/slack-huddles)

[Slack Bot Setup](/docs/slack-bot-setup)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes |  |
| email_address | string | Yes | The email address of the bot user. This is the email address that the customer will invite to their Slack workspace. |
| slack_team_domain | string | Yes | The domain of the Slack workspace that the bot user will be invited to. For instance "mycompany.slack.com". |
| bot_name | string | Yes | The name of the bot user. This is the name that will be displayed in Slack. |
| profile_photo_base64_jpg | string \| null | No | The profile photo of the bot user, encoded as a base64 string. This is the profile photo that will be displayed in Slack. This must be a 512x512px JPEG image. |
| auto_join_public_huddles | boolean | Yes | Whether the bot user should automatically join huddles occuring in public channels. |
| ask_to_join_private_huddles | boolean | Yes | Whether the bot user should ask to join huddles occuring in private channels. |
| ask_to_join_message | string | Yes | The message that the bot user will send when asking to join a private huddle. |
| filter_huddles_by_user_emails | array of strings \| null | No | A list of email addresses. If this is set, the bot user will only join huddles where one of the users is a participant of the huddle. |
| huddle_bot_config | object | Yes | The configuration of the bot to join a huddle. |
| status | string | Yes |  |
| updated_at | date-time | Yes |  |
| created_at | date-time | Yes |  |
