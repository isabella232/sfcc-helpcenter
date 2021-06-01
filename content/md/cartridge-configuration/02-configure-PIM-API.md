---
id: 02-configure-PIM-API
themes: cartridge-configuration
title: Configure your PIM API
popular: false
related: 01-where-configuration, 03-products-filter-configuration, 04-import-images-configuration, 05-import-media-configuration, 06-mapping-configuration, 07-categories-configuration, 08-multi-storefront-configuration, 09-reference-entities
---

# How to configure my PIM API?

Before setting up the Akeneo Connector for SFCC, you first need to generate a "client ID" and "secret" couple in the PIM to enable the API connection.

Please refer to our specific [documentation](https://api.akeneo.com/documentation/authentication.html#authentication) to do so.

You will be given the following items:
1. Your PIM URL (ex: https://mypim.cloud.akeneo.com)
2. Your PIM API `Client ID` and `Secret`
3. Your PIM user who will be dedicated to the use of the API (`Username` and `Password`).
Make sure you save them as you'll need them later.

# How to configure the connector with my PIM API information?

In the [connector configuration page](01-where-configuration.html), fill in the parameters below with the PIM information collected above:

| Connector parameter           | PIM information    |
| :-----------------------------| :-----------------:|
| Akeneo Client ID              |  API Client ID     |
| Akeneo Secret                 |  API Secret        |
| Akeneo Login                  |  PIM user username |
| Akeneo Password               |  PIM user password |
| Akeneo Service General URL    |  PIM URL           |

:::info
In the case of an Akeneo API unavailability, there is no automatic procedure to re-connect. However, the connector will try three times to reach the API before stopping.
:::
