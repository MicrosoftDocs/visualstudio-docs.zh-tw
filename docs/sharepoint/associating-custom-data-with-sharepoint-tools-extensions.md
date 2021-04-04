---
title: 將自訂資料與 SharePoint 工具延伸模組產生關聯 |Microsoft Docs
description: 將自訂資料與 SharePoint 工具延伸模組產生關聯。 查看可包含自訂資料的物件清單。 新增和取出自訂資料。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5665fc28bacb76c6887cb7dcb1820ec9dc0d2b3a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215314"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>將自訂資料與 SharePoint 工具延伸模組產生關聯
  您可以將自訂資料新增至 SharePoint 工具延伸模組中的特定物件。 當您的延伸模組中有您想要稍後從擴充功能的其他程式碼存取的資料時，這非常有用。 您可以將資料與延伸模組中的物件建立關聯，然後再從相同的物件取得資料，而不是執行自訂方式來儲存及存取資料。

 當您想要保留與 Visual Studio 中特定專案相關的資料時，將自訂資料新增至物件也很有用。 SharePoint 工具擴充功能只會在 Visual Studio 載入一次，因此您的延伸模組可能會在任何時間 (例如專案、專案專案或 **伺服器總管**) 節點等數個不同的專案中使用。 如果您有僅與特定專案相關的自訂資料，您可以將資料加入代表該專案的物件。

 當您將自訂資料新增至 SharePoint 工具延伸模組中的物件時，資料不會保存。 只有在物件的存留期內，資料才可供使用。 當垃圾收集回收物件之後，資料就會遺失。

 在 SharePoint 專案系統的延伸模組中，您也可以儲存在卸載延伸之後仍會保存的字串資料。 如需詳細資訊，請參閱 [在 SharePoint 專案系統的延伸中儲存資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。

## <a name="objects-that-can-contain-custom-data"></a>可以包含自訂資料的物件
 您可以將自訂資料新增至 SharePoint 工具物件模型中的任何物件，以執行 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> 介面。 這個介面只會定義一個屬性， <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 也就是自訂資料物件的集合。 下列類型會執行 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> ：

- <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>

- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>

- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>

## <a name="add-and-retrieve-custom-data"></a>新增和取出自訂資料
 若要將自訂資料新增至 SharePoint 工具擴充功能中的物件，請取得 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 您想要加入資料之物件的屬性，然後使用 <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> 方法將資料加入至物件。

 若要從 SharePoint 工具擴充功能中的物件取出自訂資料，請取得 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 物件的屬性，然後使用下列其中一種方法：

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. 如果資料物件存在，這個方法會傳回 **true** ，如果不存在則傳回 **false** 。 您可以使用這個方法來取出實值型別或參考型別的實例。

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. 如果資料物件結束，這個方法會傳回資料物件，如果不存在，則傳回 **null** 。 您只能使用這個方法來取出參考型別的實例。

  下列程式碼範例會判斷特定資料物件是否已與專案專案相關聯。 如果資料物件尚未與專案專案相關聯，則程式碼會將物件加入至專案專案的 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 屬性。 若要在較大範例的內容中查看這個範例，請參閱 [如何：將屬性加入至自訂 SharePoint 專案專案類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)。

  :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet13":::
  :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet13":::

## <a name="see-also"></a>另請參閱
- [SharePoint 工具擴充功能的程式設計概念和功能](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [逐步解說：使用專案範本建立自訂動作專案專案（第1部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [逐步解說：擴充伺服器總管以顯示 web 元件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [如何：將屬性加入至 SharePoint 專案](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [如何：將屬性加入至自訂 SharePoint 專案專案類型](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
