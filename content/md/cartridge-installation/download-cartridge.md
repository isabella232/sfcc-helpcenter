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
Please note that this **free version** connector **will not** give you access to the latest version of Akeneo Connector for SFCC as well as the Akeneo official support.
:::

* On [**Akeneo Partner Portal**](https://partners.akeneo.com), within a private **Github repository**.

:::info
This up-to-date version provides early access to **latest patches and new features** for Akeneo Connector for SFCC. It is also supported and maintained by Akeneo teams.
:::

Please [**contact us**](mailto:demandware@akeneo.com) to get access to the private **Github repository** where the supported version of the connector is hosted.

Akeneo teams will then get back to you on how to download the connector via our [**Partner Portal**](https://help.akeneo.com/portal/index.html) and how to benefit from **Akeneo support**.

::warning
**Important:**

1- In the Partner Portal, be sure to have configured your [SSH key](https://help.akeneo.com/portal/articles/get-akeneo-pim-enterprise-archive.html#import-my-public-key) for your Partner Portal profile.

2- Be sure to set up the same SSH key to interact with GitHub and to be able to access to our private Github repository using commands described below.  
:::

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

## Upload the cartridge

Upload the `bc_akeneo` cartridge into the Salesforce Commerce Cloud Studio Workspace:

*	Open **Salesforce Commerce Cloud Studio**.

*	Click `File` -> `Import` -> `General` -> `Existing Projects into Workspace`.

*	Browse to the directory where you have saved the `bc_akeneo` cartridge.

*	Click on `Finish`.

* Click `OK` when prompted to link the cartridge to the sandbox.

## Metadata Import

For Akeneo Connector for SFCC to work, the following object structures (metadata) need to be imported and configured in the Business manager.

Follow the steps below:

*	In the cartridge bundle find `metadata/simple-akeneo-workflow_site-import` and compress it to generate `simple-akeneo-workflow_site-import.zip` file.

*	Go to Business Manager Menu: `Administration > Site Development : Site Import & Export`

*	Under `Import : Upload archive`:
Ensure that the radio button with label `Local` is enabled (Else click on the radio button to enable it).

* Click on `Choose File` input field, select the `simple-akeneo-workflow_site-import.zip` file from `open dialog box` and click on `Upload` button.

*	After finishing the upload, from the `Archives` list click the radio button corresponding to `simple-akeneo-workflow_site-import.zip` and click on `Import` button.

*	Click on `OK` button of the confirmation box asking "**Are you sure that you want to import the selected archive?**"

# Add the cartridge to your sites

`1.`	Go to Business Manager Menu: `Administration > Sites : Manage Sites`.

`2.`	Select your site.

`3.`	Click on the `Settings` tab.

`4.`	Append "`:bc_akeneo`" to the `Cartridges` field.

`5.`	Click on `Apply` button.

`6.`	Repeat steps `2.` to `5.` for all sites including Business Manager site.

Fill all Akeneo configuration present in [Site Preferences](../themes-for-peter.html#cartridge-configuration).

[Schedule job](trigger.html) as needed, and start synchronization with Akeneo instance ! ;-)

::: info
Please read also the **additional documents** in the **"documentation"** folder of the **Github repository** to have more technical information around Akeneo Connector for SFCC.
:::

# Migration: I have an old "Pipeline" version of the connector, how can I migrate to the "Script" version?

If you have an old **Pipeline** version (`< v19.3.1`) of the connector and want to update to the **Script** version, please follow these steps:

## Step 1:  Upload latest cartridge code to active code version

* Get the latest cartridge code from Akeneo.
* Replace the cartridge `bc_akeneo` in UX Studio (Eclipse).
* Upload the cartridge in to the active code version of the sandbox

## Step 2:  Re-import Jobs

To setup Jobs, as mentioned below, import the `Jobs.xml` file which is available in `metadata` folder in the cartridge bundle. (`metadata/simple-akeneo-workflow_site-import`)

* In the Business Manager, go to `Administration > Operations : Import & Export`
* Under section titled as `Import & Export Files`, find the `Upload` button and click on it
* Upload the `metadata/simple-akeneo-workflow_site-import/jobs.xml` file using the `Upload File` form
* Come back to `Administration > Operations : Import & Export`
* Under section titled as `Jobs`, find the `Import` button and click on it
* Select the radio button corresponding to `jobs.xml` that you uploaded and click in `Next` button
* After automatic validation of file, click on `Next` button
When you import the `jobs.xml` properly, the jobs list under `Administration > Operations : Jobs` get updated with script version.
* On re-import of Jobs, all the jobs are reset to use for SiteGenesis Site.
* You may go through all the `Job Steps` in all the jobs.
* Find the `Job Steps` which are assigned to SiteGenesis Site.
* Reassign them to your preferred site(s).
* Leave the `Job Steps` which are assigned to Organization intact.


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
