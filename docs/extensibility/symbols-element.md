---
title: 符號元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c24c3f84df23a07b6b16272b66b29e32ad7b911
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699354"
---
# <a name="symbols-element"></a>Symbols 項目
定義其他 .VSCT 元素所使用的 Guid 和識別碼。 針對非受控碼，這項資訊通常來自 [Extern 元素](../extensibility/extern-element.md)所指定的標頭檔。 Managed 程式碼會使用符號元素的子項目來定義這項資訊。

 如果您從現有的 cto 檔建立 .vsct 檔案，則會將符號產生為符號元素的子系。 如需詳細資訊，請參閱 [如何：建立。從現有的 .vsct 檔案。Cto](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)檔案。

 符號元素不應與 [定義元素](../extensibility/define-element.md)混淆，此專案會定義預處理器所使用的名稱/值組。

## <a name="syntax"></a>語法

```
<Symbols>
  <GuidSymbol>... </GuidSymbol>
  <GuidSymbol>... </GuidSymbol>
</Symbols>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|無||

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|GuidSymbol|定義 GUID 符號。 GuidSymbol 有兩個必要屬性：名稱和值。 名稱是符號的名稱，而值則是以字串形式提供的 GUID 值。<br /><br /> 例如：\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|IDSymbol|定義符號。 IDSymbol 有兩個必要屬性：名稱和值。 名稱是符號的名稱，而值則是以字串作為符號的值。<br /><br /> 例如：\<IDSymbol name="MyMenuGroup" value="0x1020" />|

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

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
