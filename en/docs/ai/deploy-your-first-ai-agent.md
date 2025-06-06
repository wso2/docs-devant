# Deploy Your First AI Agent

## Overview

In this guide, you will:

- Create a simple AI agent that provides math tutoring assistance.
- Use Ballerina Integrator to develop the AI agent integration.
- Push the AI agent to Devant from Ballerina Integrator. This will automatically build and deploy it to the development environment.
- Test the AI agent by sending prompts.
- Once verified, promote it to the production environment and expose it as an API.

## Prerequisites

1. GitHub account: [Create a GitHub account](https://github.com/signup) if you don't have one already.
2. If signing in to Devant for the first time, [create an organization](../references/create-an-organization.md) to begin with.
3. VS Code: [Install VS Code](https://code.visualstudio.com/download) if you don't have it installed already.

## Step 1: Attach a Git repository
1. Go to [https://console.devant.dev/new](https://console.devant.dev/new) and sign in. This opens the new integration page.
2. On the new integration page, click **Attach a Git Repository**.

    !!! tip
        If you're using a public Git repository, you can skip ahead to sub-step 8. Click **Use a Third-Party Public Git Repository** and enter the repository URL.

3. Click **Authorize with GitHub** to connect Devant to your GitHub account. If you haven't connected your GitHub repository to Devant, authorize the WSO2 cloud app with your GitHub account [WSO2 Cloud App](https://github.com/marketplace/choreo-apps).
4. Under the **Organization**  dropdown click **+ Add**. This redirects you to the **Install WSO2 Cloud App** page.
5. Select your GitHub account and install [WSO2 Cloud App](https://github.com/marketplace/choreo-apps)

    !!! note
        The **WSO2 Cloud App** requires:

        - Read and write access to code and pull requests.
        - Read access to issues and metadata.

         You can [revoke access](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/reviewing-your-authorized-integrations#reviewing-your-authorized-github-apps) at any time. Write access is used to push changes directly to your repository.

6. Under the **Organization**  dropdown, select your organization. If it is still not listed, click the Refetch button.
7. Select a repository to save your integration.
8. Select a **Branch** and a **Path** of the selected repository to save your integration.
9. **Name** and **Identifier** fields are automatically populated. Additionally, you can edit them to your preference.
10. Select the **Technology** as `Ballerina Integrator`.
11. Choose the **Integration Type** as `AI Agent` and Click **Create**.

This redirects you to the overview page of the AI Agent. Now, let's develop the AI Agent.

## Step 2: Install the Ballerina Integrator extension

1. Click **Install Ballerina Integrator extension** on the overview page. This opens the VS Code extensions page.
2. Click **Install** to install the extension. This installs both **Ballerina Integrator** and **Ballerina** extensions on VS Code.

## Step 3: Set up Ballerina Integrator for the first time
1. Click the Ballerina Integrator icon on the sidebar.

    <a href="{{base_path}}/assets/img/get-started/bi-icon.png"><img src="{{base_path}}/assets/img/get-started/bi-icon.png" alt="Ballerina Integrator Icon" width="80%"></a>

2. Click **`Set Up Ballerina Integrator`**. The setup wizard installs and configures the [Ballerina](https://ballerina.io/) distribution required for the Ballerina Integrator.
3. Click **`Restart VS Code`** to complete the setup.

    <a href="{{base_path}}/assets/img/get-started/bi-setup.gif"><img src="{{base_path}}/assets/img/get-started/bi-setup.gif" alt="Ballerina Integrator Setup" width="80%"></a>

## Step 4: Develop the AI Agent in VS Code  
To build your AI Agent using Ballerina Integrator, refer to the [AI Agent Integration](https://bi.docs.wso2.com/learn/ai/agents/introduction-to-inline-agents/) guide on the Learn page.

## Step 5: Push to Devant
1. Click the **Source Control** icon on the sidebar.
2. Click **+** to stage all changes.
3. Add an appropriate commit message and commit.
4. Click **Sync Changes** to push the changes to remote.
5. Go back to the **Design** view using the back arrow in the top left corner.
6. From the right side panel, click the **View in Devant** to view this integration in Devant.

## Step 6: Test AI Agent
1. Once you push the changes, the overview page of the Devant AI Agent will automatically refresh and show you the **Latest Commit** and automatically builds and shows the **Build Status**.

    !!! note
        The build process may take some time. Once complete, the build status changes to **Success**. You can see the Build History by clicking **Build** in the left navigation.

2. Once the **Build Status** shows `Build completed`, it will be automatically deployed into the development card.
3. Then, click the **Configure to Continue** button, enter the configurable values, and click **`Apply`**.
4. Send the prompt `What is 87,657 * 67,997` to test your Math Tutor agent. Even though typically LLMs are bad at large multiplication, this agent has tool support to give an accurate answer.
   
    <a href="{{base_path}}/assets/img/ai/deploy-your-first-ai-agent/test-agent-in-devant.gif"><img src="{{base_path}}/assets/img/ai/deploy-your-first-ai-agent/test-agent-in-devant.gif" alt="Ballerina Integrator Icon" width="80%"></a>

5. After successfully testing, you can promote your AI Agent to production by clicking the **Promote** button.
6. Once deployed to production, you can access your AI Agent through the API endpoints and embed it in your applications.
