---
id: where-product-association
themes: find-data
title: Where can I find my PIM product associations?
popular: false
related: where-categories, where-family, where-groups, where-attributes
---

# Where to find my PIM product associations in SFCC?

1. Select your SFCC site, then click on `Merchant Tools`
2. Then click on `Products` menu
3. Use the search engine to find the product associations bound to your product.
4. Click on the `Recommendations` tab of this product.

![Product association](../img/sfcc-where-association.png)

:::info
Depending on the [configuration of your cartridge](05-mapping-configuration.html#product-association-mapping), the `Recommendation Type` column will indicate the PIM `association type` used.
:::

# What about "product links" in SFCC?

Salesforce recommends to use `Recommendations` instead of `Product links` in Commerce Cloud for product association. Please refer to [Salesforce documentation](https://documentation.b2c.commercecloud.salesforce.com/DOC2/topic/com.demandware.dochelp/Products/LinkingProducts.html?resultof=%22%50%72%6f%64%75%63%74%22%20%22%70%72%6f%64%75%63%74%22%20%22%6c%69%6e%6b%22%20) for more details.

:::info
However, please note that some users could use the `product links` feature to handle their product associations in SFCC. We have also added the possibility to map **PIM product associations** with **SFCC Product links** since **version 19.3.3** of the Akeneo connector.<br>
Please have a look at the [specific configuration](05-mapping-configuration.html) for this feature.
:::
