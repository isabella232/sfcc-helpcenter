---
id: 06-categories-configuration
themes: cartridge-configuration
title: How to configure my categories?
popular: false
related: 01-where-configuration, 02-configure-PIM-API, 05-mapping-configuration, 04-import-images-configuration, 03-products-filter-configuration
---

# How to define which PIM catalog will be online on the site?

In the [cartridge configuration page](01-where-configuration.html), fill the following parameter with your PIM catalog ID (you can set up several PIM catalogs):

| Cartridge parameter           | PIM information         |
| :-----------------------------| :---------------------: |
| Akeneo main catalogs          |  PIM catalogs ID        |

# How to define that the SFCC category trees will be directly online or not?

In the [cartridge configuration page](01-where-configuration.html), select `Yes` for the following parameter if you want that PIM category trees be directly online on you site, otherwise select `No`.

| Cartridge parameter           | SFCC information        |
| :-----------------------------| :---------------------: |
| Akeneo Category Online        |  Yes or No              |

# How to define automatically the "Primary" category for my SFCC products?

In the [cartridge configuration page](01-where-configuration.html), if you select `Yes` for the following parameter, the first category of products will become "primary" category for that product.

| Cartridge parameter                | SFCC information        |
| :----------------------------------| :---------------------: |
| Akeneo Product Primary Flag        |  Yes or No              |
