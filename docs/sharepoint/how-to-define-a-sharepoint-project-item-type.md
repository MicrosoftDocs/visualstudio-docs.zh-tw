---
title: HOW TO：定義 SharePoint 專案項目類型 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 839cec7ea9ab119e029e9944e3b97afe9bb9d6bd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916727"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>HOW TO：定義 SharePoint 專案項目類型
  當您想要建立自訂的 SharePoint 專案項目時，請定義專案項目類型。 如需詳細資訊，請參閱 <<c0> [ 定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)。  
  
### <a name="to-define-a-project-item-type"></a>若要定義專案項目類型  
  
1.  建立類別庫 (Class Library) 專案。  
  
2.  加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  建立實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 介面的類別。  
  
4.  將下列屬性新增至類別：  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. 這個屬性可讓 Visual Studio 來探索及載入您<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>實作。 傳遞<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>屬性建構函式的型別。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. 在專案項目類型定義中，這個屬性會指定字串識別項，為新的專案項目。 我們建議您使用的格式*公司名稱*。*功能名稱*可協助您確認所有專案項目都具有唯一的名稱。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. 這個屬性會指定要在這個專案項目的顯示的圖示**方案總管 中**。 這個屬性是選擇性的;如果您不會套用它到您的類別，Visual Studio 會顯示預設圖示為您的專案項目。 如果您設定此屬性，傳遞圖示或點陣圖，內嵌在您的組件的完整的名稱。  
  
5.  在您實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>方法，使用成員*projectItemTypeDefinition*參數來定義專案項目類型的行為。 這個參數是<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>可用來存取事件中所定義的物件<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>介面。 若要存取您的專案項目類型的特定執行個體，處理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>事件，例如<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何定義簡單的專案項目類型。 這個專案項目類型將訊息寫入**輸出**視窗和**錯誤清單**時使用者會將此類型的專案項目加入至專案 視窗。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]  
  
 此範例會使用 SharePoint 專案服務來將訊息寫入**輸出**視窗和**錯誤清單**視窗。 如需詳細資訊，請參閱 <<c0> [ 使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)。  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-project-item"></a>部署專案項目  
 若要讓其他開發人員使用您的專案項目，建立專案範本或專案項目範本。 如需詳細資訊，請參閱 <<c0> [ 建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 若要部署的專案項目，建立[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件、 範本和任何其他您想要與專案項目一起散發的檔案。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的 SharePoint 部署擴充功能工具](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱
 [定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [逐步解說：使用項目範本，第 1 部分中建立自訂動作專案項目](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [逐步解說：使用專案範本，第 1 部分建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [如何：將屬性加入至自訂的 SharePoint 專案項目類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [如何：將捷徑功能表項目新增至自訂的 SharePoint 專案項目類型](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
