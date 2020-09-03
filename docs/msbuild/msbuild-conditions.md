---
title: MSBuild 條件 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
- Exists, MSBuild condition function
- HasTrailingSlash, MSBuild condition function
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5994e3f5b17f50d707c4c5a00666d60c2efd3184
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "88711699"
---
# <a name="msbuild-conditions"></a>MSBuild 條件

MSBuild 支援一組特定的條件，可在允許屬性的任何地方套用 `Condition` 。 下表說明這些條件。

|條件|描述|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|如果 `stringA` 等於 `stringB`，即會評估為 `true`。<br /><br /> 例如：<br /><br /> `Condition="'$(Configuration)'=='DEBUG'"`<br /><br /> 不需要以單引號括住簡單的英數字元字串或布林值。 不過，需要使用單引號括住空白值。 這項檢查不區分大小寫。|
|'`stringA`' != '`stringB`'|如果 `stringA` 不等於 `stringB`，即會評估為 `true`。<br /><br /> 例如：<br /><br /> `Condition="'$(Configuration)'!='DEBUG'"`<br /><br /> 不需要以單引號括住簡單的英數字元字串或布林值。 不過，需要使用單引號括住空白值。 這項檢查不區分大小寫。|
|\<, >, \<=, >=|評估運算元的數值。 如果關聯式評估為 true，即會傳回 `true`。 運算元必須評估為十進位或十六進位數字。 十六進位數字必須以 "0x" 開頭。 **注意︰** 在 XML 中，必須逸出字元 `<` 和 `>`。 符號 `<` 是以 `&lt;` 表示。 符號 `>` 是以 `&gt;` 表示。|
|Exists('`stringA`')|如果有名稱為 `stringA` 的檔案或資料夾存在，即會評估為 `true`。<br /><br /> 例如：<br /><br /> `Condition="!Exists('$(Folder)')"`<br /><br /> 不需要以單引號括住簡單的英數字元字串或布林值。 不過，需要使用單引號括住空白值。|
|HasTrailingSlash ('`stringA`')|如果指定的字串包含尾端反斜線 (\\) 或斜線 (/) 字元，即會評估為 `true`。<br /><br /> 例如：<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> 不需要以單引號括住簡單的英數字元字串或布林值。 不過，需要使用單引號括住空白值。|
|!|如果運算元評估為 `false`，即會評估為 `true`。|
|`And`|如果這兩個運算元都評估為 `true`，即會評估為 `true`。|
|`Or`|如果至少有一個運算元評估為 `true`，即會評估為 `true`。|
|()|如果內部包含的運算式評估為 `true`，即會評估為 `true` 的群組機制。|
|$if$ ( %expression% )、$else$、$endif$|檢查指定的 `%expression%` 是否符合所傳遞自訂範本參數的字串值。 如果 `$if$` 條件評估為 `true`，即會執行它的陳述式，否則會檢查 `$else$` 條件。 如果 `$else$` 條件為`true`，即會執行它的陳述式，否則 `$endif$` 條件會結束運算式評估。<br /><br /> 如需使用方式的範例，請參閱 [Visual Studio 專案/專案範本參數邏輯](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic)。|

您可以在條件中使用字串方法，如下列範例所示，其中 [TrimEnd ( # B1 ](/dotnet/api/system.string.trimend) 函數只會用來比較字串的相關部分，以區分 .NET FRAMEWORK 和 .net Core 目標 framework。

```xml
<Project Sdk="Microsoft.NET.Sdk">

    <PropertyGroup>
        <TargetFrameworks>net45;net48;netstandard2.1;netcoreapp2.1;netcoreapp3.1</TargetFrameworks>
    </PropertyGroup>

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd(`0123456789`))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

在 MSBuild 專案檔中，沒有真正的布林類型。 布林值資料會以可能是空的或設為任何值的屬性來表示。 因此，表示「如果是，則」表示「如果 `'$(Prop)' == 'true'` `true` `'$(Prop)' != 'false'` 是，或取消 `true` 設定或設定為其他東西」。

布林邏輯只會在條件的內容中進行評估，因此的屬性設定 `<Prop2>'$(Prop1)' == 'true'</Prop>` 會以字串表示， (在變數展開) 之後，而不會評估為布林值。  

MSBuild 會執行一些特殊的處理規則，讓您更輕鬆地使用做為布林值的字串屬性。 布林常值會被接受，因此 `Condition="true"` 並 `Condition="false"` 如預期般運作。 MSBuild 也包含支援布林值負運算子的特殊規則。 因此，如果 `$(Prop)` 是 ' true '，則會將 `!$(Prop)` 展開為， `!true` 而且這 `false` 會與您預期的相等比較。

## <a name="see-also"></a>另請參閱

- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [條件式結構](../msbuild/msbuild-conditional-constructs.md)
- [逐步解說：從頭開始建立 MSBuild 專案檔](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
