---
id: 05-mapping-configuration
themes: cartridge-configuration
title: How to map PIM data content with SFCC data content?
popular: false
related: 01-where-configuration, 02-configure-PIM-API, 04-import-images-configuration, 06-categories-configuration, 03-products-filter-configuration
---
# Catalog mapping
## How to define the SFCC catalog where PIM product data will be stored?

In the [cartridge configuration page](01-where-configuration.html), fill the following parameter with your SFCC "master catalog" for your site:

| Cartridge parameter           | SFCC information        |
| :-----------------------------| :---------------------: |
| Products Catalog ID           |  SFCC master catalog ID |

# Attribute mapping
## Why mapping PIM attributes with SFCC "default" product attributes?

By default, SFCC products include attributes to describe the product: `Name`, `Brand`, `Manufacturer`, `Description`,...
It is sometimes useful to fill these attributes with PIM attributes content rather than create new custom ones... ;-)

## How to map PIM attributes with SFCC "default" product attributes?

In the [cartridge configuration page](01-where-configuration.html), you can define which PIM attributes you want to map with which SFCC default product attributes.

| Cartridge parameter               | PIM/SFCC information                        |
| :---------------------------------| :-----------------------------------------: |
| Akeneo Product attributes mapping |  akeneo_PIMAttributeID : SFCC attribute ID  |

::: warning
This field must be in JSON format.
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
Remember that each PIM attributes are prefixed with the "`akeneo_`" label in SFCC.

:::

## How to map PIM attributes with SFCC "custom" product attributes?

In the [cartridge configuration page](01-where-configuration.html), you can define which PIM attributes you want to map with which SFCC custom product attributes.

| Cartridge parameter               | PIM/SFCC information                               |
| :---------------------------------| :------------------------------------------------: |
| Akeneo Custom Attributes Mapping  |  akeneo_PIMAttributeID : SFCC custom attribute ID  |

::: warning
This field must be in JSON format.
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
Don't forget that each PIM attributes are prefixed with the `akeneo_` label in SFCC.

:::

# Product association mapping

## How to map PIM "product association" type with SFCC product "recommendation" type?

In the [cartridge configuration page](01-where-configuration.html), you can define which PIM association type you want to map with which SFCC product "recommendation" type.

| Cartridge parameter            | PIM/SFCC information                           |
| :------------------------------| :--------------------------------------------: |
| Akeneo Recommendations Mapping |  PIM_association_ID/recommendation type number |

::: warning
This field must be in JSON format.
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
:::

## How to map PIM "product association" type with SFCC product "link" type? (since SFCC Cartridge V19.3.3 only)

By default, according to Salesforce guidance, PIM "product association" is mapped with SFCC product "recommendation".

Since SFCC Cartridge V19.3.3, in the [cartridge configuration page](01-where-configuration.html), you can define that PIM "product association" is mapped with SFCC product "link" by changing this parameter:


| Cartridge parameter            | PIM/SFCC information                                 |
| :------------------------------| :--------------------------------------------------: |
| Product Association Import to  | "Product Recommendation" (default) or "Product Link" |

Then you can define which PIM "association type" you want to map with which SFCC product "link" type with this parameter:

| Cartridge parameter         | PIM/SFCC information                  |
| :---------------------------| :-----------------------------------: |
| Akeneo Product Link Mapping |  PIM_association_ID/product link type |

::: warning
This field must be in JSON format.
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
:::
