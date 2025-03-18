# Deploy Your First AI Agent

## Overview

In this guide, you will:

- Create a simple AI Agent that provides math tutoring assistance.
- Use Ballerina Integrator to develop the AI Agent integration.
- Push the AI Agent to Devant from Ballerina Integrator, which will automatically build and deploy it into the development environment.
- Test the AI Agent by sending prompts.
- Promote it to the production environment and use it as an API.

<!-- Todo add a YouTube video tutorial for this quick start -->

## Prerequisites

1. GitHub account: [Create a GitHub account](https://github.com/signup) if you don't have one already.
2. If signing in to Devant for the first time, create an organization:
    1. Go to [https://console.devant.dev/](https://console.devant.dev/) and sign in using Google, GitHub, or Microsoft account.
    2. Enter a unique organization name. For example, `Stark Industries`.
    3. Read and accept the privacy policy and terms of use and click **Create**.
3. VSCode: [Install VSCode](https://code.visualstudio.com/download) if you don't have it installed already.

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

1. Click **Install Ballerina Integrator extension** on the overview page. This opens the VSCode extensions page.
2. Click **Install** to install the extension. This installs both **Ballerina Integrator** and **Ballerina** extensions on VSCode.

## Step 3: Set up Ballerina Integrator for the first time
1. Click the Ballerina Integrator icon on the sidebar.

    <a href="{{base_path}}/assets/img/get-started/bi-icon.png"><img src="{{base_path}}/assets/img/get-started/bi-icon.png" alt="Ballerina Integrator Icon" width="80%"></a>

2. Click **`Set Up Ballerina Integrator`**. The setup wizard installs and configures the [Ballerina](https://ballerina.io/) distribution required for the Ballerina Integrator.
3. Click **`Restart VS Code`** to complete the setup.

    <a href="{{base_path}}/assets/img/get-started/bi-setup.gif"><img src="{{base_path}}/assets/img/get-started/bi-setup.gif" alt="Ballerina Integrator Setup" width="80%"></a>

## Step 4: Develop AI Agent in VSCode
1. Go to the Overview page of the integration you have created and click **Develop in Ballerina Integrator**. This will clone your project and open it in Ballerina Integrator.
2. In the Ballerina Integrator design view, click **Add Artifact**.
3. Select **AI Chat Agent** from the Constructs menu. Choosing the **AI Agent** from the Devant console disables the other options.
4. Provide the name of the Agent as `MathTutor` and click **Create**. This directs you to the AI Chat Agent diagram view.
5. Click the OpenAI icon in the diagram view to configure the LLM model, and add the following configurables:

    | Field                   | Value              |
    |-------------------------|--------------------|
    | **Select Model Family** | `AzureOpenAiModel` |
    | **Variable Name**       | `_mathTutorModel`  |
    | **API Key**             | `apiKey`           |
    | **API Version**         | `apiVersion`       |
    | **Deployment ID**       | `deploymentId`     |
    | **Service URL**         | `serviceUrl`       |

6. Click **Save**.

    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-ai-agent/initialize-agent.gif"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-ai-agent/initialize-agent.gif" alt="Initialize AI Agent" width="80%"></a>

7. From the left side panel, click **+** on the **Functions** to create a new function. Name it as `mult`.
8. Click **+ Add Parameter** and add two `decimal` parameters, `a` and `b`.
9. Set the **Return Type** as `decimal` and click **Create**.
10. Now, let's create the function return logic. Click the plus icon after the **Start** node to open the node panel.
11. Select **Return** and enter the **Expression** as `a * b`.
12. Click the source icon `(<\>)` in the top right corner to view the source code of the function.
13. Add the `isolated` keyword before the function definition to make it an isolated function.

    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-ai-agent/add-function.gif"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-ai-agent/add-function.gif" alt="Initialize AI Agent" width="80%"></a>

14. Now, let's add the `mult` function as a tool to the AI Agent. Click `mathTutor` under **Entry Points** on the left navigation. This brings up the AI Agent diagram view.
15. In the Agent box, click the plus icon to create a tool and click **+ Create New Tool** on the right panel.
16. Select the `mult` function you just created under **Current Integrations**.
17. Provide the **Tool Name** as `getMult` and click **Save Tool**.
18. Click the agent box and enter `Math Tutor` as the role and enter the instructions as `"You are a school tutor assistant. Provide answers to students' questions so they can compare their answers. Use the tools when there is query related to math".` Then click **Save**.
19. From the left side panel, click **+** on the **Configurations**, and add the following configurables,

    | Variable            | Type       |
    |---------------------|------------|
    | `apiKey`            | `string`   |
    | `apiVersion`        | `string`   |
    | `deploymentId`      | `string`   |
    | `serviceUrl`        | `string`   |

    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-ai-agent/add-tool.gif"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-ai-agent/add-tool.gif" alt="Add as a Tool" width="80%"></a>

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
3. Send the prompt `What is 2343282 * 392011` to test your Math Tutor agent. Even though typically LLMs are bad at large multiplication, this agent has tool support to give an accurate answer.
   
    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-ai-agent/test-agent-in-devant.gif"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-ai-agent/test-agent-in-devant.gif" alt="Ballerina Integrator Icon" width="80%"></a>

4. After successfully testing, you can promote your AI Agent to production by clicking **Promote** button.
5. Once deployed to production, you can access your AI Agent through the API endpoints and embed it in your applications.
