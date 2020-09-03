---
title: Include 元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ea89185d28be2816a690d867dbb3eccbb739e04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710365"
---
# <a name="include-element"></a>Include 元素
Include 元素會指定一個檔案，該檔案位於提供的 include 路徑上，以插入目前的檔案中。  所有定義的符號和類型都會成為編譯結果的一部分。

## <a name="syntax"></a>語法

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|href|必要。 標頭檔的路徑：<br /><br /> href = "stdidcmd .h"|
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|無。|無。|

### <a name="parent-elements"></a>父元素

|項目|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義 VSPackage 為 IDE 提供的命令（即功能表項目、功能表、工具列和下拉式方塊）的所有元素。|

## <a name="example"></a>範例

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
