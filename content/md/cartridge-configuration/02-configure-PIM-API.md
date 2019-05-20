---
id: 02-configure-PIM-API
themes: cartridge-configuration
title: Configure your PIM API
popular: false
related: 01-where-configuration, 05-mapping-configuration, 04-import-images-configuration, 06-categories-configuration, 03-products-filter-configuration
---

# How to configure my PIM API?

Before setting up the Akeneo connector for SFCC, you first need to generate a "client ID" and a "secret" couple in the PIM to enable the API connection.

Please refer to our specific [documentation](https://api.akeneo.com/getting-started-admin.html) to do so.

Then, note the below information:
1. Your PIM URL (ex: https://mypim.cloud.akeneo.com)
2. Your PIM API `Client ID` and `Secret`
3. Your PIM user dedicated to the use of the API (`Username` and `Password`).

# How to configure the cartridge with my PIM API information?

In the [cartridge configuration page](01-where-configuration.html), fill in the below parameters with the PIM information collected above:

| Cartridge parameter           | PIM information    |
| :-----------------------------| :-----------------:|
| Akeneo Client ID              |  API Client ID     |
| Akeneo Secret                 |  API Secret        |
| Akeneo Login                  |  PIM user username |
| Akeneo Password               |  PIM user password |
| Akeneo Service General URL    |  PIM URL           |
