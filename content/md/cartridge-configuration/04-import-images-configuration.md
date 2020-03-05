---
id: 04-import-images-configuration
themes: connector-configuration
title: How to configure the cartridge to import PIM images?
popular: false
related: 01-where-configuration, 02-configure-PIM-API, 03-products-filter-configuration, 05-mapping-configuration, 06-categories-configuration, 07-multi-storefront-configuration, 08-reference-entities 
---

# First of all, what images are we talking about exactly?!

Akeneo PIM has 2 ways to store images for your products.

Either with several `Image` attributes or by using the `Asset collection` attribute that points to one or more images from the `Assets` management feature of your PIM Enterprise Edition.

The SFCC Akeneo connector can retrieve images from the `Image` attributes, the `Asset Collection` attributes, or both.

# How can I retrieve images from the "image" attributes?

In the [connector configuration page](01-where-configuration.html), you need to select `Images` for the following parameter to retrieve images from the "image" attributes.

| Connector parameter           | PIM information        |
| :-----------------------------| :---------------------: |
| akeneoImageType               |  Images(images)        |


# How can I retrieve images from the "Asset Collection" attributes?

In the [connector configuration page](01-where-configuration.html), you need to select `Assets` for the following parameter to retrieve images from the "asset collection" attributes.

| Connector parameter           | PIM information        |
| :-----------------------------| :---------------------: |
| akeneoImageType               |  Assets(assets)        |

::: info
The order of images defined in the "Asset Collection" attribute is respected when the connector imports images in SFCC.
:::

::: info
PIM asset images are imported into the "Images" section of SFCC products.
In addition, an SFCC attribute is created for each "Asset Collection" PIM attribute to store image IDs and define the asset order.
:::

# How can I retrieve images from both my "Image" and "Asset Collection" attributes at the same time?

In the [connector configuration page](01-where-configuration.html), you need to select `Both` for the following parameter if you want to retrieve images from both "Image" AND "Asset Collection" attributes.

| Connector parameter           | PIM information        |
| :-----------------------------| :---------------------: |
| akeneoImageType               |  Both(both)            |

# How to define SFCC image view types to import PIM images?

In the [connector configuration page](01-where-configuration.html), you can define the SFCC image view types for your images.

| Connector parameter           | SFCC information        |
| :-----------------------------| :---------------------: |
| Akeneo Image View Types       |  Image view types       |

::: warning
This field must be in JSON.
Here is an example of "Akeneo Image View Types" you can use for your connector:
```json

{
    "view-types": [
        "large",
        "medium",
        "small"
    ]
}
```
Note: If you don't want to use this feature, please leave a space in curly brackets ({ }).
:::

# How to define which PIM attribute is a variant value for product images?

In the [connector configuration page](01-where-configuration.html), you can define which PIM attribute is a variant value for product images:

| Connector parameter                     | PIM information                      |
| :---------------------------------------| :----------------------------------: |
| Akeneo Variation Value for Images       |  PIM Attribute ID (mostly "color")   |
