---
title: Extern 元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34e38618a153aa74bdc2449895272fc9e399c82d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342792"
---
# <a name="extern-element"></a>Extern 元素
Extern 元素參考任何外部標頭 ( *.h*) 與合併的檔案 *.vsct*在編譯時期的檔案。 要合併的檔案必須位於 Include 路徑指定給 VSCT 編譯器，或是參照[Include 項目](../extensibility/include-element.md)。 檔案可能是其他 *.vsct*檔案或C++標頭檔。

 標頭檔中的定義的格式必須是"#define [符號] [Value]"的值可能是另一個符號，如果先前已定義。 定義可用於條件陳述式的命令項目。 將捨棄任何並未實際使用的符號。

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
|href|必要項。 標頭檔路徑：<br /><br /> href="stdidcmd.h"|
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|
|語言|選擇性。 所有的預設語言[\<字串 >](../extensibility/strings-element.md)命令表中的項目：<br /><br /> language="en-us"|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|無。|無。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義所有代表命令的項目 — 也就是功能表項目、 功能表、 工具列和下拉式方塊，VSPackage 提供給 IDE。|

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
- [Visual Studio 命令表檔案 (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Vspackage 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)