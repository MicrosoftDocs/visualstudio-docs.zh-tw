---
title: 已使用指令元素 ( C) :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76732b2a9700f1737af495098c8c23aa4b618819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698744"
---
# <a name="usedcommands-element"></a>UsedCommands 項目
「已用命令」元素對「已命令」元素和其他「已用命令」群組。

 「已使用命令」元素是可選的。 如果不調用套件外定義的命令,則不必在 .vsct 檔中包含此部分。

## <a name="syntax"></a>語法

```
<UsedCommands condition="Defined(DEBUG)">
  <UsedCommand ... />
</UsedCommands>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|條件|選擇性。 請參考[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[UsedCommand 元素](../extensibility/usedcommand-element.md)|由其他代碼實現的命令。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義 VSPackage 向整合式開發環境 (IDE) 提供的命令(例如,選單項、功能表、工具列和組合框)的所有元素。|

## <a name="example"></a>範例

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>另請參閱
- [UsedCommand 元素](../extensibility/usedcommand-element.md)
- [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
