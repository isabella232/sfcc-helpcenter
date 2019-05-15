---
id: products-filter-configuration
themes: cartridge-configuration
title: How can I filter only PIM products I want to import in SFCC?
popular: false
related: where-configuration, configure-PIM-API, mapping-configuration, import-images-configuration, categories-configuration
---

# How to import PIM product data from a specific channel?

In the [**cartridge configuration page**](where-configuration.html), you can filter from which **PIM channel** you want to retrieve your product information.

| Cartridge parameter   | PIM information  |
| :---------------------| :--------------: |
| Akeneo Scope          |  PIM channel ID  |

# How can I filter PIM products according to product properties, product model properties or product values ?

In the [**cartridge configuration page**](where-configuration.html), with the following parameter, you can choose between a `Simple` or an `Advanced` filter to retrieve PIM data :

| Cartridge parameter   | Filter mode      |
| :---------------------| :------------------: |
| Import Type           |  "Simple" or "Advanced"  |

If you select `Simple` **all** PIM product are imported in SFCC.

If you select `Advanced`, the cartridge **only imports PIM products that match your search filters** defined in the `Import builder config` parameter.

::: warning
This field must be in **JSON format**.<br>
<br>
To know all the filtering possibilities and the **JSON syntax**, please refer to this [documentation on the filters](https://api.akeneo.com/documentation/filter.html) of our API.

For example, this filter allows you to import only products from `led_tvs` family, having a completeness greater than `99`% for `en_US` and `fr_FR` locales and for the channel `ecommerce` :

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
