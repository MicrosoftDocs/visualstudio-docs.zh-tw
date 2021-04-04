---
title: 如何：定義 SharePoint 專案專案類型 |Microsoft Docs
description: 瞭解如何在您想要建立自訂 SharePoint 專案專案時，定義專案專案類型。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 16e7070769edf3ee65ee425a7f9cb5062da315cd
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216822"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>如何：定義 SharePoint 專案專案類型
  當您想要建立自訂 SharePoint 專案專案時，請定義專案專案類型。 如需詳細資訊，請參閱 [定義自訂 SharePoint 專案專案類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)。

### <a name="to-define-a-project-item-type"></a>若要定義專案專案類型

1. 建立類別庫 (Class Library) 專案。

2. 加入下列組件的參考：

    - VisualStudio SharePoint

    - System.ComponentModel.Composition

3. 建立實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 介面的類別。

4. 將下列屬性新增至類別：

    - <xref:System.ComponentModel.Composition.ExportAttribute>. 這個屬性可讓 Visual Studio 探索和載入您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 執行。 將型別傳遞 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 至屬性（attribute）的函式。

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. 在專案專案類型定義中，這個屬性會指定新專案專案的字串識別碼。 建議您使用 *公司名稱* 格式。*功能名稱* ，以協助確保所有專案專案都有唯一的名稱。

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. 這個屬性會指定要在 **方案總管** 中為此專案專案顯示的圖示。 這個屬性是選擇性的;如果您未將它套用至您的類別，Visual Studio 會顯示專案專案的預設圖示。 如果設定此屬性，請傳遞內嵌在元件中的圖示或點陣圖的完整名稱。

5. 在方法的執行中 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> ，請使用 *projectItemTypeDefinition* 參數的成員來定義專案專案類型的行為。 這個參數是一個 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> 物件，可讓您存取和介面中定義的事件 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> 。 若要存取專案專案類型的特定實例，請處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 事件，例如 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> 。

## <a name="example"></a>範例
 下列程式碼範例示範如何定義簡單的專案專案類型。 當使用者將此類型的專案專案加入至專案時，這個專案專案類型會將訊息寫入至 [ **輸出** ] 視窗和 [ **錯誤清單** ] 視窗。

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb" id="Snippet2":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs" id="Snippet2":::

 這個範例會使用 SharePoint 專案服務，將訊息寫入 [ **輸出** ] 視窗和 [ **錯誤清單** ] 視窗。 如需詳細資訊，請參閱 [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。

## <a name="compile-the-code"></a>編譯程式碼
 此範例需要下列元件的參考：

- VisualStudio SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>部署專案專案
 若要讓其他開發人員使用您的專案專案，請建立專案範本或專案專案範本。 如需詳細資訊，請參閱 [建立 SharePoint 專案專案的專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。

 若要部署專案專案，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件、範本和您想要使用專案專案散發的任何其他檔案，建立 (VSIX) 封裝的延伸模組。 如需詳細資訊，請參閱 [Visual Studio 中的部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [定義自訂 SharePoint 專案專案類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [建立 SharePoint 專案專案的專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [逐步解說：使用專案範本建立自訂動作專案專案（第1部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [逐步解說：使用專案範本建立網站資料行專案專案（第1部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [如何：將屬性加入至自訂 SharePoint 專案專案類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [如何：將快捷方式功能表項目加入至自訂 SharePoint 專案專案類型](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
