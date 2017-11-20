---
title: "將資料儲存在 SharePoint 專案系統擴充功能的 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
ms.assetid: 903b9da7-2eea-404c-9a7a-7bc15cb90d6c
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3605558fd1fd9263c5dad7ec7bc295b7f095a185
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="saving-data-in-extensions-of-the-sharepoint-project-system"></a>儲存 SharePoint 專案系統擴充功能的資料
  當您擴充 SharePoint 專案系統時，您可以儲存 SharePoint 專案關閉後持續發生的字串資料。 通常與特定的專案項目或專案本身相關聯的資料。  
  
 如果您有不需要保存的資料，您可以將資料加入至實作 SharePoint 工具物件模型中的任何物件<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>介面。 如需詳細資訊，請參閱[關聯自訂資料與 SharePoint 工具擴充功能](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
## <a name="saving-data-that-is-associated-with-a-project-item"></a>儲存資料相關聯專案項目  
 當擁有特定 SharePoint 專案項目，例如您加入專案項目之屬性的值相關聯的資料時您可以將資料儲存.spdata 檔案的專案項目。 若要這樣做，請使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>屬性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>物件。 您將加入至這個屬性的資料會儲存在**ExtensionData** .spdata 檔案的專案項目中的項目。 如需詳細資訊，請參閱[ExtensionData 項目](../sharepoint/extensiondata-element.md)。  
  
 下列程式碼範例示範如何使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>屬性來儲存自訂 SharePoint 專案項目類型中定義為字串屬性的值。 若要查看這個內容中的較大範例的範例，請參閱[How to： 將屬性加入至自訂 SharePoint 專案項目類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]  
  
## <a name="saving-data-that-is-associated-with-a-project"></a>儲存資料相關聯的專案  
 當您需要專案層級的資料，例如，您將加入至 SharePoint 專案屬性的值可以將資料儲存至專案檔 （.csproj 或.vbproj） 檔案或專案使用者選項檔 (。 檔案副檔名為.csproj.user 或。.vbproj.user 檔案)。 您選擇儲存中的資料檔案取決於您想要使用的資料的方式：  
  
-   如果您想要用來開啟 SharePoint 專案的所有人員資料，請將資料儲存至專案檔。 這個檔案會一律簽入原始檔控制資料庫，因此這個檔案中的資料是使用其他開發人員簽出專案。  
  
-   如果您想要只提供給目前已開啟 Visual Studio 中的 SharePoint 專案的人員的資料，請將資料儲存至專案使用者選項檔。 這個檔案是未通常簽入原始檔控制資料庫，因此這個檔案中的資料就無法使用其他開發人員簽出專案。  
  
### <a name="saving-data-to-the-project-file"></a>將資料儲存至專案檔  
 若要將資料儲存至專案檔，將轉換<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>物件，，然後使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>方法。 下列程式碼範例示範如何使用這個方法來儲存專案檔案的專案屬性的值。 若要查看這個內容中的較大範例的範例，請參閱[How to： 將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。  
  
 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]  
  
 如需有關轉換<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>物件為其他型別在 Visual Studio 自動化物件模型或整合物件模型，請參閱[轉換之間 SharePoint 專案系統類型與其他 Visual Studio 專案類型](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### <a name="saving-data-to-the-project-user-option-file"></a>將資料儲存至專案使用者選項檔  
 若要將資料儲存至專案使用者選項檔，使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A>屬性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>物件。 下列程式碼範例示範如何使用這個屬性來儲存專案使用者選項檔的專案屬性的值。 若要查看這個內容中的較大範例的範例，請參閱[How to： 將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。  
  
 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]  
  
## <a name="see-also"></a>另請參閱  
 [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)   
 [關聯自訂資料與 SharePoint 工具擴充功能](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [在 SharePoint 專案系統類型與其他 Visual Studio 專案類型之間轉換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  