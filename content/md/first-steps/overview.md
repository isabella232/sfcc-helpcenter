---
id: overview
themes: first-steps
title: SFCC cartridge overview
popular: false
related: trigger, what-data, where-configuration, products-filter-configuration
---

# Cartridge overview

Akeneo connector for SFCC is an add-on for Salesforce Commerce Cloud.
This add-on named "**cartridge**" is installed on SFCC side and communicates with Akeneo PIM **via Akeneo API**.

The cartridge is an **unidirectional** system: it exports PIM data to SFCC. **No SFCC data is sent back to the PIM**.

![Overview](../img/overview.png)

The PIM is considered as the master tool for product data, it should not be handled in SFCC.

# Process overview

SFCC cartridge is composed by **4 main jobs** (4 main processes):
- `1- Akeneo-Import-Attributes`									
- `2- Akeneo-Import-Media-Assets-Pricebook`
- `3-1- Akeneo-Differential-Import-Products`
- `3-2- Akeneo-Full-Import-Products`

Each job can be triggered manually or automatically on its own.

::: info
Each job is responsible for importing PIM architecture and data into Salesforce Commerce Cloud. The order above should be observed to build your catalog properly (1 then 2 then 3).
:::

## Akeneo-Import-Attributes

`1- Akeneo-Import-Attributes` job imports:
- **PIM attributes**
- **PIM attribute options** (from simple and multi select attribute type)

::: info
Depending on your [cartridge configuration](05-mapping-configuration.html), some attributes can be mapped with default SFCC product attributes.
:::

## Akeneo-Import-Media-Assets-Pricebook

`2- Akeneo-Import-Media-Assets-Pricebook` job imports:
- **PIM images from image attribute** type (depending on your [cartridge configuration](import-images-configuration.html))
- **PIM images from asset attribute** type (depending on your [cartridge configuration](import-images-configuration.html))
- **PIM currencies** (to create a Pricebook in SFCC)

## Akeneo-Full-Import-Products & Akeneo-Differential-Import-Products

These 2 jobs are quite similar and **should not be used at the same time**: they both import products from Akeneo PIM.

- `3-2- Akeneo-Full-Import-Products` imports **all products** from Akeneo PIM.
- `3-1- Akeneo-Differential-Import-Products` imports **only new products** since the last "**successful**" import made.

These jobs import:
- PIM categories
- PIM products and product models
- PIM product associations

::: info
Depending on your [cartridge configuration](03-products-filter-configuration), you can create some filters to run partial imports on products that match with the defined criteria.
:::
