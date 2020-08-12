---
id: 09-reference-entities
themes: cartridge-configuration
title: Manage your Reference entities synchronization
popular: false
related: 01-where-configuration, 02-configure-PIM-API, 03-products-filter-configuration, 04-import-images-configuration, 05-import-media-configuration, 06-mapping-configuration, 07-categories-configuration, 08-multi-storefront-configuration
---


# Understand the PIM reference entities mapping in SFCC

Since the `V19.8.0` version of the Akeneo Connector for SFCC, the connector can manage PIM reference entities.

Reference entities in the PIM don't have an exact equivalent in SFCC. This is the reason why `reference entities` will be imported as  `Content Asset` objects.

Each PIM reference entity will be represented by a `Content Asset` in SFCC.

For example, a PIM `reference entity` of a given brand (code: “**brand**”) will be imported as a `Content Asset` “akeneo_entity **brand**” in SFCC.

PIM `reference entity records` will be imported as **JSON** objects in the corresponding `custom attributes` of the SFCC `Content Asset`.

To be extra clear, let's take a look at a specific example.
First of all, you need to import all your PIM `reference entity records`. Among them all, you can find, for example, a JSON object of the “**dyson**” `reference entity record`. It belongs to the the “**brand**” reference entity. In SFCC, it will be available as a “**akeneo_entity_brand_dyson**“ `custom attribute` of “**akeneo_entity_brand**” `Content Asset`.

:::warning
**Scalability limit:** When importing PIM `reference entity records`, the SFCC connector doesn't automatically add them as SFCC custom attributes, to the SFCC `attribute group`. That is because importing PIM `reference entity records` as JSON code impacts SFCC performance and can cause SFCC scalability issues.

 By default, the connector does not automatically add the PIM `reference entity record`, as SFCC custom attributes, to the SFCC `attribute group`. Importing PIM `reference entity records` as JSON code impacts performance.

This is why having too many `reference entity records` will definitely impact the loading of the SFCC `Business Manager/Content Asset` page.
:::

You can therefore choose one of those two options:

* **Option 1:** You need to make sure that the JSON structure of the `Content Asset attribute` is correct. You can manually add a selection of PIM `reference entity records` to the desired SFCC `attribute group`.

* **Option 2:** You can use the **5-Akeneo-Entity-Record-Grouping** special job to automatically add some PIM `reference entity records` to an SFCC `attribute group`.

Before running the **5-Akeneo-Entity-Record-Grouping** job, the two `Site Preferences` parameters below must be configured according to your needs:

In the [connector configuration page](01-where-configuration.html), fill in the following connector parameter with your list of PIM **reference entity codes** and corresponding PIM **reference entity records codes**:

| Connector parameter           | PIM information                     |
| :-----------------------------| :---------------------------------: |
| Entity Records In Group       |  JSON structure: reference entity<br>codes and corresponding reference<br>entity records code.               |    

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

In the [connector configuration page](01-where-configuration.html), fill in the second parameter with the SFCC Attribute group ID of Content Asset entity records (Attributes) or leave this parameter empty to keep the default value:

| Connector parameter           | SFCC information               |
| :-----------------------------| :----------------------------: |
| Content Attribute Group ID    |  SFCC attribute group ID       |

#  How to choose in which SFCC "library" PIM references entities will be imported as Content Assets?

In the [connector configuration page](01-where-configuration.html), fill in the following parameter with your SFCC **shared** library ID or leave this parameter empty to keep your site's **private** library as the destination of your PIM `reference entities`.

| Connector parameter   | SFCC information               |
| :---------------------| :----------------------------: |
| Shared Library Id     |  SFCC shared Library ID        |
