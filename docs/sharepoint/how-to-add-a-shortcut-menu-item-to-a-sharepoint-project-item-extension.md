---
title: 將快捷方式功能表項目加入至 SharePoint 專案專案延伸模組
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5c0515fddc106418902cd2cca9fcba4c0e365da1
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014855"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>如何：將快捷方式功能表項目加入至 SharePoint 專案專案延伸模組
  您可以使用專案專案延伸模組，將快捷方式功能表項目加入至現有的 SharePoint 專案專案。 當使用者以滑鼠右鍵按一下**方案總管**中的專案專案時，就會出現功能表項目。

 下列步驟假設您已建立專案專案延伸模組。 如需詳細資訊，請參閱[如何：建立 SharePoint 專案專案延伸](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)模組。

### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>若要在專案專案延伸模組中加入快捷方式功能表項目

1. 在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 您的執行方法中 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> ，處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> *projectItemType*參數的事件。

2. 在事件的事件處理常式中 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> ，將新的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 物件加入至 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> 事件引數參數的或集合。

3. 在 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> 新物件的事件處理常式中 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> ，執行您想要在使用者按一下快捷方式功能表項目時執行的工作。

## <a name="example"></a>範例
 下列程式碼範例示範如何將快捷方式功能表項目加入至事件接收器專案專案。 當使用者以滑鼠右鍵按一下**方案總管**中的專案專案，然後按一下 [將**訊息寫入輸出視窗**] 功能表項目時，Visual Studio 會在 [**輸出**] 視窗中顯示訊息。

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs#1)]

 這個範例會使用 SharePoint 專案服務，將訊息寫入至 [**輸出**] 視窗。 如需詳細資訊，請參閱[使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要具有下列元件參考的類別庫專案：

- VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>部署延伸模組
 若要部署擴充功能，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件建立擴充功能（VSIX）封裝，以及您想要與延伸模組一起散發的任何其他檔案。 如需詳細資訊，請參閱[在 Visual Studio 中部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [如何：建立 SharePoint 專案專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [如何：將屬性加入至 SharePoint 專案專案延伸模組](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [擴充 SharePoint 專案專案](../sharepoint/extending-sharepoint-project-items.md)
- [逐步解說：擴充 SharePoint 專案專案類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
