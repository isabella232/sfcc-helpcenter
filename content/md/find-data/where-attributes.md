---
id: where-attributes
themes: find-data
title: Where can I find my PIM product attributes?
popular: false
related: where-categories, where-family, where-groups, where-product-association
---

# Where to find my PIM products in SFCC?

1. Select your SFCC site, then click on `Merchant Tools`
2. Then click on `Products` menu

![Product menu](../img/sfcc-where-products.png)

:::info
On the **Products** page, if you want to see all your products, **click on the `Find` button** (By default, no products appear in the list... ).
If you are looking for a specific product, use the search bar.  
:::

![Product list](../img/sfcc-where-products-list.png)

# Where to find my PIM product models in SFCC?

1. Select your SFCC site, then click on `Merchant Tools`
2. Then click on `Products` menu

![Product menu](../img/sfcc-where-products.png)

::: info
**Mapping between your PIM and SFCC instances:**
The Akeneo connector maps PIM product models this way:

**PIM Product models with 1 level of variation:**
- PIM product models `common` layer is mapped with SFCC `Variation master`
- PIM product models variation `level 1` part is mapped with SFCC `Variation products`

**PIM Product model with 2 levels of variation:**
- PIM product models `common` part is mapped with SFCC `Variation master`
- PIM product models variation `level 1`+ variation `level 2` parts are mapped with SFCC `Variation products`
:::

# Where to find my PIM product attributes in SFCC?

1. On the **Products** page, search for your product
2. Click on the selected product
3. Click on the `Lock` link in the top alert *"You haven't locked this product for editing. Click `Lock` if you need to edit the product."* to be able to edit product attributes.

:::info
With this last action, you could manipulate some attributes more easily such as, for example, the ability to click on the image attribute `Edit` button in order to see all product images.)
:::

![Edit Product](../img/sfcc-where-edit-product.png)

:::warning
After your product attributes review, **don't forget to click on the `Unlock` link** in the top alert *"You've locked this product for editing. Click* `Unlock` *to release."*
:::

You will find on this page all your PIM product attributes.

Depending on the [configuration of your cartridge](05-mapping-configuration.html) concerning the mapping of SFCC attributes:
- Some PIM attributes could be mapped with SFCC product default attributes
- The remaining PIM attributes will appear in the `Akeneo Attributes` part of the page

Each PIM attribute is prefixed with the ``akeneo_`` label.

![Akeneo attributes](../img/sfcc-akeneo-attributes.png)

:::info
In the `Akeneo attributes` part of your product, you may notice some attributes that do not belong to the family your product belongs to.

Indeed, there's no such thing as Family in Salesforce Commerce Cloud. Each product in SFCC will be assigned all PIM attributes by default.
:::

# Where to find my PIM "localizable" attributes in SFCC?

1. On the **Products** page, search for your product
2. Click on the selected product
3. Choose the language in the `Select Language` list on the product page, knowing that:
- The `Default` language will be populated with the content of non-localizable attributes.
- The other set languages in SFCC, matching with set languages in the PIM, will be populated with the content of localizable attributes (For example, if you have 3 languages for your products in the PIM (`fr_FR`, `en_US` and `de_DE`), you will find the content of your attributes in the `French (France)`, `English (United States)` and `German (Germany)` languages in Salesforce Commerce Cloud.

# What about PIM "scopable" attributes in SFCC?

Depending on the [configuration of your cartridge](03-products-filter-configuration.html) regarding the scope preference: the Akeneo connector will only import the attribute values of the specified channel.
