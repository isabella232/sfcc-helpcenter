---
id: overview
themes: first-steps
title: SFCC cartridge overview
popular: false
related: trigger, what-data, where-configuration, products-filter-configuration
---

# Cartridge overview

Akeneo Salesforce commerce cloud cartridge is a SFCC add-on.
This add-on named "**cartridge**" is therefore installed on the SFCC side and communicates with Akeneo PIM **via its API**.

The cartridge is an **unidirectional** system : it only retrieves PIM data and imports it into SFCC (**No SFCC data is sent to the PIM**).

![Overview](../img/overview.png)

The PIM is therefore considered as the product master, while SFCC is its slave.

# Process overview

SFCC cartridge is composed of **4 main jobs** (4 main processes):
- `1- Akeneo-Import-Attributes`									
- `2- Akeneo-Import-Media-Assets-Pricebook`
- `3-1- Akeneo-Differential-Import-Products`
- `3-2- Akeneo-Full-Import-Products`

Each job can be independently triggered manually or automatically.

::: info
Each job is responsible for importing part of PIM data. The order in which the jobs are started is important (1 then 2 then 3).
:::

## Akeneo-Import-Attributes

`1- Akeneo-Import-Attributes` job imports:
- **PIM attributes**
- **PIM attribute options** (from simple and multi select attribute type)

::: info
Depending on your [cartridge configuration](mapping-configuration.html), some attributes can be mapped with default SFCC product attributes.
:::

## Akeneo-Import-Media-Assets-Pricebook

`2- Akeneo-Import-Media-Assets-Pricebook` job imports:
- **PIM images from image attribute** type (depending on your [cartridge configuration](import-images-configuration.html))
- **PIM images from asset attribute** type (depending on your [cartridge configuration](import-images-configuration.html))
- **PIM currencies** (to create SFCC Pricebook)

## Akeneo-Full-Import-Products & Akeneo-Differential-Import-Products

These 2 jobs are really similar and **don't have to be used at the same time**: they both import products from Akeneo PIM.

`3-2- Akeneo-Full-Import-Products` imports **all products** from Akeneo PIM.

when

`3-1- Akeneo-Differential-Import-Products` imports **only new products** since the last "**successful**" import made.

These jobs import:
- PIM categories
- PIM products (and product models)
- PIM product associations

::: info
Depending on your [cartridge configuration](products-filter-configuration), you can create some filters that allow you to import only products that match the defined criteria.
:::
