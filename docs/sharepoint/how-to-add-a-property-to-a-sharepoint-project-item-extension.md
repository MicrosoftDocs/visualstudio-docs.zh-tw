---
title: HOW TO：將屬性加入至 SharePoint 專案項目擴充功能 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6dc2c0588fa3078a805f9804263afcf521ae72ed
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644425"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>HOW TO：將屬性加入至 SharePoint 專案項目擴充功能
  您可以使用專案項目擴充功能，將屬性加入至任何已安裝 Visual Studio 中的 SharePoint 專案項目。 屬性會出現在**屬性**視窗中選取的專案項目時**方案總管 中**。

 下列步驟假設您已建立的專案項目延伸模組。 如需詳細資訊，請參閱[如何：建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。

### <a name="to-add-a-property-to-a-project-item-extension"></a>若要將屬性加入至專案項目擴充功能

1.  定義具有公用的屬性，表示您要新增至專案項目類型的屬性的類別。 如果您想要將多個屬性新增至專案項目類型，您可以在相同類別中，或在不同的類別中定義的所有屬性。

2.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>方法您<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>實作、 控制代碼<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>事件*projectItemType*參數。

3.  中的事件處理常式<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>事件，將您的內容類別的執行個體<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A>事件引數參數的集合。

## <a name="example"></a>範例
 下列程式碼範例示範如何加入名為**屬性範例**至事件接收器的專案項目。

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]

### <a name="understand-the-code"></a>了解程式碼
 若要確保相同的執行個體`CustomProperties`類別每次使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>事件發生時，程式碼範例將屬性的物件加入<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>屬性就會發生此事件的專案項目的第一個時間。 此事件一次發生時，程式碼會擷取此物件。 如需使用詳細資訊<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>屬性的資料相關聯專案項目，請參閱[相關聯的自訂資料與 SharePoint 工具擴充功能](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。

 若要保存為屬性值的變更**設定**存取子`ExampleProperty`儲存新的值，以<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>屬性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>屬性相關聯的物件。 如需使用詳細資訊<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>屬性，以保存資料與專案項目，請參閱[將資料儲存於 SharePoint 專案系統擴充](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。

### <a name="specify-the-behavior-of-custom-properties"></a>指定自訂屬性的行為
 您可以定義自訂屬性如何顯示和行為**屬性**藉由套用屬性 視窗<xref:System.ComponentModel>屬性定義的命名空間。 下列屬性可用於許多案例：

-   <xref:System.ComponentModel.DisplayNameAttribute>：指定出現在屬性名稱**屬性**視窗。

-   <xref:System.ComponentModel.DescriptionAttribute>：指定描述字串出現在底部**屬性**時選取屬性 視窗。

-   <xref:System.ComponentModel.DefaultValueAttribute>：指定屬性的預設值。

-   <xref:System.ComponentModel.TypeConverterAttribute>：指定會顯示在字串之間的自訂轉換**屬性**視窗而非字串屬性值。

-   <xref:System.ComponentModel.EditorAttribute>：指定自訂編輯器，以便用來修改屬性。

## <a name="compile-the-code"></a>編譯程式碼
 這些範例需要參考下列組件的類別庫專案：

-   Microsoft.VisualStudio.SharePoint

-   System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>部署擴充功能
 若要部署的延伸模組，建立[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝組件和任何其他您想要將副檔名的檔案。 如需詳細資訊，請參閱 <<c0> [ 部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱
- [如何：建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [如何：將捷徑功能表項目新增至 SharePoint 專案項目擴充功能](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)
- [逐步解說：擴充 SharePoint 專案項目類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
