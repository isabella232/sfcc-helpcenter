---
id: 04-import-images-configuration
themes: cartridge-configuration
title: configuration to import PIM images
popular: false
related: 01-where-configuration, 02-configure-PIM-API, 03-products-filter-configuration, 05-import-media-configuration, 06-mapping-configuration, 07-categories-configuration, 08-multi-storefront-configuration, 09-reference-entities
---

# First of all, what images are we talking about exactly?!

Akeneo PIM has 2 ways to store images for your products.

Either with several `Image` attributes or by using the `Asset collection` attribute that points to one or more images from the `Assets` management feature of your PIM Enterprise Edition (using image files or image URLs).

The SFCC Akeneo connector can retrieve images from the `Image` attributes, the `Asset Collection` attributes, or both. This is managed by Akeneo Image Import Type (akeneoImageImportType). If ‘both’ is selected, Media links are managed using product custom Attributes in SFCC.

::: info
Please note that the SFCC cartridge is Asset Manager compliant for images since the 20.2.0 version.
:::

::: warning
When you use the system in 'both' mode, only image files will be visible into the grid view in Salesforce.
:::

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
| akeneoAssetSystem             |  New Asset System (PIM version >= 4.0) (new) |
|                               |  Old Asset System (PIM version < 4.0) (old)  |
| akeneoImageImportType         |  Image Media File only (media_file)          |
|                               |  Image Media Link only (media_link)          |
|                               |  Both (both)                                 |

With the Assets option selected (akeneoImageType):
* `Asset System Version` (akeneoAssetSytem): Select what type of Asset system you use, for PAM (version < 4.0) select the old Asset system and for Asset Management system (version >= 4.0) select new asset system.
* `Akeneo Image Import Type` (akeneoImageImportType): you can select here if you rather prefer to:
  * *import Image binaries only* (Image Media File only) In this mode image binaries will be linked to products.
  * *import Image media links only* (Image Media Links Only) In this mode image links will be linked to products using SFCC’s external Image Management system.
  * *import both media files and media links* (Both) In this mode image binaries will be linked to products and image links will be imported to product custom attribute with the ID matching the following pattern,
```json
akeneo_<camelizedAssetCode>_<camelizedAssetAttributeCode>
```

Natively, SFCC does not support locale specific image links. This is handled by the connector by appending view-type with locale (e.g.: large_en-US, swatch_fr-FR etc). This must be handled in storefront logic by the developer.

:::info
You can define asset attributes that can be linked to SFCC viewtypes. Please note that these attributes must have the same code across all asset families. This mapping should be filled in Image Link View-Types Mapping (akeneoImageLinkViewTypesMapping) configuration.
:::

::: info
Akeneo PIM allows 2 levels of localization and scope-management: at the asset attribute level and at the product attribute level. SFCC connector will read the locale and scope values from *asset attributes*. Because SFCC doesn't manage both level, the product attributes of the type `pim_catalog_asset_collection` **must be non-localizable and non-scopable**.
:::

::: info
The order of images defined in the "Asset Collection" attribute is respected when the connector imports images in SFCC.
:::

::: info
PIM asset images are imported into the "Images" section of SFCC products.
In addition, an SFCC attribute is created for each "Asset Collection" PIM attribute to store image IDs and define the asset order.
:::

::: warning
If you already have implemented the 20.2.X cartridge for your images assets (with the asset manager model), please note that the frontend will now reach the information by adding `product.custom.` before your `akeneo_myVar`
:::

::: warning
For any change in configuration related to Images and Assets management, there must be a run of Full Import of assets and products to rebuild the correct caches necessary for correct imports. In addition, the target catalogs may be deleted and created and assigned to the Sites again.
:::

::: warning
If you use images URLs:
All images must be hosted with the same provider and the base URL for that provider should be filled in External Image Location (akeneoExternalImageLocation) configuration.
:::

# How can I retrieve images from both my "Image" and "Asset Collection" attributes at the same time?

In the [connector configuration page](01-where-configuration.html), you need to select `Both` for the following parameter if you want to retrieve images from both "Image" AND "Asset Collection" attributes.

| Connector parameter           | PIM information        |
| :-----------------------------| :---------------------: |
| akeneoImageType               |  Both(both)            |

:::info
Only image files will be visible in the SFCC gridView (SFCC limitation), anyway the image links information are stored into the related attribute filed of the product.
:::

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

Since the 20.2.0 connector version, you do not have to set this information manually. This is automatically triggered and even more, you now are able to use many attributes on both axis instead of one.
