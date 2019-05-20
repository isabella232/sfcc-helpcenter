---
id: 06-categories-configuration
themes: cartridge-configuration
title: How to configure my categories?
popular: false
related: 01-where-configuration, 02-configure-PIM-API, 05-mapping-configuration, 04-import-images-configuration, 03-products-filter-configuration
---

# How to define which PIM master catalog I want to push to SFCC?

Within your Akeneo PIM instance, you may use different catalogs to manage your product data. The Akeneo connector for SFCC gives you the possibility to export one or several catalog IDs per website.
In the [cartridge configuration page](01-where-configuration.html), fill in the following parameter with the PIM catalog IDs of your choice:

| Cartridge parameter           | PIM information         |
| :-----------------------------| :---------------------: |
| Akeneo main catalogs          |  PIM catalogs ID        |

# How to define the status of your SFCC category trees?

In the [cartridge configuration page](01-where-configuration.html), select `Yes` for the below parameter if you want to push live the PIM category trees on your webstores directly. Otherwise, select `No`.

| Cartridge parameter           | SFCC information        |
| :-----------------------------| :---------------------: |
| Akeneo Category Online        |  Yes or No              |

# How to define automatically the "Primary" category for my SFCC products?

In the [cartridge configuration page](01-where-configuration.html), if you select `Yes` for the following parameter, the first category of products will become your "primary" category for that product (Please refer to [Salesforce documentation](https://documentation.b2c.commercecloud.salesforce.com/DOC2/topic/com.demandware.dochelp/Products/Classificationvsprimarycategory.html?resultof=%22%70%72%69%6d%61%72%79%22%20%22%63%61%74%65%67%6f%72%79%22%20) for better understand what is a primary category).

| Cartridge parameter                | SFCC information        |
| :----------------------------------| :---------------------: |
| Akeneo Product Primary Flag        |  Yes or No              |
