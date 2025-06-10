---
title: "Organization ManagementMoon (Dark Mode)Sun (Light Mode)"
description: "You can manage your organization's users and workspaces in the User Management page of the Recall dashboard. 📘 View the User Management Dashboard: (US) us-east-1 (Pay-as-you-go) us-west-2 (EU) eu-central-1 (JP) ap-northeast-1 Roles Organization-wide roles determine what actions users can perform: R..."
source_file: "docs/environments.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:47:11.043Z"
api_parameters_count: "0"
---
You can manage your organization's users and workspaces in the User Management page of the Recall dashboard.

> **CALLOUT**:

## 📘

View the User Management Dashboard
- [(US) us-east-1](https://us-east-1.recall.ai/dashboard/team)
- [(Pay-as-you-go) us-west-2](https://us-west-2.recall.ai/dashboard/team)
- [(EU) eu-central-1](https://eu-central-1.recall.ai/dashboard/team)
- [(JP) ap-northeast-1](https://ap-northeast-1.recall.ai/dashboard/team)

# Roles

[](#roles)

Organization-wide roles determine what actions users can perform:

| Role | Description |
| --- | --- |
| Developer | Able to access the dashboard and create API keys. |
| Admin | All the privileges of the "Developer" role. Can also create new workspaces, invite new users, and manage the permissions of other users. |

# User Management

[](#user-management)

Users can join multiple workspaces in your organization. This allows a single user to have their own development environment while also having access to staging and production environments if desired.

As an admin, you can delegate workspace access for the other users in your workspace.

# Workspaces

[](#workspaces)

You may want to have multiple workspaces to separate different projects, teams, or environments. Each workspace operates independently, with its own settings, users, and API keys.

If you're an Admin in your organization, you can create new workspaces from the Workspace Management page. Users without this role cannot access this page.

# Billing

[](#billing)

You **do not** have to pay an additional platform fee or other fee in order to use multiple environments.

Any usage will be consolidated under the same billing account as your production credentials.

# FAQs

[](#faqs)

## How do I manage dedicated environments?

[](#how-do-i-manage-dedicated-environments)

You can create a separate workspace per environment in the Recall dashboard. All data is scoped at the workspace level (i.e. bot data, webhook urls, calendars, platform credentials, transcription credentials, etc.) so a separate workspace will ensure the data/configs will be isolated to your environment
