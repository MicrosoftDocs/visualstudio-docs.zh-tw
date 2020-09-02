---
title: CommandPlacement 元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf9f23b5e860b895baa4c2a7a783f2ee15fcc77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739738"
---
# <a name="commandplacement-element"></a>CommandPlacement 元素
CommandPlacement 元素可讓按鈕、群組和功能表包含在一個以上的群組或功能表中。 藉由使用 CommandPlacement 專案，您就不需要完全重新定義這些專案，即可修改使用者介面的外觀。

 如需詳細資訊，請參閱 [建立可重複使用的按鈕群組](../extensibility/creating-reusable-groups-of-buttons.md)。

## <a name="syntax"></a>語法

```
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >
  <Parent>... </Parent>
</CommandPlacement>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要。 命令集的 guid，如 [符號元素](../extensibility/symbols-element.md)中所定義。|
|id|必要。 要放置之功能表、群組或命令的識別碼，如中所定義 `Symbols Element` 。|
|priority|必要。 判斷專案在其父元素中的視覺位置。|
|條件|選擇性。 請參閱 [條件式 Aattributes](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|父系|必要。 裝載要放置之專案的功能表或群組。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[CommandPlacements 元素](../extensibility/commandplacements-element.md)|指定 CommandPlacements 和 CommandPlacement 元素的群組。|

## <a name="example"></a>範例

```
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>另請參閱
- [CommandPlacements 元素](../extensibility/commandplacements-element.md)
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
