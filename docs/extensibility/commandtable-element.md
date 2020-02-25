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
ms.openlocfilehash: f577b52ad2a9b1fd66ed9c24fb2737621aa8554c
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557774"
---
# <a name="commandtable-element"></a>CommandTable 元素
CommandTable 是 *.vsct*檔案的根項目。 這是定義 VSPackage 提供給 IDE 之命令的實際配置和類型的檔案。 命令可能包含功能表項目、功能表、工具列和下拉式方塊。 如需詳細資訊，請參閱[Visual Studio 命令資料表（. .vsct）](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)檔案。

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
 下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

| 屬性 | 描述 |
|-----------| - |
| xmlns | 必要。 XML 命名空間：<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns： xs = "<http://www.w3.org/2001/XMLSchema>" |
| 語言 | 選擇性。 Language 屬性可用來指定命令資料表中 > 元素之所有 \<字串的預設語言。  如果未指定語言，則會使用目前進程的語言：<br /><br /> language = "en-us" |

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[Extern 元素](../extensibility/extern-element.md)|選擇性。 包含編譯器的預處理器指示詞。|
|[Include 元素](../extensibility/include-element.md)|選擇性。 包含要包含在編譯中之任何檔案的路徑。|
|[Define 元素](../extensibility/define-element.md)|選擇性。 定義符號，並指定其名稱和值。|
|[命令元素](../extensibility/commands-element.md)|選擇性。 父元素，定義包含所有其他元素之 VSPackage 的所有命令。|
|[CommandPlacements 元素](../extensibility/commandplacements-element.md)|選擇性。 定義命令列上要放置命令的位置。|
|[VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)|選擇性。 決定命令和工具列的靜態可見度。|
|[KeyBindings 元素](../extensibility/keybindings-element.md)|選擇性。 指定命令的快速鍵組合（如果有的話）。|
|[UsedCommands 元素](../extensibility/usedcommands-element.md)|選擇性。 允許 VSPackage 選擇性地實作為其他 Vspackage 原本支援的功能版本。|
|[符號元素](https://www.microsoft.com/download/details.aspx?id=55984)|選擇性。 包含編譯器的任何符號資料--Guid、識別碼等等。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|None||

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令資料表（. .vsct）檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)