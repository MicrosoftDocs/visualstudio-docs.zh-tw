---
title: "如何： 定義 SharePoint 專案項目類型 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: 18b56e7c-4efb-47a2-abfc-e9018ae38267
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2c5f39fea52b6f417b046a7ff1f72dff1190a038
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>如何：定義 SharePoint 專案項目類型
  當您想要建立自訂 SharePoint 專案項目時，請定義專案項目類型。 如需詳細資訊，請參閱[定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)。  
  
### <a name="to-define-a-project-item-type"></a>若要定義的專案項目類型  
  
1.  建立類別庫 (Class Library) 專案。  
  
2.  加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  建立實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 介面的類別。  
  
4.  類別中加入下列屬性：  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. 這個屬性可讓 Visual Studio 來探索和載入您<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>實作。 傳遞<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>屬性建構函式的類型。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. 在專案項目類型定義中，這個屬性會指定新的專案項目的字串識別碼。 我們建議您使用格式*公司名稱*。*功能名稱*，協助確保所有專案項目都具有唯一的名稱。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. 這個屬性會指定要針對這個專案項目中顯示的圖示**方案總管 中**。 這個屬性是選擇性的;如果您不會套用它加入至類別，Visual Studio 會顯示預設圖示為您的專案項目。 如果您設定此屬性，傳遞圖示或點陣圖內嵌於組件的完整的名稱。  
  
5.  在您實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>方法，使用成員*projectItemTypeDefinition*參數定義的專案項目類型的行為。 這個參數是<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>物件，提供存取權中定義的事件<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>介面。 若要存取您的專案項目類型的特定執行個體，處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>事件，例如<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何定義簡單的專案項目類型。 這個專案項目類型會將訊息寫入**輸出**視窗和**錯誤清單**視窗時，使用者將此類型的專案項目加入專案。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]  
  
 此範例會使用 SharePoint 專案服務寫入至訊息**輸出**視窗和**錯誤清單**視窗。 如需詳細資訊，請參閱[使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>部署專案項目  
 若要啟用其他開發人員使用您的專案項目，請建立範本的專案或專案項目範本。 如需詳細資訊，請參閱[建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 若要部署專案項目，建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件、 範本和您想要與專案項目一起散發的任何其他檔案。 如需詳細資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [建立項目範本和專案範本的 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [逐步解說： 建立自訂動作專案項目與項目範本，第 1 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [逐步解說： 建立網站欄專案項目以專案範本，第 1 部分](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [如何： 將屬性加入至自訂 SharePoint 專案項目類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [如何：將捷徑功能表項目新增至自訂 SharePoint 專案項目類型](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
  
  