---
title: 如何：定義 SharePoint 專案專案類型 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: ae709bf2d81e2b8b00dc984602c0426fdf272ebd
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016851"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>如何：定義 SharePoint 專案專案類型
  當您想要建立自訂 SharePoint 專案專案時，請定義專案專案類型。 如需詳細資訊，請參閱[定義自訂 SharePoint 專案專案類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)。

### <a name="to-define-a-project-item-type"></a>若要定義專案專案類型

1. 建立類別庫 (Class Library) 專案。

2. 加入下列組件的參考：

    - VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. 建立實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 介面的類別。

4. 將下列屬性新增至類別：

    - <xref:System.ComponentModel.Composition.ExportAttribute>. 這個屬性可讓 Visual Studio 探索及載入您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 執行。 將 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 類型傳遞給屬性的函式。

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. 在專案專案類型定義中，這個屬性會指定新專案專案的字串識別碼。 建議您使用 [*公司名稱*] 格式。*功能名稱*，以協助確保所有專案專案都具有唯一的名稱。

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. 這個屬性會指定要在**方案總管**中顯示此專案專案的圖示。 這個屬性是選擇性的;如果您未將它套用至類別，Visual Studio 會顯示專案專案的預設圖示。 如果您設定這個屬性，請傳遞內嵌在元件中之圖示或點陣圖的完整名稱。

5. 在方法的執行中 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> ，請使用*projectItemTypeDefinition*參數的成員來定義專案專案類型的行為。 這個參數是 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> 物件，可讓您存取和介面中定義的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 事件 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> 。 若要存取專案專案類型的特定實例，請處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 事件（例如 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 和） <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> 。

## <a name="example"></a>範例
 下列程式碼範例示範如何定義簡單的專案專案類型。 當使用者將此類型的專案專案加入至專案時，此專案專案類型會將訊息寫入至 [**輸出**] 視窗，並**錯誤清單**] 視窗。

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]

 這個範例會使用 SharePoint 專案服務，將訊息寫入至 [**輸出**] 視窗，並**錯誤清單**] 視窗。 如需詳細資訊，請參閱[使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要參考下列元件：

- VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>部署專案專案
 若要讓其他開發人員使用您的專案專案，請建立專案範本或專案專案範本。 如需詳細資訊，請參閱[建立 SharePoint 專案專案的專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。

 若要部署專案專案，請建立 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 元件的擴充功能（VSIX）封裝、範本，以及您想要與專案專案一起散發的任何其他檔案。 如需詳細資訊，請參閱[在 Visual Studio 中部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [定義自訂 SharePoint 專案專案類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [為 SharePoint 專案專案建立專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [逐步解說：使用專案範本建立自訂動作專案專案（第1部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [逐步解說：使用專案範本建立網站資料行專案專案（第1部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [如何：將屬性加入至自訂 SharePoint 專案專案類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [如何：將快捷方式功能表項目加入至自訂 SharePoint 專案專案類型](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
