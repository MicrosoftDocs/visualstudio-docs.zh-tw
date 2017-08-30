---
title: 'Walkthrough: Add Feature Event Receivers | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.prod: visual-studio-dev14
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
ms.assetid: fbd44c33-2c27-4d57-abca-21cddc16fbc3
caps.latest.revision: 24
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 5509743aa0d815bb2b3a7eece6c5822ac189ed14
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="walkthrough-add-feature-event-receivers"></a>Walkthrough: Add Feature Event Receivers
  Feature event receivers are methods that execute when one of the following feature-related events occurs in SharePoint:  
  
-   A feature is installed.  
  
-   A feature is activated.  
  
-   A feature is deactivated.  
  
-   A feature is removed.  
  
 This walkthrough demonstrates how to add an event receiver to a feature in a SharePoint project. It demonstrates the following tasks:  
  
-   Creating an empty project with a feature event receiver.  
  
-   Handling the **FeatureDeactivating** method.  
  
-   Using the SharePoint project object model to add an announcement to the Announcements list.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisites  
 You need the following components to complete this walkthrough:  
  
-   Supported editions of Microsoft Windows and SharePoint. For more information, see [Requirements for Developing SharePoint Solutions](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="creating-a-feature-event-receiver-project"></a>Creating a Feature Event Receiver Project  
 First, create a project to contain the feature event receiver.  
  
#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>To create a project with a feature event receiver  
  
1.  On the menu bar, choose **File**, **New**, **Project** to display the **New Project** dialog box.  
  
2.  Expand the **SharePoint** node under either **Visual C#** or **Visual Basic**, and then choose the **2010** node.  
  
3.  In the **Templates** pane, choose the **SharePoint 2010 Project** template.  
  
     You use this project type for feature event receivers because they have no project template.  
  
4.  In the **Name** box, enter **FeatureEvtTest**, and then choose the **OK** button to display the **SharePoint Customization Wizard**.  
  
5.  On the **Specify the site and security level for debugging** page, enter the URL for the SharePoint server site to which you want to add the new custom field item, or use the default location (http://\<*system name*>/).  
  
6.  In the **What is the trust level for this SharePoint solution?** section, choose the **Deploy as a farm solution** option button.  
  
     For more information about sandboxed solutions versus farm solutions, see [Sandboxed Solution Considerations](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Choose the **Finish** button, and then notice that a feature that's named Feature1 appears under the **Features** node.  
  
## <a name="adding-an-event-receiver-to-the-feature"></a>Adding an Event Receiver to the Feature  
 Next, add an event receiver to the feature and add code that executes when the feature is deactivated.  
  
#### <a name="to-add-an-event-receiver-to-the-feature"></a>To add an event receiver to the feature  
  
1.  Open the shortcut menu for the Features node, and then choose **Add Feature** to create a feature.  
  
2.  Under the **Features** node, open the shortcut menu for **Feature1**, and then choose **Add Event Receiver** to add an event receiver to the feature.  
  
     This adds a code file under Feature1. In this case, it is named either Feature1.EventReceiver.cs or Feature1.EventReceiver.vb, depending on your project's development language.  
  
3.  If your project is written in [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], add the following code at the top of the event receiver if it is not already there:  
  
     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  The event receiver class contains several commented-out methods that act as events. Replace the **FeatureDeactivating** method with the following:  
  
     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]  [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]  
  
## <a name="testing-the-feature-event-receiver"></a>Testing the Feature Event Receiver  
 Next, deactivate the feature to test whether the **FeatureDeactivating** method outputs an announcement to the SharePoint Announcements list.  
  
#### <a name="to-test-the-feature-event-receiver"></a>To test the feature event receiver  
  
1.  Set the value of the project's **Active Deployment Configuration** property to **No Activation**.  
  
     Setting this property prevents the feature from activating in SharePoint and lets you debug feature event receivers. For more information, see [Debugging SharePoint Solutions](../sharepoint/debugging-sharepoint-solutions.md).  
  
2.  Choose the **F5** key to run the project and deploy it to SharePoint.  
  
3.  At the top of the SharePoint Web page, open the **Site Actions** menu, and then choose **Site Settings**.  
  
4.  Under the **Site Actions** section of the **Site Settings** page, choose the **Manage site features** link.  
  
5.  On the **Features** page, choose the **Activate** button next to the **FeatureEvtTest Feature1** Feature.  
  
6.  On the **Features** page, choose the **Deactivate** button next to the **FeatureEvtTest Feature1** Feature, and then choose the **Deactivate this feature** confirmation link to deactivate the Feature.  
  
7.  Choose the **Home** button.  
  
     Notice that an announcement appears in the **Announcements** list after the feature is deactivated.  
  
## <a name="see-also"></a>See Also  
 [How to: Create an Event Receiver](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  
