---
id: 05-import-media-configuration
themes: cartridge-configuration
title: Configuration to import PIM media
popular: false
related: 01-where-configuration, 02-configure-PIM-API, 03-products-filter-configuration, 04-import-images-configuration, 06-mapping-configuration, 07-categories-configuration, 08-multi-storefront-configuration, 09-reference-entities
---

# First of all, what images are we talking about exactly?!

Akeneo PIM since its 4.0 version (and then higher) offers to manage media with the Asset Manager.

Since the 20.3.0 version, our SFCC connector allows the use of the Asset Manager for **Videos (Youtube & Vimeo)**, **PDF** and **Other** *(File or Media Link)*


# How can I retrieve media from the "image" attributes?

The media gathering process will be impacted by the way you have configured the cartridge in the [connector configuration page](01-where-configuration.html) regarding the way to manage images. If you need information on the images management please check the [image configuration page](04-import-images-configuration.html).

# How can I retrieve media from the "Asset Collection" attributes?

Please note that since the 20.3.0 version we have slightly changed the way to manage media (and then images): in order to not be constrained by the SharedLibraries limits anymore, whe have changed the way to store the media information: you will have the **asset collection and its content described as a custom product attribute**.

1. your asset collection will be created as a custom attribute (whatever the media is a link or a file)
![Asset collection converted into a product attribute](../img/sfcc-cartridge-attribute-link-array.png)

2. The related information is stored as an index array (the sorting of the media in the PIM is maintained into this index order). By searching in the product attribute the ID you will find the related media information.

3. in our exemple `akeneo_amAssetCollectionLinkAndBinScopable` is equal to `["asset1_vdo_ytb_en"]`. That means: there is only one asset in the asset collection and this asset has `asset1_vdo_ytb_en` for ID. If you search the product attribute `asset1_vdo_ytb_en` then you will find:

| If the asset is a MEDIA LINK           | If the asset is a MEDIA FILE      |
| :-----------------------------| :---------------------: |
| The URL of your media  |  the static path to reach your file. |
| i.e: https://www.youtube.com/watch?v=X5P9sEcFaKc    |  i.e: `Assets/my_file/f/0/d/2/myDoc.pdf?$staticlink$` |

::: info
Please note then for your frontend development that the **number** and the **place** in the Array list of IDs is fundamental to define the way to pick the right information.
:::

::: warning
Due to the PIM API way to work, the deletion information is not explicitly sent to the connector, then if you delete an asset, please check the ID Array first for your frontend to "know" what information to gather from product, because information will not be deleted from the product attribute itself.
:::

::: warning
If you already have implemented the 20.2.X cartridge for your images assets (with the asset manager model), please note that the frontend will now reach the information by adding `product.custom.` befor you `akeneo_myVar`
:::

# What are videos that the connector can handle?

Exactly the same that the PIM do: **Youtube** or **Vimeo** videos links only.

# What are the files that the connectors can handle?

You have to know that the "files" can be either "PDF" or "Other". The main difference is related to the PIM thumbnail generation. Anyway for the files (PDF & Other) you are able to use **URL** or **binaries**.

::: warning
Even if you can upload video files by using "Other", please consider That
1. the PIM **is not** a CDN nor a DAM
2. the upload processing time can be extremely long, depending the size of your files.
:::
