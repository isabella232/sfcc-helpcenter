---
id: 03-products-filter-configuration
themes: cartridge-configuration
title: How can I filter only PIM products I want to import in SFCC?
popular: false
related: 01-where-configuration, 02-configure-PIM-API, 04-import-images-configuration, 05-mapping-configuration, 06-categories-configuration, 07-multi-storefront-configuration
---

# How to import PIM product data from a specific channel?

In the [**connector configuration page**](01-where-configuration.html), you can decide which **PIM channel** you want to retrieve your product information from.

| Connector parameter   | PIM information  |
| :---------------------| :--------------: |
| Akeneo Scope          |  PIM channel ID  |

# How can I filter PIM products according to product properties, product model properties or product values?

In the [**connector configuration page**](01-where-configuration.html), with the following parameter, you can choose between a `Simple` or an `Advanced` filter to retrieve your PIM data:

| Connector parameter   | Filter mode      |
| :---------------------| :------------------: |
| Import Type           |  "Simple" or "Advanced"  |

If you select `Simple` **all** PIM product will be imported in SFCC.

If you select `Advanced`, the connector will **only import PIM products that match your search filters** defined in the `Import builder config` parameter.

For example, you can filter on product properties or product values...

::: warning
This field must be written in **JSON format**.<br>
<br>
To know all the filtering possibilities and the **JSON syntax**, please refer to this [documentation on the filters](https://api.akeneo.com/documentation/filter.html) of our API.
<br>


For example, the below filter enables to import products from `led_tvs` family whose completeness is greater than `99`% for `en_US` and `fr_FR` locales, for the channel `ecommerce`:

```json

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

:::info
Since SFCC Connector version 19.5.3, you can also filter "product value" and "locales".

For example, the below filter enables to import products with a completeness greater than `99%` in the `en_US` and `fr_FR` locales ine the `ecommerce` channel **and ONLY retrieves `name`, `description` and `mytext` attributes from these products**:

```json

{
    "search": {
        "completeness": [{
            "operator": ">",
            "value": 99,
            "locales": ["en_US", "fr_FR"],
            "scope": "ecommerce"
        }]
    },
    "attributes": ["name", "description", "mytext"]
}
```
:::
