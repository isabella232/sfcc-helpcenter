---
id: overview
themes: first-data
title: SFCC cartridge overview
popular: false
related:
---

# Cartridge overview

Akeneo Salesforce commerce cloud cartridge is a SFCC add-on.
This add-on named "cartridge" is therefore installed on the SFCC side and communicates with Akeneo PIM via its API.

The cartridge is a unidirectionnal system : it only retrieves PIM data and imports it into SFCC (No SFCC data is sent to the PIM).

![Overview](../img/overview.png)

The PIM is therefore considered as the product master, while SFCC is its slave.

# Process overview

SFCC cartridge is composed of 4 main jobs:
- `1- Akeneo-Import-Attributes`									
- `2- Akeneo-Import-Media-Assets-Pricebook`
- `3-1- Akeneo-Differential-Import-Products`
- `3-2- Akeneo-Full-Import-Products`

Each job can be independently triggered manually or automatically.

::: info
Each job is responsible for importing part of PIM data. The order in which the jobs are started is therefore important (1 then 2 then 3-1 (or 3-2)).
:::

## Akeneo-Import-Attributes

`1- Akeneo-Import-Attributes` job imports:
- PIM attributes
- PIM attribute options (from simple and multi select attribute type)

## Akeneo-Import-Media-Assets-Pricebook

`2- Akeneo-Import-Media-Assets-Pricebook` job imports:
- PIM images from image attributes type (Depending on your cartridge configuration)
- PIM images from asset attributes type (Depending on your cartridge configuration)
- PIM currencies (to create SFCC Pricebook)

## Akeneo-Full-Import-Products & Akeneo-Differential-Import-Products

These 2 jobs are really similar and must not be used at the same time.: they both import products from Akeneo PIM.

`3-2- Akeneo-Full-Import-Products` imports **all** products from Akeneo PIM.

when

`3-1- Akeneo-Differential-Import-Products` imports **only new products** since the last import made.

These jobs import:
- PIM categories
- PIM products (and product models)
- PIM product associations

::: warning
- In the case of an automatic trigger, be sure to properly schedule all jobs to have time to import all PIM data between each scheduled import process.
- In the case of a manual triggering, be careful not to combine the manual and automatic processes.
- Use the differential import of products as much as possible, which will optimize the import time.
:::

# How to manually trigger the cartridge?

## How do I go to the cartridge jobs page in SFCC?

Click on the `Administration` menu then go to `Operations : Jobs`:

![Cartridge jobs](../img/sfcc-jobs.png)

## How to manually trigger each jobs?

Select the job you want to start and click on the `Run` button.

![Cartridge jobs page](../img/sfcc-jobs-page.png)

You can refresh the job status by clicking on the `Refresh` button. Wait until the process ends.

The Job import process is completed when its status changes to `Ok`.

# How to check that all jobs have been executed correctly?

Click on the `Administration` menu then go to `Operations : Jobs History`:

![Cartridge jobs history](../img/sfcc-jobs-history.png)

On this page, you will find a list of jobs that have been done before. By browsing this list, you will be able to find the Akeneo SFCC cartridge jobs that have been executed and know the status of those.

![Cartridge jobs history page](../img/sfcc-jobs-history-page.png)

::: info
If you experience an error with one of the cartridge jobs : by clicking on the small icon in the "log file" column, you can download the log file and give it to your technical team for analysis.
:::
