---
title: "Slack Huddle Bots OverviewMoon (Dark Mode)Sun (Light Mode)"
description: "This section covers everything you need to know about Recall.ai’s Slack integration, from setting up the Slack app to capturing Slack Huddle data with bots and the Slack Huddle Bots. Seamlessly manage meetings, automate workflows, and power AI-driven applications within Slack. Why Slack Huddle Data ..."
source_file: "docs/slack-huddle-bots-overview.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:15.773Z"
api_parameters_count: "0"
---
This section covers everything you need to know about Recall.ai’s Slack integration, from setting up the Slack app to capturing Slack Huddle data with bots and the Slack Huddle Bots. Seamlessly manage meetings, automate workflows, and power AI-driven applications within Slack.

## Why Slack Huddle Data Matters

[](#why-slack-huddle-data-matters)

Slack Huddles are great for quick collaboration—like incident response, brainstorming, or daily syncs—but lack native tools to retain or retrieve data post-conversation. Recall.ai bridges this gap by providing bots to capture transcripts, recordings, speaker timelines, and participant events, enabling automation, analytics, and AI-powered insights.

The Slack Huddle bots lets developers programmatically access real-time Slack Huddle data—transcripts, recordings, and events—to build custom tools. Some popular use-cases include (but not limited to):
- **Incident Management**: Automate logs and track escalations
- **Workflow Automation**: Sync standup summaries to Jira or Asana
- **AI Applications**: Generate summaries or analyze sentiment with NLP

## Joining Behavior

[](#joining-behavior)

Slack enforces guidelines for bots in calls and conversations. Recall.ai bots manage joining and recording consent with flexible options:

1.  **Automatically Join Huddles (Public Channels)**
2.  **Automatically Join Huddles (Private Channels)**
3.  **Request to Join Huddles (Public Channels)** - Manually invite bot to join a huddle in a public channel
4.  **Request to Join Huddles (Private Channels)** - Manually invite bot to join a huddle in a public channel
5.  **Request to Join Private Huddles (Between Workspace Users)** - Manually invite bot to join a huddle in a private conversation

## Limitations

[](#limitations)
- Slack huddle bots can only join SSO-enabled workspaces as guests
- Slack Enterprise is currently not supported
- Bots will **not** be able to join workspaces with two-factor authentication required
