---
id: where-product-association
themes: find-data
title: Where can I find my PIM product associations?
popular: false
related: where-categories, where-family, where-groups, where-attributes
---

# How to find my PIM product associations in SFCC?

1. Select your SFCC site, then click on `Merchant Tools`
2. Then click on `Products` menu
3. Use the search engine to find the product you want to know about its product associations.
4. Click on the `Recommendations` tab of this product.

![Product association](../img/sfcc-where-association.png)

:::info
Depending on the [configuration of your cartridge](05-mapping-configuration.html#product-association-mapping), the `Recommendation Type` column will indicate the PIM `association type` used.
:::

# What about "product links" in SFCC?

Salesforce recommends using `Recommendations` instead of `Product links` in SFCC for product association (please refer to the Salesforce documentation).

:::info
 However, aware that some customers still use the notion of `product links` in SFCC for their product association, we have also added the possibility to map **PIM product associations** to **SFCC Product links** since **version 19.3.3** of the cartridge.<br>
 Please consult the [specific configuration](05-mapping-configuration.html) for this feature.
:::
