---
title: 將資料儲存在 SharePoint 專案系統的延伸模組中 |Microsoft Docs
titleSuffix: ''
description: 瞭解如何在關閉包含擴充功能的 SharePoint 專案之後，儲存保留的字串資料。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 87e05ba763095a818cc5db6f92828e6259d30e73
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217433"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>將資料儲存在 SharePoint 專案系統的延伸模組中
  當您延伸 SharePoint 專案系統時，可以儲存在 SharePoint 專案關閉之後仍會保存的字串資料。 資料通常與特定專案專案或專案本身相關聯。

 如果您有不需要保存的資料，您可以將資料新增至 SharePoint 工具物件模型中的任何物件，以執行 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> 介面。 如需詳細資訊，請參閱 [將自訂資料與 SharePoint 工具延伸](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)模組產生關聯。

## <a name="save-data-that-is-associated-with-a-project-item"></a>儲存與專案專案相關聯的資料
 當您有與特定 SharePoint 專案專案相關聯的資料時（例如加入至專案專案的屬性值），您可以將資料儲存至專案專案的 *.spdata 檔案。* 若要這樣做，請使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 物件的屬性 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> 。 您加入至這個屬性的資料會儲存在專案專案的 *.spdata* 檔案中的 **ExtensionData** 元素。 如需詳細資訊，請參閱 [ExtensionData 元素](../sharepoint/extensiondata-element.md)。

 下列程式碼範例示範如何使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 屬性來儲存自訂 SharePoint 專案專案類型中所定義之字串屬性的值。 若要在較大範例的內容中查看這個範例，請參閱 [如何：將屬性加入至自訂 SharePoint 專案專案類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)。

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet14":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet14":::

## <a name="save-data-that-is-associated-with-a-project"></a>儲存與專案相關聯的資料
 當您擁有專案層級的資料（例如，加入至 SharePoint 專案的屬性值）時，您可以 (*.csproj* 檔案或 *vbproj* 檔案，將資料儲存至專案檔，) 或 (*.csproj. 使用者* 檔案或 *. vbproj* 的專案使用者選項檔) 。 您選擇用來儲存資料的檔案，取決於您想要使用資料的方式：

- 如果您想要讓所有開啟 SharePoint 專案的開發人員都能使用資料，請將資料儲存至專案檔。 這個檔案一律會簽入原始檔控制資料庫中，因此可供簽出項目的其他開發人員使用此檔案中的資料。

- 如果您想要讓資料僅適用于目前在 Visual Studio 中開啟 SharePoint 專案的開發人員，請將資料儲存至 project 使用者選項檔。 這個檔案通常不會簽入原始檔控制資料庫中，因此簽出項目的其他開發人員無法使用這個檔案中的資料。

### <a name="save-data-to-the-project-file"></a>將資料儲存至專案檔
 若要將資料儲存至專案檔，請將 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 物件轉換為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 物件，然後使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> 方法。 下列程式碼範例將示範如何使用這個方法，將專案屬性的值儲存至專案檔。 若要在較大範例的內容中查看這個範例，請參閱 [如何：將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb" id="Snippet3":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs" id="Snippet3":::

 如需 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 在 Visual Studio automation 物件模型或整合物件模型中將物件轉換成其他類型的詳細資訊，請參閱在 [SharePoint 專案系統類型與其他 Visual Studio 專案類型之間轉換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)。

### <a name="save-data-to-the-project-user-option-file"></a>將資料儲存至 project 使用者選項檔
 若要將資料儲存至 project 使用者選項檔，請使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> 物件的屬性 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 。 下列程式碼範例將示範如何使用這個屬性，將專案屬性的值儲存至專案使用者選項檔。 若要在較大範例的內容中查看這個範例，請參閱 [如何：將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb" id="Snippet2":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs" id="Snippet2":::

## <a name="see-also"></a>另請參閱
- [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)
- [將自訂資料與 SharePoint 工具延伸模組產生關聯](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [在 SharePoint 專案系統類型與其他 Visual Studio 專案類型之間轉換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
