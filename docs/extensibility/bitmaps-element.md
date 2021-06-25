---
title: 點陣圖元素 |Microsoft Docs
description: 點陣圖元素會將一或多個點陣圖元素分組。 本文包含點陣圖元素的範例。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a86943e683502bdd1cd19668e9aafcb8fe7e1bc8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903303"
---
# <a name="bitmaps-element"></a>點陣圖元素
群組 [點陣圖元素](../extensibility/bitmap-element.md) 元素。

## <a name="syntax"></a>Syntax

```
<Bitmaps>
  <Bitmap>... </Bitmap>
  <Bitmap>... </Bitmap>
</Bitmaps>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[點陣圖元素](../extensibility/bitmaps-element.md)|群組點陣圖元素。|
|[Bitmap 元素](../extensibility/bitmap-element.md)|定義點陣圖。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[命令元素](../extensibility/commands-element.md)|代表 VSPackage 工具列上的命令集合。|

## <a name="example"></a>範例

```
<Bitmaps>
  <Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
  <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
    usedList="1, 2, 3, 4"/>
</Bitmaps>
```

## <a name="see-also"></a>另請參閱
- [Vspackage 如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
