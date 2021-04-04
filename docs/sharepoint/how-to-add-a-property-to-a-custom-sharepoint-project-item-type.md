---
title: 將屬性加入至自訂 SharePoint 專案專案類型
description: 將屬性加入至自訂 SharePoint 專案專案類型。 當您在方案總管中選取專案專案時，屬性會出現在屬性視窗中。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 17d9ac144b97c090292395dd5ae5e85319dd1308
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215509"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>如何：將屬性加入至自訂 SharePoint 專案專案類型
  當您定義自訂 SharePoint 專案專案類型時，您可以將屬性加入至專案專案。 當 **方案總管** 中選取專案專案時，屬性會出現在 [**屬性**] 視窗中。

 下列步驟假設您已經定義自己的 SharePoint 專案專案類型。 如需詳細資訊，請參閱 [如何：定義 SharePoint 專案專案類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。

### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>將屬性加入至專案專案類型的定義

1. 定義具有公用屬性的類別，此屬性代表您要加入至自訂專案專案類型的屬性。 如果您要將多個屬性加入至自訂專案專案類型，您可以在相同類別或不同類別中定義所有屬性。

2. 在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 您的實作為方法中 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> ，處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> *projectItemTypeDefinition* 參數的事件。

3. 在事件的事件處理常式中 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> ，將自訂屬性類別的實例加入至 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> 事件引數參數的集合。

## <a name="example"></a>範例
 下列程式碼範例示範如何將名為 **Example 屬性** 的屬性加入至自訂專案專案類型。

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet11":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet11":::

### <a name="understand-the-code"></a>了解程式碼
 為了確保 `CustomProperties` 每次發生事件時都會使用相同的類別實例 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> ，程式碼範例 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 會在第一次發生此事件時，將屬性物件儲存至專案專案的屬性。 每當此事件再次發生時，程式碼就會抓取此物件。 如需使用 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 屬性以專案專案儲存資料的詳細資訊，請參閱 [將自訂資料與 SharePoint 工具延伸模組建立關聯](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。

 若要保存屬性值的變更， **set** 存取子 `ExampleProperty` 會將新的值儲存至與 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> 屬性相關聯之物件的屬性。 如需使用屬性來保存專案專案資料的詳細資訊 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> ，請參閱 [在 SharePoint 專案系統的延伸中儲存資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。

### <a name="specify-the-behavior-of-custom-properties"></a>指定自訂屬性的行為
 您可以透過將命名空間中的屬性套用至屬性定義，來定義自訂屬性在 [ **屬性** ] 視窗中的顯示和行為 <xref:System.ComponentModel> 。 下列屬性在許多案例中很有用：

- <xref:System.ComponentModel.DisplayNameAttribute>：指定出現在 [ **屬性** ] 視窗中之屬性的名稱。

- <xref:System.ComponentModel.DescriptionAttribute>：指定在選取屬性時，出現在 [ **屬性** ] 視窗底部的描述字串。

- <xref:System.ComponentModel.DefaultValueAttribute>：指定屬性的預設值。

- <xref:System.ComponentModel.TypeConverterAttribute>：指定在 [ **屬性** ] 視窗中顯示的字串與非字串屬性值之間的自訂轉換。

- <xref:System.ComponentModel.EditorAttribute>：指定用來修改屬性的自訂編輯器。

## <a name="compile-the-code"></a>編譯程式碼
 這些程式碼範例需要類別庫專案，其中包含下列元件的參考：

- VisualStudio SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>部署專案專案
 若要讓其他開發人員使用您的專案專案，請建立專案範本或專案專案範本。 如需詳細資訊，請參閱 [建立 SharePoint 專案專案的專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。

 若要部署專案專案，請 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 為元件、範本和您想要使用專案專案散發的任何其他檔案，建立 (VSIX) 封裝的延伸模組。 如需詳細資訊，請參閱 [Visual Studio 中的部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [如何：定義 SharePoint 專案專案類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [如何：將快捷方式功能表項目加入至自訂 SharePoint 專案專案類型](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [定義自訂 SharePoint 專案專案類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)
