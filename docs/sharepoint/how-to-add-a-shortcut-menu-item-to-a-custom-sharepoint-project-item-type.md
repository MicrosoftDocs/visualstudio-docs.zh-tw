---
title: 將捷徑功能表項目新增至自訂 SharePoint 專案項目類型
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 95c47cdc00fc9035870aed4ac2e0bee4d3c1c5af
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401626"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>作法：將捷徑功能表項目新增至自訂的 SharePoint 專案項目類型
  當您定義自訂的 SharePoint 專案項目類型時，您可以快顯功能表項目加入專案項目。 使用者以滑鼠右鍵按一下專案項目中的時，會出現的功能表項目**方案總管 中**。

 下列步驟假設您已經定義自己的 SharePoint 專案項目類型。 如需詳細資訊，請參閱[如何：定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。

### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>若要將捷徑功能表項目新增至自訂專案項目類型

1. 在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>方法您<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>實作、 控制代碼<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>事件*projectItemTypeDefinition*參數。

2. 在您的事件處理常式，如<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>事件，加入新<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>物件<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A>或<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A>事件引數參數的集合。

3. 在 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>新的事件處理常式<xref:Microsoft.VisualStudio.SharePoint.IMenuItem>物件中，執行您想要在使用者選擇您的快顯功能表項目時所執行的工作。

## <a name="example"></a>範例
 下列程式碼範例示範如何加入自訂專案項目類型的操作功能表項目。 當使用者開啟快顯功能表中的專案項目從**方案總管**並選擇**將訊息寫入至輸出視窗**功能表項目，Visual Studio 會顯示在訊息**輸出**視窗。

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]

 此範例會使用 SharePoint 專案服務來將訊息寫入**輸出**視窗。 如需詳細資訊，請參閱 <<c0> [ 使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要參考下列組件的類別庫專案：

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>部署專案項目
 若要讓其他開發人員使用您的專案項目，建立專案範本或專案項目範本。 如需詳細資訊，請參閱 <<c0> [ 建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。

 若要部署的專案項目，建立[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件、 範本和任何其他您想要與專案項目一起散發的檔案。 如需詳細資訊，請參閱 <<c0> [ 部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱
- [如何：定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [如何：將屬性加入至自訂的 SharePoint 專案項目類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)
