---
title: Integration
description: Learn about Integrations in Devant.
---

# Integration

An integration within a project represents a single unit of work in an integration solution. An integration is usually a single microservice, API, or job/task. Each integration in Devant is attached to a given directory path in a Git repository which contains the program source. An integration is Devant’s unit of deployment. Each integration maps to a single pod in the Kubernetes cluster (data plane) at deployment time. Therefore, you can deploy, manage, and scale each integration in Devant independently.

Devant supports different integration types for various use cases. These include integration types such as Automation, AI Agent, Integration as API, and so on. Each integration type hosts unique features based on its characteristics. For example, a scheduled integration can accept a cron expression as a configuration to schedule an integration job/task.
