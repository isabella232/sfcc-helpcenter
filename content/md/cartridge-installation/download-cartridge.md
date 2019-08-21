---
id: download-cartridge
themes: cartridge-installation
title: How to download and install the connector?
popular: true
related: all-pre-requisite, where-configuration
---

# Where can I get Akeneo Connector for SFCC?

There are 2 ways to put your hands on Akeneo Connector for SFCC:

* On [**Salesforce marketplace**](https://www.salesforce.com/products/commerce-cloud/partner-marketplace/partners/akeneo/), where you can download the **free version** that includes the latest certified version of the connector.

You will need a Salesforce Xchange account to get access to this archive.

:::warning
Please note that this **free version** connector **will not** give you access to the last version of Akeneo Connector for SFCC as well as the Akeneo official support.
:::

* On [**Akeneo Partner Portal**](https://partners.akeneo.com), within a private **Github repository**.

:::warning
This up-to-date version provides early access to **latest patches and new features** for Akeneo Connector for SFCC. It is also supported and maintained by Akeneo teams.
:::

Please [**contact us**](mailto:demandware@akeneo.com) to get access to the private **Github repository** where the supported version of the connector is hosted.

Akeneo teams will then get back to you on how to download the connector via our [**Partner Portal**](https://help.akeneo.com/portal/index.html) and how to benefit from **Akeneo support**.

# Download the connector

Clone the repository by using this command:

```bash
git clone ssh://git@distribution.akeneo.com:443/sfcc-cartridge
```

If you encounter a HEAD error, please perform the following actions :

`1.` Go to your project repository

`2.` List all available tag:
```bash
git tag
```

`3.` Select the latest tag (**the following example is for 19.7.0**) to retrieve all files:
```bash
git checkout v19.7.0
```

`4.` Please read carefully all instructions from the previous Github command.


# Install the connector

:::info
This connector has been designed to work with the Integration Framework. For those who are not familiar with the Integration Framework, we suggest to read the following articles:
https://xchange.demandware.com/docs/DOC-11159
https://xchange.demandware.com/docs/DOC-11951
:::

`1.` In the Business Manager go to `Administration > Site Development : Site Import & Export`, upload the `simple-akeneo-workflow_site-import.zip` file to the server and import it.

This will automatically create the following elements:
* Akeneo Custom Object for stock current token
* All jobs as Akeneo connector
* Akeneo configuration in Site Preferences

`2.` Deploy the cartridge contained in the attached `simple-akeneo-workflow_cartridges.zip` file to your instance

`3.` Add `bc_akeneo` to your `Business Manager` site cartridge path.

Fill all Akeneo configuration present in [Site Preferences](../themes-for-peter.html#cartridge-configuration).

[Schedule job](trigger.html) as needed, and start synchronization with Akeneo instance ! ;-)

::: info
Please read also the **additional document** in the **"documentation"** folder of the **Github repository** to have more technical information around Akeneo Connector for SFCC.
:::

# What can I do if I have a question, if I want to report a bug or a suggestion for the connector?

Please use our [**Helpdesk**](https://helpdesk.akeneo.com) platform to contact us.

**In the event of a bug report, please install the latest version of the connector and try to reproduce the bug again before reporting it**

If the issue occurs with the latest version of the connector, feel free to report the bug to us. Please provide us with the below information when you open a ticket on our Help Center:
- The version of your PIM instance
- The version of your Salesforce Commerce Cloud instance
- The version of the installed connector
- Steps to reproduce your issue (please be as precise as possible).

::: warning
**For our Support team to be able to take this issue into account, the steps to reproduce should be performed in a non-customized environment on both Akeneo and SFCC sides, with a vanilla connector.**
<br>
Please note that we do not offer support on the **free version** of Akeneo connector for SFCC (which you get from [Salesforce marketplace](https://www.salesforce.com/products/commerce-cloud/partner-marketplace/partners/akeneo/))
:::
