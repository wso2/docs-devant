---
title: Develop Your First MCP Server
description: Build your first MCP server with Devant by WSO2. Learn to create and deploy MCP-based integrations using WSO2 Integrator BI.
---

# Develop Your First MCP Server

## Overview

In this guide, you will:

- Create a simple MCP server.
- Use WSO2 Integrator: BI to develop the MCP service integration.
- Push the MCP server to Devant from WSO2 Integrator: BI. This will automatically build and deploy it to the development environment.
- Test the MCP server.
- Once verified, promote it to the production environment and expose it as an API.

## Prerequisites

1. GitHub account: [Create a GitHub account](https://github.com/signup) if you don't have one already.
2. If signing in to Devant for the first time, [create an organization](../references/create-an-organization.md) to begin with.
3. VS Code: [Install VS Code](https://code.visualstudio.com/download) if you don't have it installed already.

## Step 1: Create the new integration

1. Import a new repository to begin your integration. Refer [Import a Repository](../references/import-a-repository.md) for more details.
2. Select the **Technology** as `WSO2 Integrator: BI`.
3. Choose the **Integration Type** as `MCP Server` and click **Create**.

This redirects you to the **Create New Integration in VS Code** page.

## Step 2: Install the WSO2 Integrator: BI extension and open the integration

1. Install WSO2 Integrator: BI extension. Refer [Install and Set Up WSO2 Integrator: BI](../references/install-and-setup-wso2-integrator-bi.md) for more details.
2. Click **Develop in WSO2 Integrator: BI**. This will clone your integration project and open it in BI.

## Step 3: Develop the MCP Server in WSO2 Integrator: BI

To build your MCP Server using WSO2 Integrator: BI, refer to the [MCP Service Integration](https://bi.docs.wso2.com/integration-guides/ai/mcp-service/mcp-service/) guide on the Learn page.

## Step 4: Push to Devant

1. Click the **Source Control** icon on the sidebar.
2. Click **+** to stage all changes.
3. Add an appropriate commit message and commit.
4. Click **Sync Changes** to push the changes to remote.
5. Go back to the **Design** view using the back arrow in the top left corner.
6. From the right side panel, click the **View in Devant** to view this integration in Devant.

## Step 5: Test MCP server

1. Once you push the changes, the overview page of the Devant MCP Server will automatically refresh and show you the **Latest Commit** and automatically build and show the **Build Status**.

    !!! note
        The build process may take some time. Once complete, the build status changes to **Success**. You can see the Build History by clicking **Build** in the left navigation.

2. Once the **Build Status** shows `Build completed`, it will be automatically deployed into the development environment.

3. Then, click the **Configure to Continue** button, enter the configurable values, and click **Apply**.

4. Navigate to the **Test** page of your MCP Server in Devant and use the **MCP Playground** to explore available tools. Select a tool, provide the required inputs, and execute it to test functionality.

    <a href="{{base_path}}/assets/img/get-started/deploy-your-first-mcp-server/test-in-mcp-playground.gif"><img src="{{base_path}}/assets/img/get-started/deploy-your-first-mcp-server/test-in-mcp-playground.gif" alt="Test in MCP Playground" width="80%"></a> 

5. After successfully testing, you can promote your MCP Server to production by clicking the **Promote** button.

6. Once deployed to production, you can access your MCP server through the exposed endpoints and integrate it with your applications.
