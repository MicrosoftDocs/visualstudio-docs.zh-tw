---
title: SafeControls 元素 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e840f0040cf94fea408615525358580d207f07c0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547897"
---
# <a name="safecontrols-element"></a>SafeControls 項目
  ASPX 控制項和 Web 組件的集合，指定為任何使用者在 SharePoint 網站上的任何 ASPX 網頁上存取的安全性。

## <a name="syntax"></a>語法

```xml
<SafeControls>
  <SafeControl.../>
</SafeControls>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[SafeControl](../sharepoint/safecontrol-element.md)|選擇性項目。<br /><br /> 代表 ASPX 控制項或 Web 元件，指定為任何使用者在 SharePoint 網站上的任何 ASPX 頁面上存取的安全性。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|表示 SharePoint 專案專案。 這個元素是 *.spdata*檔案的必要根項目。|

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
