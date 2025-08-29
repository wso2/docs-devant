# Import a Repository

Once you’ve logged into [Devant Console](https://console.devant.dev/), you’ll land in the default project automatically created under your organization. Alternatively, you can choose to create a new project within the organization.

Once you're inside the desired project, follow the steps below to start creating an integration by importing a repository.

The steps provided are for a [GitHub](https://github.com/) repository, but you can follow a similar approach to authorize and connect with [Bitbucket](https://bitbucket.org/product) or [GitLab](https://about.gitlab.com/).


1. On the Project Overview page, click **Import an Integration**.

    <a href="{{base_path}}/assets/img/references/import-a-repository/import.png"><img src="{{base_path}}/assets/img/references/import-a-repository/import.png" alt="Import a repository" width="80%"></a>

3. Click **Authorize with GitHub** to connect Devant to your GitHub account.

    <a href="{{base_path}}/assets/img/references/import-a-repository/authorize-github.png"><img src="{{base_path}}/assets/img/references/import-a-repository/authorize-github.png" alt="Authorize with Github" width="80%"></a>

    !!! tip
        If you're using a public Git repository, you can skip ahead to Step 8. Click **Use a Third-Party Public Git Repository** and enter the repository URL.

4. If you haven't connected your GitHub repository to Devant, authorize the WSO2 cloud app with your GitHub account [WSO2 Cloud App](https://github.com/marketplace/choreo-apps). Under the **Organization** dropdown, click **+ Add**. This redirects you to the **Install WSO2 Cloud App** page.

5. Select your GitHub account and install [WSO2 Cloud App](https://github.com/marketplace/choreo-apps).

    <a href="{{base_path}}/assets/img/references/import-a-repository/wso2-cloud-app.png"><img src="{{base_path}}/assets/img/references/import-a-repository/wso2-cloud-app.png" alt="Install WSO2 Cloud app" width="60%"></a>

    !!! note
        The **WSO2 Cloud App** requires:

        - Read and write access to code and pull requests.
        - Read access to issues and metadata.

        You can [revoke access](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/reviewing-your-authorized-integrations#reviewing-your-authorized-github-apps) at any time. Write access is used to push changes directly to your repository.

6. Select your organization under the **Organization** dropdown. If your organization is not listed, click the Refetch button.

7. Select a repository to save your integration. You can either create a new repository or choose an existing one. You’ll be prompted to authorize the WSO2 Cloud App for the selected repository to enable integration.

8. Select a **Branch** and a **Path** of the selected repository to save your integration.

9. The **Name** and **Identifier** fields are automatically populated. Optionally, you can edit them to your preference.