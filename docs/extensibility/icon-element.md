---
title: 圖示元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf4f8a69e565620007fba4b9970ce96bb1513995
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710512"
---
# <a name="icon-element"></a>圖示元素
圖示標記的 guid 屬性是已定義的點陣圖的 guid。 屬性`id`選擇點陣圖條中的槽。 這是選擇性的項目。 如果未包含此元素,則隱含了**guidOfficeIcon:msotcidNoIcon**的值。

## <a name="syntax"></a>語法

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要。 已定義的點陣圖的 guid。|
|id|必要。 選擇點陣圖條中的插槽。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|無。|無。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[按鈕項目](../extensibility/buttons-element.md)||

## <a name="see-also"></a>另請參閱
- [視覺化工作室指令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
