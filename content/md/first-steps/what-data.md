---
id: what-data
themes: first-steps
title: What PIM data are imported into SFCC?
popular: false
related: trigger, overview
---

# Attribute types

The SFCC cartridge imports all these PIM attribute types:
- Text
- Text area
- Date
- Number
- Simple select (1)
- Multiple select (1)
- Yes/No
- Metric (2)
- Image
- File (3)
- Asset collection (EE) (4)
- Price
- Identifier
- Table attribute (5)

::: info
(1) The cartridge imports all **attribute options** with their translations.<br>
(2) As **metric attributes** do not exist in SFCC, the cartridge converts this into **text attribute** type.<br>
(3) As SFCC does not support the import of binary files other than images, we only import **the relative PIM path** for this attribute.<br>
(4) As SFCC does not support the import of binary files other than images, we only import **image assets binaries**.<br>
(5) `Table attribute` type doesn't exist by default in the PIM, it is an add-on that has been developed by [Flagbit](https://marketplace.akeneo.com/extension/table-attribute) and [Webkul](https://marketplace.akeneo.com/extension/akeneo-table-attribute) company and allows you to add an additional "table" attribute type in your PIM.
**The cartridge is therefore compatible with these 2 extensions !** :-)
As SFCC does not have a table attribute type, the cartridge imports table data into an SFCC **text area** attribute as a **JSON structure**.  
:::


# Attributes

The SFCC cartridge imports all your PIM products attributes.

If you have some **localizable** attributes (attributes that can have different values per **locale**): the SFCC cartridge imports the content of these attributes in the different languages of SFCC product.

If you have some **scopable** attributes (attributes that can have different values per **channel**): depending on your [channel configuration](03-products-filter-configuration.html), the SFCC cartridge imports the channel content of these attributes.

# Categories

Depending on your [category configuration](06-categories-configuration.html), the SFCC cartridge imports all PIM category trees.

::: info
**Mapping between your PIM and SFCC:**<br>
The SFCC cartridge maps PIM categories with SFCC categories.<br>
Because you **PIM categories contain** only a title while **SFCC categories** allow you to have more information (description, image, ...), the SFCC cartridge only imports PIM category title information in SFCC category.
:::

# Products, Product models

Depending on your [product filter configuration](03-products-filter-configuration.html), the SFCC cartridge imports products and product models of your PIM catalog.

::: info
**Mapping between your PIM and SFCC:**<br>
The SFCC cartridge maps PIM products with SFCC `products`.
:::

::: info
**Mapping between your PIM and SFCC:**<br>
The SFCC cartridge maps PIM product model like this :

**PIM Product model with 1 level of variation:**<br>
- PIM product model `common` part with SFCC `Variation master`<br>
- PIM product model variation `level 1` part with SFCC `Variation products`

**PIM Product model with 2 level of variation:**<br>
- PIM product model `common` part with SFCC `Variation master`<br>
- PIM product model variation `level 1`+ variation part `level 2` with SFCC `Variation products`
:::

# Product associations

Depending on your [product association mapping configuration](05-mapping-configuration.html), the SFCC cartridge imports your PIM product associations.

**Mapping between your PIM and SFCC:**<br>
The SFCC cartridge maps PIM `product associations` with SFCC `product recommendations`.<br>
Depending on your [product association mapping configuration](05-mapping-configuration.html), each PIM `product association type` is mapped with SFCC `product recommendation type`.

::: info
** With the SFCC Cartridge since V19.3.3 **
The SFCC cartridge can also map PIM `product associations` with SFCC `product links`.<br>
Depending on your [product association mapping configuration](05-mapping-configuration.html), each PIM `product association type` is mapped with SFCC `product link type`.
:::

# Currencies

The SFCC cartridge imports all your PIM currencies.

::: info
**Mapping between your PIM and SFCC:**<br>
The SFCC cartridge maps PIM `currencies` in the SFCC `Pricebook`.
:::

# Product groups

::: warning
As we have not found an equivalent notion in SFCC, the cartridge does not yet import PIM product groups.
:::

# Reference entities [EE] [3.x]

::: warning
The current cartridge version does not yet take into account the import of **Reference Entities**. However, a new cartridge version is being prepared in 2019 to take into account theses **Reference Entities** in SFCC.
:::
