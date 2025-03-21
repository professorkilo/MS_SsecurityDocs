---
title: Protect APIs with registration, permissions, and consent
description: Learn best practices for protecting your API through registration, defining permissions and consent, and enforcing access to achieve your Zero Trust goals.
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.date: 02/24/2025
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to learn best practices for protecting my API through registration, defining permissions and consent, and enforcing access to achieve my Zero Trust goals.
---
# API Protection

When you, as a developer, protect your API, you focus on authorization. To call your resource's API, applications need to [acquire application authorization](acquire-application-authorization-to-access-resources.md). The resource enforces the authorization. In this article, you learn best practices to achieve your [Zero Trust](overview.md) goals. It describes how to protect your API through registration, permission and consent definition, and access enforcement.

## Register your protected API

To [protect your API with Microsoft Entra ID](/azure/api-management/api-management-howto-protect-backend-with-aad) (Microsoft Entra ID), [register your API](/entra/identity-platform/scenario-protected-web-api-app-registration). Then you can [manage your registered APIs](/entra/identity-platform/app-objects-and-service-principals). In Microsoft Entra ID, an API is an app with specific app registration settings that define it as a resource or API that another application can access. In the **Microsoft Entra admin center**, **Microsoft Identity Developer**, **App registrations** are APIs that are in the tenant either as line of business APIs or services from Software-as-a-Servcie (SaaS) providers that have APIs that Microsoft Entra ID protects.

During registration, you define how calling applications reference your API and its [delegated](developer-strategy-delegated-permission.md) and [application permissions](developer-strategy-application-permissions.md). An app registration can represent a solution that has both client applications and APIs. However, in this article, we address the scenario where a standalone resource exposes an API.

Normally, an API doesn't perform authentication or directly ask for authorization. The API validates a token that the calling app presents. APIs don't have interactive sign-ins, so you don't need to register settings such as redirect URI or application type. APIs get their tokens from the applications that are calling those APIs, not by interacting with Microsoft Entra ID. For web APIs, use OAuth2 [access tokens](/entra/identity-platform/access-tokens) for authorization. Web APIs validate bearer tokens to authorize callers. Don't accept [ID tokens](/entra/identity-platform/id-tokens) as a proof of permission.

By default, Microsoft Entra ID adds `User.Read` to the API permissions of any new app registration. You remove this permission for most [web APIs](/entra/identity-platform/scenario-protected-web-api-app-registration). Microsoft Entra ID requires API permissions only when an API calls another API. If your API doesn't call another API, remove the `User.Read` permission when you register your API.

You need a unique identifier for your API, known as the [Application ID URI](/entra/identity-platform/scenario-protected-web-api-app-registration#scopes-and-the-application-id-uri), that client apps that need to access your API asks for permission to call your API. The Application ID URI needs to be unique across all Microsoft Entra tenants. You can use `api://<clientId>`​ (the default suggestion in the portal) where `<clientId>` is the Application ID of your registered API.

To provide developers who are calling your API with a more user-friendly name, you can use your API's address as your Application ID URI. For example, you can use `https://API.yourdomain.com` where `yourdomain.com` is a configured publisher domain in your Microsoft Entra tenant. Microsoft validates that you have ownership of the domain so that you can use it as the unique identifier for your API. You don't need to have code at this address. The API can be wherever you want it to be, but it's a good practice to use the `https` address of the API as the Application ID URI.

## Define delegated permissions with least privilege

If applications that have users are going to call your API, define at least one delegated permission (see [Add a scope](/entra/identity-platform/quickstart-configure-app-expose-web-apis#add-a-scope) on the app registration **Expose an API**).

APIs that provide access to organization data stores can attract the attention of bad actors who want to access that data. Instead of having only one delegated permission, design your permissions with the Zero Trust principle of [least privilege access](/entra/identity-platform/secure-least-privileged-access) in mind. It can be difficult to get into a least privileged model later if all client apps start with full privileged access.

Often, developers fall into a pattern of using a single permission like *access as user* or *user impersonation* (which is a common technically inaccurate phrase). Single permissions like these only allow full privileged access to your API.

Declare least privilege scopes so that your applications aren't vulnerable to compromise or used to perform a task that you never intended. Define your multiple scopes in [**API Permissions**](/entra/identity-platform/quickstart-configure-app-access-web-apis#add-permissions-to-access-your-web-api). For example, separate scopes from reading and updating data and consider offering read-only permissions. *Write access* includes privileges for create, update, and delete operations. A client should never require write access to only read data.

Consider *standard* and *full* access permissions when your API works with sensitive data. Restrict the sensitive properties so that a standard permission doesn't allow access (for example, `Resource.Read`). Then implement a *full* access permission (for example, `Resource.ReadFull`) that returns properties and sensitive information.

Always evaluate permissions that you request to ensure that you seek the absolute least privileged set to get the job done. Avoid requesting higher privilege permissions. Instead, create an individual permission for each core scenario. Refer to [Microsoft Graph permissions reference](/graph/permissions-reference) for good examples of this approach. Locate and use just the right number of permissions to address your needs.

## Define user consent and admin consent

As part of your scope definitions, decide whether the range of operation that can be performed with a particular scope [requires admin consent](permissions-require-admin-consent.md).

As the API designer, you can provide guidance on which scopes can safely require only user consent. However, tenant admins can configure a tenant so that all permissions require admin consent. If you define a scope as requiring admin consent, the permission always requires admin consent.

When you decide upon user or admin consent, you have these primary considerations:

- **Whether the range of operations behind the permission affect more than a single user.** If permission allows the user to choose which application can access only their own information, then user consent might be appropriate. For example, the user can consent to choosing their preferred application for email. However, if the operations behind the permission involve more than a single user (such as viewing full user profiles of other users), then define that permission as requiring admin consent.

- **Whether the range of operations behind the permission have a broad scope.** For example, a broad scope is when a permission enables an app to change everything in a tenant or to do something that might be irreversible. A broad scope indicates that you require admin consent rather than user consent.

Err on the conservative side and require admin consent if you're in doubt. Clearly and concisely describe the consequences of consent in your permission strings. Assume that the individual reading your description strings has no familiarity with your APIs or product.

Avoid adding your APIs to existing permissions in a way that changes the semantics of the permission. Overloading existing permissions dilutes the reasoning upon which clients previously granted consent.

## Define application permissions

When you build [nonuser applications](identity-non-user-applications.md), you don't have a user whom you can prompt for a username and password or Multifactor Authentication (MFA). If applications without users (such as workloads, services, and daemons) call your API, define [application permissions](developer-strategy-application-permissions.md) for your API. When you define an application permission, use an [application role](/entra/identity-platform/howto-add-app-roles-in-apps) instead of using scopes.

As with delegated permissions, you provide granular application permissions so that workloads that call your API can follow least privilege access and align with Zero Trust principles. Avoid publishing just one app role (app permission) and one scope (delegated permission) or exposing all operations to each client.

Workloads authenticate with [client credentials](/entra/identity-platform/v2-oauth2-client-creds-grant-flow) and request a token with the [`.default` scope](/entra/identity-platform/permissions-consent-overview#client-credentials-grant-flow-and-default) as demonstrated in the following example code.

```javascript
// With client credentials flows the scopes is ALWAYS of the shape "resource/.default", as the 
// application permissions need to be set statically (in the portal or by PowerShell), 
// and then granted by a tenant administrator
string[] scopes = new string[] { "https://kkaad.onmicrosoft.com/webapi/.default" };
 
AuthenticationResult result = null;
try
{
  result = await app.AcquireTokenForClient(scopes)
    .ExecuteAsync();
  Console.WriteLine("Token acquired \n");
}
catch (MsalServiceException ex) when (ex.Message.Contains("AADSTS70011"))
{
  // Invalid scope. The scope has to be of the form "https://resourceurl/.default"
  // Mitigation: change the scope to be as expected
  Console.WriteLine("Scope provided is not supported");
}
```

Permissions require admin consent when there's no user in front of the app and when the application permission enables a broad range of operations.

## Enforce access

Ensure that your APIs enforce access by validating and interpreting access tokens that calling applications provide as bearer tokens in the `https` request's authorization header. Enforce access by validating tokens, managing metadata refresh, and enforcing scopes and roles as described in the following sections.

### Validate tokens

After your API receives a token, ensure that it [validates the token](/entra/identity-platform/access-tokens#validate-tokens). Validation ensures that the token comes from the proper issuer as untampered and unmodified. Check the signature because you don't get the token directly from Microsoft Entra ID as you do with ID tokens. Validate the signature after your API receives a token from an untrusted source on the network.

Because there are known vulnerabilities around JSON web token signature verification, use a well-maintained and established standard token validation library. Authentication libraries (such as [Microsoft.Identity.Web](/entra/msal/dotnet/microsoft-identity-web/)) use the proper steps and mitigate for known vulnerabilities.

Optionally, [extend token validation](https://github.com/Azure-Samples/active-directory-dotnet-webapi-manual-jwt-validation/blob/master/README.md). Use the tenant ID (`tid`) claim to restrict the tenants in which your API can obtain a token. Use the `azp` and `appid` claims to filter apps that can call your API. Use the object ID (`oid`) claim to further narrow down access to individual users.

### Manage metadata refresh

Always ensure that your token validation library effectively manages the required metadata. In this case, the metadata are the public keys, the pair of private keys, that Microsoft uses to sign Microsoft Entra tokens. When your libraries validate these tokens, they get our published list of public signing keys from a well-known internet address. Ensure that the hosting environment has the right timing to get those keys.

For example, older libraries were occasionally hard coded to update those public signing keys every 24 hours. Consider when Microsoft Entra ID has to quickly rotate those keys and the keys that you downloaded didn't include the new rotated keys. Your API could be offline for a day while it waits for its metadata refresh cycle. Reference [specific metadata refresh guidance](/entra/identity-platform/howto-build-services-resilient-to-metadata-refresh) to ensure that you properly get the metadata. If you're using a library, ensure that it treats that metadata within reasonable timing.

### Enforce scopes and roles

After you validate your token, your API looks at the claims in the token to determine how it should work.

For delegated permission tokens, have your API inspect the scope (`scp`) claim to see what the application has consent to do. Inspect the object ID (`oid`) or subject key (`sub`) claims to see the user on whose behalf the application is working.

Then have your API check to ensure that the user also has access to the requested operation. If your API defines [roles for assigning to users and groups](configure-tokens-group-claims-app-roles.md), have your API check for any roles claims in the token and behave accordingly. Application permission tokens don't have a scope (`scp`) claim. Instead, have your API inspect the roles claim to determine which application permissions the workload received.

After your API validates the token and scopes and processes the object ID (`oid`), subject key (`sub`), and roles claims, your API can return the results.

## Next steps

- [Example of API protected by Microsoft identity consent framework](protected-api-example.md) helps you to design least privilege application permissions strategies for the best user experience.
- [Call an API from another API](api-calls-api.md) helps you to ensure Zero Trust when you have one API that needs to call another API and securely develop your application when it's working on behalf of a user.
- [Customize tokens](zero-trust-token-customization.md) describes the information that you can receive in Microsoft Entra tokens. It explains how to customize tokens to improve flexibility and control while increasing application Zero Trust security with least privilege.
- [Configure group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) shows you how to configure your apps with app role definitions and assign security groups to app roles. These methods help to improve flexibility and control while increasing application Zero Trust security with least privilege.
- [Acquire authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
- [Request permissions that require administrative consent](permissions-require-admin-consent.md) describes the permission and consent experience when application permissions require administrative consent.
- In this [Quickstart: Protect a web API with the Microsoft identity platform](/entra/identity-platform/index-web-api), learn how to protect an ASP.NET web API by restricting access to its resources to authorized accounts only.
- In this [Tutorial - Transform and protect your API in Azure API Management](/azure/api-management/transform-api), learn about configuring common policies to hide the technology stack info or the original URLs in API's HTTP response.
