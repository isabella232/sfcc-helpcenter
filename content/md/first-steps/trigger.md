---
id: trigger
themes: first-steps
title: How to trigger the cartridge?
popular: false
related:
---

# How to trigger the cartridge?

## How do I go to the cartridge jobs page in SFCC?

Click on the `Administration` menu then go to `Operations : Jobs`:

![Cartridge jobs](../img/sfcc-jobs.png)

## How to manually trigger each jobs?

Select the job you want to start and click on the `Run` button.

![Cartridge jobs page](../img/sfcc-jobs-page.png)

You can refresh the job status by clicking on the `Refresh` button. Wait until the process ends.

The Job import process is completed when its status changes to `Ok`.

## How to automatically trigger each jobs?

When you are on the [Cartridge job page](#how-do-i-go-to-the-cartridge-jobs-page-in-sfcc), click on the job you want to automate.

Then click on the `Schedule and History` tab and define the job scheduling settings.

![Cartridge jobs schedule](../img/sfcc-jobs-schedule.png)



::: warning
- In the case of an automatic trigger, be sure to properly schedule all jobs to have time to import all PIM data between each scheduled import process.
- In the case of a manual triggering, be careful not to combine the manual and automatic processes.
- Use the differential import of products as much as possible, which will optimize the import time.
:::

# How to check that all jobs have been executed correctly?

Click on the `Administration` menu then go to `Operations : Jobs History`:

![Cartridge jobs history](../img/sfcc-jobs-history.png)

On this page, you will find a list of jobs that have been done before. By browsing this list, you will be able to find the Akeneo SFCC cartridge jobs that have been executed and know the status of those.

![Cartridge jobs history page](../img/sfcc-jobs-history-page.png)

::: info
If you experience an error with one of the cartridge jobs : by clicking on the small icon in the "log file" column, you can download the log file and give it to your technical team for analysis.
:::
