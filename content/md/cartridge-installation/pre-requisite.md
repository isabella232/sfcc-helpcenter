---
id: pre-requisite
themes: cartridge-installation
title: Prerequisites for installing the cartridge
popular: true
related: download-cartridge, where-configuration
---

# Cartridge Compatibility

## PIM compatibility

Please refer to our [Marketplace website](https://marketplace.akeneo.com/extension/salesforce-commerce-cloud-cartridge) to identify which **PIM versions** the last cartridge release is compatible with.

## SFCC compatibility

SFCC is a cloud solution that **automatically updates itself**. The cartridge is compatible with your SFCC version as soon as its `compatibility mode` has been configured on **17.7**.

## SFRA compatibility

Since the cartridge **doesn't deal with any storefront features** (The current Cartridge version is in "**Script**" mode), the cartridge is therefore **SFRA compatible**.


# Who can install the cartridge?

The cartridge installation is a **technical process** and requires a **very good knowledge of SFCC**.

::: warning
We therefore recommend that you use someone with **very good SFCC technical skills** to install the cartridge.
:::

# Does the cartridge work "out of the box"?

As it is possible to create many **different catalog structures** with Akeneo's PIM, it depends on the modeling of your catalogue and the functionalities of your project.

We have tried to do everything possible to ensure that the cartridge adapts to the different modeling required. The cartridge has **different parameters** to adapt to your needs.

::: warning
Please consult the documentation relating to the [**cartridge configuration**](themes-for-peter.html#cartridge-configuration) to fully understand the impact of each parameter.
:::

However, we know from experience that it is sometimes necessary to implement **specific customization** compared to your project. ;-) This is why we deliver **all the code sources** of the cartridge.

The cartridge is developed in a **SFCC proprietary Javascript**. The customization of the cartridge therefore requires a development team **that knows this language perfectly**.
