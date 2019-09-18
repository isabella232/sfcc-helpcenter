---
id: 08-reference-entities
themes: cartridge-configuration
title: How to retrieve PIM reference entities in SalesForce
popular: false
related: 01-where-configuration, 02-configure-PIM-API, 03-products-filter-configuration, 04-import-images-configuration, 05-mapping-configuration, 06-categories-configuration, 07-multi-storefront-configuration
---


# Understand the mapping PIM Reference Entities in SFCC

Since Akeneo Connector for SFCC `V19.8.0` version, the connector can manage PIM Reference Entities.

There are no special objects in SFCC corresponding to the PIM Reference Entities. Because of this limit, the connector imports the PIM reference entities to special SFCC **Content Asset** objects.

Each PIM reference entity will be represented by a “Content Asset” in SFCC.

For example, a PIM reference entity of a brand (code: “**brand**”) will be imported into a the Content Asset “akeneo_entity_**brand**” in SFCC.

PIM reference entity records will be imported as **JSON** objects into the corresponding custom attributes of the SFCC Content Asset.

For example, after successfully importing all PIM reference entity records, the JSON object of the “**dyson**” reference entity record (which is an element of the “**brand**” reference entity) will be available in SFCC as the “**akeneo_entity_brand_dyson**“ custom attribute of “**akeneo_entity_brand**” Content Asset.

:::warning
**Scalability limit:** by default, the connector does not automatically add any PIM reference entity record (as SFCC custom attributes) to any attribute group. Importing PIM reference entity records as JSON code, makes the structure becomes heavier.

Furthermore, having too many records may affect the loading of SFCC `Business Manager/Content Asset` page.
:::

Integrators/merchants can then choose one of these options:

* **Option 1:** make sure that the JSON structure of the `Content Asset attribute` is ok, they can manually add a selection of PIM reference entity records to the desired SFCC `attribute group`.

* **Option 2:** use **5-Akeneo-Entity-Record-Grouping** special job to automatically add some PIM reference entity records to an SFCC `attribute group`.

Before running the **5-Akeneo-Entity-Record-Grouping** job, the following two `Site Preferences` parameters must be configured according to your needs:

In the [connector configuration page](01-where-configuration.html), fill in the following connector parameter with your list of PIM **reference entity codes** and corresponding PIM **reference entity records codes**:

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

In the [connector configuration page](01-where-configuration.html), fill in the following second parameter with the SFCC Attribute group ID of Content Asset entity records (Attributes) or let this parameter empty to keep the default value:

| Connector parameter           | SFCC information               |
| :-----------------------------| :----------------------------: |
| Content Attribute Group ID    |  SFCC attribute group ID       |

#  How to choose in which SFCC "library" PIM references entities will be imported as Content Assets?

In the [connector configuration page](01-where-configuration.html), fill in the following parameter with your SFCC **shared** library ID or let this parameter empty to keep your site's **private** library as the destination of your PIM `Reference Entities`.

| Connector parameter   | SFCC information               |
| :---------------------| :----------------------------: |
| Shared Library Id     |  SFCC shared Library ID        |
