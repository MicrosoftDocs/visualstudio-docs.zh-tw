---
title: 將資料儲存於 SharePoint 專案系統擴充 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eba3f66e55c06efad2a540b1be7d3ad66ddfa3d0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599671"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>將資料儲存在 SharePoint 專案系統的擴充功能
  當您擴充 SharePoint 專案系統時，您可以儲存 SharePoint 專案已關閉之後依然存在的字串資料。 通常與特定專案項目或專案本身相關聯的資料。

 如果您有不需要保存的資料，您可以將資料新增至實作 SharePoint 工具物件模型中的任何物件<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>介面。 如需詳細資訊，請參閱 <<c0> [ 相關聯的自訂資料與 SharePoint 工具擴充功能](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。

## <a name="save-data-that-is-associated-with-a-project-item"></a>儲存專案項目相關聯的資料
 當您有特定 SharePoint 專案項目，例如您加入專案項目之屬性的值相關聯的資料可以儲存的資料 *.spdata*專案項目的檔案。 若要這樣做，請使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>屬性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>物件。 您將加入至這個屬性的資料會儲存在**ExtensionData**中的項目 *.spdata*專案項目的檔案。 如需詳細資訊，請參閱 < [ExtensionData 項目](../sharepoint/extensiondata-element.md)。

 下列程式碼範例示範如何使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>屬性，以儲存自訂的 SharePoint 專案項目類型中定義為字串屬性的值。 若要查看這個內容中的較大範例的範例，請參閱[How to:將屬性加入至自訂的 SharePoint 專案項目類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)。

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]

## <a name="save-data-that-is-associated-with-a-project"></a>儲存與專案相關聯的資料
 當您需要專案層級的資料，例如您新增至 SharePoint 專案的屬性值可以將資料儲存至專案檔 ( *.csproj*檔案或 *.vbproj*檔案) 或專案的 [使用者] 選項檔案 ( *.csproj.user*檔案或 *.vbproj.user*檔案)。 您選擇要儲存資料的檔案取決於您想要使用的資料的方式：

-   如果您想要所有的開發人員開啟 SharePoint 專案可用的資料，請將資料儲存到專案檔。 此檔案會一律簽入原始檔控制資料庫，讓此檔案中的資料可供其他開發人員簽出專案。

-   如果您想要只提供給目前的開發人員在 Visual Studio 中開啟 SharePoint 專案的資料，請將資料儲存到專案使用者選項檔。 這個檔案是未通常簽入原始檔控制資料庫，因此這個檔案中的資料就無法使用其他開發人員簽出專案。

### <a name="save-data-to-the-project-file"></a>將資料儲存到專案檔
 若要將資料儲存到專案檔中，將轉換<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>物件至<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>物件，並接著使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>方法。 下列程式碼範例示範如何使用這個方法來儲存專案檔案的專案屬性的值。 若要查看這個內容中的較大範例的範例，請參閱[How to:將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。

 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]

 如需轉換的詳細資訊<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>物件，為其他型別中的 Visual Studio 自動化物件模型或整合物件模型，請參閱[SharePoint 專案系統類型與其他 Visual Studio 專案類型之間轉換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

### <a name="save-data-to-the-project-user-option-file"></a>將資料儲存到專案使用者選項檔
 若要將資料儲存到專案使用者選項檔中，使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A>屬性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>物件。 下列程式碼範例示範如何使用這個屬性來儲存專案使用者選項檔的專案屬性的值。 若要查看這個內容中的較大範例的範例，請參閱[How to:將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。

 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)
- [將自訂的資料產生關聯的 SharePoint 工具擴充功能](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [SharePoint 專案系統類型與其他 Visual Studio 專案類型之間轉換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
