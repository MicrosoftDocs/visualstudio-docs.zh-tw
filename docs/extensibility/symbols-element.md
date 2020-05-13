---
title: 符號元素 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699354"
---
# <a name="symbols-element"></a>Symbols 項目
定義其他 VSCT 元素使用的 GUID 和 I。 對於非託管代碼,此資訊通常來自[Extern 元素](../extensibility/extern-element.md)指定的標頭檔。 託管代碼使用 Symbols 元素的子元素來定義此資訊。

 如果從現有的 .cto 檔案建立 .vsct 檔案,則符號將作為 Symbol 元素的子級生成。 有關詳細資訊,請參閱[如何:創建 。來自現有的 Vct 檔。Cto 檔案](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)。

 符號元素不應與[定義元素](../extensibility/define-element.md)混淆,該元素定義名稱值對供預處理器使用。

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
|None||

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|吉德符號|定義 GUID 符號。 GuidSymbol 有兩個必需的屬性:名稱和值。 名稱是符號的名稱,該值是 GUID 作為字串的值。<br /><br /> 例如:GuidSymbol\<名稱="guidV 包裝1Pkg"值="{c5f54698-101a-4846-84d3-dc748f9cd848}"/>|
|ID符號|定義符號。 IDSymbol 具有兩個必需的屬性:名稱和值。 名稱是符號的名稱,值是符號作為字串的值。<br /><br /> 例如:IDSymbol\<名稱="MyMenuGroup"值="0x1020"/>|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[CommandTable 元素](../extensibility/commandtable-element.md)|.vsct 檔案的根元素。|

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
