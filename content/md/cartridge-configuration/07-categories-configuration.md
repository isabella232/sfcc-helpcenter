---
id: 07-categories-configuration
themes: cartridge-configuration
title: configuration of categories
popular: false
related: 01-where-configuration, 02-configure-PIM-API, 03-products-filter-configuration, 04-import-images-configuration, 05-import-media-configuration, 06-mapping-configuration, 08-multi-storefront-configuration, 09-reference-entities
---

# How to define which PIM category trees I want to push to SFCC?

Within your Akeneo PIM instance, you may use different category trees to manage your product data. The Akeneo Connector for SFCC gives you the possibility to export one or several category trees per website.

In the [connector configuration page](01-where-configuration.html), fill in the following parameter with the PIM categories ID of your choice:

| Connector parameter           | PIM information         |
| :-----------------------------| :---------------------: |
| Akeneo main catalogs          |  PIM categories ID      |   

# How to define the status of your SFCC category trees?

In the [connector configuration page](01-where-configuration.html), select `Yes` for the parameter below if you want to push live the PIM category trees on your webstores directly. Otherwise, select `No`.

| Connector parameter           | SFCC information        |
| :-----------------------------| :---------------------: |
| Akeneo Category Online        |  Yes or No              |

# How to automatically define the "Primary" category for my SFCC products?

In the [connector configuration page](01-where-configuration.html), if you select `Yes` for the following parameter, the first category of products will become your "primary" category for that product. (Please refer to [Salesforce documentation](https://documentation.b2c.commercecloud.salesforce.com/DOC1/topic/com.demandware.dochelp/Products/Classificationvsprimarycategory.html) to better understand what a primary category is).

| Connector parameter                | SFCC information        |
| :----------------------------------| :---------------------: |
| Akeneo Product Primary Flag        |  Yes or No              |

# How to not import PIM categories in SFCC?

In the [connector configuration page](01-where-configuration.html), select `Yes` for the parameter below if you want to copy the PIM categories into SFCC. Otherwise, select `No`.

| Connector parameter           | SFCC information        |
| :-----------------------------| :---------------------: |
| akeneoWriteCategories        |  Yes (default value) or No              |
