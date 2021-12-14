---
id: where-attributes
themes: find-data
title: Where can I find my PIM product attributes?
popular: false
related: where-categories, where-family, where-groups, where-product-association, where-reference-entities
---

# Where to find my PIM products in SFCC?

1. Select your SFCC site, then click on `Merchant Tools`
2. Then click on the `Products` menu

![Product menu](../img/sfcc-where-products.png)

:::info
On the **Products** page, if you want to see all your products, **click on the `Find` button** (By default, there are no products in the list.).
If you are looking for a specific product, use the search bar.  
:::

![Product list](../img/sfcc-where-products-list.png)

# Where can you find your PIM product models in SFCC?

1. Select your SFCC site, then click on `Merchant Tools`
2. Then click on the `Products` menu

![Product menu](../img/sfcc-where-products.png)

::: info
**Mapping between your PIM and SFCC instances:**
Akeneo Connector for SFCC maps PIM product models this way:

**PIM Product models with 1 level of variation:**
- PIM product models `common` part is mapped with SFCC `Variation master`
- PIM product models variation `level 1` part is mapped with SFCC `Variation products`

**PIM Product model with 2 levels of variation:**
- PIM product models `common` part is mapped with SFCC `Variation master`
- PIM product models variation `level 1`+ variation `level 2` parts are mapped with SFCC `Variation products`

Alternative: since the SFCC Connector **v19.6.0** version, you can model PIM Product model with 2 levels of variation like this:
- PIM product models `common` part is mapped with SFCC `Variation master`
- PIM product models variation `level 1` part is mapped with SFCC `Variation group`
- PIM product models variation `level 2` part is mapped with SFCC `Variation products`

Please consult our [cartridge configuration page](06-mapping-configuration.html) to know how to configure this alternative.

:::

# Where can you find your PIM product attributes in SFCC?

1. On the **Products** page, search for your product
2. Click on the selected product
3. Click on the `Lock` link in the top alert *"You haven't locked this product for editing. Click `Lock` if you need to edit the product."* to be able to edit product attributes.

:::info
With this last action, you are able to manipulate some attributes more easily. For example, you can click on the image attribute `Edit` button in order to see all the product images.
:::

![Edit Product](../img/sfcc-where-edit-product.png)

:::warning
After your product attributes review, **don't forget to click on the `Unlock` link** in the top alert *"You've locked this product for editing. Click* `Unlock` *to release."*
:::

On this page, you will find all your PIM product attributes.

Depending on the [configuration of your connector](06-mapping-configuration.html) the mapping of SFCC attributes may be as follows:
- Some PIM attributes could be mapped with SFCC product default attributes
- The remaining PIM attributes will appear in the `Akeneo Attributes` part of the page

Each PIM attribute is prefixed with the ``akeneo_`` label.

![Akeneo attributes](../img/sfcc-akeneo-attributes.png)

:::info
In the `Akeneo attributes` part of your product, you may notice some attributes that do not belong to the family your product belongs to.

Indeed, there's no such thing as Family in Salesforce Commerce Cloud. Each product in SFCC will be assigned all PIM attributes by default.
:::

# Where can you find you PIM "localizable" attributes in SFCC?

1. On the **Products** page, search for your product
2. Click on the selected product
3. Choose the language in the `Select Language` list on the product page, knowing that:
- The `Default` language will be populated with the content of non-localizable attributes.
- The other set languages in SFCC, matching with set languages in the PIM, will be populated with the content of localizable attributes (For example, if you have 3 languages for your products in the PIM (`fr_FR`, `en_US` and `de_DE`), you will find the content of your attributes in the `French (France)`, `English (United States)` and `German (Germany)` languages in Salesforce Commerce Cloud.

# What about PIM "scopable" attributes in SFCC?

Depending on the [configuration of your connector](03-products-filter-configuration.html) the scope preference will be as follows: the Akeneo connector will only import the attribute values of the specified channel.

# Where can I find Table attribute information in SFCC?

:::info
The table attribute has been recovered in the most **native** way (for SFCC) to preserve the connector's performance.
Raw data recovered from the Akeneo's API are not processed in any way, therefore:
- The order of the attribute values & translations is given to us by the Akeneo's API
- The empty attribute values (as for the other attributes) are not transmitted to the connector.
:::

Table attribute is stored in **two places** in the SFCC interface.

On the **product level**, you will be able to recover table attribute values for the specific table in the dedicated field - one field per table (ex. akeneo_FoodComposition).
Those values will be automatically transmitted to the SFCC during import.

![Table attribute](../img/Table-attribute1.png)

To recover translations and table structure, you will need to retrieve them from the custom object created during import.

Go to `Merchant tools` >> `Custom Objects` >> Look for `AkeneoAttributeTable` Object or search the Custom Object directly by its name (ex. Food_Composition)

This custom object is used to store the definition of the structure of the attribute table (columns order/columns translation / etc.). Each new element corresponds to a **“table attribute”** in the PIM. You can use this information to display the table correctly on **SFRA or headless**. Please consider this custom object as a mirror of the attribute definition in Akeneo.        
You can retrieve the translation of the column in the “labels” node. However, the translated values corresponding to a product are defined in the System Product Object as a new custom attribute (a standard attribute from Akeneo).

![Table attribute](../img/Table-attribute2.png)
