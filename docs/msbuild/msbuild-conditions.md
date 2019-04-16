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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb0f29224bb87611f010421dd372832f2a014d7e
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59366480"
---
# <a name="msbuild-conditions"></a>MSBuild 條件
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 支援一組只要允許 `Condition` 屬性就能套用的特定條件。 下表說明這些條件。

|條件|說明|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|如果 `stringA` 等於 `stringB`，即會評估為 `true`。<br /><br /> 例如：<br /><br /> `Condition="$(CONFIG)=='DEBUG'"`<br /><br /> 不需要以單引號括住簡單的英數字元字串或布林值。 不過，需要使用單引號括住空白值。|
|'`stringA`' != '`stringB`'|如果 `stringA` 不等於 `stringB`，即會評估為 `true`。<br /><br /> 例如：<br /><br /> `Condition="$(CONFIG)!='DEBUG'"`<br /><br /> 不需要以單引號括住簡單的英數字元字串或布林值。 不過，需要使用單引號括住空白值。|
|\<、>、\<=、>=|評估運算元的數值。 如果關聯式評估為 true，即會傳回 `true`。 運算元必須評估為十進位或十六進位數字。 十六進位數字必須以 "0x" 開頭。 **注意：** 在 XML 中，必須逸出字元 `<` 和 `>`。 符號 `<` 是以 `&lt;` 表示。 符號 `>` 是以 `&gt;` 表示。|
|Exists('`stringA`')|如果有名稱為 `stringA` 的檔案或資料夾存在，即會評估為 `true`。<br /><br /> 例如：<br /><br /> `Condition="!Exists($(builtdir))"`<br /><br /> 不需要以單引號括住簡單的英數字元字串或布林值。 不過，需要使用單引號括住空白值。|
|HasTrailingSlash ('`stringA`')|如果指定的字串包含尾端反斜線 (\\) 或斜線 (/) 字元，即會評估為 `true`。<br /><br /> 例如：<br /><br /> `Condition="!HasTrailingSlash($(OutputPath))"`<br /><br /> 不需要以單引號括住簡單的英數字元字串或布林值。 不過，需要使用單引號括住空白值。|
|!|如果運算元評估為 `false`，即會評估為 `true`。|
|及|如果這兩個運算元都評估為 `true`，即會評估為 `true`。|
|或|如果至少有一個運算元評估為 `true`，即會評估為 `true`。|
|()|如果內部包含的運算式評估為 `true`，即會評估為 `true` 的群組機制。|
|$if$ ( %expression% )、$else$、$endif$|檢查指定的 `%expression%` 是否符合所傳遞自訂範本參數的字串值。 如果 `$if$` 條件評估為 `true`，即會執行它的陳述式，否則會檢查 `$else$` 條件。 如果 `$else$` 條件為`true`，即會執行它的陳述式，否則 `$endif$` 條件會結束運算式評估。<br /><br /> 如需使用方式的範例，請參閱 [Visual Studio project/item template parameter logic](http://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic) (Visual Studio 專案/項目範本參數邏輯)。|

## <a name="see-also"></a>另請參閱
- [MSBuild 參考](../msbuild/msbuild-reference.md)
- [條件式建構](../msbuild/msbuild-conditional-constructs.md)
- [逐步解說：從頭開始建立 MSBuild 專案檔](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
