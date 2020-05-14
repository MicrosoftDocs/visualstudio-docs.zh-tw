---
title: 命令放置元素 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739738"
---
# <a name="commandplacement-element"></a>命令放置元素
「命令放置」元素允許按鈕、組和功能表包含在多個組或功能表中。 通過使用 Command 放置元素,您不必完全重新定義這些專案,以修改使用者介面的外觀。

 關於詳細資訊,請參閱[建立可重用的按鈕群組](../extensibility/creating-reusable-groups-of-buttons.md)。

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
|guid|必要。 命令集的 guid,如[符號元素](../extensibility/symbols-element.md)中定義的那樣。|
|id|必要。 要放置的功能表、組或命令的 ID,如`Symbols Element`中定義的那樣。|
|priority|必要。 確定項在其父元素中的可視位置。|
|條件|選擇性。 請參考[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|父系|必要。 承載要放置的項的功能表或組。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[命令放置元素](../extensibility/commandplacements-element.md)|指定命令放置和指令放置元素的群組。|

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
- [命令放置元素](../extensibility/commandplacements-element.md)
- [視覺化工作室指令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
