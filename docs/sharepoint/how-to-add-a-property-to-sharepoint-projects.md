---
title: HOW TO：將屬性加入至 SharePoint 專案 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 51f4aeef55d20a728567b50e67c2232a0a77b1e6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646053"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>HOW TO：將屬性加入至 SharePoint 專案
  若要將屬性加入至任何 SharePoint 專案，您可以使用專案擴充功能。 屬性會出現在**屬性**視窗中選取專案時**方案總管 中**。

 下列步驟假設您已建立的專案擴充功能。 如需詳細資訊，請參閱[如何：建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。

### <a name="to-add-a-property-to-a-sharepoint-project"></a>若要將屬性加入至 SharePoint 專案

1.  定義具有公用的屬性，表示您要新增至 SharePoint 專案的屬性的類別。 如果您想要新增多個屬性，您可以在相同類別中，或在不同的類別中定義的所有屬性。

2.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>方法您<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>實作、 控制代碼<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>事件*projectService*參數。

3.  中的事件處理常式<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>事件，將您的內容類別的執行個體<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A>事件引數參數的集合。

## <a name="example"></a>範例
 下列程式碼範例示範如何將兩個屬性新增至 SharePoint 專案。 一個屬性其資料保存在專案使用者選項檔 ( *.csproj.user*檔案或 *.vbproj.user*檔案)。 另一個屬性其資料保存在專案檔 (*.csproj*檔案或 *.vbproj*檔案)。

 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]

### <a name="understand-the-code"></a>了解程式碼
 若要確保相同的執行個體的`CustomProjectProperties`類別每次使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>事件發生時，程式碼範例將屬性的物件加入<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>專案第一個時間就會發生此事件的屬性。 此事件一次發生時，程式碼會擷取此物件。 如需使用詳細資訊<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>屬性，以將資料產生關聯的專案，請參閱[相關聯的自訂資料與 SharePoint 工具擴充功能](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。

 若要保存屬性值，來變更**設定**屬性存取子會使用下列 Api:

- `CustomUserFileProperty` 使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A>屬性，以將其值儲存到專案使用者選項檔。

- `CustomProjectFileProperty` 使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>方法，將其值儲存至專案檔。

  如需這些檔案中保存資料的詳細資訊，請參閱[將資料儲存於 SharePoint 專案系統擴充](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。

### <a name="specify-the-behavior-of-custom-properties"></a>指定自訂屬性的行為
 您可以定義自訂屬性如何顯示和行為**屬性**藉由套用屬性 視窗<xref:System.ComponentModel>屬性定義的命名空間。 下列屬性可用於許多案例：

-   <xref:System.ComponentModel.DisplayNameAttribute>：指定出現在屬性名稱**屬性**視窗。

-   <xref:System.ComponentModel.DescriptionAttribute>：指定描述字串出現在底部**屬性**時選取屬性 視窗。

-   <xref:System.ComponentModel.DefaultValueAttribute>：指定屬性的預設值。

-   <xref:System.ComponentModel.TypeConverterAttribute>：指定會顯示在字串之間的自訂轉換**屬性**視窗而非字串屬性值。

-   <xref:System.ComponentModel.EditorAttribute>：指定自訂編輯器，以便用來修改屬性。

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要參考下列組件：

-   Microsoft.VisualStudio.SharePoint
-
-   Microsoft.VisualStudio.Shell
-
-   Microsoft.VisualStudio.Shell.Interop
-
-   Microsoft.VisualStudio.Shell.Interop.8.0
-
-   System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>部署擴充功能
 若要部署的延伸模組，建立[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要將副檔名的檔案。 如需詳細資訊，請參閱 <<c0> [ 部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 專案](../sharepoint/extending-sharepoint-projects.md)
- [如何：建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [如何：加入 SharePoint 專案的捷徑功能表項目](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)
