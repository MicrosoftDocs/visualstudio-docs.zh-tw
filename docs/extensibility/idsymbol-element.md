---
title: IDSymbol 元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d02a26a6874165738d917a14986d16d142c01915
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710367"
---
# <a name="idsymbol-element"></a>IDSymbol 元素
該`IDSymbol`元素包含表示功能表、組或命令的 GUID:ID 對的 ID。 GUID 來自`GuidSymbol`父 元素。 元素`IDSymbol`具有一`name`個 屬性,該屬性為 ID 提供友好名稱,`value`該名稱包含在 屬性中。

## <a name="syntax"></a>語法

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|NAME|必要。 ID 符號的名稱。|
|value|必要。 ID 符號的數字 ID 值。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[吉德符號元素](../extensibility/guidsymbol-element.md)|包含表示功能表、組或命令的 GUID:ID 對的 GUID。 將 `IDSymbol` 項目設為群組。|

## <a name="remarks"></a>備註
 指定元素`IDSymbol``GuidSymbol`的元素必須具有唯一的`value`。 但是,`IDSymbol`具有相同值的元素可以存在於包中,只要它們具有不同的父項。

## <a name="see-also"></a>另請參閱
- [視覺化工作室指令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
