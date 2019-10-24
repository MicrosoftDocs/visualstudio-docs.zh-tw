---
title: UsedCommand 元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44ea8f27cafb166968f66c53dc68398526e0aa5d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718778"
---
# <a name="usedcommand-element"></a>UsedCommand 項目
可讓 VSPackage 存取 .vsct 檔案中定義的命令。 例如，如果您的 VSPackage 使用由 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell 定義的標準**複製**命令，您可以將命令新增至功能表或工具列，而不需要重新執行它。

## <a name="syntax"></a>語法

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要項。 識別命令之 GUID 識別碼組的 GUID。|
|id|必要項。 識別命令之 GUID 識別碼組的識別碼。|
|條件|選擇項。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子項目

|項目|描述|
|-------------|-----------------|
|None||

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[UsedCommands 元素](../extensibility/usedcommands-element.md)|將 UsedCommand 元素和其他 UsedCommands 群組分組。|

## <a name="remarks"></a>備註
 藉由將命令新增至 `<UsedCommands>` 元素，VSPackage 會通知 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 環境，VSPackage 需要命令。 您應該為您的套件所需的任何命令新增 `<UsedCommand>` 元素，此專案可能不會包含在 Visual Studio 的所有版本和設定中。 例如，如果您的套件呼叫視覺效果C++特有的命令，則 Visual Web Developer 的使用者將無法使用此命令，除非您包含命令的 `<UsedCommand>` 元素。

## <a name="example"></a>範例

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>請參閱
- [UsedCommands 元素](../extensibility/usedcommands-element.md)
- [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)