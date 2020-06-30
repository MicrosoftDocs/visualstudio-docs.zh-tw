---
title: SafeControl 元素 |Microsoft Docs
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
ms.openlocfilehash: 6c9936054c5cc622e6f335d81d1568ebed16518f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547923"
---
# <a name="safecontrol-element"></a>SafeControl 項目
  代表 ASPX 控制項或 Web 元件，指定為任何使用者在 SharePoint 網站上的任何 ASPX 頁面上存取的安全性。

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
|**組件**|選擇性的**xs： string**屬性。<br /><br /> 定義 ASPX 控制項或 Web 元件之元件的名稱。 根據預設，這個屬性會使用元件名稱 **$SharePoint 的 AssemblyFullName $** 可取代參數。 如需詳細資訊，請參閱可[取代的參數](../sharepoint/replaceable-parameters.md)。|
|**IsSafe**|選擇性的**xs： boolean**屬性。<br /><br /> 指定 ASPX 控制項或 Web 元件是否安全，不受信任的使用者存取。|
|**IsSafeAgainstScript**|選擇性的**xs： boolean**屬性。<br /><br /> 指定不受信任的使用者是否可以查看或編輯 ASPX 控制項或 Web 元件的屬性。|
|**名稱**|選擇性的**xs： string**屬性。<br /><br /> 此安全控制項專案在集合中的名稱。|
|**Namespace**|選擇性的**xs： string**屬性。<br /><br /> ASPX 控制項或 Web 元件的命名空間。|
|**類型**|選擇性的**xs： string**屬性。<br /><br /> ASPX 控制項或 Web 元件的類型名稱。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[SafeControls](../sharepoint/safecontrols-element.md)|代表 ASPX 控制項和 Web 組件的集合，其指定為任何使用者在 SharePoint 網站上的任何 ASPX 頁面上存取的安全性。|

## <a name="remarks"></a>備註
 如需安全控制項的詳細資訊，請參閱[在專案專案中提供封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。

## <a name="element-information"></a>項目資訊

|屬性|值|
|-|-|
|**Namespace**|HTTP： \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**架構名稱**|SharePoint 專案專案架構|
|**驗證檔案**|ProjectItemModelSchema .xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
- [SharePoint 專案專案架構參考](../sharepoint/sharepoint-project-item-schema-reference.md)
- [提供專案專案中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
