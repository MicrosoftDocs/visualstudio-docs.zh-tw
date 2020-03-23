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
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e69e5c8fc7404c0c313774271fd07b6315e5270
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633365"
---
# <a name="msbuild-conditions"></a>MSBuild 條件

MSBuild 支援一組特定的條件，可在允許的屬性`Condition`的任何位置應用。 下表說明這些條件。

|條件|描述|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|如果 `stringA` 等於 `stringB`，即會評估為 `true`。<br /><br /> 例如：<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> 不需要以單引號括住簡單的英數字元字串或布林值。 不過，需要使用單引號括住空白值。|
|'`stringA`' != '`stringB`'|如果 `stringA` 不等於 `stringB`，即會評估為 `true`。<br /><br /> 例如：<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> 不需要以單引號括住簡單的英數字元字串或布林值。 不過，需要使用單引號括住空白值。|
|\<, >, \<=, >=|評估運算元的數值。 如果關聯式評估為 true，即會傳回 `true`。 運算元必須評估為十進位或十六進位數字。 十六進位數字必須以 "0x" 開頭。 **注意︰** 在 XML 中，必須逸出字元 `<` 和 `>`。 符號 `<` 是以 `&lt;` 表示。 符號 `>` 是以 `&gt;` 表示。|
|Exists('`stringA`')|如果有名稱為 `stringA` 的檔案或資料夾存在，即會評估為 `true`。<br /><br /> 例如：<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> 不需要以單引號括住簡單的英數字元字串或布林值。 不過，需要使用單引號括住空白值。|
|HasTrailingSlash ('`stringA`')|如果指定的字串包含尾端反斜線 (\\) 或斜線 (/) 字元，即會評估為 `true`。<br /><br /> 例如：<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> 不需要以單引號括住簡單的英數字元字串或布林值。 不過，需要使用單引號括住空白值。|
|!|如果運算元評估為 `false`，即會評估為 `true`。|
|And|如果這兩個運算元都評估為 `true`，即會評估為 `true`。|
|Or|如果至少有一個運算元評估為 `true`，即會評估為 `true`。|
|()|如果內部包含的運算式評估為 `true`，即會評估為 `true` 的群組機制。|
|$if$ ( %expression% )、$else$、$endif$|檢查指定的 `%expression%` 是否符合所傳遞自訂範本參數的字串值。 如果 `$if$` 條件評估為 `true`，即會執行它的陳述式，否則會檢查 `$else$` 條件。 如果 `$else$` 條件為`true`，即會執行它的陳述式，否則 `$endif$` 條件會結束運算式評估。<br /><br /> 有關使用的示例，請參閱[視覺化工作室專案/專案範本參數邏輯](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic)。|

## <a name="see-also"></a>另請參閱

- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [條件構造](../msbuild/msbuild-conditional-constructs.md)
- [演練：從頭開始創建 MSBuild 專案檔案](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
