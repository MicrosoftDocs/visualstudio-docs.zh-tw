---
title: UsedCommands 元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e43834517855f72dd32c024c222089cf42c7c3ac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316289"
---
# <a name="usedcommands-element"></a>UsedCommands 項目
UsedCommands 元素分組 UsedCommand 元素和其他 UsedCommands 分組。

 UsedCommands 元素是選擇性的。 如果您未呼叫您的套件之外定義的命令，您不必在.vsct 檔案中加入此區段。

## <a name="syntax"></a>語法

```
<UsedCommands condition="Defined(DEBUG)">
  <UsedCommand ... />
</UsedCommands>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[UsedCommand 元素](../extensibility/usedcommand-element.md)|其他程式碼實作命令。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表整合式的開發環境 (IDE) 的 VSPackage 提供的命令 （例如，功能表項目、 功能表、 工具列和下拉式方塊） 的所有項目。|

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