---
title: SafeControl 項目 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a80606297c61d59d5670473755e667c6d3c538de
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56601261"
---
# <a name="safecontrol-element"></a>SafeControl 項目
  代表 ASPX 控制項或指定為安全的任何使用者存取 SharePoint 網站上的任何 ASPX 頁面上的 Web 組件。

## <a name="syntax"></a>語法

```xml
<SafeControl Assembly = "Name of assembly that contains the safe control"
    IsSafe = "true/false"
    IsSafeAgainstScript = "true/false"
    Name = "Name of this safe control entry"
    Namespace = "Namespace of the safe control"
    TypeName = "Type of the safe control" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|**Assembly**|選擇性**xs: string**屬性。<br /><br /> 定義 ASPX 控制項或 Web 組件的組件名稱。 根據預設，這個屬性會使用 **$SharePoint.Project.AssemblyFullName$** 組件名稱的可取代參數。 如需詳細資訊，請參閱 <<c0> [ 可置換的參數](../sharepoint/replaceable-parameters.md)。|
|**IsSafe**|選擇性**xs: boolean**屬性。<br /><br /> 指定 Web 組件的 ASPX 控制項是否安全，不受信任的使用者才能存取。|
|**IsSafeAgainstScript**|選擇性**xs: boolean**屬性。<br /><br /> 指定不受信任的使用者可以檢視或編輯網頁組件的 ASPX 控制項的屬性。|
|**名稱**|選擇性**xs: string**屬性。<br /><br /> 此集合中的安全控制項項目的名稱。|
|**命名空間**|選擇性**xs: string**屬性。<br /><br /> ASPX 控制項或 Web 組件的命名空間。|
|**TypeName**|選擇性**xs: string**屬性。<br /><br /> ASPX 控制項或 Web 組件的型別名稱。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[SafeControls](../sharepoint/safecontrols-element.md)|代表 ASPX 控制項和被指定為安全的任何使用者存取 SharePoint 網站上的任何 ASPX 頁面上的 Web 組件的集合。|

## <a name="remarks"></a>備註
 如需有關安全控制項的詳細資訊，請參閱[提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。

## <a name="element-information"></a>項目資訊

|||
|-|-|
|**命名空間**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**結構描述名稱**|SharePoint 專案項目結構描述|
|**驗證檔案**|ProjectItemModelSchema.xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
- [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)
- [提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
