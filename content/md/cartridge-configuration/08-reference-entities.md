---
id: 08-reference-entities
themes: cartridge-configuration
title: How to retrieve PIM Reference Entities
popular: false
related: 01-where-configuration, 02-configure-PIM-API, 03-products-filter-configuration, 04-import-images-configuration, 05-mapping-configuration, 06-categories-configuration, 07-multi-storefront-configuration
---


# Understand the difficulty of mapping PIM Reference Entities in SFCC...

Since Akeneo Connector for SFCC `V19.8.0`, the Connector can manage PIM Reference Entity.

There are no special objects in SFCC corresponding to PIM Reference Entities. Because of this limit, the connector imports the PIM `Reference Entities` to special SFCC `Content Asset` objects.

Each PIM `Reference Entity` will be represented by a `Content Asset` in SFCC.

For example, a PIM `Reference Entity` of a brand (code: “**brand**”) will be imported into a the `Content Asset` “akeneo_entity_**brand**” in SFCC.

PIM `Reference Entity Records` will be imported as **JSON** objects into the corresponding `custom attributes` of the SFCC `Content Asset`.

For example, after successfully importing all PIM `Reference Entity Records`, the JSON object of `Reference Entity Record` “**dyson**” (an element of `Reference Entity` “**brand**”) will be available in SFCC as `custom attribute` “**akeneo_entity_brand_dyson**“ of `Content Asset`  “**akeneo_entity_brand**”.

:::warning
**Scalability limit:** by default, the connector does not automatically add any PIM `Reference Entity Record` (as SFCC `custom attributes`) to any `attribute group`.

This is due to the fact that when importing PIM `Reference entity Records` as **JSON** code, the structure becomes too heavy. Furthermore, when there are too many of them, it may cause problems when trying to load SFCC `Content Asset page` in `Business Manager` (because the page becomes too heavy).
:::

Integrators/Merchants can then choose one of these options:

* **Option 1:** To make sure that the JSON structure of `Content Asset attribute` is ok, Integrators/Merchants can manually add a selection of PIM `Reference Entity Records` to the SFCC `attribute group` of their choice.

* **Option 2:** Integrators/Merchants can use **5-Akeneo-Entity-Record-Grouping** special job to automatically add some of PIM `Reference Entity Records` to an SFCC `attribute group`.

Before running the **5-Akeneo-Entity-Record-Grouping** job, the following `Site Preferences` (2 parameters) can be configured according to your needs:

In the [connector configuration page](01-where-configuration.html), fill in the following parameter with your list of PIM `Reference Entity` **Codes** and corresponding PIM `Reference Entity Records` **Codes**:

| Connector parameter           | PIM information                     |
| :-----------------------------| :---------------------------------: |
| Entity Records In Group       |  JSON structure: Reference Entity<br>Codes and corresponding Reference<br>Entity Records Code.               |    

Example :

```json

[
    {
        "entity_id": "brand",
        "entity_record_ids": ["alessi", "fatboy", "fermob"]
    },
    {
        "entity_id": "designer",
        "entity_record_ids": ["arad", "dyson", "newson"]
    },
    {
        "entity_id": "color",
        "entity_record_ids": ["bluestorm", "redchilli", "redpoppy"]
    }
]

```

In the [connector configuration page](01-where-configuration.html), fill in the following parameter with the SFCC Attribute group ID of Content Asset entity records (Attributes) or let this parameter empty to keep the default value:

| Connector parameter           | SFCC information               |
| :-----------------------------| :----------------------------: |
| Content Attribute Group ID    |  SFCC attribute group ID       |

#  How to choose in which SFCC "library", PIM References Entities will be imported as Content Assets?

In the [connector configuration page](01-where-configuration.html), fill in the following parameter with your SFCC **shared** library ID or let this parameter empty to keep your site's **private** library as the destination of your PIM `Reference Entities`.

| Connector parameter   | SFCC information               |
| :---------------------| :----------------------------: |
| Shared Library Id     |  SFCC shared Library ID        |
