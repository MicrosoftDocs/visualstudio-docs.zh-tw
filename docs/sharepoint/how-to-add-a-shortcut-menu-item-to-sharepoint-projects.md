---
title: 如何：將快捷方式功能表項目加入至 SharePoint 專案 |Microsoft Docs
titleSuffix: ''
description: 在 Visual Studio 中，將快捷方式功能表項目加入至 SharePoint 專案。 當您在方案總管中的專案節點上按一下滑鼠右鍵時，功能表項目就會出現。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 54ac53ad317f500e787baebfdfeb4a86dc917e06
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216809"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>如何：將快捷方式功能表項目加入至 SharePoint 專案
  您可以將快捷方式功能表項目加入至任何 SharePoint 專案。 當使用者以滑鼠右鍵按一下 **方案總管** 中的專案節點時，就會顯示功能表項目。

 下列步驟假設您已建立專案延伸模組。 如需詳細資訊，請參閱 [如何：建立 SharePoint 專案延伸](../sharepoint/how-to-create-a-sharepoint-project-extension.md)模組。

### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>將快捷方式功能表項目加入至 SharePoint 專案

1. 在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 您的實作為方法中 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> ，處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> *projectService* 參數的事件。

2. 在事件的事件處理常式中 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> ，將新的 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 物件加入至 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> 事件引數參數的或集合。

3. 在 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> 新物件的事件處理常式中 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> ，執行您要在使用者按一下快捷方式功能表項目時執行的工作。

## <a name="example"></a>範例
 下列程式碼範例示範如何在 **方案總管** 中，將快捷方式功能表項目加入至 SharePoint 專案節點。 當使用者以滑鼠右鍵按一下專案節點，然後按一下 [ **寫入訊息至輸出視窗** ] 功能表項目時，Visual Studio 會在 [ **輸出** ] 視窗中顯示一則訊息。 這個範例會使用 SharePoint 專案服務來顯示訊息。 如需詳細資訊，請參閱 [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs" id="Snippet1":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb" id="Snippet1":::

## <a name="compile-the-code"></a>編譯程式碼
 此範例需要類別庫專案，其中包含下列元件的參考：

- VisualStudio SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>部署延伸模組
 若要部署擴充功能，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件和您想要使用擴充功能散發的任何其他檔案，建立 (VSIX) 封裝的延伸模組。 如需詳細資訊，請參閱 [Visual Studio 中的部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 專案](../sharepoint/extending-sharepoint-projects.md)
- [如何：建立 SharePoint 專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [如何：將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
