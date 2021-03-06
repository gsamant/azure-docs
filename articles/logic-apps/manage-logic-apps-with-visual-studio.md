---
title: Manage logic apps with Visual Studio - Azure Logic Apps | Microsoft Docs
description: Manage logic apps and other Azure assets with Visual Studio Cloud Explorer
author: ecfan
manager: SyntaxC4
editor: ''
services: logic-apps
documentationcenter: ''

ms.assetid: 
ms.service: logic-apps
ms.workload: logic-apps
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.custom: mvc
ms.date: 03/15/2018
ms.author: estfan; LADocs
---

# Manage logic apps with Visual Studio

Although you can create, edit, manage, and deploy logic apps 
in the <a href="https://portal.azure.com" target="_blank">Azure portal</a>, 
you can also use Visual Studio when you want to add logic apps to source control, 
publish different versions, and create 
[Azure Resource Manager](../azure-resource-manager/resource-group-overview.md) 
templates for different deployment environments. With Visual Studio Cloud Explorer, 
you can find and manage your logic apps along with other Azure resources. 
For example, you can open, download, edit, run, view run history, 
disable, and enable logic apps that are already deployed in the Azure portal. 
If you're new to working with Azure Logic Apps in Visual Studio, learn 
[how to create logic apps with Visual Studio](../logic-apps/quickstart-create-logic-apps-with-visual-studio.md).

> [!IMPORTANT]
> Deploying or publishing a logic app from Visual Studio 
> overwrites the version of that app in the Azure portal. 
> So if you make changes in the Azure portal that you want to keep, 
> make sure that you [refresh the logic app in Visual Studio](#refresh) 
> from the Azure portal before the next time you deploy or publish from Visual Studio.

<a name="requirements"></a>

## Prerequisites

* If you don't have an Azure subscription, 
<a href="https://azure.microsoft.com/free/" target="_blank">sign up for a free Azure account</a>.

* Download and install these tools, if you don't have them already: 

  * <a href="https://www.visualstudio.com/downloads" target="_blank">Visual Studio 2017 or Visual Studio 2015 - Community edition or greater</a>. 
  This quickstart uses Visual Studio Community 2017, which is free.

  * <a href="https://azure.microsoft.com/downloads/" target="_blank">Azure SDK (2.9.1 or later)</a> 
  and <a href="https://github.com/Azure/azure-powershell#installation" target="_blank">Azure PowerShell</a>

  * <a href="https://marketplace.visualstudio.com/items?itemName=VinaySinghMSFT.AzureLogicAppsToolsforVisualStudio-18551" target="_blank">Azure Logic Apps Tools for Visual Studio 2017</a> 
  or the <a href="https://marketplace.visualstudio.com/items?itemName=VinaySinghMSFT.AzureLogicAppsToolsforVisualStudio" target="_blank">Visual Studio 2015 version</a> 
  
    You can either download and install Azure Logic Apps Tools 
    directly from the Visual Studio Marketplace, or learn 
    <a href="https://docs.microsoft.com/visualstudio/ide/finding-and-using-visual-studio-extensions" target="_blank">how to install this extension from inside Visual Studio</a>. 
    Make sure that you restart Visual Studio after you finish installing.

* Access to the web while using the embedded Logic App Designer

  The designer requires an internet connection to create resources in Azure 
  and to read the properties and data from connectors in your logic app. 
  For example, if you use the Dynamics CRM Online connector, 
  the designer checks your CRM instance for available 
  default and custom properties.

<a name="find-logic-apps-vs"></a>

## Find your logic apps

In Visual Studio, you can find all the logic 
apps that are associated with your Azure subscription 
and are deployed in the Azure portal by using Cloud Explorer.

1. Open Visual Studio. On the **View** menu, 
select **Cloud Explorer**.

2. In Cloud Explorer, choose **Account Management**. 
Select the Azure subscription associated with your logic apps, 
then choose **Apply**. For example:

   ![Choose "Account Management"](./media/manage-logic-apps-with-visual-studio/account-management-select-Azure-subscription.png)

2. Based on whether you're searching by **Resource Groups** 
or **Resource Types**, follow these steps:

   * **Resource Groups**: Under your Azure subscription, 
   Cloud Explorer shows all the resource groups that are 
   associated with that subscription. 
   Expand the resource group that contains your logic app, 
   then select your logic app.

   * **Resource Types**: Under your Azure subscription, 
   expand **Logic Apps**. After Cloud Explorer shows all 
   the deployed logic apps that are associated with your subscription, 
   select your logic app.

<a name="open-designer"></a>

## Open in Visual Studio

In Visual Studio, you can open logic apps previously created 
and deployed either directly through the Azure portal 
or as Azure Resource Manager projects with Visual Studio.

1. Open Cloud Explorer, and find your logic app. 

2. On the logic app's shortcut menu, 
select **Open With Logic App Editor**.

   This example shows logic apps by resource type, 
   so your logic apps appear under the **Logic Apps** section.

  ![Open deployed logic app from Azure portal](./media/manage-logic-apps-with-visual-studio/open-logic-app-in-editor.png)

   After the logic app opens in Logic App Designer, 
   at the bottom of the designer, you can choose **Code View** 
   so that you can review the underlying logic app definition structure. 
   If you want to create a deployment template for the logic app, 
   learn [how to download an Azure Resource Manager template](#download-logic-app) 
   for that logic app. Learn more about 
   [Resource Manager templates](../azure-resource-manager/resource-group-overview.md#template-deployment).

<a name="download-logic-app"></a>

## Download from Azure

You can download logic apps from the 
<a href="https://portal.azure.com" target="_blank">Azure portal</a> 
and save them as [Azure Resource Manager](../azure-resource-manager/resource-group-overview.md) 
templates. You can then locally edit the templates with Visual Studio 
and customize logic apps for different deployment environments. 
Downloading logic apps automatically *parameterizes* their 
definitions inside [Resource Manager templates](../azure-resource-manager/resource-group-overview.md#template-deployment), 
which also use JavaScript Object Notation (JSON).

1. In Visual Studio, open Cloud Explorer, 
then find and select the logic app 
that you want to download from Azure.

2. On that app's shortcut menu, 
select **Open With Logic App Editor**.

   The Logic App Designer opens and shows the logic app. 
   To review logic app's underlying definition and structure, 
   at the bottom of the designer, choose **Code View**. 

3. On the designer toolbar, choose **Download**.

   ![Choose "Download"](./media/manage-logic-apps-with-visual-studio/download-logic-app.png)

4. When you're prompted for a location, 
browse to that location and save the 
Resource Manager template for the 
logic app definition in JSON (.json) file format. 

Your logic app definition appears in the `resources` 
subsection inside the Resource Manager template. 
You can now edit the logic app definition 
and Resource Manager template with Visual Studio. 
You can also add the template as an Azure Resource 
Manager project to a Visual Studio solution. 
Learn about [Resource Manager projects for logic apps in Visual Studio](../logic-apps/quickstart-create-logic-apps-with-visual-studio.md). 

<a name="refresh"></a>

## Refresh from Azure

If you edit your logic app in the Azure portal and want to keep those changes, 
make sure that you refresh that app's version in Visual Studio with those changes. 

* In Visual Studio, on the Logic App Designer toolbar, choose **Refresh**.

  -or-

* In Visual Studio Cloud Explorer, open your logic app's shortcut menu, 
and select **Refresh**. 

![Refresh logic app with updates](./media/manage-logic-apps-with-visual-studio/refresh-logic-app.png)

## Publish logic app updates

When you're ready to deploy your logic app updates from Visual Studio to Azure, 
on the Logic App Designer toolbar, choose **Publish**.

![Publish updated logic app](./media/manage-logic-apps-with-visual-studio/publish-logic-app.png)

## Manually run your logic app

You can manually trigger a logic app deployed in Azure from Visual Studio. 
On the Logic App Designer toolbar, choose **Run Trigger**.

![Manually run logic app](./media/manage-logic-apps-with-visual-studio/manually-run-logic-app.png)

## Review run history

To check the status and diagnose problems with logic app runs, 
you can review the details, such as inputs and outputs, 
for those runs in Visual Studio.

1. In Cloud Explorer, open your logic app's shortcut menu, 
and select **Open run history**.

   ![Open run history](./media/manage-logic-apps-with-visual-studio/view-run-history.png)

2. To view the details for a specific run, 
double-click a run. For example:

   ![Detailed run history](./media/manage-logic-apps-with-visual-studio/view-run-history-details.png)
  
   > [!TIP]
   > To sort the table by property, 
   > choose the column header for that property. 

3. Expand the steps whose inputs and outputs you want to review. 
For example:

   ![View inputs and outputs for each step](./media/manage-logic-apps-with-visual-studio/run-inputs-outputs.png)

## Disable or enable logic app

Without deleting your logic app, you can stop the trigger from 
firing the next time when the trigger condition is met. 
Disabling your logic app prevents the Logic Apps engine 
from creating and running future workflow instances for your logic app.
In Cloud Explorer, open your logic app's shortcut menu, 
and select **Disable**.

![Disable your logic app](./media/manage-logic-apps-with-visual-studio/disable-logic-app.png)

When you're ready for your logic app to resume operation, 
you can reactivate your logic app. In Cloud Explorer, 
open your logic app's shortcut menu, and select **Enable**.

![Enable your logic app](./media/manage-logic-apps-with-visual-studio/enable-logic-app.png)

## Delete your logic app

To delete your logic app from the Azure portal, 
in Cloud Explorer, open your logic app's shortcut menu, 
and select **Delete**.

![Delete your logic app](./media/manage-logic-apps-with-visual-studio/delete-logic-app.png)

## Next steps

In this article, you learned how to manage deployed logic apps with Visual Studio. 
Next, learn about customizing logic app definitions for deployment:

> [!div class="nextstepaction"]
> [Author logic app definitions in JSON](../logic-apps/logic-apps-author-definitions.md)