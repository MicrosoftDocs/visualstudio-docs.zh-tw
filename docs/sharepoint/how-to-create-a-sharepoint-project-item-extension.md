---
title: HOW TO：建立 SharePoint 專案項目擴充功能 |Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 42cea2633ceb0cbda1c63b76a4e2b7775e967bc2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597097"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>HOW TO：建立 SharePoint 專案項目擴充功能
  當您想要將功能新增至已安裝 Visual Studio 中 SharePoint 專案項目，請建立專案項目擴充功能。 如需詳細資訊，請參閱 <<c0> [ 擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)。

### <a name="to-create-a-project-item-extension"></a>若要建立專案項目擴充功能

1.  建立類別庫 (Class Library) 專案。

2.  加入下列組件的參考：

    -   Microsoft.VisualStudio.SharePoint

    -   System.ComponentModel.Composition

3.  建立實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 介面的類別。

4.  將下列屬性新增至類別：

    -   <xref:System.ComponentModel.Composition.ExportAttribute>. 這個屬性可讓 Visual Studio 來探索及載入您<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>實作。 傳遞<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>屬性建構函式的型別。

    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. 在專案項目擴充功能，此屬性會識別您想要擴充的專案項目。 將專案項目識別碼傳遞至屬性建構函式中。 如需隨附於 Visual Studio 的專案項目識別碼的清單，請參閱 <<c0> [ 擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)。

5.  在您實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>方法，使用成員*projectItemType*參數來定義您的延伸模組的行為。 這個參數是<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>可用來存取事件中所定義的物件<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>介面。 若要存取您要擴充的專案項目類型的特定執行個體，處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>事件，例如<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>。

## <a name="example"></a>範例
 下列程式碼範例示範如何建立簡單的擴充功能事件接收器的專案項目。 每次使用者在 SharePoint 專案中加入事件接收器專案項目，此延伸模組將訊息寫入至**輸出**視窗和**錯誤清單**視窗。

 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]

 此範例會使用 SharePoint 專案服務來將訊息寫入**輸出**視窗和**錯誤清單**視窗。 如需詳細資訊，請參閱 <<c0> [ 使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要參考下列組件：

-   Microsoft.VisualStudio.SharePoint

-   System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>部署擴充功能
 若要部署的延伸模組，建立[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要將副檔名的檔案。 如需詳細資訊，請參閱 <<c0> [ 部署 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)
- [逐步解說：擴充 SharePoint 專案項目類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
