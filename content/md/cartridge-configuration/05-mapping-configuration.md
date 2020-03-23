---
id: 05-mapping-configuration
themes: cartridge-configuration
title: How to map PIM data content with SFCC data content?
popular: false
related: 01-where-configuration, 02-configure-PIM-API, 03-products-filter-configuration, 04-import-images-configuration, 06-categories-configuration, 07-multi-storefront-configuration, 08-reference-entities
---
# Catalog mapping
## How to define which SFCC master catalog will be used to spread your PIM product data?

In the [connector configuration page](01-where-configuration.html), fill in the parameter below with your SFCC "master catalog ID" for your website:

| Connector parameter           | SFCC information        |
| :-----------------------------| :---------------------: |
| SFCC Master Catalog ID        |  SFCC master catalog ID |
| (or Products Catalog ID)      |                         |

## How to define which PIM categories will be used for my storefront catalog?

Since the **version 19.7.0** Akeneo connector, and depending on your needs, you can configure which PIM categories will be used for your storefront catalog.

In the [connector configuration page](01-where-configuration.html), fill in the parameter below with the PIM level category ID that represents your storefront categories:

| Connector parameter                       | PIM information         |
| :-----------------------------------------| :---------------------: |
| Top Level Category for Storefront Catalog |  PIM category ID        |

::: info
Want to know more? Please read our [documentation](07-multi-storefront-configuration.html) on how to manage multiple organizations, multiple storefronts with the Akeneo Connector for SFCC.
:::               


# Attribute mapping
## Why should I map PIM attributes with SFCC "default" product attributes?

By default, SFCC products include a handful of attributes assigned to each product: `Name`, `Brand`, `Manufacturer`, `Description`, etc.
For performance and cleaning purposes, it would be more convenient to map the default attributes with the PIM's to avoid duplicates in the SFCC product edit forms. If no mapping is performed on a default attribute, SFCC will import the PIM attribute as a custom one. The attribute value will be populated in this custom attribute rather than in the standard one.

## How to map PIM attributes with SFCC "default" product attributes?

In the [connector configuration page](01-where-configuration.html), you can define which PIM attributes you want to map with existing SFCC default product attributes.

| Connector parameter               | PIM/SFCC information                        |
| :---------------------------------| :-----------------------------------------: |
| Akeneo Product attributes mapping |  akeneo_PIMAttributeID : SFCC attribute ID  |

::: warning
This field must be written in JSON format.
Here is an example of content for this "Akeneo Product attributes mapping" parameter:
```json

{
    "matching": {
        "akeneo_name": "name",
        "akeneo_description": "longDescription",
        "akeneo_shortDescription": "shortDescription",
        "akeneo_ean": "EAN"
    }
}
```
Please note that each PIM attribute is prefixed with the "`akeneo_`" label in Salesforce Commerce Cloud.

Note: If you don't want to use this feature, please leave a space between curly brackets ({}).
:::

## How to map PIM attributes with SFCC "custom" product attributes?

In the [connector configuration page](01-where-configuration.html), you can define which PIM attributes you want to map with SFCC custom product attributes.

| Connector parameter               | PIM/SFCC information                               |
| :---------------------------------| :------------------------------------------------: |
| Akeneo Custom Attributes Mapping  |  akeneo_PIMAttributeID : SFCC custom attribute ID  |

::: warning
This field must be written in JSON format.
Here is an example of content for this "Akeneo Custom Attributes Mapping" parameter:
```json

{
    "matching": {
        "akeneo_size": "size",
        "akeneo_axisVar": "size",
        "akeneo_color": "color",
        "akeneo_displayDiagonal": "displaySize"            
    }
}
```
Please, note that each PIM attribute is prefixed with the `akeneo_` label in Salesforce Commerce Cloud.

Note: If you don't want to use this feature, please leave a space between curly brackets ({ }).
:::

# Product association mapping

## How to map PIM "Product Associations" with Product "Recommendations" in SFCC?

In the [connector configuration page](01-where-configuration.html), you can define which PIM association type you want to map with SFCC product recommendation type.

| Connector parameter            | PIM/SFCC information                                 |
| :------------------------------| :--------------------------------------------------: |
| Akeneo Recommendations Mapping |  "PIM_association_ID" : "Recommendation type number" |

::: warning
This field must be written in JSON format.
Here is an example of content for this "Akeneo Recommendations Mapping" parameter:
```json

{
    "matching": {
        "X_SELL" : 1,
        "UPSELL" : 2,
        "PACK" : 3,
        "SUBSTITUTION" : 4
    }
}
```
In this example:
X_SELL is the PIM product association type ID.
1 is the SFCC recommendation type number.

Note: If you don't want to use this feature, please leave a space between curly brackets ({ }).
:::

## How to map PIM "Product Associations" with Product "Links" in SFCC? (Connector V19.4.1 and higher)

::: warning
According to the Salesforce guidance, PIM "product associations" should be mapped with SFCC product "recommendations" instead of product "links" (Please refer to the [SFCC documentation](https://documentation.b2c.commercecloud.salesforce.com/DOC2/topic/com.demandware.dochelp/Products/linkingproducts.html)).
:::

But since the V19.4.1 Akeneo Connector for SFCC, in the [connector configuration page](01-where-configuration.html), you can define that PIM "product associations" can be mapped with SFCC product "links" by changing this parameter:


| Connector parameter            | PIM/SFCC information                                 |
| :------------------------------| :--------------------------------------------------: |
| Product Association Import to  | "Product Recommendation" (default) or "Product Link" |

Then you can define which PIM "association type" you want to map with SFCC product "link" type with the following parameter:

| Connector parameter         | PIM/SFCC information                        |
| :---------------------------| :-----------------------------------------: |
| Akeneo Product Link Mapping |  "PIM_association_ID" : "Product link type" |

::: warning
This field must be written in JSON format.
Here is an example of content for this "Akeneo Product Link Mapping" parameter:
```json

{
    "matching": {
        "X_SELL": "cross-sell",
        "UPSELL": "up-sell",
        "PACK": "other",
        "SUBSTITUTION": "replacement"
    }
}
```
In this example:
"X_SELL" is the PIM product association type ID.
"cross-sell" is the SFCC product link type ID.

Note: If you don't want to use this feature, please leave a space between curly brackets ({ }).
:::

# SFCC Product set (Connector V19.5.0 and higher)

## How to create an SFCC "Product set" with the PIM?

As there is no concept of a **Product set** in the PIM, it is modeled by combining:
* A specific **Family** (allowing "Product set" attributes to be defined)
* A specific **Product association type** (allowing products to be associated to this "Product set").

To set up a "Product set" in your PIM you need to:
1. Create a "Product set" **Family**
2. Create a "Product set" **Association type**
3. Create a **Product** representing your "Product set" with the help of the "Product set" **Family** you previously created.
4. **Associate products** with the help of your "Product set" **Association** type to populate your product set.

## How to configure the Connector for your "Product set"?

First, in the [connector configuration page](01-where-configuration.html), configure your "Product set" Family:

| Connector parameter         | PIM information              |
| :---------------------------| :--------------------------: |
| Product Set Family          |  PIM "Product set" Family ID |

Then, configure your "Product set" Association type:

| Connector parameter          | PIM information                        |
| :----------------------------| :------------------------------------: |
| Product Set Association Type |  PIM "Product set" Association type ID |

# SFCC Product bundle (Connector V19.9.0 and higher)

## How to create an SFCC "Product bundle" with the PIM?

As there is no such thing as a **Product bundle** in the PIM, it is modeled by combining:
* A specific **Family** (allowing "Product bundle" attributes to be defined)
* A specific **Product association type** (allowing products to be associated with this "Product bundle").

To set up a "Product bundle" in your PIM you need to:
1. Create a "Product bundle" **Family**
2. Create a "Product bundle" **Association type**
3. Create a **Product** representing your "Product bundle" with the help of the "Product bundle" **Family** you previously created.
4. **Associate products** with the help of your "Product bundle" **Association** type to populate your product bundle.

:::warning
**Limitation of this model:**
Since a product bundle is represented by a specific product association in the PIM, it is impossible to indicate **a quantity** for each product in this bundle.
It is therefore impossible to put the same product several times in an SFCC bundle.
:::


## How to configure the Connector for "Product bundle"?

First, in the [connector configuration page](01-where-configuration.html), configure your "Product bundle" Family:

| Connector parameter         | PIM information                 |
| :---------------------------| :-----------------------------: |
| Product Bundle Family       |  PIM "Product bundle" Family ID |

Then, configure your "Product bundle" Association type:

| Connector parameter             | PIM information                            |
| :-------------------------------| :-----------------------------------------: |
| Product Bundle Association Type |  PIM "Product bundle" Association type ID |


# Product model

## How to map PIM "product model" in SFCC?

### Product model with 1 level of variation

By default, without any configuration, PIM product models with 1 level of variation are modeled this way in SFCC:

**PIM Product models with 1 level of variation:**
- PIM product models `common` layer is mapped with SFCC `Variation master`
- PIM product models variation `level 1` part is mapped with SFCC `Variation products`

### Product model with 2 levels of variation (since v19.6.0)

Since SFCC v19.6.0, with the following parameter, you can obtain 2 types of modelization for product model with 2 levels of variation:

| Connector parameter          | PIM information                                 |
| :----------------------------| :--------------------------------------------:  |
| Model Import                 |  "Master-Variation" or "Master-Group-Variation" |


**Master-Variation modelization:**
- The PIM product models `common` part is mapped with SFCC `Variation master`
- The PIM product models variation `level 1` and variation `level 2` parts are mapped with SFCC `Variation products`

**Master-Group-Variation modelization:**
- The PIM product models `common` part is mapped with SFCC `Variation master`
- The PIM product models variation `level 1` part is mapped with SFCC `Variation group`
- The PIM product models variation `level 2` part is mapped with SFCC `Variation products`

We recommend you to use the "Master-Group-Variation" modelization instead, which will give you more flexibility in managing your product model with 2 levels of variation.

:::warning
**Known limitation:**
In the PIM, when you define a [**Family variant**](https://help.akeneo.com/pim/v3/articles/manage-your-families.html#create-a-new-family-variant) in order to create a **Product model**, you must define your **variation axes**.

In the PIM, an attribute of the family could be a variant axis only if its attribute type is structured:
- Simple select
- Simple reference data
- Reference entity single link (EE only)
- Metric
- Boolean (Yes/No)

But the current version of the Akeneo Connector for SFCC only retrieves product models based on "size" or "color" **simple select** attribute type to define the variation axis.

We are currently working to improve our connector compared to SFCC capabilities to take into account other attribute types.
:::
