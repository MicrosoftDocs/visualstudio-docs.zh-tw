---
title: ExtensionData 項目 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionData element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e065c64445710e6ff0a99d3bcf8a27c71425879e
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765709"
---
# <a name="extensiondata-element"></a>ExtensionData 項目
  代表 SharePoint 專案項目相關聯的自訂資料項目的集合。  
  
## <a name="syntax"></a>語法  
  
```xml  
<ExtensionData>  
  <ExtensionDataItem.../>  
</ExtensionData>  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素
  
|項目|描述|  
|-------------|-----------------|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|選擇性項目。<br /><br /> 代表索引鍵/值格式中的 SharePoint 專案項目相關聯的自訂資料項目。 索引鍵和值都必須是字串。|  
  
### <a name="parent-elements"></a>父元素
  
|元素|描述|  
|-------------|-----------------|  
|[專案項目](../sharepoint/projectitem-element.md)|代表 SharePoint 專案項目。 這個項目為必要的根元素的`.spdata`檔案。|  
  
## <a name="remarks"></a>備註  
 當您自訂的資料使用與相關聯的 SharePoint 專案項目<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>屬性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>物件時，Visual Studio 會儲存到資料**ExtensionData**中的項目`.spdata`專案檔項目。 如需詳細資訊，請參閱[擴充 SharePoint 專案系統中儲存的資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
## <a name="element-information"></a>項目資訊
  
|||  
|-|-|  
|**命名空間**|http<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔**|ProjectItemModelSchema.xsd|  
|**可以是空的**|否|  
  
## <a name="see-also"></a>另請參閱
 [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  
