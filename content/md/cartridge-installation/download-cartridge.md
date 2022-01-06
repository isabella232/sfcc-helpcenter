---
id: download-cartridge
themes: cartridge-installation
title: How to download and install the connector?
popular: true
related: all-pre-requisite, where-configuration
---

# Where can I get the Akeneo Connector for SFCC?

There are 2 ways for you to put your hands on the Akeneo Connector for SFCC:

* First, you can find it on the [**Salesforce marketplace**](https://www.salesforce.com/products/commerce-cloud/partner-marketplace/partners/akeneo/), where you can download the **free version** that includes the latest certified version of the connector.

You will need a Salesforce Xchange account to get access to this archive.

:::warning
Please note that this **free version** of the connector **will not** give you access to the latest version of the Akeneo Connector for SFCC as well as the Akeneo official support.
:::

* The other place where you can download it is the [**Akeneo Partner Portal**](https://partners.akeneo.com).

:::info
This up-to-date version provides early access to **the latest patches and features** of the Akeneo Connector for SFCC. It is also supported and maintained by Akeneo teams.
:::

# Download the connector via the Partner Portal

**Pre-requisites:**

First of all, you need to access the [**Akeneo partner Portal**](https://partners.akeneo.com/) and select the project on which the cartridge has to be installed.

:::info
Your CSM has to activate the connector access for this project for you to able able to see the download link.
:::

Once you clicked, you will have to select the archive version that you want to install.
![SFCC download button](../img/Download-cartridge-button.gif)

:::info
We strongly recommend you to get the latest version.
:::

# Install the connector

:::info
In case of the version upgrade of the cartridge, please reinstall the connector by follow the exact same steps as for the installation.
:::

## Upload the cartridge

:::warning
For the 21.0.0 or higher version of the cartridge, the name is `bm_akeneo` instead of `bc_akeneo`
:::

Upload the `bc_akeneo` cartridge to the Salesforce Commerce Cloud Studio Workspace:

*	Open **Salesforce Commerce Cloud Studio**.

*	Click on `File` -> `Import` -> `General` -> `Existing Projects into Workspace`.

*	Go to the directory where you saved the `bc_akeneo` cartridge.

*	Click on `Finish`.

* Select `OK` when you are ready to link the cartridge to the sandbox.

## Metadata Import

For the Akeneo Connector for SFCC to work, the following object structures (metadata) need to be imported and configured in the Business manager.

Follow the steps below:

*	In the cartridge bundle find `metadata/simple-akeneo-workflow_site-import` and compress it to generate the `simple-akeneo-workflow_site-import.zip` file.

*	Go to the Business Manager Menu: `Administration > Site Development : Site Import & Export`

*	Under `Import : Upload archive`:
Make sure that the radio button with label `Local` is enabled (otherwise click on the radio button to enable it).

* Click on the `Choose File` input field, select the `simple-akeneo-workflow_site-import.zip` file from the `open dialog box` and click on `Upload`.

*	After finishing the upload, from the `Archives` list click on the radio button corresponding to `simple-akeneo-workflow_site-import.zip` and click on `Import`.

*	Click on the `OK` button of the confirmation box asking "**Are you sure that you want to import the selected archive?**"

## Log API communication (debug mode)

* Go to Business Manager Menu: `Administration > Operations : Services > AkeneoGetGeneral`

* Tick the `Communication Log Enabled` checkbox if you want API communication to be logged.

* Repeat the same for `AkeneoGetToken`.

# Add the cartridge to your sites

`1.`	Go to Business Manager Menu: `Administration > Sites : Manage Sites`.

`2.`	Select your site.

`3.`	Click on the `Settings` tab.

`4.`	Append "`:bc_akeneo`" (or `bm_akeneo` depending on the cartridge version) to the `Cartridges` field.

`5.`	Click on `Apply`.

`6.`	Repeat steps `2.` to `5.` for all sites including the Business Manager one.

Fill in all Akeneo configuration in [Site Preferences](../themes-for-peter.html#cartridge-configuration).

[Schedule job](trigger.html) as needed, and start the synchronization with the Akeneo instance! ;-)

::: info
Please read also the **additional documents** in the **"documentation"** folder of the **Github repository** to have more technical information about the Akeneo Connector for SFCC.
:::

# Migration: You have a very old "Pipeline" version of the connector, how can you migrate to the "Script" version?

If you have an old **Pipeline** version (`< v19.3.1`) of the connector and want to update to the **Script** version, please follow these steps:

## Step 1:  Upload the latest cartridge code to the active code version

* Get the latest cartridge code from Akeneo.
* Replace the `bc_akeneo` (or `bm_akeneo` depending on the cartridge version) cartridge in the UX Studio (Eclipse).
* Upload the cartridge to the active code version of the sandbox

## Step 2:  Re-import Jobs

To setup Jobs, as mentioned below, import the `Jobs.xml` file which is available in the `metadata` folder in the cartridge bundle. (`metadata/simple-akeneo-workflow_site-import`)

* In the Business Manager, go to `Administration > Operations : Import & Export`
* Under the `Import & Export Files` section, click on `Upload`
* Upload the `metadata/simple-akeneo-workflow_site-import/jobs.xml` file using the `Upload File` form
* Come back to `Administration > Operations : Import & Export`
* Under the `Jobs`section, click on `Import`
* Select the radio button corresponding to `jobs.xml` and click on the `Next` button
* After the file is automatically validated, click on `Next`
When you import the `jobs.xml` properly, the jobs list under `Administration > Operations : Jobs` get updated with the script version.
* When Jobs are imported again, they will be reset to use the SiteGenesis Site.
* You may go through all the `Job Steps` in all the jobs.
* Find the `Job Steps` which are assigned to SiteGenesis Site.
* Reassign them to your preferred site(s).
* Leave the `Job Steps` which are assigned to Organization intact.


# What can you do if you have a question, if you want to report a bug or a suggestion for the connector?

Please use our [**Helpdesk**](https://helpdesk.akeneo.com) platform to contact us.

**In the event of a bug report, please install the latest version of the connector and try to reproduce the bug again before reporting it**

If the issue occurs with the latest version of the connector, feel free to report the bug to us. Please provide us with the information below when you open a ticket on our Help Center:
- The version of your PIM instance
- The version of your Salesforce Commerce Cloud instance
- The version of the installed connector
- Steps to reproduce your issue (please be as specific as possible).

::: warning
**For our Support team to be able to take this issue into account, the steps to reproduce should be performed in a non-customized environment on both Akeneo and SFCC sides, with a vanilla connector.**
<br>
Please note that we do not offer support on the **free version** of Akeneo connector for SFCC (which you get from [Salesforce marketplace](https://www.salesforce.com/products/commerce-cloud/partner-marketplace/partners/akeneo/))
:::

::: warning
Custom product attributes fields are automatically created while the *cartridge installation process* (and then not while the import process), so do not delete them or you will have to re install the connector to retrieve your custom fields.
:::
