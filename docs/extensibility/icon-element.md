---
title: Icon 元素 |Microsoft Docs
description: 瞭解 Icon 元素（代表 Visual Studio IDE 延伸模組中使用的圖示），其中包含使用的點陣圖屬性和點陣圖區域中的位置。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7ad5bfdf000232ef92a9e9a27b12152df36a4335
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900820"
---
# <a name="icon-element"></a>Icon 元素
Icon 標記的 guid 屬性是已定義點陣圖的 guid。 `id`屬性會選取點陣圖區域中的位置。 這是選擇性的項目。 如果未包含此元素，則會隱含 **guidOfficeIcon： msotcidNoIcon** 的值。

## <a name="syntax"></a>Syntax

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

|元素|描述|
|-------------|-----------------|
|無。|無。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[按鈕元素](../extensibility/buttons-element.md)||

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
