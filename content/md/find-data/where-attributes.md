---
id: where-attributes
themes: find-data
title: Where can I find my PIM product attributes?
popular: false
related: where-categories, where-family, where-groups, where-product-association
---

# How to find my PIM products in SFCC?

1. Select your SFCC site, then click on `Merchant Tools`
2. Then click on `Products` menu

![Product menu](../img/sfcc-where-products.png)

:::info
On the **Products** page, if you want to see all your products, **don't forget to click on the `Find` button** (By default, no products appear in the list... ).<br>
If you are looking for a specific product, use the search field.  
:::

![Product list](../img/sfcc-where-products-list.png)

# How to find my PIM product models in SFCC?

1. Select your SFCC site, then click on `Merchant Tools`
2. Then click on `Products` menu

![Product menu](../img/sfcc-where-products.png)

::: info
**Mapping between your PIM and SFCC:**<br>
The SFCC cartridge maps PIM product model like this :

**PIM Product model with 1 level of variation:**<br>
- PIM product model `common` part is mapped onto SFCC `Variation master`<br>
- PIM product model variation `level 1` part is mapped onto SFCC `Variation products`

**PIM Product model with 2 level of variation:**<br>
- PIM product model `common` part is mapped onto SFCC `Variation master`<br>
- PIM product model variation `level 1`+ variation part `level 2` are mapped onto SFCC `Variation products`
:::

![Product list](../img/sfcc-where-products-list.png)

# How to find my PIM product attributes in SFCC?

1. On the **Products** page, search your product
2. Click on your selected product
3. Click on the `Lock` link in the top alert *"You haven't locked this product for editing. Click `Lock` if you need to edit the product."* to be able to edit the product attributes.

:::info
With this last manipulation, you will be able to manipulate some attributes more easily such as, for example, the ability to click on the image attribute `Edit` button in order to see all product images.)
:::

![Edit Product](../img/sfcc-where-edit-product.png)

:::warning
After your product attributes review, **don't forget to click on the `Unlock` link** in the top alert *"You've locked this product for editing. Click* `Unlock` *to release."*
:::

You will find on this page all your PIM product attributes.

Depending on the [configuration of your cartridge](mapping-configuration.html) concerning the mapping of SFCC attributes:
- Some PIM attributes will be mapped with SFCC product default attributes
- Some PIM attributes will be visible in the `Akeneo Attributes` part of the page

Each PIM attributes are prefixed with the ``akeneo_`` label.

![Akeneo attributes](../img/sfcc-akeneo-attributes.png)

:::info
In the `Akeneo attributes` part of your product, you will probably be surprised to find some attribute names that do not belong to your product family.<br>
<br>
Indeed, since SFCC does not have a notion of Family (as in the PIM), each SFCC product has the same list of attributes.<br>
<br>
As a result, the cartridge has to retrieve all PIM attributes of all PIM families in each SFCC product.
:::

# How to find my PIM "localizable" attributes in SFCC?

1. On the **Products** page, search your product
2. Click on your selected product
3. Choose in the `Select Language` list on the product page, the desired language knowing that :
- The `Default` language contains the content of non-localizable attributes.
- The other SFCC languages, identical to PIM languages, contain the content of localizable attributes (For example, if you have 3 languages for your products in the PIM (`fr_FR`, `en_US` and `de_DE`), you will find the content of your attributes in the `French (France)`, `English (United State)` and `German (Germany)` languages in SFCC.

# What about PIM "scopable" attributes in SFCC?

Depending on the [configuration of your cartridge](products-filter-configuration.html) concerning the scope filter: the cartridge only imports the attribute content of the specified channel.
