---
id: all-pre-requisite
themes: cartridge-installation
title: Prerequisites for installing the cartridge
popular: true
related: download-cartridge, where-configuration
---

# Cartridge Compatibility

## PIM compatibility

Akeneo connector for SFCC was originally built with Akeneo PIM 1.7. It has been maintained until then, to support the newer versions and features of Akeneo PIM.
Please refer to our [**Marketplace website**](https://marketplace.akeneo.com/extension/salesforce-commerce-cloud-cartridge) to know if our connector is compatible with your **PIM version**.

## SFCC compatibility

Salesforce Commerce Cloud is a Cloud solution that **automatically updates itself**.<br>
The latest connector version is therefore compatible with the latest SFCC version.

## SFRA compliance

Since the Akeneo connector for SFCC was build in "**Script**" mode and **doesn't have any storefront feature**, the connector is therefore **compliant with the new StoreFront Reference Architecture** of Salesforce Commerce Cloud.

# Who can install the cartridge?

Installing the Akeneo connector for SFCC is a **technical process** that requires **advanced knowledge of Salesforce Commerce Cloud**.

::: warning
We therefore recommend that you refer to a technical resource **with proven track of SFCC skills** to perform the installation of such connector.
:::

# Does the Akeneo connector work "out-of-the-box"?

Akeneo PIM being flexible enough for you to create many **different catalog structures**, the modeling of your catalogue and the features of your project will impact the usage or your Akeneo connector.

We did everything possible to ensure that this connector adapts to your modeling, hence the **different parameters** of this connector to adapt to your needs.

::: warning
Please read the documentation related to the [**cartridge configuration**](themes-for-peter.html#cartridge-configuration) to understand the impact of each parameter.
:::

However, we know from experience that it may be necessary to implement **specific customizations** for your project. This is why Akeneo provides you with the **source code** of this connector.

The Akeneo connector for SFCC is developed in a **SFCC proprietary Javascript**. Its customization therefore requires a development team **aware of this specific Javascript language**.
