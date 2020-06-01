---
id: overview
themes: first-steps
title: Akeneo Connector for SFCC overview
popular: false
related: trigger, what-data, where-configuration, products-filter-configuration
---

# Connector overview

Akeneo Connector for SFCC is an add-on for Salesforce Commerce Cloud.
This add-on named "**cartridge**" is installed on SFCC side and communicates with Akeneo PIM **via its API**.

The connector is an **unidirectional** system: it exports PIM data to SFCC. **No SFCC data is sent back to the PIM**.

![Overview](../img/overview.png)

The PIM is considered as the master tool for product data, it should not be handled in SFCC.

# Process overview

The connector is composed by **9 jobs**:
- `1- Akeneo-Import-Attributes`
- `2-1-Akeneo-Differential-Import-Assets`
- `2-2-Akeneo-Full-Import-Media-Assets-Pricebook`
- `3-1-1 Akeneo-Differential-Import-Master`
- `3-1-2 Akeneo-Differential-Import-Storefront`
- `3-2-1 Akeneo-Full-Import-Master`
- `3-2-2 Akeneo-Full-Import-Master-Variation`
- `3-2-3 Akeneo-Full-Master-Image`
- `3-2-4-Akeneo-Full-Import-Storefront`
- `4- Akeneo-Entity-Import`
- `5- Akeneo-Entity-Record-Grouping`
- `6-Akeneo-Save-Catalog-Refinements`

::: info
Two New jobs have been introduced to support the new asset system since the SFCC v20.2.0.
o	2-1-Akeneo-Differential-Import-Assets
o	2-2-Akeneo-Full-Import-Media-Assets-Pricebook
:::

::: info
The	2-Akeneo-Import-Media-Assets-Pricebook job (the old one) has do be deleted manually.
:::

Each job can be triggered manually or automatically on its own.

::: info
Each job is responsible for importing PIM architecture and data into Salesforce Commerce Cloud. The order above should be observed to build your catalog properly (1 then 2 then 3).
:::

## 1- Akeneo-Import-Attributes job

`1- Akeneo-Import-Attributes` job imports:
- **PIM attributes**
- **PIM attribute options** (from simple and multi select attribute type)

::: info
Depending on your [connector configuration](05-mapping-configuration.html), some attributes can be mapped with default SFCC product attributes.
:::

## 2-1-Akeneo-Differential-Import-Assets job
`2-1-Akeneo-Differential-Import-Assets` job imports the change in assets. That will copy the PIM data into the cartridge. However, to see the changes applied to the products, you have to run the `3-1-1 Akeneo-Differential-Import-Master` after that.


## 2-2 Akeneo-Import-Media-Assets-Pricebook job

`2-2 Akeneo-Import-Media-Assets-Pricebook` job imports:
- **PIM images from image attribute** type (depending on your [connector configuration](04-import-images-configuration.html))
- **PIM images from asset attribute** type (depending on your [connector configuration](04-import-images-configuration.html))
- **PIM currencies** (to create a Pricebook in SFCC)

## 3- Akeneo-Full-Import & Akeneo-Differential-Import jobs

"Full import" and "Differential import" jobs are quite similar and **should not be used at the same time**: they both import products from Akeneo PIM.

- `3-2.x Akeneo-Full-Import-xxx` jobs import **all products** from Akeneo PIM.
- `3-1.x Akeneo-Differential-Import-xxx` jobs import **only new products** since the last "**successful**" import made.

These jobs import:
- PIM categories
- PIM products and product models
- PIM product associations

::: info
Depending on your [connector configuration](03-products-filter-configuration.html), you can create some filters to run partial imports on products that match with your defined criteria.
:::

## 4- Akeneo-Entity-Import

`4- Akeneo-Entity-Import` job imports:
- PIM Reference Entities
- PIM Reference Entity Records


## 5- Akeneo-Entity-Record-Grouping

`5- Akeneo-Entity-Import` job add some Reference Entity Records to an SFCC attribute group.

::: info
Depending on your [connector configuration](08-reference-entities.html), you can manage how your reference entities will be mapped into SFCC.
:::

## 6-Akeneo-Save-Catalog-Refinements

`6-Akeneo-Save-Catalog-Refinements` job will save the manually contributed catalog refinements to custom cache so that they are not overwritten every time the catalog is reimported in merge mode. This job needs to be run every time some change is made in the catalog refinements.
