---
id: 03-products-filter-configuration
themes: cartridge-configuration
title: How can I filter only the PIM products I want to import in SFCC?
popular: false
related: 01-where-configuration, 02-configure-PIM-API, 04-import-images-configuration, 05-mapping-configuration, 06-categories-configuration, 07-multi-storefront-configuration, 08-reference-entities
---

# How to import PIM product data from a specific channel?

In the [**connector configuration page**](01-where-configuration.html), you can decide from which **PIM channel** you want to retrieve your product information.

| Connector parameter   | PIM information  |
| :---------------------| :--------------: |
| Akeneo Scope          |  PIM channel ID  |

# How can I filter PIM products according to product properties, product model properties or product values?

In the [**connector configuration page**](01-where-configuration.html), with the following parameter, you can choose between a `Simple` or an `Advanced` filter to retrieve your PIM data:

| Connector parameter   | Filter mode      |
| :---------------------| :------------------: |
| Import Type           |  "Simple" or "Advanced"  |

If you select `Simple` **all** PIM products will be imported in SFCC.

If you select `Advanced`, the connector will **only import the PIM products that match the search filters** defined in the `Import builder config` parameters. You will use the `Product Model Import builder config` to filter product models and the `Products Import builder config` to filter Products).

For example, you can filter product properties or product values.

::: warning
This field must be written in **JSON**.<br>
<br>
To discover all the filtering possibilities of our API and the **JSON syntax**, please refer to this [documentation](https://api.akeneo.com/documentation/filter.html).
<br>


For example, the filter below enables you to import products from the `led_tvs` family when the completeness is greater than `99`% for the `en_US` and `fr_FR` locales, for the `ecommerce` channel:

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

::: warning

It is important to understand that there is a inheritance link between the filter on **products** (`Products Import builder config`) and the filter on **product models** (`Product Model Import builder config`).  

Indeed, a product with 2 levels of variation is a structure with:
* A `product model` for the **common part**
* A `product model` for **variation level 1** (example: "color")
* A `product` for **variation level 2** (example: "size")

As the `product` for **variation level 2** part inherits data from its 2 `product models` parent levels, if you apply a filter on a `product model` part, you have to put the same filter on the `product` part.

:::


Since the SFCC Connector version 19.5.3, you can also filter "product value" and "locales".

For example, the filter below enables you to import products with a completeness greater than `99%` in the `en_US` and `fr_FR` locales in the `ecommerce` channel. **It ONLY retrieves the following attributes: `name`, `description` and `mytext`**:

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

# How can I synchronize my product PIM status with the SalesForce online status (onlineFlag)?

Since the 20.2.2 version, you are able to configure in the [**connector configuration page**](01-where-configuration.html), how you want to synchronize your PIM Product status with Salesforce:

![Connector configuration](../img/sfcc-cartridge-PIM-status-synchro.png)

This configuration will allow you to map the PIM product status
![PIM configuration](../img/sfcc-cartridge-PIM-status-set.png)
with the SalesForce online status:
![SalesForce configuration](../img/sfcc-cartridge-sf-onlineStatus.png)

:::info
The use of this feature will overwrite the manual link you maybe created according to the SalesForce system attribute mapping described into the [filter configuration page](05-mapping-configuration.html)
:::
