---
title: 擴充 SharePoint 專案專案 |Microsoft Docs
description: 查看延伸 SharePoint 專案專案的工作。 瞭解專案專案延伸和專案專案實例的關聯方式。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e8486120b0f08077bc30c2a5177a8aba915c37f4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948670"
---
# <a name="extend-sharepoint-project-items"></a>擴充 SharePoint 專案專案
  當您想要將功能加入至已安裝在 Visual Studio 中的 SharePoint 專案專案類型時，請建立專案專案延伸模組。 例如，您可以在 Visual Studio 中建立內建 **事件接收器** 或 **清單定義** 專案專案的延伸模組，也可以建立自訂專案專案類型的擴充功能。 您也可以建立所有 SharePoint 專案專案類型的擴充功能。

## <a name="tasks-for-extending-sharepoint-project-items"></a>擴充 SharePoint 專案專案的工作
 若要擴充專案專案，請建立一個 Visual Studio 擴充元件來執行 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 介面。 如需詳細資訊，請參閱 [如何：建立 SharePoint 專案專案延伸](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)模組。

 當您擴充專案專案時，您也可以將下列功能加入至專案專案：

- 將快捷方式功能表項目加入至專案專案。 當您在 **方案總管** 中開啟專案專案的快捷方式功能表時，功能表項目就會出現。 您可以開啟快捷方式功能表，方法是以滑鼠右鍵按一下專案專案，或選擇它，然後選擇 **Shift** + **F10** 鍵。 如需詳細資訊，請參閱 [如何：將快捷方式功能表項目加入至 SharePoint 專案專案延伸](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)模組。

- 將自訂屬性加入至專案專案。 當您在 **方案總管** 中選擇專案專案時，屬性會出現在 [**屬性**] 視窗中。 如需詳細資訊，請參閱 [如何：將屬性加入至 SharePoint 專案專案延伸](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)模組。

  如需示範如何建立、部署和測試專案專案延伸的逐步解說，請參閱 [逐步解說：擴充 SharePoint 專案專案類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)。

## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>瞭解專案專案延伸和專案專案實例之間的關聯性
 當您建立專案專案延伸時，Visual Studio 將相關聯類型的專案專案加入至 SharePoint 專案時，會載入您的延伸模組。 例如，如果您建立 **事件接收器** 專案專案的擴充功能，Visual Studio 當使用者將 **事件接收器** 專案專案加入至專案時，就會載入您的延伸模組。 Visual Studio 針對所有相關聯專案專案類型的實例，使用相同的延伸模組實例。 在上述範例中，如果使用者將第二個 **事件接收器** 專案專案加入至專案，則會使用您的延伸模組實例來自訂第二個專案專案。

 若要存取您所擴充之專案專案類型的特定實例，請 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 在方法的執行中處理 *projectItemType* 參數的其中一個事件 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 。 例如，若要判斷當您要擴充之類型的專案專案加入至專案時，請處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 事件。 如需詳細資訊，請參閱 [如何：建立 SharePoint 專案專案延伸](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)模組。

## <a name="identifiers-for-sharepoint-project-items"></a>SharePoint 專案專案的識別碼
 每個 SharePoint 專案專案都有對應的字串識別碼。 如果您想要執行下列工作，您必須知道專案專案的識別碼：

- 建立專案專案的擴充功能。 在此情況下，您必須將想要擴充之專案專案的識別碼傳遞給的函式 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> 。 若要建立所有專案專案類型的延伸模組，請傳遞 **\\** * 字串值。

- 以程式設計方式將專案專案加入至專案。 在此情況下，您必須將專案專案的識別碼傳遞給 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> 方法。

  下表列出 Visual Studio 隨附的 SharePoint 專案專案識別碼。

|專案專案名稱|字串識別碼|
|-----------------------|-----------------------|
|商務資料目錄模型|VisualStudio. BusinessDataConnectivity|
|內容類型|VisualStudio。|
|事件接收器|VisualStudio. EventHandler|
|空元素|VisualStudio. GenericElement|
|清單定義<br /><br /> 來自內容類型的清單定義|VisualStudio. ListDefinition|
|清單實例|VisualStudio. ListInstance|
|模組|VisualStudio. Module|
|循序性工作流程<br /><br /> 狀態機器工作流程|VisualStudio，工作流程|
|網站定義|VisualStudio. SiteDefinition|
|視覺網頁元件|VisualStudio. VisualWebPart|
|Web 組件|VisualStudio。|
|工作流程關聯表單|VisualStudio. WorkflowAssociation|

## <a name="see-also"></a>另請參閱
- [如何：建立 SharePoint 專案專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [如何：將快捷方式功能表項目加入至 SharePoint 專案專案延伸模組](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [如何：將屬性加入至 SharePoint 專案專案延伸模組](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [逐步解說：擴充 SharePoint 專案專案類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
- [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)
