---
id: global-use-guidelines
themes: cartridge-installation
title: All you need to know before starting...
popular: true
related: download-cartridge, 01-where-configuration
---

*This page aims at sharing some best practices regarding our connector implementation and some basic guidelines to keep in mind.*

# What you need to know?
First of all, Akeneo Connector is a bridge between Akeneo PIM (in its core version) and Salesforce Commerce Cloud (in its core version). Why is it important to notice? Because our Akeneo Connector is an agnostic connector that is independent of customer's specificities. Our goal is to provide a solid technical basis to plug Akeneo PIM into a Salesforce Commerce Cloud instance. If some particularities are required, this is not a problem; ask your IT referral (integrator or IT team) to **[customize the connector](notion://www.notion.so/akeneo/Cheat-Sheet-054e422ca048464ca4d59a1237747093#what-are-the-best-practice-for-a-customization-of-the-connector)**.

Another important notion here is to consider that Akeneo Connectors are 3rd-party plug-ins and therefore, we are fully impacted by the SalesForce system limitations. Basically, SF is made to manage a massive volume of data, but with as little data transformation as possible. The very first rule you need to keep in mind is: "**When you model your product data in Akeneo PIM, always prefer a native SFCC approach**". This means that, if in SFCC a piece of data is managed as an integer, please highly prefer creating an integer field in your Akeneo PIM rather than considering the connector will take care of it (the connector will do the job, but the performance will decrease).

## Talking about performance
We are often asked about metrics and performance of Akeneo Connectors. Unfortunately, this is not that easy. In general, please note that four main criteria impact the performance of the connector:

* The catalog **volume**: even if that's the first one that comes to mind it is not the only one to consider.
* The catalog **complexity**: indeed, importing 500 000 products can be an easy task if the product is described by "just" a name, a description, and an image. However, if the product is very complex (high number of attributes, many reference entities, plenty of variations, etc.), importing 2 000 products can be a very painful and long process.
* The **SalesForce limitations**: in addition to what we already said in the introduction, and to preserve its own performances, [SalesForce limits some uses](https://documentation.b2c.commercecloud.salesforce.com/DOC2/advanced/content.jsp?topic=%2Fcom.demandware.dochelp%2FDWAPI%2Fquota%2Fhtml%2FAPI_Quotas.html).
* The **Media/Assets management**: Asset binaries are often cumbersome to synchronize to transfer from Akeneo PIM to SFCC. Imagine the time it takes to transfer and copy 80Go of assets through the connector to SFCC.

## So what can I do to preserve my connector's performances?
1. Always prefer direct data mapping between Akeneo PIM and SFCC, this way you don't need to rely on SF to convert the PIM data into the required format. By doing so, you will help your system to be more efficient.
2. One of the most impactful use is the Asset Binaries use. So if it is possible for you to consider using a DAM and the Asset Manager (media link & file link) instead of Image binaries directly uploaded in the PIM, you will save a lot of time. Prefer saving a string of characters (URL) versus an actual HD picture.
3. Challenge the amount of data you will copy over to Salesforce. You might have attributes on Akeneo PIM that are not needed for your storefront. Filtering them out of the synchronization can help you save some time during imports.

## Full import or partial import?
There are two ways to import product data:

* **Full import**: this is the longest import process because everything, including media, will be synchronized between Akeneo PIM and SFCC. However, this full import happens once for the very first synchronization used to actually build your catalog on SFCC side. Then, most of the time, it is automatically executed every night to resync everything. The four performance criteria highly impact this import process. This is why this process is often automated with a CRON task. To illustrate the catalog volume vs. complexity, please consider those figures:
|Industries|Product Amount|Average full import time|
| ------------- |:-------------:| -----:|
|Clothing - Streetwear | 250 000 | 6 hours|
|Luxury (way more complex) | 80 000 | 8 hours|

:::warning
Please consider those figures as indications and not as exact references
:::

* **Differential import**: Depending on the last successful import date, the system can sync only new products when it's necessary. However, to reconstruct some data on the SFCC side, some tasks have to be run as a full import anyway (e.g., categories are fully imported even in a differential import). However, this differential import process will allow you to decrease the needed import time. This type of import is used daily to resync data that has changed in the days. This one is often a manual operation.

You will have to define your data update policy to adjust the threshold between full import and differential import.

# What are the best practices to customize Akeneo Connector?

As part of our [**SFCC online training**] ([https://akademy.akeneo.com/akeneo-connector-fundamentals-sfcc](https://akademy.akeneo.com/akeneo-connector-fundamentals-sfcc)), here are the tech guidelines to help you create a customization on top of the Akeneo Core version of the cartridge:

1. As a standard practice in SFCC cartridge development, do not edit Akeneo Connector for SFCC directly. Create another cartridge (bc_akeneo_custom) and place it on the cartridge path before bc_akeneo. Customized files will be copied here. It will be helpful when newer versions of Akeneo Connector for SFCC are released.
2. The right approach is to generate a sample catalog with Akeneo Connector for the SFCC core version then to download the XMLs from the Impex location. After that, compare the customized version and check that it does not introduce any unexpected changes in the generated XMLs by comparing the two sets.

# How to ensure the success of my integration?

This is pretty easy: you should **test the Connector as early as possible in the integration process**. By doing so, you will challenge the data model and ensure the efficiency of the mapping.

You should ask yourself:

1. Are Akeneo **PIM and/or the eCommerce platform customized in any way**? If they are, that should raise a warning.
2. Are all the project actors **aware of their responsibilities?** Check the RACI, if there are any doubts, make sure everyone attends the [Akeneo Akademy Training](https://akademy.akeneo.com/). Confusions around responsibilities may lead to errors in commercial quotations and therefore unnecessary frustrations.
3. does the system integrator (or the IT team in charge of the integration) know that:
    1. every month, there will be a **new version** of Akeneo Connector and they will have to update their Connector accordingly (with or without customizations)?
    2. if there is a customization, the related **support** (level 1 to 3) and **maintenance** fall with the team that has developed this customization.
4. **The bigger** the catalog, the sooner the Connector has to be tested, especially in terms of performance and synchro data policy definition.
5. The more **complex** the catalog, the sooner the connector mapping has to be considered. waiting until the end of the project would take a lot more time which might lead to delaying the go-live date and create frustration.
6. Be brave, don't worry about trying out new things. Benefit from this opportunity to challenge your existing data model and to get rid of all the complexity inherited from a legacy solution. Our advice here is that this is better to modify an existing data model slightly on the eCommerce side to be able to efficiently map and smoothly import your data rather than recreating a legacy complexity in the PIM.
7. An Akeneo Connector will do what it is made for to plug any standard PIM into a standard version of Salesforce, by maintaining the highest performance and scalability for all its users. If Akeneo Connectors tests are not up to your performance standards, then there are two options for you:
    1. Not using the Akeneo Connector at all and creating yours from scratch (and we are totally fine with that)
    2. Creating customizations to enhance performances according to your performance standard.
