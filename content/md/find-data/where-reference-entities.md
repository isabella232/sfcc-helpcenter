---
id: where-reference-entities
themes: find-data
title: Where can I find my PIM Reference entities?
popular: false
related: where-categories, where-family, where-groups, where-attributes, where-product-association
---

# Where to find my PIM Reference Entities in SFCC?

Since Akeneo Connector for SFCC `V19.8.0`, the Connector can manage PIM Reference Entity.

:::warning
As SFCC does not have a Reference Entity feature (with the same modeling flexibility offered by the PIM), the connector uses the SFCC **Content Asset** objects to map PIM Reference Entities.

Please be sure to read our [specific documentation](08-reference-entities.html) about Reference Entities to know the limit of this mapping, how to configure it and how to manage these **Content Asset** objects.
:::

1. Select your SFCC site, then click on `Merchant Tools > Libraries`
2. Depending on the [configuration of your connector](08-reference-entities.html#how-to-choose-in-which-sfcc-library-pim-references-entities-will-be-imported-as-content-assets), click on the library where you decided to store PIM Reference Entities as `Content Assets` (`Share` or `Private` library).
3. Click on `Show All Content` in `Folder Content` part of the page.
4. You should see PIM Reference Entities in this new `Content` page (Prefixed with `akeneo_entity_` label)


![Content Asset](../img/sfcc-where-ref-entities.png)
