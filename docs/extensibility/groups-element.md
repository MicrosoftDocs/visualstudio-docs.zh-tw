---
title: Groups 元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 740ca4ec-79fa-4b98-8f9a-2a137f9f7f98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6383c3c7a28f9aa7778fddcbfe36b237d21323f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711180"
---
# <a name="groups-element"></a>Groups 項目
包含定義 VSPackage 之命令群組的專案。

## <a name="syntax"></a>語法

```xml
<Groups>
  <Group>... </Group>
  <Group>... </Group>
</Groups>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[Group 元素](../extensibility/group-element.md)|表示單一命令群組。|
|[Groups 元素](../extensibility/groups-element.md)|包含定義 VSPackage 之命令群組的專案。|

### <a name="parent-elements"></a>父元素

|項目|描述|
|-------------|-----------------|
|[命令元素](../extensibility/commands-element.md)|代表 VSPackage 工具列上的命令集合。|

## <a name="example"></a>範例

```xml
<Groups>
  <Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>
  </Group>
</Groups>
```

## <a name="see-also"></a>另請參閱
- [Vspackage 如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
