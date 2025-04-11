# Project

A project in Devant is a logical group of related integrations that typically represent a complete solution. A project consists of one or more integrations. All integrations within a project can ideally be (but are not restricted to) in a single GitHub repository under different paths. This is also known as the monorepo architecture.

At deployment time, all integrations within a given project are deployed into a single namespace of the Kubernetes cluster. Integrations within a project can be exposed to the public internet, internally to the rest of the organization, or privately within the project only. A project in Devant is represented as a cell with regard to the [Cell-based architecture](https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md). The following diagram illustrates a project and how the integration within a project are laid out at runtime:

![Project](../assets/img/devant-concepts/project.png){.cInlineImage-threeQuarter}
