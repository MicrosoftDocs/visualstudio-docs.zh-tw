---
title: 如何：建立 SharePoint 專案專案延伸模組 |Microsoft Docs
description: 當您想要將功能加入至已安裝在 Visual Studio 中的 SharePoint 專案專案時，請參閱如何建立專案專案延伸模組。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0f55eb3ba06f2541bf1f4777c24927993444c6b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873602"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>如何：建立 SharePoint 專案專案延伸模組
  當您想要將功能加入至已安裝在 Visual Studio 中的 SharePoint 專案專案時，請建立專案專案延伸模組。 如需詳細資訊，請參閱 [擴充 SharePoint 專案專案](../sharepoint/extending-sharepoint-project-items.md)。

### <a name="to-create-a-project-item-extension"></a>若要建立專案專案延伸模組

1. 建立類別庫 (Class Library) 專案。

2. 加入下列組件的參考：

    - VisualStudio SharePoint

    - System.ComponentModel.Composition

3. 建立實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 介面的類別。

4. 將下列屬性新增至類別：

    - <xref:System.ComponentModel.Composition.ExportAttribute>. 這個屬性可讓 Visual Studio 探索和載入您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 執行。 將型別傳遞 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 至屬性（attribute）的函式。

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. 在專案專案延伸中，這個屬性會識別您想要擴充的專案專案。 將專案專案的識別碼傳遞給屬性的函式。 如需 Visual Studio 內含之專案專案的識別碼清單，請參閱 [擴充 SharePoint 專案專案](../sharepoint/extending-sharepoint-project-items.md)。

5. 在方法的執行中 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> ，請使用 *projectItemType* 參數的成員定義您的延伸模組行為。 這個參數是一個 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> 物件，可讓您存取和介面中定義的事件 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> 。 若要存取您所擴充之專案專案類型的特定實例，請處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 事件，例如 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> 。

## <a name="example"></a>範例
 下列程式碼範例示範如何建立事件接收器專案專案的簡單擴充。 每次使用者將事件接收器專案專案加入至 SharePoint 專案時，此延伸模組會將訊息寫入至 [ **輸出** ] 視窗和 [ **錯誤清單** ] 視窗。

 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]

 這個範例會使用 SharePoint 專案服務，將訊息寫入 [ **輸出** ] 視窗和 [ **錯誤清單** ] 視窗。 如需詳細資訊，請參閱 [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。

## <a name="compile-the-code"></a>編譯程式碼
 此範例需要下列元件的參考：

- VisualStudio SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>部署延伸模組
 若要部署擴充功能，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件和您想要使用擴充功能散發的任何其他檔案，建立 (VSIX) 封裝的延伸模組。 如需詳細資訊，請參閱 [Visual Studio 中的部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 專案專案](../sharepoint/extending-sharepoint-project-items.md)
- [逐步解說：擴充 SharePoint 專案專案類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
