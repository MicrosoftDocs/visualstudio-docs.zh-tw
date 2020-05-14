---
title: 群組元素 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711180"
---
# <a name="groups-element"></a>Groups 項目
包含定義 VSPackage 的命令組的條目。

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
|條件|選擇性。 請參考[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[Group 元素](../extensibility/group-element.md)|表示單個命令組。|
|[群組項目](../extensibility/groups-element.md)|包含定義 VSPackage 的命令組的條目。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[指令元素](../extensibility/commands-element.md)|表示 VSPackage 工具列上的命令集合。|

## <a name="example"></a>範例

```xml
<Groups>
  <Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>
  </Group>
</Groups>
```

## <a name="see-also"></a>另請參閱
- [VS 套件如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [命令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
