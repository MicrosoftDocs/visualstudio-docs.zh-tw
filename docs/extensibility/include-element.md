---
title: 包含項目 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7287f4e8b611f55ea28e648aec3f95d1407bf07e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350101"
---
# <a name="include-element"></a>包含項目
Include 項目指定可找到的檔案上提供包含可插入至目前檔案的路徑。  所有符號和定義型別都會編譯結果的一部分。

## <a name="syntax"></a>語法

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|href|必要項。 標頭檔路徑：<br /><br /> href="stdidcmd.h"|
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|無。|無。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義所有代表命令的項目 — 也就是功能表項目、 功能表、 工具列和下拉式方塊，VSPackage 提供給 IDE。|

## <a name="example"></a>範例

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表檔案 (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)