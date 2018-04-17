---
title: ExtensionDataItem 項目 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8c991d3fece3e5997e8d470d168af9eba47c8663
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem 項目
  代表索引鍵/值格式中的 SharePoint 專案項目相關聯的自訂資料項目。 索引鍵和值都必須是字串。  
  
## <a name="syntax"></a>語法  
  
```  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**Key**|需要**xs: string**屬性。<br /><br /> 用來儲存和擷取資料的項目索引鍵。|  
|**值**|需要**xs: string**屬性。<br /><br /> 資料項目的值。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|代表 SharePoint 專案項目相關聯的自訂資料項目的集合。|  
  
## <a name="remarks"></a>備註  
 當您自訂的資料使用與相關聯的 SharePoint 專案項目<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>屬性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>物件時，Visual Studio 會將資料儲存至新**ExtensionDataItem** .spdata 檔案的專案項目中的項目。 如需詳細資訊，請參閱[擴充 SharePoint 專案系統中儲存的資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
## <a name="element-information"></a>項目資訊  
  
|||  
|-|-|  
|**命名空間**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔**|ProjectItemModelSchema.xsd|  
|**可以是空的**|否|  
  
## <a name="see-also"></a>另請參閱  
 [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  