---
title: Icon 元素 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710512"
---
# <a name="icon-element"></a>Icon 元素
Icon 標記的 guid 屬性是已定義點陣圖的 guid。 `id`屬性會選取點陣圖區域中的位置。 這是選擇性的項目。 如果未包含此元素，則會隱含 **guidOfficeIcon： msotcidNoIcon** 的值。

## <a name="syntax"></a>語法

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要。 已定義點陣圖的 guid。|
|id|必要。 選取點陣圖條紋中的位置。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|無。|無。|

### <a name="parent-elements"></a>父元素

|項目|描述|
|-------------|-----------------|
|[按鈕元素](../extensibility/buttons-element.md)||

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
