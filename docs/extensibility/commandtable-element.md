---
title: CommandTable 元素 |Microsoft Docs
description: CommandTable 是 .vsct 檔的根項目，它會定義 VSPackage 提供給 IDE 的命令配置和類型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 507bdd20602c680f58b62e85251eaaa592982bc7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089520"
---
# <a name="commandtable-element"></a>CommandTable 元素
CommandTable 是 *.vsct* 檔的根項目。 此檔案會定義 VSPackage 提供給 IDE 之命令的實際版面配置和類型。 命令可能包含功能表項目、功能表、工具列和下拉式方塊。 如需詳細資訊，請參閱 [Visual Studio 命令表格 (. .vsct) ](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)檔。

## <a name="syntax"></a>Syntax

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
| xmlns | 必要。 XML 命名空間：<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns： xs = " <http://www.w3.org/2001/XMLSchema> " |
| 語言 | 選擇性。 Language 屬性可用來指定命令資料表中所有元素的預設語言 \<Strings> 。  如果未指定語言，則會使用目前進程的語言：<br /><br /> language = "en-us" |

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[Extern 元素](../extensibility/extern-element.md)|選擇性。 包含編譯器的預處理器指示詞。|
|[Include 元素](../extensibility/include-element.md)|選擇性。 包含要包含在編譯中之任何檔案的路徑。|
|[Define 元素](../extensibility/define-element.md)|選擇性。 定義指定其名稱和值的符號。|
|[命令元素](../extensibility/commands-element.md)|選擇性。 父元素，定義包含所有其他元素之 VSPackage 的所有命令。|
|[CommandPlacements 元素](../extensibility/commandplacements-element.md)|選擇性。 定義命令列上要放置命令的位置。|
|[VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)|選擇性。 決定命令和工具列的靜態可見度。|
|[Keybindings.json 元素](../extensibility/keybindings-element.md)|選擇性。 指定命令的快捷方式按鍵組合（如果有的話）。|
|[UsedCommands 元素](../extensibility/usedcommands-element.md)|選擇性。 允許 VSPackage 選擇性地執行其他 Vspackage 原本支援的功能版本。|
|[符號元素](https://www.microsoft.com/download/details.aspx?id=55984)|選擇性。 包含編譯器的任何符號資料--Guid、識別碼等等。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|無||

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
