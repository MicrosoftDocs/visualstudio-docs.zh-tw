---
title: CommandPlacements 元素 |Microsoft Docs
description: CommandPlacements 元素會將 CommandPlacement 元素和其他 CommandPlacements 群組分組。 CommandPlacements 元素是選擇性的。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 21e0feb3913b148b4320e69461bc5035655a392d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901886"
---
# <a name="commandplacements-element"></a>CommandPlacements 元素
CommandPlacements 元素會將 CommandPlacement 元素和其他 CommandPlacements 群組分組。

 CommandPlacements 元素是選擇性的。 如果次要位置中必須未包含任何命令、群組或功能表，您就不需要在 *.vsct* 檔案中包含此區段。

## <a name="syntax"></a>Syntax

```xml
<CommandPlacements>
  <CommandPlacement>... </CommandPlacement>
  <CommandPlacement>... </CommandPlacement>
</CommandPlacements>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|CommandPlacements|群組 CommandPlacement 元素和其他 CommandPlacements 群組。|
|[CommandPlacement 元素](../extensibility/commandplacement-element.md)|可將按鈕、群組和功能表包含在一個以上的群組或功能表中。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表命令的所有元素。|

## <a name="example"></a>範例

```xml
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>另請參閱
- [CommandPlacement 元素](../extensibility/commandplacement-element.md)
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
