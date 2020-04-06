---
title: 指令表元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a362763d34335b9a18c4114a7c35b23f0efee020
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739654"
---
# <a name="commandtable-element"></a>指令表元素
指令表是 *.vsct*檔案的根元素。 這是定義 VS 包向 IDE 提供的命令的實際佈局和類型的檔案。 命令可能包括功能表項、功能表、工具列和組合框。 有關詳細資訊,請參閱[可視化工作室命令表 (.vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。

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
| xmlns | 必要。 XML 命名空間:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns:xs="<http://www.w3.org/2001/XMLSchema> |
| 語言 | 選擇性。 語言屬性可用於指定命令表中所有\<字串>元素的默認語言。  沒有指定該語言,將使用目前程序的語言:<br /><br /> 語言="en-us" |

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[外部元素](../extensibility/extern-element.md)|選擇性。 包含編譯器的預處理器指令。|
|[包括元素](../extensibility/include-element.md)|選擇性。 包含要包含在編譯中的任何文件的路徑。|
|[定義項目](../extensibility/define-element.md)|選擇性。 定義給定其名稱和值的符號。|
|[指令元素](../extensibility/commands-element.md)|選擇性。 定義包含所有其他元素的 VSPackage 的所有命令的父元素。|
|[命令放置元素](../extensibility/commandplacements-element.md)|選擇性。 定義命令列上要放置命令的位置。|
|[可見性限制元素](../extensibility/visibilityconstraints-element.md)|選擇性。 確定命令和工具列的靜態可見性。|
|[鍵繫結元素](../extensibility/keybindings-element.md)|選擇性。 指定命令的快捷鍵組合(如果有)。|
|[已用指令元素](../extensibility/usedcommands-element.md)|選擇性。 允許 VSPackage 可以選擇實現其最初由其他 VSPackage 支援的功能版本。|
|[符號元素](https://www.microsoft.com/download/details.aspx?id=55984)|選擇性。 包含編譯器的任何符號數據(GUID、DOd 等)。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|None||

## <a name="see-also"></a>另請參閱
- [視覺化工作室指令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
