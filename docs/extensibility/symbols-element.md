---
title: 符號元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce299f99699a7bc048b3dc7da39aea3f734addeb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719406"
---
# <a name="symbols-element"></a>Symbols 項目
定義其他 .VSCT 元素所使用的 Guid 和識別碼。 若是非受控程式碼，這項資訊通常來自[Extern 元素](../extensibility/extern-element.md)所指定的標頭檔。 Managed 程式碼會使用符號元素的子項目來定義這項資訊。

 如果您從現有的 cto 檔案建立 .vsct 檔案，則會產生符號做為符號元素的子系。 如需詳細資訊，請參閱[如何：建立。從現有的 .vsct 檔案。Cto](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)檔案。

 符號元素不應該與[定義元素](../extensibility/define-element.md)混淆，這會定義預處理器所使用的名稱/值配對。

## <a name="syntax"></a>語法

```
<Symbols>
  <GuidSymbol>... </GuidSymbol>
  <GuidSymbol>... </GuidSymbol>
</Symbols>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|None||

### <a name="child-elements"></a>子項目

|項目|描述|
|-------------|-----------------|
|GuidSymbol|定義 GUID 符號。 GuidSymbol 有兩個必要的屬性： name 和 value。 名稱是符號的名稱，而值則是 GUID 的值做為字串。<br /><br /> 例如： \<GuidSymbol name = "guidVsPackage1Pkg" value = "{c5f54698-101a-4846-84d3-dc748f9cd848}"/>|
|IDSymbol|定義符號。 IDSymbol 有兩個必要的屬性： name 和 value。 名稱是符號的名稱，而值是符號的值做為字串。<br /><br /> 例如： \<IDSymbol name = "MyMenuGroup" value = "0x1020"/>|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|.Vsct 檔案的根項目。|

## <a name="example"></a>範例

```
<Symbols>
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
    <IDSymbol name="cmdidMyTool" value="0x0101" />
  </GuidSymbol>
</Symbols>
```

## <a name="see-also"></a>請參閱
- [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)