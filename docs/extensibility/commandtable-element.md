---
title: CommandTable 元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9bb10232c725eb2f538df73f6a7ca98e534a4c14
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341812"
---
# <a name="commandtable-element"></a>CommandTable 元素
CommandTable 是根項目 *.vsct*檔案。 這是定義 VSPackage 提供給 IDE 命令的類型與實際配置的檔案。 命令可能會包含功能表項目、 功能表、 工具列和下拉式方塊。 如需詳細資訊，請參閱 < [Visual Studio 命令表檔案 (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。

## <a name="syntax"></a>語法

```xml
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >
  <Extern>... </Extern>
  <Include>... </Include>
  <Define>... </Define>
  <Commands>... </Commands>
  <CommandPlacements>... </CommandPlacements>
  <VisibilityConstraints>... </VisibilityConstraints>
  <KeyBindings>... </KeyBindings>
  <UsedCommands... </UsedCommands>
  <Symbols>... </Symbols>
</CommandTable>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

| 屬性 | 描述 |
|-----------| - |
| xmlns | 必要項。 XML 命名空間：<br /><br /> xmlns="<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"<br /><br /> xmlns:xs="<http://www.w3.org/2001/XMLSchema>" |
| 語言 | 選擇性。 [語言] 屬性可以用來指定所有的預設語言\<字串 > 命令表中的項目。  如果未指定語言，就會使用目前的處理序的語言：<br /><br /> language="en-us" |

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[Extern 元素](../extensibility/extern-element.md)|選擇性。 包含編譯器的前置處理器指示詞。|
|[包含項目](../extensibility/include-element.md)|選擇性。 包含要包含在編譯中的任何檔案的路徑。|
|[定義項目](../extensibility/define-element.md)|選擇性。 定義指定其名稱及值的符號。|
|[Commands 元素](../extensibility/commands-element.md)|選擇性。 Vspackage，其中包含所有其他項目定義的所有命令的父項目。|
|[CommandPlacements 元素](../extensibility/commandplacements-element.md)|選擇性。 定義位置命令列上的命令要放置。|
|[VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)|選擇性。 決定命令和工具列的靜態可見。|
|[KeyBindings 元素](../extensibility/keybindings-element.md)|選擇性。 如果有任何命令，請指定的快速鍵組合。|
|[UsedCommands 元素](../extensibility/usedcommands-element.md)|選擇性。 可讓 VSPackage 也可以選擇性地實作自己的版本，其他 Vspackage 原本支援的功能。|
|[Symbols 元素](https://www.microsoft.com/download/details.aspx?id=55984)|選擇性。 包含的所有符號資料-Guid、 識別碼和其他等等-編譯器。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|None||

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表檔案 (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)