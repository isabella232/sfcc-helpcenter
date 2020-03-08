---
id: all-pre-requisite
themes: cartridge-installation
title: Prerequisites for installing the connector
popular: true
related: download-cartridge, 01-where-configuration
---

# Connector Compatibility

## PIM compatibility

Akeneo Connector for SFCC was originally built with Akeneo PIM 1.7. It has been maintained since then, to support the newer versions and features of Akeneo PIM.
Please refer to our [**Marketplace website**](https://marketplace.akeneo.com/extension/akeneo-connector-salesforce-commerce-cloud) to know if our connector is compatible with your **PIM version**.

:::info
Ensuring compatibility from one version to another remains our priority. Thanks to Akeneo API, Akeneo Connector for SFCC is natively compatible with new versions of Akeneo PIM although it may not include all latest features. Get in touch with Akeneo to learn about our product roadmap.
:::

## SFCC compatibility

Salesforce Commerce Cloud is a Cloud solution that **automatically updates itself**.<br>
The latest connector version works in SFCC `Compatibility mode 19.10` so it is therefore compatible with the latest SFCC version.

## SFRA compliance

Since the Akeneo Connector for SFCC was build in "**Script**" mode and **doesn't have any storefront feature**, the connector is therefore **compliant with the new StoreFront Reference Architecture** of Salesforce Commerce Cloud.

# Configure your Akeneo PIM

1. Set your API user credentials
2. Create an API user who has the full permission to view, edit, and manage products
3. Create currencies enabled in Akeneo that match with SFCC currencies
4. Translate your families, attributes, and attribute options labels for all languages available in SFCC

:::info
If you need help setting up your Akeneo PIM, please refer to our [**PIM Help Center**](https://help.akeneo.com/pim/index.html).
:::

# Configure your Salesforce Commerce Cloud

`1.` Set up at least one **site** activated for associate job to site scope<br>
(`Administration > Sites : Manager sites`)

`2.` Set up at least one **master catalog** to store details of all products<br>
(`Merchant Tools > Products and Catalogs : Catalogs`)

`3.` Set up at least one **storefront catalog** associate to your current site<br>
(`Merchant Tools > Products and Catalogs : Catalogs`)

# Who can install the connector?

Installing the Akeneo Connector for SFCC is a **technical process** that requires **advanced knowledge of Salesforce Commerce Cloud**.

::: warning
We therefore recommend that you refer to a technical resource **with proven track of SFCC skills** to perform the installation of such connector.
:::

# Does the Akeneo Connector for SFCC work "out-of-the-box"?

Akeneo PIM being flexible enough for you to create many **different catalog structures**, the modeling of your catalogue and the features of your project will impact the usage or your Akeneo Connector.

We did everything possible to ensure that this connector adapts to your modeling, hence the **different parameters** of this connector to adapt to your needs.

::: warning
Please read the documentation related to the [**connector configuration**](../themes-for-peter.html#cartridge-configuration) to understand the impact of each parameter.
:::

# So, can I customize Akeneo Connector for SFCC?

If the multiple configurations of the Akeneo Connector don't suit your business logic, or if you want to have other possibilities for import, you can customize Akeneo Connector for SFCC.

We know from experience that it may be necessary to implement **specific customizations** for your project. This is why Akeneo provides you with the **source code** of this Connector.

The Akeneo Connector for SFCC is developed in a **SFCC proprietary Javascript**. Its customization therefore requires a development team **aware of this specific Javascript language**.
