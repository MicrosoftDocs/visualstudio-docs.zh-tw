---
title: 如何：將屬性加入至 SharePoint 專案 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: eb72b0546b504e2df1a7e93ea9d4def350143d1d
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015915"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>如何：將屬性加入至 SharePoint 專案
  您可以使用專案延伸模組，將屬性加入至任何 SharePoint 專案。 當**方案總管**中選取專案時，屬性就會出現在 [**屬性**] 視窗中。

 下列步驟假設您已建立專案延伸模組。 如需詳細資訊，請參閱[如何：建立 SharePoint 專案延伸](../sharepoint/how-to-create-a-sharepoint-project-extension.md)模組。

### <a name="to-add-a-property-to-a-sharepoint-project"></a>若要將屬性加入至 SharePoint 專案

1. 定義具有公用屬性的類別，以代表您要加入至 SharePoint 專案的屬性。 如果您想要加入多個屬性，您可以在相同類別或不同類別中定義所有屬性。

2. 在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 您的執行方法中 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> ，處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> *projectService*參數的事件。

3. 在事件的事件處理常式中 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> ，將屬性類別的實例新增至 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> 事件引數參數的集合。

## <a name="example"></a>範例
 下列程式碼範例示範如何將兩個屬性新增至 SharePoint 專案。 其中一個屬性會將其資料保存在專案使用者選項檔案中（ *.csproj. user*檔案或 *. vbproj. user*檔案）。 另一個屬性會將其資料保存在專案檔（*.csproj*檔案或 *. vbproj*檔案）中。

 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]

### <a name="understand-the-code"></a>了解程式碼
 為確保 `CustomProjectProperties` 每次發生事件時都使用相同的類別實例 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> ，程式碼範例 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 會在第一次發生此事件時，將 properties 物件加入至專案的屬性。 每當這個事件再次發生時，程式碼就會抓取這個物件。 如需使用 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 屬性將資料與專案產生關聯的詳細資訊，請參閱[將自訂資料與 SharePoint 工具擴充](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)功能產生關聯。

 若要保存屬性值的變更，屬性的**set**存取子會使用下列 api：

- `CustomUserFileProperty`使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> 屬性，將其值儲存至專案使用者選項檔案。

- `CustomProjectFileProperty`會使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> 方法，將其值儲存至專案檔。

  如需保存這些檔案中之資料的詳細資訊，請參閱在[SharePoint 專案系統的延伸模組中儲存資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。

### <a name="specify-the-behavior-of-custom-properties"></a>指定自訂屬性的行為
 您可以藉由將命名空間中的屬性套用至屬性定義，定義自訂屬性在 [**屬性**] 視窗中的顯示方式和行為 <xref:System.ComponentModel> 。 下列屬性在許多情況下很有用：

- <xref:System.ComponentModel.DisplayNameAttribute>：指定出現在 [**屬性**] 視窗中的屬性名稱。

- <xref:System.ComponentModel.DescriptionAttribute>：指定當選取屬性時，出現在 [**屬性**] 視窗底部的描述字串。

- <xref:System.ComponentModel.DefaultValueAttribute>：指定屬性的預設值。

- <xref:System.ComponentModel.TypeConverterAttribute>：指定在 [**屬性**] 視窗中顯示的字串與非字串屬性值之間的自訂轉換。

- <xref:System.ComponentModel.EditorAttribute>：指定要用來修改屬性的自訂編輯器。

## <a name="compile-the-code"></a>編譯程式碼
 這個範例需要參考下列元件：

- VisualStudio. SharePoint

- VisualStudio Shell

- VisualStudio。

- VisualStudio. Shell. Interop 8。0

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>部署延伸模組
 若要部署擴充功能，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件建立擴充功能（VSIX）封裝，以及您想要與延伸模組一起散發的任何其他檔案。 如需詳細資訊，請參閱[在 Visual Studio 中部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 專案](../sharepoint/extending-sharepoint-projects.md)
- [如何：建立 SharePoint 專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [如何：將快捷方式功能表項目加入至 SharePoint 專案](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)
