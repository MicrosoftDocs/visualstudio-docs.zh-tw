---
title: 如何：將屬性加入至 SharePoint 專案專案延伸模組 |Microsoft Docs
titleSuffix: ''
description: 使用 SharePoint 專案專案延伸模組，將屬性加入至 Visual Studio 中已安裝的任何 SharePoint 專案專案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3d721c8d4f381e99a814852839de0e808d326b3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889638"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>如何：將屬性加入至 SharePoint 專案專案延伸模組
  您可以使用專案專案延伸，將屬性加入至 Visual Studio 中已安裝的任何 SharePoint 專案專案。 當 **方案總管** 中選取專案專案時，屬性會出現在 [**屬性**] 視窗中。

 下列步驟假設您已建立專案專案延伸模組。 如需詳細資訊，請參閱 [如何：建立 SharePoint 專案專案延伸](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)模組。

### <a name="to-add-a-property-to-a-project-item-extension"></a>將屬性加入至專案專案延伸模組

1. 定義具有公用屬性的類別，此屬性代表您要加入專案專案類型的屬性。 如果您要將多個屬性加入至專案專案類型，您可以在相同類別或不同類別中定義所有屬性。

2. 在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 您的實作為方法中 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> ，處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> *projectItemType* 參數的事件。

3. 在事件的事件處理常式中 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> ，將屬性類別的實例加入至 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> 事件引數參數的集合。

## <a name="example"></a>範例
 下列程式碼範例示範如何將名為 **Example 屬性** 的屬性加入至事件接收器專案專案。

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]

### <a name="understand-the-code"></a>了解程式碼
 為了確保 `CustomProperties` 每次發生事件時都會使用相同的類別實例 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> ，程式碼範例 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 會在第一次發生此事件時，將屬性物件加入至專案專案的屬性。 每當此事件再次發生時，程式碼就會抓取此物件。 如需使用 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 屬性將資料與專案專案產生關聯的詳細資訊，請參閱 [將自訂資料與 SharePoint 工具延伸](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)模組產生關聯。

 若要保存屬性值的變更， **set** 存取子 `ExampleProperty` 會將新的值儲存至與 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> 屬性相關聯之物件的屬性。 如需使用屬性來保存專案專案資料的詳細資訊 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> ，請參閱 [在 SharePoint 專案系統的延伸中儲存資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。

### <a name="specify-the-behavior-of-custom-properties"></a>指定自訂屬性的行為
 您可以透過將命名空間中的屬性套用至屬性定義，來定義自訂屬性在 [ **屬性** ] 視窗中的顯示和行為 <xref:System.ComponentModel> 。 下列屬性在許多案例中很有用：

- <xref:System.ComponentModel.DisplayNameAttribute>：指定出現在 [ **屬性** ] 視窗中之屬性的名稱。

- <xref:System.ComponentModel.DescriptionAttribute>：指定在選取屬性時，出現在 [ **屬性** ] 視窗底部的描述字串。

- <xref:System.ComponentModel.DefaultValueAttribute>：指定屬性的預設值。

- <xref:System.ComponentModel.TypeConverterAttribute>：指定在 [ **屬性** ] 視窗中顯示的字串與非字串屬性值之間的自訂轉換。

- <xref:System.ComponentModel.EditorAttribute>：指定用來修改屬性的自訂編輯器。

## <a name="compile-the-code"></a>編譯程式碼
 這些範例需要類別庫專案，其中包含下列元件的參考：

- VisualStudio SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>部署延伸模組
 若要部署擴充功能，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件和您想要使用擴充功能散發的任何其他檔案，建立 (VSIX) 封裝的延伸模組。 如需詳細資訊，請參閱 [Visual Studio 中的部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [如何：建立 SharePoint 專案專案延伸模組](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [如何：將快捷方式功能表項目加入至 SharePoint 專案專案延伸模組](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [擴充 SharePoint 專案專案](../sharepoint/extending-sharepoint-project-items.md)
- [逐步解說：擴充 SharePoint 專案專案類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
