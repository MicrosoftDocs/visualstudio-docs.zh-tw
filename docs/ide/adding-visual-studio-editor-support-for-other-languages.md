---
title: 新增其他語言的編輯器支援
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax colorization
- IntelliSense
- IDE, navigation
- documents [Visual Studio], navigation
- TextMate bundle
- TextMate language grammar
- language support
ms.assetid: d78c43ee-4ef2-42e5-984e-d137de4e7e92
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ae0b2f606b4fe04ad390712f48ac1e06ff9bb86
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "65805333"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>新增其他語言的 Visual Studio 編輯器支援

了解 Visual Studio 編輯器如何支援讀取，並在不同的電腦語言之間巡覽，以及如何新增其他語言的 Visual Studio 編輯器支援。

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>語法顏色標示、陳述式完成和「巡覽至」支援

Visual Studio 編輯器中的語法顏色標示、陳述式完成 (也稱為 IntelliSense) 和「巡覽至」等功能，可協助您更輕鬆地撰寫、閱讀和編輯您的程式碼。 下列螢幕擷取畫面顯示在 Visual Studio 中編輯 Perl 指令碼的範例。 語法會自動以色彩標示。 比方說，程式碼中的註解會標示為綠色、程式碼為黑色、路徑為是紅色，陳述式則為藍色。 Visual Studio 編輯器會自動將語法顏色標示套用至任何支援的語言。 此外，當您開始輸入已知的語言關鍵字或物件時，陳述式完成就會顯示可能陳述式和物件的清單。 陳述式完成可協助您更快速且輕鬆地撰寫程式碼。

![Perl 指令碼中的語法顏色標示](../ide/media/vside_perledit.png)

Visual Studio 目前使用 [TextMate 文法](https://manual.macromates.com/en/language_grammars)，提供下列語言版本之語法顏色標示和基本陳述式完成的支援。 不過，如果您偏好的語言不在資料表中，不用擔心&mdash;您可以新增它。

|||||||
|-|-|-|-|-|-|
|Bat|F#|Java|Markdown|Rust|Visual Basic|
|Clojure|移至|JavaDoc|Objective-C|ShaderLab|C#|
|CMake|Groovy|JSON|Perl|ShellScript|Visual C++|
|CoffeeScript|HTML|LESS|Python|SQL|VBNet|
|CSS|INI|LUA|R|Swift|XML|
|Docker|Jade|品牌|Ruby|TypeScript|YAML|

除了語法顏色標示和基本陳述式完成之外，Visual Studio 也有一項稱為 [「巡覽至」](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/)的功能。 這項功能可讓您快速搜尋程式碼檔案、檔案路徑和程式碼符號。 Visual Studio 提供下列語言版本的「巡覽至」支援。

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- 移至

- Java

- PHP

這些檔案類型全都有稍早描述的功能，即使尚未安裝指定語言的支援亦然。 安裝某些語言的特殊支援，也可能提供其他語言支援，例如 IntelliSense 或燈泡這樣的其他進階語言功能。

## <a name="add-support-for-non-supported-languages"></a>為不支援的語言新增支援

Visual Studio 藉由使用 [TextMate 文法](https://manual.macromates.com/en/language_grammars) \(英文\)，在編輯器中提供語言支援。 如果您慣用的程式設計語言目前在 Visual Studio 編輯器中不受支援，則請先搜尋網頁 &mdash; 該語言的 TextMate 組合可能已經存在。 不過，如果找不到，您可以在 Visual Studio 中，藉由為語言文法及程式碼片段建立 TextMate 組合模型，自行為它新增支援。

在下列資料夾中，為 Visual Studio 新增任何新的 TextMate 文法︰

*%userprofile%\\.vs\Extensions*

如果適用於您的情況，在此基底路徑下，新增下列資料夾︰

|資料夾名稱|說明|
|-----------------|-----------------|
|\\\<語言名稱>|語言資料夾。 將 \<語言名稱> 取代為語言的名稱。 例如 *\Matlab*。|
|*\Syntaxes*|文法資料夾。 包含語言的文法 *.json* 檔案，例如 *Matlab.json*。|
|*\Snippets*|程式碼片段資料夾。 包含語言的程式碼片段。|

在 Windows 中，會將 *%userprofile%* 解析為 *c:\Users\\\<使用者名稱>* 路徑。 如果您的系統上的 [Extensions] 資料夾不存在，您必須建立它。 如果資料夾已存在，它會隱藏。

> [!TIP]
> 如果您在編輯器中有檔案，您將需要關閉它們再重新開啟，以在您新增 TextMate 文法之後查看語法醒目提示。

如需如何建立 TextMate 文法的詳細資料，請參閱 [TextMate - 語言文法簡介](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) \(英文\) 和[如何為 Textmate 組合建立語言文法及自訂佈景主題的筆記](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle) \(英文\)。

## <a name="see-also"></a>另請參閱

- [新增語言伺服器通訊協定延伸模組](../extensibility/adding-an-lsp-extension.md)
- [逐步解說：建立程式碼片段](../ide/walkthrough-creating-a-code-snippet.md)
- [逐步解說：顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)
