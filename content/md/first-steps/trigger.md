---
id: trigger
themes: first-steps
title: How to use the cartridge?
popular: false
related: overview, what-data
---

# How to trigger import jobs?

## Where to find import jobs in Salesforce Commerce Cloud?

Once the connector is installed in your SFCC instance,
1. Click on the `Administration` menu
2. Then go to `Operations : Jobs`:

![Cartridge jobs](../img/sfcc-jobs.png)

## How to manually trigger each job?

1. Select the job you want to run
2. Then click on the `Run` button to trigger the selected job
3. Wait until the process ends. You can refresh the job status by clicking on the `Refresh` button.

![Cartridge jobs page](../img/sfcc-jobs-page.png)



The Job import process is completed when its status changes to `Ok`. If it fails, you could download the log file to understand why the import job did not succeed.

## How to automatically trigger each job?

When you are on the [Cartridge job page](#how-do-i-go-to-the-cartridge-jobs-page-in-sfcc), click on the job you want to automate.

Then click on the `Schedule and History` tab and define the job scheduling settings.

![Cartridge jobs schedule](../img/sfcc-jobs-schedule.png)



::: warning
- In the event of an automatic trigger, please let a buffer between all jobs so the system can complete all import jobs before switching to another.
- In the event of a manual trigger, please make sure no automatic process is set in the meantime.
- Use the differential product import job as much as possible, to enhance the performances of the connector.
:::

# How to check that all jobs have been executed correctly?

1. Click on the `Administration` menu.
2. Then go to `Operations : job History`:

![Cartridge jobs history](../img/sfcc-jobs-history.png)

Here, you will find the list of jobs that have been executed until now. You could check the status of each job while browsing this list.

![Cartridge jobs history page](../img/sfcc-jobs-history-page.png)

::: info
If you experience an error with one of the cartridge jobs: click on the small icon in the "log file" column to download the log file. You can give it to your technical team for analysis.
:::
