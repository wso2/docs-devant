# Develop Integrations With Git

Devant enables you to develop integrations by connecting your GitHub, Bitbucket, or GitLab repository. You have the flexibility to either connect an existing repository or start with an empty repository and commit the source code later. By integrating your repositories with Devant, you can automate tasks and optimize workflows across multiple systems, all within Devant.  Devant currently supports GitHub, Bitbucket, and GitLab as Git providers. 

Following are the authorization methods supported by Devant for each Git provider:

- GitHub: OAuth authorization
- Bitbucket: App Password
- GitLab: Personal Access Token (PAT)

!!! tip
    Devant supports both Bitbucket Server and Bitbucket Cloud. The currently supported Bitbucket Server version is 8.9.2.

## Connect a GitHub repository to Devant

1. Sign in to [Devant](https://console.devant.dev/).
2. When creating a new project or an integration, select **Authorize with GitHub**.
3. You can follow the on-screen prompts to authorize [WSO2 Cloud App](https://github.com/marketplace/choreo-apps) with your GitHub account.

Authorizing WSO2 Cloud App as a GitHub application grants the following permissions to perform the respective actions on your behalf within the repository:

|Permission   | Read| Write| Description                                                           |
|-------------|-----|------|-----------------------------------------------------------------------|
|Issues       | Y   | N    | Read integration ID label to filter the pull requests                   |
|Metadata     | Y   | N    | List repositories                                                     |
|Contents     | Y   | Y    | List branches and create a branch to commit sample code               |
|Pull Request | Y   | Y    | Create a pull request if you start with a Devant sample               |
|Webhooks     | Y   | Y    | Trigger automatic deployment and configuration generation             |

## Connect a Bitbucket repository to Devant

1. Sign in to [Devant](https://console.devant.dev/).
2. In the Devant Console header, go to the **Organization** list and select your organization. 
3. In the left navigation menu, under **Admin**, click **Settings**. This opens the organization-level settings page. 
4. Click the **Credentials** tab.
5. Click **+Add Credentials** to configure the Git repository connection.
6. Enter a **Credential Name** and select Bitbucket as the Git provider. 
7. Enter your Bitbucket **Username**.
8. Enter the **App Password** you obtained from Bitbucket.

    !!! tip
        You can refer to [Atlassian Documentation](https://support.atlassian.com/bitbucket-cloud/docs/create-an-app-password/) to create an app password in Bitbucket.

9. Click **Save**.

Authorizing using an App Password from Bitbucket grants Devant the following permissions to perform the respective actions on your behalf within the repository.

|Permission    | Read| Write| Description                                                        |
|--------------|-----|------|--------------------------------------------------------------------|
|Account       | Y   | N    | Get user information and workspace details                         |
|Repositories  | Y   | Y    | List branches and create a branch to commit sample code            |
|Pull Requests | Y   | Y    | Create a pull request if you start with a Devant sample            |
|Webhooks      | Y   | Y    | Trigger automatic deployment and configuration generation          |

## Connect a GitLab repository to Devant

1. Sign in to [Devant](https://console.devant.dev/).
2. In the Devant Console header, go to the **Organization** list and select your organization. 
3. In the left navigation menu, under **Admin**, click **Settings**. This opens the organization-level settings page. 
4. Click the **Credentials** tab.
5. Click **+Add Credentials** to configure the Git repository connection.
6. Enter a **Credential Name** and select GitLab as the Git provider.
7. Please note that Devant supports only self-managed GitLab instances.
8. Enter the **Server URL** of your GitLab self-managed instance.
9. Enter the **Access Token** you obtained from GitLab.

    !!! tip
        You can refer to [GitLab Documentation](https://docs.gitlab.com/user/profile/personal_access_tokens/#create-a-personal-access-token) to create a PAT in GitLab.

10. Click **Save**.

Authorizing using a personal access token (PAT) obtained from your GitLab self-managed server grants Devant the following permissions to perform the respective actions on your behalf within the repository.

|Permission    | Description                                                                         |
|--------------|-------------------------------------------------------------------------------------|
|API           | Grants full read/write access to the API, covering all groups and projects, as well as read/write access to the repository.|

## Connect an Azure DevOps repository to Devant

1. Sign in to [Devant](https://console.devant.dev/).
2. In the Devant Console header, go to the **Organization** list and select your organization. 
3. In the left navigation menu, under **Admin**, click **Settings**. This opens the organization-level settings page. 
4. Click the **Credentials** tab.
5. Click **+Add Credentials** to configure the Git repository connection.
6. Enter a **Credential Name** and select Azure DevOps as the Git provider.
7. Enter your Azure DevOps **Organization Name**.
8. Enter the **Access Token** you obtained from Azure DevOps.

    !!! tip
        You can refer to [Azure DevOps Documentation](https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=Windows) to create a PAT in Azure DevOps.

9. Click **Save**.

Authorizing using a personal access token (PAT) obtained from your Azure DevOps organization grants Devant the following permissions to perform the respective actions on your behalf within the repository.

|Permission       | Read| Write| Description                                                                                                           |
|-----------------|-----|------|-----------------------------------------------------------------------------------------------------------------------|
|Code             | Y   | N    | Allows viewing and cloning repositories, branches, commits, and pull requests.                                        |
|Project and Team | Y   | N    | Allows reading project-level information, including team details, project settings, and other project configurations. |
