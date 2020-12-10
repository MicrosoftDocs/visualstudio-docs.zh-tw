---
title: Extern 元素 |Microsoft Docs
description: Extern 元素會參考任何外部標頭 ( .h) 檔案，以便在編譯時期與 .vsct 檔案合併。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e975c3f721d65b64fc7994824406b0c9af13022
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994520"
---
# <a name="extern-element"></a>Extern 元素
Extern 元素會參考任何外部標頭 (*.h*) 檔案，以便在編譯時期與 *.vsct* 檔案合併。 要合併的檔案必須位於提供給 .VSCT 編譯器的 Include 路徑上，或是由 [include 元素](../extensibility/include-element.md)所參考。 檔案可能是其他 *.vsct* 檔案或 c + + 標頭檔。

 標頭檔中的定義必須是 "#define [Symbol] [Value]" 格式，如果先前已定義，該值可能是另一個符號。 定義可以用於命令專案的條件陳述式中。 所有未實際使用的符號都會被捨棄。

 CommandTable 元素 Extern 元素

## <a name="syntax"></a>語法

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|href|必要。 標頭檔的路徑：<br /><br /> href = "stdidcmd .h"|
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|
|語言|選擇性。 [\<Strings>](../extensibility/strings-element.md)命令資料表中所有元素的預設語言：<br /><br /> language = "en-us"|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|無。|無。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義 VSPackage 為 IDE 提供的命令（即功能表項目、功能表、工具列和下拉式方塊）的所有元素。|

## <a name="example"></a>範例

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>
    ...
  <Commands package="guidMyPackage">
</CommandTable>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Vspackage 如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
