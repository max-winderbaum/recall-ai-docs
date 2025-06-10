---
title: "Microsoft Teams: FAQMoon (Dark Mode)Sun (Light Mode)"
description: "Frequently asked questions: Microsoft Teams bots"
source_file: "docs/microsoft-teams-bots-faq.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:00:11.725Z"
api_parameters_count: "0"
---
## Why does the bot have Unverified after the name?

[](#why-does-the-bot-have-unverified-after-the-name)

Microsoft released an [update](https://learn.microsoft.com/en-us/answers/questions/1534900/unverified-text-is-appearing-next-to-the-acs-user) February 2024 that affects how Teams participants are displayed depending on their account's relationship with the organization.

This only affects the new version of teams (teams.microsoft.com), and is not applicable for the old version (teams.live.com).

Below is a summary of these changes:

> **No label:** All participants who are part of the organizer’s organization.
>
> **External:** All participants who are external to the organizer’s organization but have a trusted relationship with the organizer or their organization.
>
> **Unverified:** All other participants will be seen with this label. This will include Microsoft Entra ID users who belong to organizations that do not have an explicit external access setup with the organizer’s organization, Microsoft Account (personal) users, users who are not using any Microsoft ID while joining meetings, and others.

This means that, by default, bot that join a Teams meetings hosted at teams.microsoft.com will have the `Unverified` suffix.

**How to remove the unverified tag**

If you wish to remove this tag in favor of the `(External)` tag, you can authenticate Teams bots as outlined in [Microsoft Teams Bot Login](/docs/microsoft-teams-bot-login-getting-started).

Microsoft Tenants can specify trusted organizations by following [these steps](https://learn.microsoft.com/en-us/microsoftteams/trusted-organizations-external-meetings-chat?tabs=organization-settings).
