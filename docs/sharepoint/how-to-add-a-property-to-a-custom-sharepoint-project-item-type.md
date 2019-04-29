---
title: HOW TO：將屬性加入至自訂 SharePoint 專案項目類型 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e9695755967aa1b66aa7cda2d784ae88b0fc1b42
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967288"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>HOW TO：將屬性加入至自訂的 SharePoint 專案項目類型
  當您定義自訂的 SharePoint 專案項目類型時，則可以將屬性加入專案項目。 屬性會出現在**屬性**視窗中選取的專案項目時**方案總管 中**。

 下列步驟假設您已經定義自己的 SharePoint 專案項目類型。 如需詳細資訊，請參閱[如何：定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。

### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>若要將屬性加入至專案項目類型定義

1. 定義具有公用的屬性，表示您要新增至自訂專案項目類型的屬性的類別。 如果您想要將多個屬性新增至自訂專案項目類型，您可以在相同類別中，或在不同的類別中定義的所有屬性。

2. 在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>方法您<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>實作、 控制代碼<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>事件*projectItemTypeDefinition*參數。

3. 中的事件處理常式<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>事件，將您的自訂屬性類別的執行個體<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A>事件引數參數的集合。

## <a name="example"></a>範例
 下列程式碼範例示範如何加入名為**屬性範例**給自訂專案項目類型。

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]

### <a name="understand-the-code"></a>了解程式碼
 若要確保相同的執行個體`CustomProperties`類別每次使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>事件發生時，程式碼範例會將儲存的屬性物件<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>屬性就會發生此事件的專案項目的第一個時間。 此事件一次發生時，程式碼會擷取此物件。 如需使用詳細資訊<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>屬性，以將資料儲存與專案項目，請參閱[相關聯的自訂資料與 SharePoint 工具擴充功能](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。

 若要保存為屬性值的變更**設定**存取子`ExampleProperty`儲存新的值，以<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>屬性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>屬性相關聯的物件。 如需使用詳細資訊<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>屬性，以保存資料與專案項目，請參閱[將資料儲存於 SharePoint 專案系統擴充](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。

### <a name="specify-the-behavior-of-custom-properties"></a>指定自訂屬性的行為
 您可以定義自訂屬性如何顯示和行為**屬性**藉由套用屬性 視窗<xref:System.ComponentModel>屬性定義的命名空間。 下列屬性可用於許多案例：

- <xref:System.ComponentModel.DisplayNameAttribute>：指定出現在屬性名稱**屬性**視窗。

- <xref:System.ComponentModel.DescriptionAttribute>：指定描述字串出現在底部**屬性**時選取屬性 視窗。

- <xref:System.ComponentModel.DefaultValueAttribute>：指定屬性的預設值。

- <xref:System.ComponentModel.TypeConverterAttribute>：指定會顯示在字串之間的自訂轉換**屬性**視窗而非字串屬性值。

- <xref:System.ComponentModel.EditorAttribute>：指定自訂編輯器，以便用來修改屬性。

## <a name="compile-the-code"></a>編譯程式碼
 這些程式碼範例需要參考下列組件的類別庫專案：

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>部署專案項目
 若要讓其他開發人員使用您的專案項目，建立專案範本或專案項目範本。 如需詳細資訊，請參閱 <<c0> [ 建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。

 若要部署的專案項目，建立[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件、 範本和任何其他您想要與專案項目一起散發的檔案。 如需詳細資訊，請參閱 <<c0> [ 部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱
- [如何：定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [如何：將捷徑功能表項目新增至自訂的 SharePoint 專案項目類型](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)
