---
title: Icon 元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd56391084788729c0f8439728f9afffd59da946
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311246"
---
# <a name="icon-element"></a>Icon 元素
Guid 屬性的圖示標記會定義點陣圖的 guid。 `id`屬性選取點陣圖區中的位置。 這是選擇性的項目。 如果這個項目不包含值**guidOfficeIcon:msotcidNoIcon**會隱含。

## <a name="syntax"></a>語法

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要項。 定義點陣圖的 guid。|
|id|必要項。 選取的位置中的點陣圖區。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|無。|無。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[Buttons 元素](../extensibility/buttons-element.md)||

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表檔案 (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)