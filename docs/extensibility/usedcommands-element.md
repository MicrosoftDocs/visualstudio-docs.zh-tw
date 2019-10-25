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
ms.openlocfilehash: 66361ad58c15e8539fcda6d0ec4468dd8b68289b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718618"
---
# <a name="usedcommands-element"></a>UsedCommands 項目
UsedCommands 元素會將 UsedCommand 元素和其他 UsedCommands 群組分組。

 UsedCommands 元素是選擇性的。 如果您未呼叫在封裝外部定義的命令，則不需要在 .vsct 檔案中包含此區段。

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
|條件|選擇項。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子項目

|項目|描述|
|-------------|-----------------|
|[UsedCommand 元素](../extensibility/usedcommand-element.md)|由其他程式碼所執行的命令。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義 VSPackage 為整合式開發環境（IDE）提供的所有專案，這些專案代表命令（例如，功能表項目、功能表、工具列和下拉式方塊）。|

## <a name="example"></a>範例

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>請參閱
- [UsedCommand 元素](../extensibility/usedcommand-element.md)
- [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)