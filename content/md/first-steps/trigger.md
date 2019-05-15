---
id: trigger
themes: first-steps
title: How to use the cartridge?
popular: false
related: overview, what-data
---

# How to use the cartridge?

## How do I go to the cartridge jobs page in SFCC?

1. Click on the `Administration` menu
2. Then go to `Operations : Jobs`:

![Cartridge jobs](../img/sfcc-jobs.png)

## How to manually trigger each jobs?

1. Select the job you want to start
2. Then click on the `Run` button to trigger the selected job
3. Wait until the process ends. You can refresh the job status by clicking on the `Refresh` button.

![Cartridge jobs page](../img/sfcc-jobs-page.png)



The Job import process is completed when its status changes to `Ok`.

## How to automatically trigger each jobs?

When you are on the [Cartridge job page](#how-do-i-go-to-the-cartridge-jobs-page-in-sfcc), click on the job you want to automate.

Then click on the `Schedule and History` tab and define the job scheduling settings.

![Cartridge jobs schedule](../img/sfcc-jobs-schedule.png)



::: warning
- In the case of an automatic trigger, be sure to properly schedule all jobs to have time to import all PIM data between each scheduled import process.
- In the case of a manual triggering, be careful not to combine the manual and automatic processes.
- Use the differential import of products as much as possible, which will optimize the time of import.
:::

# How to check that all jobs have been executed correctly?

1. Click on the `Administration` menu.
2. Then go to `Operations : job History`:

![Cartridge jobs history](../img/sfcc-jobs-history.png)

On this page, you will find a list of jobs that have been executed before. You will be able to find the Akeneo SFCC cartridge jobs that have been executed and know its status by browsing this list.

![Cartridge jobs history page](../img/sfcc-jobs-history-page.png)

::: info
If you experience an error with one of the cartridge jobs : click on the small icon in the "log file" column to download the log file. You can give it to your technical team for analysis.
:::
