---
title: "使用 Visual Studio R 工具編輯程式碼 | Microsoft Docs"
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: data-science
ms.openlocfilehash: 013c32cb1567b3a4830a5c63059b14ea23df5427
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="editing-r-code-in-visual-studio"></a>在 Visual Studio 中編輯 R 程式碼

Visual Studio R 工具 (RTVS) 可針對 R 量身打造 Visual Studio 編輯體驗，同時保留所有功能和使用延伸模組的能力。 (例如，如果您偏好 VIM 按鍵繫結，您可以從 Visual Studio 組件庫安裝免費的 [VsVim 延伸模組](https://visualstudiogallery.msdn.microsoft.com/59ca71b3-a4a3-46ca-8fe1-0e90e3f79329)。)

本主題內容：

- [語法醒目提示](#syntax-highlighting)
- [編輯及組織程式碼](#editing-and-organizing-code)
- [程式碼巡覽](#code-navigation)
- [將程式碼傳送至互動式視窗](#sending-code-to-the-interactive-window)
- [格式化程式碼](#formatting-code)
- [插入 Roxygen 註解](#inserting-roxygen-comments)
- [編輯器選項](#editor-options)

另請參閱 [IntelliSense](code-intellisense.md)、[Linting](code-linting.md)、[程式碼片段](code-snippets.md)和 [R Markdown](rmarkdown.md) 的主題。

## <a name="syntax-highlighting"></a>語法醒目提示

除了將程式碼的不同部分，例如字串、註解和關鍵字等著色，RTVS 也會醒目提示並啟用註解中的連結︰

![R 程式碼的語法著色](media/editing-syntax-colors.png)

若要自訂字型和某些醒目提示色彩，請選取 [工具] > [選項] 命令、巡覽至 [環境] > [字型和色彩]，然後變更 [顯示項目︰] 方塊中的 R 相關項目設定︰

![R 程式碼的字型和色彩選項](media/editing-syntax-colors-options.png)

Visual Studio 也會在編輯器中的語法錯誤加上底線︰

![R 程式碼中的語法錯誤醒目提示](media/editing-syntax-error.png)

若要變更此行為，請參閱[編輯器選項](#editor-options)下的 [進階] > [語法檢查] 設定。

## <a name="editing-and-organizing-code"></a>編輯及組織程式碼

在您輸入程式碼時，RTVS 提供自動完成，如 [IntelliSense](code-intellisense.md) 頁面上所述。 它也會自動設定格式，例如大括弧和括弧的完成︰ 

![內嵌格式化的動畫](media/editing-inline-formatting.gif)

輸入有許多參數的函式呼叫時，您經常會想要對齊參數，讓程式碼更容易閱讀。 RTVS 會記住您為參數設定的縮排，並針對接下來的數行自動套用該縮排︰

![自動縮排的動畫](media/editing-auto-indentation.gif)

若要變更此行為，請參閱 [定位點] 群組的[編輯器選項](#editor-options)。

可摺疊程式碼區域可讓您在編輯器中暫時隱藏程式碼的一部分。 Visual Studio 會為您自動建立不同的多行陳述式區域，除非 [進階] > [大綱] > [程式碼大綱] 選項設定為 Off。

若要建立自己的區域，請將想要的程式碼圍上以 `---` 為結尾的註解。 程式碼左邊的小型 +/- 控制項，可讓您展開和摺疊區域︰

![使用註解建立可摺疊區域](media/editing-collapsible-regions.gif)

根據預設，Visual Studio 會在您按 Tab 鍵時插入空格。 您可以再次變更此行為，如[選項、文字編輯器、定位點](../ide/reference/options-text-editor-all-languages.md)所述。

## <a name="code-navigation"></a>程式碼巡覽

程式碼巡覽可讓您快速存取 R 程式和其程式庫的原始程式碼。 這些功能會讓您停留在工作流程中，不必以手動方式搜尋程式碼。

[移至定義] 會快速跳至函式定義，或彈出內嵌迷你編輯器來讀取程式庫函式的原始程式碼。 只要以滑鼠右鍵按一下感興趣的函式，然後選取 [移至定義]，或將游標放在函式中，並按 F12 鍵。

此命令會開啟新的編輯器視窗，包含此函式的原始程式碼。 資料指標為方便您將會位於函式定義的開頭。

從快顯功能表或 Alt + F12 叫用的 [查看定義]，會插入唯讀、可捲動區域，其中在函式呼叫下包含函式的原始程式碼︰

![查看定義的動畫](media/editing-peek-definition.gif)

## <a name="sending-code-to-the-interactive-window"></a>將程式碼傳送至互動式視窗

許多開發人員喜歡在編輯器中撰寫程式碼，然後將該程式碼傳送到[互動式視窗](interactive-repl.md)來立即測試 (也稱為讀取-評估-列印-重複，或稱 REPL)。 在 R 編輯器中按 Ctrl+Enter 鍵會將目前這一行程式碼傳送到互動式視窗，並將資料指標放在下一行。 使用 Ctrl + Enter 鍵，您便可以實際上從編輯器逐步執行程式碼。

您也可以選取程式碼，然後按 Ctrl + Enter 鍵，套用整個選取範圍。 或者，以滑鼠右鍵按一下選取範圍，然後選取 [以互動方式執行]。

## <a name="formatting-code"></a>格式化程式碼

Visual Studio 的自動格式化會讓您撰寫的程式碼以及您貼到編輯器中的程式碼，保持為您的喜好設定所設的格式。 您也可以進行選取、按一下滑鼠右鍵，然後選取 [格式化選取範圍](Ctrl + K、F)，以套用這些喜好設定。 例如，如果您的函式定義全都在同一行︰

```R
f<-function  (a){  return(a + 1) }
```

套用格式化會將它清理為︰

```R
f <- function(a) { return(a + 1) }
```

若要重新格式化整個程式碼檔案，請選取 [編輯] > [進階] > [格式化文件]\(Ctrl+E、D)。

自動格式化是可以復原的個別作業。 例如，如果您將程式碼貼入編輯器，以及它套用的格式化，則選取 [編輯] > [復原] 或按 Ctrl+Z，會反轉格式化，第二次 [復原] 則會反轉貼上作業本身。

格式化選項 (包括關閉格式化) 是透過 [文字編輯器] > [R] > [進階] 索引標籤的 [工具] > [選項] 設定。您可以使用 [R 工具] > [編輯器選項] 命令，或在編輯器中按一下滑鼠右鍵，然後選取 [格式選項]，直接移至此頁面。如需詳細資訊，請參閱[編輯器選項](#editor-options)一節。

## <a name="inserting-roxygen-comments"></a>插入 Roxygen 註解

RTVS 提供使用函式參數名稱產生 [Roxygen](http://roxygen.org/) 註解的捷徑。 只要在函式定義上方的空白行上輸入 `###`︰

![插入 Roxygen 註解的動畫](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>編輯器選項

編輯器特有的選項設定方法透過 [工具] > [選項] 命令、巡覽至 [文字編輯器] > [R]，或使用捷徑命令 [R 工具] > [編輯器選項]。

[一般]、[捲軸] 和 [定位點] 索引標籤上的選項並不專屬於 R，而是一般的 Visual Studio 設定，適用於任何語言，但會以每個語言為基礎套用。 如需詳細資料，請參閱下列主題︰

- [所有語言、文字編輯器、選項](../ide/reference/options-text-editor-all-languages.md)
- [自訂捲軸以追蹤程式碼](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [選項、文字編輯器、定位點](../ide/reference/options-text-editor-all-languages-tabs.md)

[R] > [進階] 索引標籤上的選項為專屬於 RTVS:

| 群組 | 選項 | 預設 | 描述 |
| --- | --- | --- | --- |
| 格式化 | 自動格式化 | 開啟 | 會在您鍵入時重新格式化程式碼。 不會影響 [格式化選取範圍] 或 [格式化文件] 命令。 |
| | 展開的大括弧 | Off | 在新的一行放置開始的 {。 |
| | 於貼上時格式化 | 開啟 | 於貼上時套用格式化。 |
| | } 時將範圍格式化 | 開啟 | 在鍵入右大括弧後將範圍格式化。 |
| | 逗號之後的空格 | 開啟 | 在逗號之後放置空格。 |
| | 關鍵字之後的空格 | 開啟 | 在 `if`、`while` 和 `repeat` 等關鍵字之後放置空格。 |
| | { 之前的空格 | 開啟 | 在左大括弧之前放置空格。 |
| | = 前後的空格 | 開啟 | 在等號前後放置空格。 |
| IntelliSense | 使用 Enter 鍵認可 | Off | 按下 Enter 鍵時認可自動完成選取範圍。 |
| | 使用空格鍵認可 | Off | 按下空格鍵時認可自動完成選取範圍。|
| | 第一個字元即出現自動完成清單 | 開啟 | 在鍵入第一個字元時顯示自動完成清單。 關閉時，在按一下 [編輯] > [IntelliSense] > [列出成員] (Ctrl + J) 時會顯示完成清單。 |
| | 按 Tab 鍵時會出現自動完成清單 | Off | 鍵入一或多個字元並按 Tab 鍵來叫用完成清單。 |
| | 符合部分鍵入的引數名稱 | Off | 在函式呼叫中鍵入引數名稱時，特徵標記可協助顯示最貼切的引數描述。 |
| 互動式視窗 | R Console 中的語法檢查 | Off | 在 Interactive 視窗中套用語法檢查。 語法檢查可能無法正確運作於多行陳述式。 | 
| 大綱 | 程式碼大綱 | 開啟 | 自動為多行陳述式等區域建立可摺疊區域。 |
| 語法檢查 | 顯示語法錯誤 | 開啟 | 啟用程式碼的自動語法檢查。 |
