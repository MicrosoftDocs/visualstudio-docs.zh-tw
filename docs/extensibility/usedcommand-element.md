---
title: 已用指令元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65030c3fe24c3456b0c4c99a667362d2a4c67703
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698830"
---
# <a name="usedcommand-element"></a>UsedCommand 項目
使 VSPackage 能夠造訪在另一個 .vsct 檔案中定義的命令。 例如,如果 VSPackage**Copy**[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]使用由 shell 定義的標準 Copy 命令,則可以將該命令添加到選單或工具列,而無需重新實現該命令。

## <a name="syntax"></a>語法

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要。 標識命令的 GUID ID 對的 GUID。|
|id|必要。 標識命令的 GUID ID 對的識別碼。|
|條件|選擇性。 請參考[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|None||

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[UsedCommands 元素](../extensibility/usedcommands-element.md)|對「已使用命令」元素和其他「已使用命令」群組進行分組。|

## <a name="remarks"></a>備註
 通過將命令添加到元素,VS`<UsedCommands>`包[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]通知 環境 VSPackage 需要該命令。 應為包要求`<UsedCommand>`的任何命令添加一個元素,該命令可能不包含在 Visual Studio 的所有版本和配置中。 例如,如果包調用特定於 Visual C++的命令,則該命令將不適用於 Visual Web 開發人員的使用者,`<UsedCommand>`除非您包含該命令的元素。

## <a name="example"></a>範例

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>另請參閱
- [UsedCommands 元素](../extensibility/usedcommands-element.md)
- [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
