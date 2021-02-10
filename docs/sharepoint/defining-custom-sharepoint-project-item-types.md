---
title: 定義自訂 SharePoint 專案專案類型 |Microsoft Docs
description: 當您想要建立新種類的 SharePoint 專案專案時，請定義自訂 SharePoint 專案專案類型。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 00ee9f41695078d8bea5daacf1c0ccfd392a64cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948865"
---
# <a name="define-custom-sharepoint-project-item-types"></a>定義自訂 SharePoint 專案專案類型
  當您想要建立新種類的 SharePoint 專案專案時，請定義新的 SharePoint 專案專案類型。 例如，Visual Studio 不包含將欄位或自訂動作加入至 SharePoint 網站的 SharePoint 專案專案。 您可以定義自己的 SharePoint 專案專案類型，以建立欄位、自訂動作或其他類型的 SharePoint 元件。

## <a name="tasks-for-defining-sharepoint-project-item-types"></a>定義 SharePoint 專案專案類型的工作
 若要定義自訂專案專案類型，請建立一個 Visual Studio 擴充元件來執行 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 介面。 如需詳細資訊，請參閱 [如何：定義 SharePoint 專案專案類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。

 當您定義自訂專案專案類型時，您也可以將下列功能加入至專案專案：

- 將快捷方式功能表項目加入至專案專案。 當您在 [**方案總管**] 中開啟專案專案的快捷方式功能表時，會顯示功能表項目，方法是以滑鼠右鍵按一下專案專案，或選擇該專案，然後選擇 [ **Shift** + **F10** 鍵]。 如需詳細資訊，請參閱 [如何：將快捷方式功能表項目加入至自訂 SharePoint 專案專案類型](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)。

- 將自訂屬性加入至專案專案。 當您在 **方案總管** 中選擇專案專案時，屬性會出現在 [**屬性**] 視窗中。 如需詳細資訊，請參閱 [如何：將屬性加入至自訂 SharePoint 專案專案類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)。

  若要讓其他開發人員可以在 Visual Studio 中使用您的專案專案，請建立 .spdata 檔案，並建立與專案專案相關聯的專案範本或專案範本。 如需詳細資訊，請參閱 [建立 SharePoint 專案專案的專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。

## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>瞭解專案專案類型和專案專案實例之間的關聯性
 當您定義 SharePoint 專案專案類型時，Visual Studio 當相關聯類型的專案專案加入至 SharePoint 專案時，會載入您的延伸模組。 例如，如果您定義新的 **自訂動作** 專案專案類型，Visual Studio 當使用者將 **自訂動作** 專案專案加入至專案時，就會載入您的延伸模組。 Visual Studio 針對所有相關聯專案專案類型的實例，使用相同的延伸模組實例。 在上述範例中，如果使用者將第二個 **自訂動作** 專案專案加入至專案，則會使用您的延伸模組實例來自訂第二個專案專案。

 若要存取專案專案類型的特定實例，請 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 在方法的執行中處理 *projectItemTypeDefinition* 參數的其中一個事件 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 。 例如，若要判斷何時將自訂類型的專案專案加入至專案，請處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 事件。 如需詳細資訊，請參閱 [如何：定義 SharePoint 專案專案類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。

## <a name="see-also"></a>另請參閱
- [如何：定義 SharePoint 專案專案類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [如何：將屬性加入至自訂 SharePoint 專案專案類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [如何：將快捷方式功能表項目加入至自訂 SharePoint 專案專案類型](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [建立 SharePoint 專案專案的專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [逐步解說：使用專案範本建立自訂動作專案專案（第1部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [逐步解說：使用專案範本建立網站資料行專案專案（第1部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [逐步解說：使用專案範本建立自訂動作專案專案（第2部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [逐步解說：使用專案範本建立網站資料行專案專案（第2部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [在 Visual Studio 中部署 SharePoint 工具的延伸模組](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
