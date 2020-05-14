---
title: 圖元素 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85310923134a6db59f1b6a3a15ac4b96a127e239
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739984"
---
# <a name="bitmaps-element"></a>點陣圖元素
對[位圖元素](../extensibility/bitmap-element.md)元素。

## <a name="syntax"></a>語法

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
|條件|選擇性。 請參考[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[點陣圖元素](../extensibility/bitmaps-element.md)|對位圖元素。|
|[點陣圖元素](../extensibility/bitmap-element.md)|定義點陣圖。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[指令元素](../extensibility/commands-element.md)|表示 VSPackage 工具列上的命令集合。|

## <a name="example"></a>範例

```
<Bitmaps>
  <Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
  <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
    usedList="1, 2, 3, 4"/>
</Bitmaps>
```

## <a name="see-also"></a>另請參閱
- [VS 套件如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [命令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
