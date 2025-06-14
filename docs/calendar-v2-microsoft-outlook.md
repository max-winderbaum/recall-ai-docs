---
title: "Microsoft OutlookMoon (Dark Mode)Sun (Light Mode)"
description: "Setup OAuth 2.0 Client Register Microsoft OAuth App. More info on this here https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app . Choose Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xb..."
source_file: "docs/calendar-v2-microsoft-outlook.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:14.945Z"
api_parameters_count: "0"
---
# Setup OAuth 2.0 Client

[](#setup-oauth-20-client)

1.  Register Microsoft OAuth App. More info on this here [https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app). Choose **Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)** as **Supported Account Type** option. Copy **Application (client) ID** (`CLIENT_ID`) value.
2.  Configure platform settings for the app, choose "Web" as the platform type. Add a redirect uri. You should be able to verify ownership of this domain in order publish to production.
3.  Create a new client secret for the application. Copy the secret value(`CLIENT_SECRET`) as this will be needed in a later step.
4.  Configure permissions `Calendars.Read` API permission.

# Implement OAuth 2.0 Authorization Code Flow

[](#implement-oauth-20-authorization-code-flow)

[https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow#redeem-a-code-for-an-access-token](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow#redeem-a-code-for-an-access-token)

Code samples from Calendar V2 Demo Repository:
- [https://github.com/recallai/calendar-integration-demo/blob/v2/v2-demo/logic/oauth.js#L21](https://github.com/recallai/calendar-integration-demo/blob/v2/v2-demo/logic/oauth.js#L21)
- [https://github.com/recallai/calendar-integration-demo/blob/v2/v2-demo/routes/oauth-callback/microsoft-outlook.js#L27](https://github.com/recallai/calendar-integration-demo/blob/v2/v2-demo/routes/oauth-callback/microsoft-outlook.js#L27)
