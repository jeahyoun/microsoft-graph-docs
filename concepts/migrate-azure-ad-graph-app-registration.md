---
title: "Review app registration, permissions, and consent migration issues"
description: "Describes app registration, permission, and consent migration from Azure Active Directory (Azure AD) to Microsoft Graph API."
author: "dkershaw10"
localization_priority: Normal
ms.prod: "microsoft-identity-platform"
---

# Review app registration, permissions, and consent

This article is part of *step 3: review app details* of the [process to migrate apps](migrate-azure-ad-graph-planning-checklist.md).

When migrating an app from Azure AD Graph to Microsoft Graph, you can continue to use your existing app registration and app permissions without any changes. Additionally your end-users can continue to use your app (after migration to Microsoft Graph) without being required to consent again.  

For any app update, there are three main areas of concern:

- **App registration**: You can continue to use your existing app registration (`appId`) in your application code.  

    You do **not** have to re-register your app to migrate to Microsoft Graph.  

    Simply update the code, test heavily, and then deploy your update.  

- **Permissions**: You can continue to use the existing configured permissions for your app. You do not have to request new permissions because Azure AD Graph permissions are shared with Microsoft Graph.

    For example, if your existing app has _User.Read.All_ and _Group.Read.All_ permissions, those permissions are implicitly granted to your updated app for Microsoft Graph as well.

    If your update also incudes the use of features or capabilities that aren't available to Azure AD Graph, you'll likely need to request permissions for these new features. If that's the case, you can switch your app to use MSAL and the v2 endpoint, and request additional/incremental consent dynamically. Find more details about switching to MSAL in [review app authentication library changes](/graph/migrate-azure-ad-graph-authentication-library).

- **Consent**: End-users can continue using your app without being asked to grant consent again.

    Users who have already granted consent to your app (to access theor data) can continue to use your app (even after you make the update to Microsoft Graph), without being asked to consent again.

Simple migration projects should experience no issues in these areas.

However, if you use new features, services, or add additional capabilities, you may need new permissions and end-user consent may be required.  In such cases, consent is requested when tokens are refreshed.

## Next Steps

- Learn [authentication library](migrate-azure-ad-graph-authentication-library.md) differences between Azure AD Graph and Microsoft Graph.
- Explore [Microsoft Graph](/graph/overview) concepts and practices.
- Use [Graph Explorer](https://aka.ms/ge) to experiment with Microsoft Graph.