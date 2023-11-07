# CloudEye: A Clear View into Azure Monitoring

## Overview

Welcome to the CloudEye project, where we explore the world of Azure Monitoring and gain a clear view into the performance and configuration of Azure resources, with a focus on Azure virtual machines. This project demonstrates expertise in Azure Monitoring and showcases various aspects of Azure Monitor and Log Analytics.

## Table of Contents

- [Project Setup](#project-setup)
- [Objectives](#objectives)
- [Lab Scenario](#lab-scenario)
- [Instructions](#instructions)
  - [Exercise 1](#exercise-1)
    - [Task 1: Provision the lab environment](#task-1-provision-the-lab-environment)
    - [Task 2: Register the Microsoft.Insights and Microsoft.AlertsManagement resource providers](#task-2-register-the-microsoftinsights-and-microsoftalertsmanagement-resource-providers)
    - [Task 3: Create and configure an Azure Log Analytics workspace and Azure Automation-based solutions](#task-3-create-and-configure-an-azure-log-analytics-workspace-and-azure-automation-based-solutions)
    - [Task 4: Review default monitoring settings of Azure virtual machines](#task-4-review-default-monitoring-settings-of-azure-virtual-machines)
    - [Task 5: Configure Azure virtual machine diagnostic settings](#task-5-configure-azure-virtual-machine-diagnostic-settings)
    - [Task 6: Review Azure Monitor functionality](#task-6-review-azure-monitor-functionality)
    - [Task 7: Review Azure Log Analytics functionality](#task-7-review-azure-log-analytics-functionality)
  - [Clean Up Resources](#clean-up-resources)
- [Review](#review)

## Project Setup

Before you begin, make sure you have access to an Azure subscription and the Azure portal. The project involves provisioning resources and configuring Azure Monitoring solutions, so ensure you have the necessary permissions and resources.

## Objectives

In this CloudEye project, you will:

- Provision the lab environment for Azure Monitoring exploration.
- Register the Microsoft.Insights and Microsoft.AlertsManagement resource providers.
- Create and configure an Azure Log Analytics workspace and Azure Automation-based solutions.
- Review default monitoring settings of Azure virtual machines.
- Configure Azure virtual machine diagnostic settings.
- Review Azure Monitor functionality.
- Review Azure Log Analytics functionality.

## Lab Scenario

In this scenario, you will evaluate Azure functionality to gain insights into the performance and configuration of Azure resources, with a special focus on Azure virtual machines. This project explores the capabilities of Azure Monitor, including Log Analytics, to provide a comprehensive view of your Azure environment.

## Instructions

The CloudEye project is organized into multiple tasks and exercises to guide you through various aspects of Azure Monitoring. Follow the instructions for each task to gain expertise in Azure Monitoring.

### Exercise 1

#### Task 1: Provision the lab environment

1. Sign in to the [Azure portal](https://portal.azure.com).

2. In the Azure portal, open the **Azure Cloud Shell** by clicking on the icon in the top right of the Azure Portal.

3. If prompted to select either **Bash** or **PowerShell**, select **PowerShell**.

...

(Continue with the detailed instructions for each task and exercise as per your original content.)

### Clean Up Resources

Don't forget to remove any Azure resources created during the project that you no longer need. This ensures you won't incur unexpected charges.

1. In the Azure portal, open the **PowerShell** session within the **Cloud Shell** pane.

2. List all resource groups created throughout the project by running the following command:

   ```powershell
   Get-AzResourceGroup -Name 'lab1*'

1. Delete all resource groups you created throughout the labs of this module by running the following command:

   ```powershell
   Get-AzResourceGroup -Name 'az104-11*' | Remove-AzResourceGroup -Force -AsJob
   ```

    >**Note**: The command executes asynchronously (as determined by the -AsJob parameter), so while you will be able to run another PowerShell command immediately afterwards within the same PowerShell session, it will take a few minutes before the resource groups are actually removed.

## Review

In this lab, you have:

+ Provisioned the lab environment
+ Created and configured an Azure Log Analytics workspace and Azure Automation-based solutions
+ Reviewed default monitoring settings of Azure virtual machines
+ Configured Azure virtual machine diagnostic settings
+ Reviewed Azure Monitor functionality
+ Reviewed Azure Log Analytics functionality
