---
title: SafeControls 元素 |Microsoft Docs
description: 取得 SafeControls 元素的相關資訊，其中包含在 SharePoint 網站的 ASPX 頁面上標示為安全存取的 ASPX 控制項或網頁元件的集合。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c3423d1b6efd106ef7f947bd8573dcd1aa548a66
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440671"
---
# <a name="safecontrols-element"></a>SafeControls 項目
  ASPX 控制項和 Web 組件的集合，可在 SharePoint 網站上的任何 ASPX 頁面上，指定為可存取的任何使用者的安全。

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

|項目|描述|
|-------------|-----------------|
|[SafeControl](../sharepoint/safecontrol-element.md)|選擇性項目。<br /><br /> 代表在 SharePoint 網站上的任何 ASPX 頁面上，指定為可存取之任何使用者的 ASPX 控制項或網頁元件。|

### <a name="parent-elements"></a>父元素

|項目|描述|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|表示 SharePoint 專案專案。 這個元素是 *.spdata* 檔案的必要根項目。|

## <a name="remarks"></a>備註
 如需安全控制項的詳細資訊，請參閱 [在專案專案中提供封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。

## <a name="element-information"></a>項目資訊

|屬性|值|
|-|-|
|**Namespace**|HTTP： \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**結構描述名稱**|SharePoint 專案專案架構|
|**驗證檔**|ProjectItemModelSchema .xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
- [SharePoint 專案專案架構參考](../sharepoint/sharepoint-project-item-schema-reference.md)
- [提供專案專案中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
