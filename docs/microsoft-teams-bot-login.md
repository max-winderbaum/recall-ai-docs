---
title: "OverviewMoon (Dark Mode)Sun (Light Mode)"
description: "Sign-In your Teams bots into a Microsoft account."
source_file: "docs/microsoft-teams-bot-login.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:15.416Z"
api_parameters_count: "0"
---
By default the Teams bot will join meeting as an anonymous guest participant.

This means that, by default, MS Teams bots cannot join meetings which only allow signed in users or have [CAPTCHA enabled](https://learn.microsoft.com/en-us/microsoftteams/join-verification-check). If your bot is signed in to a Teams account and your domain is whitelisted by your customer's Teams tenant, your bot will be able to join calls without running into a CAPTCHA.

To overcome these limitations, you can configure your Teams bots to sign into a Microsoft account before joining a meeting.

# Important Considerations

[](#important-considerations)

There are some important things to be aware of when using Microsoft Teams bots:
- **The bot name *cannot* be overridden:** Signed in Teams bots get their name from the Teams account used to authenticate the bot, which overrides the `bot_name` parameter in [Create Bot](/reference/bot_create.md).
- **Signed in bots only work for [Business Microsoft Teams](https://recallai.readme.io/docs/personal-vs-business-ms-teams#business-ms-teams) meetings.**

> **CALLOUT**:

## ⚠️

Personal MS Teams not supported

Bots will fail to join Personal MS Teams links if mandatory login is enabled. While a vast majority of Teams meetings are using Business Teams, you should still be aware of this limitation if you have users that use the Personal version of MS teams.



# FAQ

[](#faq)
- * *

## Will the bot *always* sign into teams calls?

[](#will-the-bot-always-sign-into-teams-calls)

This behavior is configurable according to your use case.

When settings up the credentials in the Recall dashboard, you can toggle this behavior using the **Login mandatory** checkbox:

![Login mandatory checkbox
If turned on, the bot will **always** sign in before joining Teams calls.
Otherwise, the bot will only sign in if required by the meeting.](https://files.readme.io/222be2c1804a9f95726250d77bd04b85ea81a3afcc6dc4157642ccfe690c2c54-CleanShot_2024-10-24_at_08.42.37.png)

Login mandatory checkbox

If turned on, the bot will **always** sign in before joining Teams calls.
Otherwise, the bot will only sign in if required by the meeting.
