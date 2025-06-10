---
title: "Zoom App Submission: Required URL'sMoon (Dark Mode)Sun (Light Mode)"
description: "Required URL's for your Zoom SDK App submission."
source_file: "docs/zoom-app-submission-required-urls.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:00:12.245Z"
api_parameters_count: "0"
---
As part of your Zoom app submission, you must provide several URL's that provide information, instructions, and support for your app.

While some are optional, most of these links are required and must follow Zoom's guidelines in order for your app submission to be approved.

> **CALLOUT**:

## 🤝

Important

These URL's are **essential** for getting your Zoom app approved.

Failing to follow these instructions or provide proper links will result in app rejection and increase the time for your Zoom app to get approved.

## Privacy Policy

[](#privacy-policy)

Provide the URL to your app’s Privacy Policy that must comply with applicable laws and regulations and that clarify how you collect, use, share, retain and otherwise process personal information.

*[Learn More](https://developers.zoom.us/docs/distribute/app-submission/submission-checklist/#4-provide-a-privacy-policy-url)*

## Terms of Use

[](#terms-of-use)

Provide the URL for your app’s Terms of Use agreement.

*[Learn More](https://developers.zoom.us/docs/distribute/app-submission/submission-checklist/#5-provide-a-terms-of-use-url)*

## Support

[](#support)

This should **at the very least** include an email to get in contact with your team for support. Ideally, this would include more.

Zoom suggests to include a combination of the following:
- Link to create a support case
- Link to email support
- Link to your KB/Forums
- Link to your Zoom IM - Live Customer Support Channel (if available)
- Support Phone Number (if available)
- Description of what customers can expect when engaging your support team, such as:
- Hours of Your Support Team (if not follow-the-sun)
- 1st Response SLA (Maximum time a customer should expect to wait until they receive their 1st HUMAN response from your Customer Support Team)

[*Learn More*](https://developers.zoom.us/docs/distribute/app-submission/submission-checklist/#6-provide-a-support-url)

## Documentation

[](#documentation)

Your documentation page should clearly demonstrate how to use your product, as well as how to get started with it and remove it from their Zoom account.

This page must include:

1.  **Usage**: How a user would use your app (e.g. how to record meetings, see recordings, other app features)
    1.  Importantly, this should highlight how a user uses your product to send a bot to a Zoom call
2.  **Installation**: How to install your app and get started
3.  **Uninstallation**: How to remove your app and revoke permissions
4.  (Optional - Highly recommended) **Troubleshooting**: Common problems users run into when using your app and how to resolve them.
5.  (Optional - Highly recommended) **FAQ**: Frequently asked questions about your app - Installation, Uninstallation, Usage, Email preferences, etc.

For more information, please see Zoom's [*Detailed Instructions for Documentation Pages*](https://drive.google.com/file/d/1P5Hsq52Z0qIv6z_BzGNewvEHnBa23cKe/view).

### Usage

[](#usage)

The usage page should clearly demonstrate how a user actually interacts with your application.

For instance, if you app allows users to send bots to meetings by providing a meeting URL, you should include information on where and how they would do this.

### Installation

[](#installation)

If you're *not* using the Zoom OAuth integration, this can simply be:

**No installation is required.**

If you **are** using the Zoom OAuth integration this should be a few bullet points walking through where and how your user can grant OAuth permissions to your application.

### Uninstallation

[](#uninstallation)

If you're *not* using the Zoom OAuth integration, this can simply be:

**No uninstallation is required.**

If you **are** using Zoom OAuth, this should be instructions on how to deauthorize your app.

Since all Zoom apps are removed the same way, this is typically something like:

1.  Login to your Zoom Account and navigate to the Zoom App Marketplace
2.  Click Manage > Installed Apps, or search for the {YOUR\_APP\_NAME} app.
3.  Click on the {YOUR\_APP\_NAME} app.
4.  Click uninstall.

*Note: If you're using the Calendar integration, this should include instructions on how to disconnect your calendar.*

## Direct Landing Page

[](#direct-landing-page)

Provide a URL link to add the app from the app's landing page.

This is the URL that Zoom users will be redirected to when adding your app:

![](https://files.readme.io/a469c4a-CleanShot_2024-02-12_at_12.12.01.png)

*For example, a signup page or your home page.*

## Deauthorization Endpoint URL

[](#deauthorization-endpoint-url)

When a user removes your app, Zoom will send a webhook event to this URL to notify you that the user has removed your app.

![](https://files.readme.io/bbaacf4-CleanShot_2024-02-12_at_11.43.42.png)

What you put here depends on whether or not you're using the Recall Zoom OAuth integration.

### Not using OAuth

[](#not-using-oauth)

If you're not using the Zoom OAuth integration, **you can simply put your application's home page.**

### Using OAuth

[](#using-oauth)

If your Zoom app uses OAuth, you should put the same Recall webhook URL you used when setting up the Recall Zoom OAuth integration:

`https://us-east-1.recall.ai/api/v2/zoom-oauth-apps/{RECALL_ZOOM_OAUTH_APP_ID}/webhook`

Where `RECALL_ZOOM_OAUTH_APP_ID` is the ID of your [Zoom OAuth App](/reference/zoom_oauth_apps_list) in Recall.
