# Manage custom polices in Azure AD B2C using Graph API

This is a sample command line tool that demonstrates managing custom trust framework policies (custom policy for short) in an Azure AD B2C tenant.  [Custom policy](https://docs.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-overview-custom) allows you to customize every aspect of the authentication flow.

## Features

This sample demonstrates the following:

* **Create** a custom policy
* **Read** details of a custom policy
* **Update** a custom policy
* **Delete** a custom policy
* **List** all custom policies

## Getting Started

### Prerequisites

This sample requires the following:

* Request access to the private preview.  This API is in private preview and must be enabled for your test tenant.  Please contact [AADB2CPreview@microsoft.com](mailto:AADB2CPreview@microsoft.com) with the name of your test tenant and 'custom policy APIs' in the title of your email.  This feature is not yet ready for production tenants.
* [Visual Studio](https://www.visualstudio.com/en-us/downloads)
* [Azure AD B2C tenant](https://docs.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-get-started)

### Quickstart

#### Create global administrator

* An global administrator account is required to run admin-level operations and to consent to application permissions.  (for example: admin@myb2ctenant.onmicrosoft.com)

#### Register the delegated permissions application

1. Sign in to the [Application Registration Portal](https://apps.dev.microsoft.com/) using your Microsoft account.
1. Select **Add an app**, and enter a friendly name for the application (such as **Console App for Microsoft Graph (Delegated perms)**). Click **Create**.
1. On the application registration page, select **Add Platform**. Select the **Native App** tile and save your change. The **delegated permissions** operations in this sample use permissions that are specified in the AuthenticationHelper.cs file. This is why you don't need to assign any permissions to the app on this page.
1. Open the solution and then the Constants.cs file in Visual Studio. 
1. Make the **Application Id** value for this app the value of the **ClientIdForUserAuthn** string.
1. Update **Tenant** with the name of your tenant.  (for example: myb2ctenantname.onmicrosoft.com)

#### Build and run the sample

1. Open the sample solution in Visual Studio.
1. Replace the tenant name and application id in Constants.cs by following [Register the delegated permissions application](#register-the-delegated-permissions-application)
1. Press F5 to build and run the sample. This will restore the NuGet package dependencies and open the console application.
1. Sign in as a global administrator.  (for example: admin@myb2ctenant.onmicrosoft.com)
1. The output will show the results of calling the Graph API for trustFrameworkPolices.

>[!NOTE]
> If you see `Unauthorized. Access to this Api requires feature: EnableIEFPoliciesGraphApis` then your tenant has not been enabled for this private preview.  Please see [Prerequisites](#Prerequisites).

## Questions and comments

Questions about this sample should be posted to [Stack Overflow](https://stackoverflow.com/questions/tagged/azure-ad-b2c). Make sure that your questions or comments are tagged with [azure-ad-b2c].

## Contributing

If you'd like to contribute to this sample, see [CONTRIBUTING.MD](/CONTRIBUTING.md).

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Resources

The sample uses the Microsoft Authentication Library (MSAL) for authentication. The sample demonstrates both delegated admin permissions.  (app only permissions are not supported yet)

**Delegated permissions** are used by apps that have a signed-in user present (in this case tenant administrator). For these apps either the user or an administrator consents to the permissions that the app requests and the app is delegated permission to act as the signed-in user when making calls to Microsoft Graph. Some delegated permissions can be consented to by non-administrative users, but some higher-privileged permissions require administrator consent.

See [Delegated permissions, Application permissions, and effective permissions](https://developer.microsoft.com/en-us/graph/docs/concepts/permissions_reference#delegated-permissions-application-permissions-and-effective-permissions) for more information about these permission types.