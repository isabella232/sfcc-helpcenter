---
id: 05-mapping-configuration
themes: cartridge-configuration
title: How to map PIM data content with SFCC data content?
popular: false
related: 01-where-configuration, 02-configure-PIM-API, 04-import-images-configuration, 06-categories-configuration, 03-products-filter-configuration
---
# Catalog mapping
## How to define which SFCC catalog will be used to spread your PIM product data?

In the [cartridge configuration page](01-where-configuration.html), fill in the below parameter with your SFCC "master catalog ID" for your website:

| Cartridge parameter           | SFCC information        |
| :-----------------------------| :---------------------: |
| Products Catalog ID           |  SFCC master catalog ID |

# Attribute mapping
## Why should I map PIM attributes with SFCC "default" product attributes?

By default, SFCC products include a handful of attributes assigned to each product: `Name`, `Brand`, `Manufacturer`, `Description`,...
For performance and cleaning reasons, it will be more convenient to map the default attributes with the PIM ones to avoid duplicates in the SFCC product edit forms. If no mapping is performed on a default attribute, SFCC will import the PIM attribute as a custom one. The attribute value will be populated in this custom attribute rather than the standard one. 

## How to map PIM attributes with SFCC "default" product attributes?

In the [cartridge configuration page](01-where-configuration.html), you can define which PIM attributes you want to map with existing SFCC default product attributes.

| Cartridge parameter               | PIM/SFCC information                        |
| :---------------------------------| :-----------------------------------------: |
| Akeneo Product attributes mapping |  akeneo_PIMAttributeID : SFCC attribute ID  |

::: warning
This field must be written in JSON format.
Here is an example of content for this "Akeneo Product attributes mapping" parameter:
```
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

:::

## How to map PIM attributes with SFCC "custom" product attributes?

In the [cartridge configuration page](01-where-configuration.html), you can define which PIM attributes you want to map with SFCC custom product attributes.

| Cartridge parameter               | PIM/SFCC information                               |
| :---------------------------------| :------------------------------------------------: |
| Akeneo Custom Attributes Mapping  |  akeneo_PIMAttributeID : SFCC custom attribute ID  |

::: warning
This field must be written in JSON format.
Here is an example of content for this "Akeneo Custom Attributes Mapping" parameter:
```
{
	"matching": {
               "akeneo_size": "size",
               "akeneo_axisVar": "size",
               "akeneo_color": "color",
               "akeneo_displayDiagonal": "displaySize"            
	}
}
```
Note that each PIM attribute is prefixed with the `akeneo_` label in Salesforce Commerce Cloud.

:::

# Product association mapping

## How to map PIM "Product Associations" with Product "Recommendations" in SFCC?

In the [cartridge configuration page](01-where-configuration.html), you can define which PIM association type you want to map with SFCC product recommendation type.

| Cartridge parameter            | PIM/SFCC information                           |
| :------------------------------| :--------------------------------------------: |
| Akeneo Recommendations Mapping |  PIM_association_ID/recommendation type number |

::: warning
This field must be written in JSON format.
Here is an example of content for this "Akeneo Recommendations Mapping" parameter:
```
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
:::

## How to map PIM "Product Associations" with Product "Links" in SFCC? (available for V19.3.3 of the connector and higher)

By default, according to Salesforce guidance, PIM "product associations" should be mapped with SFCC product "recommendations" instead of product "link" (Please refer to the [SFCC documentation](https://documentation.b2c.commercecloud.salesforce.com/DOC2/index.jsp?topic=%2Fcom.demandware.dochelp%2FProducts%2FLinkingProducts.html&resultof=%22product%22%20%22link%22%20)).

But since SFCC Cartridge V19.3.3, in the [cartridge configuration page](01-where-configuration.html), you can define that PIM "product associations" can be mapped with SFCC product "links" by changing this parameter:


| Cartridge parameter            | PIM/SFCC information                                 |
| :------------------------------| :--------------------------------------------------: |
| Product Association Import to  | "Product Recommendation" (default) or "Product Link" |

Then you can define which PIM "association type" you want to map with SFCC product "link" type with the following parameter:

| Cartridge parameter         | PIM/SFCC information                  |
| :---------------------------| :-----------------------------------: |
| Akeneo Product Link Mapping |  PIM_association_ID/product link type |

::: warning
This field must be written in JSON format.
Here is an example of content for this "Akeneo Product Link Mapping" parameter:
```
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
:::
