# CloudEye: A Clear View into Azure Monitoring

## Project Scenario: Azure Monitoring and Log Analytics Lab
The project aimed to assess Azure's capabilities for gaining insights into the performance and configuration of Azure resources, with a specific focus on Azure virtual machines. The primary objective was to explore and evaluate the features offered by Azure Monitor, including Log Analytics, to enhance resource monitoring and management.

## Objectives

In this lab, you will:

+ Task 1: Provision the lab environment
+ Task 2: Register the Microsoft.Insights and Microsoft.AlertsManagement resource providers
+ Task 3: Create and configure an Azure Log Analytics workspace and Azure Automation-based solutions
+ Task 4: Review default monitoring settings of Azure virtual machines
+ Task 5: Configure Azure virtual machine diagnostic settings
+ Task 6: Review Azure Monitor functionality
+ Task 7: Review Azure Log in storagea account

## Architecture diagram


![Screenshot 2023-11-08 152254](https://github.com/Saurabh-Bhargav/Project/assets/143943258/79c4a36b-fbde-4f81-bf3d-c98e1e3db451)


### Instructions

## Exercise 1

## Task 1: Create VM and Storage Account

1. **Login to the Azure Portal**
   - Open a web browser and navigate to [Azure Portal](https://portal.azure.com/).
   - Sign in with your Azure account.

2. **Create a Storage Account**
   - In the Azure Portal, click on "Create a resource."
   - Search for "Storage account" and select it.
   - Click "Create" and fill out the necessary details, including name, region, and resource group.
  
     
     ![CReate-storage-accpunt](https://github.com/Saurabh-Bhargav/Project/assets/143943258/84f2404f-1af3-449f-93d3-83e7f9b95a93)


   - Review and confirm your settings, then click "Create" to provision the storage account.

3. **Create a Virtual Machine**
   - In the Azure Portal, click on "Create a resource."
   - Search for "Virtual machine" and select it.
   - Follow the wizard to configure your VM settings, including choosing the OS image, virtual network, and storage account created in the previous step.
     
     
     ![Screenshot 2023-11-08 092629](https://github.com/Saurabh-Bhargav/Project/assets/143943258/929350dd-b1ed-4ccb-bec4-8588ca470e67)
     

   - Review and confirm your settings, then click "Create" to provision the VM.

## Task 2: Register Resource Providers

1. **Register Microsoft.Insights Resource Provider**

   To enable access to Azure Monitor services, you need to register the Microsoft.Insights resource provider. You can do this using PowerShell or the Azure Portal.
   

![register-onption-in-subscription](https://github.com/Saurabh-Bhargav/Project/assets/143943258/78b7059e-528c-418e-a182-bae5b6bba555)


   - **Azure Portal Method**
     - In the Azure Portal, navigate to "All services."
     - Search for "Subscriptions" and select it.
     - Choose the target subscription where you created your VM.
     - In the left pane, select "Resource providers."
     - Search for "Microsoft.Insights" and click "Register" to enable it.

2. **Register Microsoft.AlertsManagement Resource Provider**

   To enable access to Alerts Management services, you need to register the Microsoft.AlertsManagement resource provider. You can do this using PowerShell or the Azure Portal.

   - **Azure Portal**
     - In the Azure Portal, navigate to "All services."
     - Search for "Subscriptions" and select it.
     - Choose the target subscription where you created your VM.
     - In the left pane, select "Resource providers."
     - Search for "Microsoft.AlertsManagement" and click "Register" to enable it.


## Task 3: Create and configure an Azure Log Analytics workspace and Azure Automation-based solutions

In this task, you will create and configure an Azure Log Analytics workspace and Azure Automation-based solutions

1. In the Azure portal, search for and select **Log Analytics workspaces** and, on the **Log Analytics workspaces** blade, click **+ Create**.

1. On the **Basics** tab of the **Create Log Analytics workspace** blade, enter the following settings, click **Review + Create** and then click **Create**:

    | Settings | Value |
    | --- | --- |
    | Subscription | the name of the Azure subscription you are using in this lab |
    | Resource group | the name of a new resource group **Cloudeye** |
    | Log Analytics Workspace | any unique name |
    | Region | the name of the Azure region into which you deployed the virtual machine in the previous task |
   

![Create-log-analysius-workspace](https://github.com/Saurabh-Bhargav/Project/assets/143943258/d9a81f5e-d619-4455-bb67-a8a4b188f16e)


    >**Note**: Make sure that you specify the same region into which you deployed virtual machines in the previous task.

    >**Note**: Wait for the deployment to complete. The deployment should take about 1 minute.

1. In the Azure portal, search for and select **Automation Accounts**, and on the **Automation Accounts** blade, click **+ Create**.

1. On the **Create an Automation Account** blade, specify the following settings, and click **Review + Create** upon validation click **Create**:

    | Settings | Value |
    | --- | --- |
    | Automation account name | any unique name |
    | Subscription | the name of the Azure subscription you are using in this lab |
    | Resource group | **Cloudeye** |
    | Region | the name of the Azure region determined based on [Workspace mappings documentation](https://docs.microsoft.com/en-us/azure/automation/how-to/region-mappings) |

    >**Note**: Make sure that you specify the Azure region based on the [Workspace mappings documentation](https://docs.microsoft.com/en-us/azure/automation/how-to/region-mappings)

    >**Note**: Wait for the deployment to complete. The deployment might take about 3 minutes.

1. Click **Go to resource**.

1. On the Automation account blade, in the **Configuration Management** section, click **Inventory**.
   

   ![Enable-inventory-inaccountautomation](https://github.com/Saurabh-Bhargav/Project/assets/143943258/aa26434e-f187-4724-b741-9b961ff70191)


1. In the **Inventory** pane, in the **Log Analytics workspace** drop-down list, select the Log Analytics workspace you created earlier in this task and click **Enable**.


    >**Note**: Wait for the installation of the corresponding Log Analytics solution to complete. This might take about 3 minutes.

    >**Note**: This automatically installs the **Change tracking** solution as well.

1. On the Automation account blade, in the **Update Management** section, click **Update management** and click **Enable**.
   

   ![Update-management-in-automation-acccount](https://github.com/Saurabh-Bhargav/Project/assets/143943258/7abb984a-9842-4afd-ab3c-82f97cad8bf3)

   
    >**Note**: Wait for the installation to complete. This might take about 5 minutes.

## Task 4: Review default monitoring settings of Azure virtual machines

In this task, you will review default monitoring settings of Azure virtual machines

1. In the Azure portal, search for and select **Virtual machines**, and on the **Virtual machines** blade, click **CloudeyeVM1**.

1. On the **CloudeyeVM1** blade, in the **Monitoring** section, click **Metrics**.

1. On the **CloudeyeVM1 \| Metrics** blade, on the default chart, note that the only available **Metrics Namespace** is **Virtual Machine Host**.

    >**Note**: This is expected, since no guest-level diagnostic settings have been configured yet. You do have, however, the option of enabling guest memory metrics directly from the **Metrics Namespace** drop down-list. You will enable it later in this exercise.

1. In the **Metric** drop-down list, review the list of available metrics.

    >**Note**: The list includes a range of CPU, disk, and network-related metrics that can be collected from the virtual machine host, without having access into guest-level metrics.

1. In the **Metric** drop-down list, select **Percentage CPU**, in the **Aggregation** drop-down list, select **Avg**, and review the resulting chart.

   
![Filter-on-metrics-before-mointor-confihuration](https://github.com/Saurabh-Bhargav/Project/assets/143943258/2073b9e1-c974-4e18-877a-1d8d4c35b5ed)


## Task 5: Configure Azure virtual machine diagnostic settings

In this task, you will configure Azure virtual machine diagnostic settings.

1. On the **cloudeyeVM1** blade, in the **Monitoring** section, click **Diagnostic settings**.

1. On the **Overview** tab of the **cloudeyeVM1 \| Diagnostic settings** blade, select a **Diagnostic storage account**, and then click **Enable guest-level monitoring**.

   
![Enable-Diagnosis-VM](https://github.com/Saurabh-Bhargav/Project/assets/143943258/55a5f9e4-35b8-406f-b99a-8783500eca0b)


    >**Note**: Wait for the diagnostic settings extension to be installed. This might take about 3 minutes.

1. Switch to the **Performance counters** tab of the **CloudeyeVM1 \| Diagnostic settings** blade and review the available counters.
   

![Check-performance-after-enabling-diagnosis](https://github.com/Saurabh-Bhargav/Project/assets/143943258/2f48f956-7df6-4171-9c34-cda0574ae0cc)


    >**Note**: By default, CPU, memory, disk, and network counters are enabled. You can switch to the **Custom** view for more detailed listing.

1. Switch to the **Logs** tab of the **CloudeyeVM1 \| Diagnostic settings** blade and review the available event log collection options.


    >**Note**: By default, log collection includes critical, error, and warning entries from the Application Log and System log, as well as Audit failure entries from the Security log. Here as well you can switch to the **Custom** view for more detailed configuration settings.

1. On the **CloudeyeVM1** blade, in the **Monitoring** section, click **Logs** and then click **Enable**.
   
   
![Enable-Logs-in_VM](https://github.com/Saurabh-Bhargav/Project/assets/143943258/bb58f4d5-9133-406a-9719-6ea608528bac)


1. On the **ClludeyeVM1 - Logs** blade, ensure **Azure Monitor agent (Recommended)** is selected, and then click **Configure**.  

    >**Note**: Do not wait for the operation to be completed, but instead proceed to the next step. The operation might take about 5 minutes.

1. On the **CloudeyeVM1 \| Logs** blade, in the **Monitoring** section, click **Metrics**.

1. On the **CloudeyeVM1 \| Metrics** blade, on the default chart, note that at this point, the **Metrics Namespace** drop-down list, in addition to the **Virtual Machine Host** entry includes also the **Guest (classic)** entry.


   ![GuestClassic-VM-Filter](https://github.com/Saurabh-Bhargav/Project/assets/143943258/9edc4319-17b7-47ad-bd0c-0345f87addb6)


    >**Note**: This is expected, since you enabled guest-level diagnostic settings. You also have the option to **Enable new guest memory metrics**.

1. In the **Metrics Namespace** drop-down list, select  the **Guest (classic)** entry.


   ![GuestClassic-VM-Filter](https://github.com/Saurabh-Bhargav/Project/assets/143943258/fb888a2f-4499-4114-88d4-dd1a2bb2e1f8)


1. In the **Metric** drop-down list, review the list of available metrics.

    >**Note**: The list includes additional guest-level metrics not available when relying on the host-level monitoring only.

1. In the **Metric** drop-down list, select **Memory\\Available Bytes**, in the **Aggregation** drop-down list, select **Max**, and review the resulting chart.


## Task 6: Review Azure Monitor functionality

1. In the Azure portal, search for and select **Monitor** and, on the **Monitor \| Overview** blade, click **Metrics**.

1. On the **Select a scope** blade, on the **Browse** tab, navigate to the **cloudeye** resource group, expand it, select the checkbox next to the **cloudeyeVM1** virtual machine entry within that resource group, and click **Apply**.

    >**Note**: This gives you the same view and options as those available from the **cloudeyeVM1 - Metrics** blade.

1. In the **Metric** drop-down list, select **Percentage CPU**, in the **Aggregation** drop-down list, select **Avg**, and review the resulting chart.

   
![Screenshot 2023-11-08 101048](https://github.com/Saurabh-Bhargav/Project/assets/143943258/8d35fac4-a6b2-4ada-941c-c672283a311e)


1. On the **Monitor \| Metrics** blade, on the **Avg Percentage CPU for CloudeyeVM1** pane, click **New alert rule**.

    >**Note**: Creating an alert rule from Metrics is not supported for metrics from the Guest (classic) metric namespace. This can be accomplished by using Azure Resource Manager templates, as described in the document [Send Guest OS metrics to the Azure Monitor metric store using a Resource Manager template for a Windows virtual machine](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/collect-custom-metrics-guestos-resource-manager-vm)

1. On the **Create alert rule** blade, in the **Condition** section, click the existing condition entry.

1. On the **Configure signal logic** blade, in the list of signals, in the **Alert logic** section, specify the following settings (leave others with their default values) and click **Done**:

    | Settings | Value |
    | --- | --- |
    | Threshold | **Static** |
    | Aggregation type | **Average** |
    | Operator | **Greater than** |
    | Threshold value | **2** |
    | Check every | **1 minute** |
    | Lookback period| **1 Minute** |


1. Click **Next: Actions >**, on the **Create an alert rule** blade, in the **Action group** section, click the **+ Create action group** button.

1. On the **Basics** tab of the **Create action group** blade, specify the following settings (leave others with their default values) and select **Next: Notifications >**:

    | Settings | Value |
    | --- | --- |
    | Subscription | the name of the Azure subscription you are using in this lab |
    | Resource group | **cloudeye** |
    | Action group name | **cloudeyeact** |
    | Display name | **cloudeyeact** |


1. On the **Notifications** tab of the **Create an action group** blade, in the **Notification type** drop-down list, select **Email/SMS message/Push/Voice**. In the **Name** text box, type **admin email**. Click the **Edit details** (pencil) icon.

1. On the **Email/SMS message/Push/Voice** blade, select the **Email** checkbox, type your email address in the **Email** textbox, leave others with their default values, click **OK**, back on the **Notifications** tab of the **Create an action group** blade, select **Next: Actions  >**.

1. On the **Actions** tab of the **Create action group** blade, review items available in the **Action type** drop-down list without making any changes and select **Review + create**.

1. On the **Review + create** tab of the **Create action group** blade, select **Create**.

   
![Create-action-group](https://github.com/Saurabh-Bhargav/Project/assets/143943258/532fbeb9-9549-4ebc-b32a-cdf80dbe5654)


1. Back on the **Create alert rule** blade, click **Next: Details >**, and in the **Alert rule details** section, specify the following settings (leave others with their default values):

    | Settings | Value |
    | --- | --- |
    | Alert rule name | **CPU Percentage above the test threshold** |
    | Alert rule description | **CPU Percentage above the test threshold** |
    | Severity | **Sev 3** |
    | Enable upon creation | **Yes** |



1. Click **Review + create** and on the **Review + create** tab click **Create**.


   ![Create-alert-rule](https://github.com/Saurabh-Bhargav/Project/assets/143943258/20b3f8d4-8847-4d96-ac8a-fef525b9e86a)


    >**Note**: It can take up to 10 minutes for a metric alert rule to become active.

1. In the Azure portal, search for and select **Virtual machines**, and on the **Virtual machines** blade, click **cloudeyeVM1**.

1. On the **cloudeyeVM1** blade, click **Connect**, in the drop-down menu, click **RDP**, on the **Connect with RDP** blade, click **Download RDP File** and follow the prompts to start the Remote Desktop session.

    >**Note**: This step refers to connecting via Remote Desktop from a Windows computer. On a Mac, you can use Remote Desktop Client from the Mac App Store and on Linux computers you can use an open source RDP client software.

    >**Note**: You can ignore any warning prompts when connecting to the target virtual machines.

1. When prompted, sign in by using the **Student** username and the password from the parameters file.

1. Within the Remote Desktop session, click **Start**, expand the **Windows System** folder, and click **Command Prompt**.

1. From the Command Prompt, run the following to trigger increased CPU utilization on the **cloudeyeVM1** Azure VM:

   ```sh
   for /l %a in (0,0,1) do echo a
   ```

![RDP-VM-CMD-COmmand](https://github.com/Saurabh-Bhargav/Project/assets/143943258/b37a52bd-c357-406c-a0b3-e6dc08f9bdfa)


    >**Note**: This will initiate the infinite loop that should increase the CPU utilization above the threshold of the newly created alert rule.

1. Leave the Remote Desktop session open and switch back to the browser window displaying the Azure portal on your lab computer.

1. In the Azure portal, navigate back to the **Monitor** blade and click **Alerts**.


   ![Monitor-Alert-Fired](https://github.com/Saurabh-Bhargav/Project/assets/143943258/b2241f8d-5372-4f39-9f50-25d7a8e02667)


1. Note the number of **Sev 3** alerts and then click the **Sev 3** row.

    >**Note**: You might need to wait for a few minutes and click **Refresh**.

1. On the **All Alerts** blade, review generated alerts.

## Task 7: Review Azure Log in Storage account

1. In the Azure portal, navigate back to the **Monitor** blade, click **Logs**.

    >**Note**: You might need to click **Get Started** if this is the first time you access Log Analytics.

1. If necessary, click **Select scope**, on the **Select a scope** blade, select the **Recent** tab, select **cloudeyeVM1**, and click **Apply**.

1. In the query window, paste the following query, click **Run**, and review the resulting chart:

   ```sh
   // Virtual Machine available memory
   // Chart the VM's available memory over the last hour.
   InsightsMetrics
   | where TimeGenerated > ago(1h)
   | where Name == "AvailableMB"
   | project TimeGenerated, Name, Val
   | render timechart
   ```

    > **Note**: The query should not have any errors (indicated by red blocks on the right scroll bar). If the query will not paste without errors directly from the instructions, paste the query code into a text editor such as Notepad, and then copy and paste it into the query window from there.

### Logs in Storage Account

Here is a screenshot showing the logs saved in the storage account:

![image](https://github.com/Saurabh-Bhargav/Project/assets/143943258/c8179b59-7524-45dd-a9e3-65ea5c9c6d9c)



## Clean up resources

>**Note**: Remember to remove any newly created Azure resources that you no longer use. Removing unused resources ensures you will not see unexpected charges.

## Review

In this lab, you have:

+ Provisioned the lab environment
+ Created and configured an Azure Log Analytics workspace and Azure Automation-based solutions
+ Reviewed default monitoring settings of Azure virtual machines
+ Configured Azure virtual machine diagnostic settings
+ Reviewed Azure Monitor functionality
+ Reviewed Azure Log Analytics functionality
