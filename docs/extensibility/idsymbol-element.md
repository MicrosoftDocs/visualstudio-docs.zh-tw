---
title: IDSymbol 元素 |Microsoft Docs
description: IDSymbol 元素包含 GUID： ID 組的識別碼，代表功能表、群組或命令。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e4feb477f8507bc3fe57e6db355538ab98ceeeaa
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995534"
---
# <a name="idsymbol-element"></a>IDSymbol 元素
`IDSymbol`元素包含 GUID： id 組的識別碼，代表功能表、群組或命令。 GUID 來自父 `GuidSymbol` 元素。 專案 `IDSymbol` 具有屬性， `name` 該屬性會提供識別碼的易記名稱，該名稱包含在屬性中 `value` 。

## <a name="syntax"></a>語法

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|NAME|必要。 識別碼符號的名稱。|
|值|必要。 識別碼符號的數值識別碼值。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GuidSymbol 元素](../extensibility/guidsymbol-element.md)|包含代表功能表、群組或命令之 GUID： ID 組的 GUID。 將 `IDSymbol` 項目設為群組。|

## <a name="remarks"></a>備註
 `IDSymbol`指定專案中的每個元素都 `GuidSymbol` 必須有唯一的 `value` 。 不過， `IDSymbol` 具有相同值的專案可以存在於封裝中，前提是它們有不同的父系。

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
