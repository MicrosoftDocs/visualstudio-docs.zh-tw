---
title: "如何： 將屬性加入至 SharePoint 專案 |Microsoft 文件"
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
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
ms.assetid: c5eb4900-c35f-490a-b856-bf167da2d293
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e43e4921a32cc84b8384950e88c589b1bbddc31
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>如何：將屬性加入至 SharePoint 專案
  若要將屬性加入至任何 SharePoint 專案，您可以使用專案擴充功能。 屬性會出現在**屬性**視窗中選取專案時**方案總管 中**。  
  
 下列步驟假設您已經建立專案擴充功能。 如需詳細資訊，請參閱[How to： 建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>若要將屬性加入至 SharePoint 專案  
  
1.  以定義類別的公用屬性，代表您要加入至 SharePoint 專案的屬性。 如果您想要新增多個屬性，您可以在相同類別中，或是在不同的類別中定義的所有屬性。  
  
2.  在<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>方法您<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>實作、 控制代碼<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>事件*projectService*參數。  
  
3.  中的事件處理常式<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>事件，加入您的屬性類別的執行個體<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A>事件引數參數的集合。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何將兩個屬性加入至 SharePoint 專案。 一個屬性保存其資料在專案使用者選項檔 (。 檔案副檔名為.csproj.user 或。.vbproj.user 檔案)。 其他屬性會保留其專案檔 （.csproj 或.vbproj） 檔案中的資料。  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understanding-the-code"></a>了解程式碼  
 為了確保相同的執行個體`CustomProjectProperties`類別每次使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>事件發生時，程式碼範例會將屬性的物件加入<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>專案第一個時間就會發生此事件的屬性。 此事件一次發生時，程式碼會擷取此物件。 如需有關使用<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>屬性產生關聯的專案，請參閱[關聯自訂資料與 SharePoint 工具擴充功能](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
 若要保存為屬性的值變更**設定**屬性存取子會使用下列 Api:  
  
-   `CustomUserFileProperty`使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A>屬性，將其值儲存到專案使用者選項檔。  
  
-   `CustomProjectFileProperty`使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>方法，將其值儲存至專案檔。  
  
 如需這些檔案中的保存資料的詳細資訊，請參閱[擴充 SharePoint 專案系統中儲存的資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>指定自訂屬性的行為  
 您可以定義自訂屬性會出現，在行為的方式**屬性**藉由套用屬性 視窗<xref:System.ComponentModel>屬性定義的命名空間。 下列屬性可用於許多案例：  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>： 指定出現在屬性名稱**屬性**視窗。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>： 指定描述字串，會出現在底部**屬性**時選取屬性 視窗。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>： 指定屬性的預設值。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>： 指定之間的字串中所顯示的自訂轉換**屬性**視窗及非字串屬性值。  
  
-   <xref:System.ComponentModel.EditorAttribute>： 指定用來修改屬性的自訂編輯器。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   Microsoft.VisualStudio.Shell.Interop  
  
-   Microsoft.VisualStudio.Shell.Interop.8.0  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>部署擴充功能  
 若要部署延伸模組，建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要發佈副檔名的檔案。 如需詳細資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 SharePoint 專案](../sharepoint/extending-sharepoint-projects.md)   
 [如何： 建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [如何： 將捷徑功能表項目加入至 SharePoint 專案](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  