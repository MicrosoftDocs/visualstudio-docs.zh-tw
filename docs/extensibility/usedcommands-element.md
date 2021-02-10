---
title: UsedCommands 元素 |Microsoft Docs
description: UsedCommands 元素會將 UsedCommand 元素和其他 UsedCommands 群組分組。 UsedCommands 元素是選擇性的。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89ecd1d0f7697a38ef7318ddf93a91a4397b5d72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934060"
---
# <a name="usedcommands-element"></a>UsedCommands 項目
UsedCommands 元素會將 UsedCommand 元素和其他 UsedCommands 群組分組。

 UsedCommands 元素是選擇性的。 如果您未呼叫在套件之外定義的命令，就不需要在 .vsct 檔案中包含此區段。

## <a name="syntax"></a>Syntax

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
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[UsedCommand 元素](../extensibility/usedcommand-element.md)|由其他程式碼所執行的命令。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表命令 (的所有元素，例如，功能表項目、功能表、工具列和下拉式方塊) VSPackage 提供給整合式開發環境 (IDE) 。|

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
