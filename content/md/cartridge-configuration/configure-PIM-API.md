---
id: configure-PIM-API
themes: cartridge-configuration
title: Configure your PIM API
popular: false
related: where-configuration, mapping-configuration, import-images-configuration, categories-configuration, products-filter-configuration
---

# How to configure my PIM API?

Before starting to configure your cartridge to connect it to the PIM API, you must first generate a "client id" and "secret" couple in the PIM to allow the API connection.

Please refer to our specific [documentation](https://api.akeneo.com/getting-started-admin.html) for this action.

Then note these information from your PIM :
1. Your PIM URL (ex: https://mypim.cloud.akeneo.com)
2. Your PIM API `Client ID` and `Secret`
3. Your PIM user dedicated to the use of the API (`Username` and `Password`).

# How to configure the cartridge with my PIM API information?

In the [cartridge configuration page](where-configuration.html), fill in the following parameters with the PIM information collected in the previous step :

| Cartridge parameter           | PIM information    |
| :-----------------------------| :-----------------:|
| Akeneo Client ID              |  API Client ID     |
| Akeneo Secret                 |  API Secret        |
| Akeneo Login                  |  PIM user username |
| Akeneo Password               |  PIM user password |
| Akeneo Service General URL    |  PIM URL           |
