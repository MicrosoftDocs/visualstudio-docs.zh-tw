---
title: Group 元素 |Microsoft Docs
description: Group 元素定義 VSPackage 命令群組。 本文說明屬性、子項目和父元素。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0a5520a8a47b4b356a79832b619395f86e8231d9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945782"
---
# <a name="group-element"></a>Group 元素
定義 VSPackage 命令群組。

## <a name="syntax"></a>Syntax

```xml
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">
  <Parent>... </Parent>
</Group>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要。 GUID/識別碼命令識別碼的 GUID。|
|id|必要。 GUID/識別碼命令識別碼的識別碼。|
|priority|選擇性。 指定優先權的數位值。|
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|父代|選擇性。 按鈕的父元素。|
|Annotation|選擇性批註。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[Groups 元素](../extensibility/groups-element.md)|包含定義 VSPackage 之命令群組的專案。|

## <a name="example"></a>範例

```xml
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>
</Group>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
