---
title: AEM and third Party Commerce Integration using Commerce Integration Framework
description: Enterprise businesses may require additional third party commerce solutions to power their storefront. The Commerce Integration Framework (CIF) can be used in such integration scenarios to connect a third party commerce solution to Adobe Experience Manager using I/O Runtime.
thumbnail: cif-third-party-architecture.jpg
---
# AEM and Third Party Commerce Integration using Commerce Integration Framework {#aem-third-party}

The integration of non-Adobe Commerce solution is a common scenario for CIF. third party solutions with different APIs and schemas get connected via an integration layer.

## Architecture {#architecture}

The overall architecture is as follows:

![AEM non-Magento/third Party Architecture Overview](../assets//AEM_nonMagento_Architecture.png)

The purpose of this integration layer is to map third-party APIs and schemas against the supported Adobe Commerce GraphQL APIs and schemas outside of the Experience Manager. Thanks to this encapsulation, the integration logic and systems can get updated without changing code inside the Experience Manager.

## Solution requirements for an integration

As the Experience Manager retrieves data on-demand, real-time APIs for product catalog are required.

>[!TIP]
>
>If no real-time APIs are available, an external product cache with APIs should be used for the integration. Example [Magento open-source](https://magento.com/products/magento-open-source).

There is no need to implement the complete GraphQL schema, just the objects of the schema to enable the desired use-cases.

## Backend use-cases

CIF extends the Experience Manager with real-time product catalog access and product experience management tools. This seamless integration enables authors to access commerce data using embedded UIs whenever needed without leaving the content context.

The integration of product catalog APIs is required to unlock these use-cases.

## Frontend Use-Cases

[AEM CIF Core Components](https://github.com/adobe/aem-core-cif-components) retrieve and exchange data via the CIF supported Adobe Commerce APIs. To re-use components, the respective APIs need to be implemented.

The recommendation for performance critical client-side components is to communicate directly with the third party solution to avoid latency.

## Developing an Integration {#develop-integration}

We recommend using [Adobe I/O Runtime](https://www.adobe.io/apis/experienceplatform/runtime.html) for the integration layer. It is included in the CIF add-on for third parties. As it works with a microservice-like approach, it is suited well to integrate easily multiple solutions.

The [reference implementation](https://github.com/adobe/commerce-cif-graphql-integration-reference) is a great starting point to build the integration to your commerce solution. Although it supports GraphQL, it can also be integrated with any other type of API such as REST.

This integration layer is not required if a third party layer is available (such as Mulesoft) or the integration gets built on top of the third party solution.
