---
id: 03-products-filter-configuration
themes: cartridge-configuration
title: How can I filter only PIM products I want to import in SFCC?
popular: false
related: 01-where-configuration, 02-configure-PIM-API, 05-mapping-configuration, 04-import-images-configuration, 06-categories-configuration
---

# How to import PIM product data from a specific channel?

In the [**cartridge configuration page**](01-where-configuration.html), you can decide which **PIM channel** you want to retrieve your product information from.

| Cartridge parameter   | PIM information  |
| :---------------------| :--------------: |
| Akeneo Scope          |  PIM channel ID  |

# How can I filter PIM products according to product properties, product model properties or product values?

In the [**cartridge configuration page**](01-where-configuration.html), with the following parameter, you can choose between a `Simple` or an `Advanced` filter to retrieve your PIM data:

| Cartridge parameter   | Filter mode      |
| :---------------------| :------------------: |
| Import Type           |  "Simple" or "Advanced"  |

If you select `Simple` **all** PIM product will be imported in SFCC.

If you select `Advanced`, the cartridge will **only import PIM products that match your search filters** defined in the `Import builder config` parameter.

::: warning
This field must be written in **JSON format**.<br>
<br>
To know all the filtering possibilities and the **JSON syntax**, please refer to this [documentation on the filters](https://api.akeneo.com/documentation/filter.html) of our API.

For example, the below filter enables to import products from `led_tvs` family whose completeness is greater than `99`% for `en_US` and `fr_FR` locales, for the channel `ecommerce`:

```
{
	"search": {
                "family":[{
                        "operator":"IN",
                         "value":["led_tvs"]
                }],
		"completeness": [{
			"operator": ">",
			"value": 99,
			"locales": ["en_US", "fr_FR"],
			"scope": "ecommerce"
		}]
	}
}

```
:::
