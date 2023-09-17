# NewHire AutoWizard

## Overview
The NewHire AutoWizard automates the onboarding of new employees into Azure Active Directory (Azure AD), simplifying user creation, group assignments, and welcome emails. This streamlined solution enhances efficiency, reduces manual tasks, and showcases automation capabilities.

## Prerequisites
- Azure Subscription (30 days free program utilized)
- Access to Azure AD and Logic Apps
- Visual Studio Code with Thunder Client extension

## Steps

### 1. Azure Resources Setup
- Create an Azure account.
- Design a Logic App workflow triggered by an event (e.g., SharePoint list entry or specific mailbox email) indicating a new employee hire.

### 2. Azure Logic App step up and User creation

Step 1: Receive HTTP Request in Logic App
Begin by setting up a step to receive an HTTP request. This serves as the trigger for the onboarding process.

Step 2: Create Azure AD User
Use the Azure AD connector in Logic Apps to automatically create a new user in Azure AD based on trigger event details.

### 3. Role and Group Assignment
- Assign predefined roles and groups to the new user based on job positions or departments indicated in the trigger.

### 4. Resource Provisioning
- Use the Azure Resource Manager connector in Logic Apps to provision necessary Azure resources for the user (e.g., VMs or specific permissions).

### 5. Welcome Email
- Leverage the Email connector in Logic Apps to send a welcome email to the new hire with instructions and necessary access details.

  
![Screenshot 2023-09-17 160748](https://github.com/Saurabh-Bhargav/Project/assets/143943258/47926877-0b3f-4514-af23-522944c49ce3)

## Benefits
- Eliminates manual onboarding tasks.
- Enhances efficiency.

## Additional Information
- No external dependencies.
- Trigger automation using an HTTP link from the Logic App.
- Integration with Azure services and Outlook for email (you can use other service providers also).
- Customizable Logic App for specific organizational needs.
- Access Logic App run history for troubleshooting.

## LinkedIn
Connect with me on [Saurabh Bhargav](www.linkedin.com/in/saurabh-bhargav) for further details and collaboration.

