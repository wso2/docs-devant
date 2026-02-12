---
title: Endpoint
description: Learn about Endpoints in Devant integrations.
---

# Endpoint

An Endpoint is a network-exposed function that resides within an integration. In Devant, **Integration Type** `Integration as API` exposes one or more endpoints. Each endpoint in an integration can have a service contract (OpenAPI, GraphQL SDL) associated with it. This contract is used to expose the endpoint to consumers. In the absence of a contract, Devant uses /* exposed on all HTTP verbs as the default contract to expose the service or the integration.

Each endpoint exposed in an integration is considered a single API. Therefore, Devant allows you to do API management per endpoint for a given integration. For example, you can perform lifecycle management and configure security settings per endpoint in a given integration.

[//]: # (Todo: Uncomment the following after the required page is completed)
[//]: # (See [Configure Endpoints]&#40;../develop-components/configure-endpoints.md&#41; to learn how to configure endpoints when developing components in Devant.)
