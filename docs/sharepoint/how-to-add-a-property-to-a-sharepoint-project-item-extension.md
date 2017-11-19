---
title: "如何： 將屬性加入 SharePoint 專案項目擴充功能 |Microsoft 文件"
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
ms.assetid: 4fd97ef2-86e7-4d92-8e34-5b0ec3cc43a0
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 51b75626a76778c5f00ed9408950f999133209dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>如何：將屬性加入至 SharePoint 專案項目擴充功能
  您可以使用專案項目擴充功能，將屬性加入至任何已安裝 Visual Studio 中的 SharePoint 專案項目。 屬性會出現在**屬性**視窗中選取專案項目時**方案總管 中**。  
  
 下列步驟假設您已經建立專案項目擴充功能。 如需詳細資訊，請參閱[How to： 建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
### <a name="to-add-a-property-to-a-project-item-extension"></a>若要將屬性加入至專案項目擴充功能  
  
1.  以定義類別的公用屬性，代表您要加入至專案項目類型的屬性。 如果您想要將多個屬性加入至專案項目類型，您可以在相同類別中，或是在不同的類別中定義的所有屬性。  
  
2.  在<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>方法您<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>實作、 控制代碼<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>事件*projectItemType*參數。  
  
3.  中的事件處理常式<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>事件，加入您的屬性類別的執行個體<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A>事件引數參數的集合。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何加入屬性，名為**範例屬性**至事件接收器專案項目。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]  
  
### <a name="understanding-the-code"></a>了解程式碼  
 為了確保相同的執行個體`CustomProperties`類別每次使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>事件發生時，程式碼範例會將屬性的物件加入<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>屬性就會發生此事件的專案項目的第一個時間。 此事件一次發生時，程式碼會擷取此物件。 如需有關使用<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>屬性資料與專案項目，請參閱[關聯自訂資料與 SharePoint 工具擴充功能](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
 若要保存為屬性的值，變更**設定**存取子`ExampleProperty`儲存新的值以<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>屬性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>屬性相關聯的物件。 如需有關使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>屬性來保存資料與專案項目，請參閱[擴充 SharePoint 專案系統中儲存的資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>指定自訂屬性的行為  
 您可以定義自訂屬性會出現，在行為的方式**屬性**藉由套用屬性 視窗<xref:System.ComponentModel>屬性定義的命名空間。 下列屬性可用於許多案例：  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>： 指定出現在屬性名稱**屬性**視窗。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>： 指定描述字串，會出現在底部**屬性**時選取屬性 視窗。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>： 指定屬性的預設值。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>： 指定之間的字串中所顯示的自訂轉換**屬性**視窗及非字串屬性值。  
  
-   <xref:System.ComponentModel.EditorAttribute>： 指定用來修改屬性的自訂編輯器。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這些範例需要參考下列組件的類別庫專案：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>部署擴充功能  
 若要部署延伸模組，建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要發佈副檔名的檔案。 如需詳細資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [如何： 將捷徑功能表項目加入至 SharePoint 專案項目擴充功能](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)   
 [逐步解說：擴充 SharePoint 專案項目類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  