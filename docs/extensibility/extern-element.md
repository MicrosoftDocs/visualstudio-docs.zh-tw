---
title: 外部元素 |微軟文件
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
ms.openlocfilehash: 2cf6f9db77abaa7034af8d074b9833a4c1560f07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711492"
---
# <a name="extern-element"></a>外部元素
Extern 元素引用任何外部標頭 *(.h*) 檔案,以便在編譯時與 *.vsct*檔合併。 要合併的文件必須位於提供給 VSCT 編譯器的「包含」路徑上,或者由[Include 元素](../extensibility/include-element.md)引用。 這些檔可能是其他 *.vsct*檔或C++頭檔。

 標題檔案中的定義必須為"#define [符號] [值]"的形式。 定義可用於命令項的條件語句。 任何未實際使用的符號都將被丟棄。

 指令表元素外部元素

## <a name="syntax"></a>語法

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|href|必要。 標頭檔案的路徑:<br /><br /> href="stdidcmd.h"|
|條件|選擇性。 請參考[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|
|語言|選擇性。 指令表中所有[\<字串的](../extensibility/strings-element.md)預設語言>元素:<br /><br /> 語言="en-us"|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|無。|無。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[指令表元素](../extensibility/commandtable-element.md)|定義表示 VSPackage 向 IDE 提供的命令的所有元素(即選單項、功能表、工具列和組合框)。|

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
- [視覺化工作室指令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VS 套件如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [命令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
