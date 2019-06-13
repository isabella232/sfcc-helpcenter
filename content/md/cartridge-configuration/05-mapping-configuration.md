---
id: 05-mapping-configuration
themes: cartridge-configuration
title: How to map PIM data content with SFCC data content?
popular: false
related: 01-where-configuration, 02-configure-PIM-API, 04-import-images-configuration, 06-categories-configuration, 03-products-filter-configuration
---
# Catalog mapping
## How to define which SFCC catalog will be used to spread your PIM product data?

In the [connector configuration page](01-where-configuration.html), fill in the below parameter with your SFCC "master catalog ID" for your website:

| Connector parameter           | SFCC information        |
| :-----------------------------| :---------------------: |
| Products Catalog ID           |  SFCC master catalog ID |

# Attribute mapping
## Why should I map PIM attributes with SFCC "default" product attributes?

By default, SFCC products include a handful of attributes assigned to each product: `Name`, `Brand`, `Manufacturer`, `Description`,...
For performance and cleaning reasons, it will be more convenient to map the default attributes with the PIM ones to avoid duplicates in the SFCC product edit forms. If no mapping is performed on a default attribute, SFCC will import the PIM attribute as a custom one. The attribute value will be populated in this custom attribute rather than the standard one.

## How to map PIM attributes with SFCC "default" product attributes?

In the [connector configuration page](01-where-configuration.html), you can define which PIM attributes you want to map with existing SFCC default product attributes.

| Connector parameter               | PIM/SFCC information                        |
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

Note: If you don't want to use this feature, please leave a space in curly brackets ({}).
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

Note: If you don't want to use this feature, please leave a space in curly brackets ({}).
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

Note: If you don't want to use this feature, please leave a space in curly brackets ({}).
:::

## How to map PIM "Product Associations" with Product "Links" in SFCC? (Connector V19.4.1 and higher)

By default, according to Salesforce guidance, PIM "product associations" should be mapped with SFCC product "recommendations" instead of product "links" (Please refer to the [SFCC documentation](https://documentation.b2c.commercecloud.salesforce.com/DOC2/index.jsp?topic=%2Fcom.demandware.dochelp%2FProducts%2FLinkingProducts.html&resultof=%22product%22%20%22link%22%20)).

But since Akeneo Connector for SFCC V19.4.1, in the [connector configuration page](01-where-configuration.html), you can define that PIM "product associations" can be mapped with SFCC product "links" by changing this parameter:


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

Note: If you don't want to use this feature, please leave a space in curly brackets ({}).
:::

# Product set (Connector V19.5.0 and higher)

## How to create SFCC "Product set" with the PIM?

As there is no concept of a **Product set** in the PIM, it is modelled by combining :
* A specific **Family** (allowing "Product set" attributes to be defined)
* A specific **Product association type** (allowing products to be associated with this "Product set").

To set up a "Product set" in your PIM you need therefore:
1. Create a "Product set" **Family** ()
2. Create a "Product set" **Association type** ()
3. Create a **Product** representing your "Product set" with the help of the "Product set" **Family** you previously created.
4. **Associate products** with the help of your "Product set" **Association** type to populate your product set.

## How to configure the Connector?

First, in the [connector configuration page](01-where-configuration.html), configure your "Product set" Family:

| Connector parameter         | PIM information              |
| :---------------------------| :--------------------------: |
| Product Set Family          |  PIM "Product set" Family ID |

Then, configure your "Product set" Association type:

| Connector parameter          | PIM information                        |
| :----------------------------| :------------------------------------: |
| Product Set Association Type |  PIM "Product set" Association type ID |
