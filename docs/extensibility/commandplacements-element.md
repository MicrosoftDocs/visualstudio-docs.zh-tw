---
title: CommandPlacements 元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcacd56700867682e10ead8e46cfdadcdc66b31d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926867"
---
# <a name="commandplacements-element"></a>CommandPlacements 元素
CommandPlacements 元素分組 CommandPlacement 元素和其他 CommandPlacements 分組。

 CommandPlacements 元素是選擇性的。 如果任何命令、 群組或功能表必須包含在次要位置中，您就不必包含本節中的您 *.vsct*檔案。

## <a name="syntax"></a>語法

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
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|CommandPlacements|群組 CommandPlacement 元素，而且其他 CommandPlacements 分組。|
|[CommandPlacement 元素](../extensibility/commandplacement-element.md)|可讓按鈕、 群組和包含在一個以上的群組或功能表的功能表。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表命令的所有項目。|

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
- [Visual Studio 命令表檔案 (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)