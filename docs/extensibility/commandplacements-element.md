---
title: 命令放置元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72b087652a654b563fd4e00bacc52290a29fe1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739694"
---
# <a name="commandplacements-element"></a>命令放置元素
命令放置元素對命令放置元素和其他命令放置分組。

 命令放置元素是可選的。 如果輔助位置中不得包含任何命令、組或功能表,則不必在 *.vsct*檔中包含此部分。

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
|條件|選擇性。 請參考[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|命令放置|對命令放置元素和其他命令放置分組。|
|[命令放置元素](../extensibility/commandplacement-element.md)|使按鈕、組和功能表包含在多個組或功能表中。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[指令表元素](../extensibility/commandtable-element.md)|定義表示命令的所有元素。|

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
- [命令放置元素](../extensibility/commandplacement-element.md)
- [視覺化工作室指令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
