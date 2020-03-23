---
title: 編輯 R 程式碼
description: Visual Studio 提供針對 R 量身打造的編輯體驗，同時保留所有功能和使用延伸模組的能力。
ms.date: 11/05/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7ecfd8f1cf50e94991ce2fd94ad94ac9815c92ca
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302711"
---
# <a name="edit-r-code-in-visual-studio"></a>在 Visual Studio 中編輯 R 程式碼

Visual Studio R 工具 (RTVS) 可針對 R 量身打造 Visual Studio 編輯體驗，同時保留所有功能和使用延伸模組的能力。 (例如，如果您偏好 VIM 按鍵繫結，您可以從 Visual Studio Marketplace 安裝免費的 [VsVim 延伸模組](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)。)

除了本文中的功能之外，另請參閱 [IntelliSense](r-intellisense.md)、[Linting](linting-r-code.md)、[程式碼片段](code-snippets-for-r.md)，和[R Markdown](rmarkdown-with-r-in-visual-studio.md)。

## <a name="syntax-highlighting"></a>語法醒目提示

除了將程式碼的不同部分，例如字串、註解和關鍵字等著色，RTVS 也會醒目提示並啟用註解中的連結︰

![R 程式碼的語法著色](media/editing-syntax-colors.png)

要自訂字體和某些突出顯示顏色，請選擇 **"工具** > **選項"** 命令，導航**到環境** > **字體和顏色**，然後在 **"顯示專案"** 框中更改 R 相關專案的設置：

![R 程式碼的字型和色彩選項](media/editing-syntax-colors-options.png)

Visual Studio 也會在編輯器中的語法錯誤加上底線︰

![R 程式碼中的語法錯誤醒目提示](media/editing-syntax-error.png)

要更改此行為，請參閱[編輯器選項](#editor-options)下的 **"高級** > **語法"檢查**設置。

## <a name="edit-and-organize-code"></a>編輯及組織程式碼

在您輸入程式碼時，RTVS 提供自動完成，如 [IntelliSense](r-intellisense.md) 頁面上所述。 它也會自動設定格式，例如大括弧和括弧的完成︰

![內嵌格式化的動畫](media/editing-inline-formatting.gif)

輸入有許多參數的函式呼叫時，您經常會想要對齊參數，讓程式碼更容易閱讀。 RTVS 會記住您為參數設定的縮排，並針對接下來的數行自動套用該縮排︰

![自動縮排的動畫](media/editing-auto-indentation.gif)

若要變更此行為，請參閱 [定位點]**** 群組的[編輯器選項](#editor-options)。

可摺疊程式碼區域可讓您在編輯器中暫時隱藏程式碼的一部分。 Visual Studio 會自動為您創建各種區域，如多行語句，除非 **"高級** > **大綱** > **代碼"大綱**選項設置為"關閉"。

若要建立自己的區域，請將想要的程式碼圍上以 `---` 為結尾的註解。 程式碼左邊的小型 +/- 控制項，可讓您展開和摺疊區域︰

![使用註解建立可摺疊區域](media/editing-collapsible-regions.gif)

預設情況下，當您按下**Tab**鍵時，Visual Studio 會插入空格。 您可以再次變更此行為，如[選項、文字編輯器、定位點](../ide/reference/options-text-editor-all-languages.md)所述。

## <a name="code-navigation"></a>程式碼巡覽

程式碼巡覽可讓您快速存取 R 程式和其程式庫的原始程式碼。 這些功能會讓您停留在工作流程中，不必以手動方式搜尋程式碼。

[移至定義]**** 會快速跳至函式定義，或彈出內嵌迷你編輯器來讀取程式庫函式的原始程式碼。 恰到好處按一下感興趣的函數並選擇 **"轉到定義**"，或將游標放在函數中，然後按**F12**。

此命令會開啟新的編輯器視窗，包含此函式的原始程式碼。 資料指標為方便您將會位於函式定義的開頭。

**從**按右鍵功能表或**Alt**+**F12**調用的 Peek 定義插入一個唯讀、可滾動的區域，其中包含函式呼叫下方函數的原始程式碼：

![查看定義的動畫](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>將程式碼傳送至互動式視窗

許多開發人員喜歡在編輯器中撰寫程式碼，然後將該程式碼傳送到[互動式視窗](interactive-repl-for-r-in-visual-studio.md)來立即測試 (也稱為讀取-評估-列印-重複，或稱 REPL)。 按 R 編輯器中的**Ctrl**+**Enter**將當前程式碼發送到互動式視窗，然後將游標放在下一行上。 使用**Ctrl**+**Enter**，然後，您可以有效地從編輯器中單一步驟代碼。

您還可以選擇代碼並按**Ctrl**+**Enter**以應用整個選擇。 或者，以滑鼠右鍵按一下選取範圍，然後選取 [以互動方式執行]****。

## <a name="format-code"></a>格式化程式碼

Visual Studio 的自動格式化會讓您撰寫的程式碼以及您貼到編輯器中的程式碼，保持為您的喜好設定所設的格式。 您還可以進行選擇、按右鍵和選擇 **"格式選擇**"（Ctrl**Ctrl**+**K****、F）** 以應用這些首選項。 例如，如果您的函式定義全都在同一行︰

```R
f<-function  (a){  return(a + 1) }
```

套用格式化會將它清理為︰

```R
f <- function(a) { return(a + 1) }
```

要重新格式化整個代碼檔，請選擇 **"編輯** > **高級** > **格式文檔**"（Ctrl**Ctrl**+**E**，**D**）。

自動格式化是可以復原的個別作業。 例如，如果將代碼粘貼到編輯器中並應用其格式，則選擇 **"編輯** > **撤銷"** 或按 Ctrl Z，一旦反轉格式;如果將代碼粘貼到編輯器中，則選擇"編輯撤銷"或按**Ctrl**+**Z。** 第二次**撤銷**將反轉粘貼本身。

 > 通過**文字編輯器****R**R > **高級**選項卡**上的"工具** > **選項**"設置格式選項（包括關閉格式）。您可以使用**R Tools** > **編輯器選項**命令或按右鍵編輯器並選擇 **"格式化"選項**直接轉到此頁面。 如需詳細資訊，請參閱[編輯器選項](#editor-options)一節。

## <a name="inserting-roxygen-comments"></a>插入 Roxygen 註解

RTVS 提供使用函式參數名稱產生 [Roxygen](https://cran.r-project.org/web/packages/roxygen2/index.html) 註解的捷徑。 只要在函式定義上方的空白行上輸入 `###`︰

![插入 Roxygen 註解的動畫](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>編輯器選項

特定于編輯器的選項通過 **"工具** > **選項"** 命令設置，導航到**文字編輯器** > **R**，或使用快捷方式命令**R Tools** > **編輯器選項**。

[一般]****、[捲軸]**** 和 [定位點]**** 索引標籤上的選項並不專屬於 R，而是一般的 Visual Studio 設定，適用於任何語言，但會以每個語言為基礎套用。 如需詳細資料，請參閱下文：

- [所有語言、文字編輯器、選項](../ide/reference/options-text-editor-all-languages.md)
- [自訂捲軸以追蹤程式碼](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [選項、文字編輯器、定位點](../ide/reference/options-text-editor-all-languages-tabs.md)

**R** > **高級**選項卡上的選項特定于 RTVS：

| 群組 | 選項 | 預設 | 描述 |
| --- | --- | --- | --- |
| 格式化 | 自動格式化 | 另一 | 會在您鍵入時重新格式化程式碼。 不會影響 [格式化選取範圍]**** 或 [格式化文件]**** 命令。 |
| | 展開的大括弧 | 關閉 | 在新的一行放置開始的 {。 |
| | 於貼上時格式化 | 另一 | 於貼上時套用格式化。 |
| | } 時將範圍格式化 | 另一 | 在鍵入右大括弧後將範圍格式化。 |
| | 逗號之後的空格 | 另一 | 在逗號之後放置空格。 |
| | 關鍵字之後的空格 | 另一 | 在 `if`、`while` 和 `repeat` 等關鍵字之後放置空格。 |
| | { 之前的空格 | 另一 | 在左大括弧之前放置空格。 |
| | = 前後的空格 | 另一 | 在等號前後放置空格。 |
| IntelliSense | 使用 Enter 鍵認可 | 關閉 | 按下**Enter**時提交自動完成選擇。 |
| | 使用空格鍵認可 | 關閉 | 按下 **"空間**"時提交自動完成選擇。|
| | 第一個字元即出現自動完成清單 | 另一 | 在鍵入第一個字元時顯示自動完成清單。 關閉時，將顯示一個完成清單，其中顯示 **"編輯** > **感知清單** > **成員**"（Ctrl**Ctrl**+**J**）。 |
| | **選項卡**鍵上的完成清單 | 關閉 | 通過鍵入一個或多個字元並按**Tab**調用完成清單。 |
| | 符合部分鍵入的引數名稱 | 關閉 | 在函式呼叫中鍵入引數名稱時，特徵標記可協助顯示最貼切的引數描述。 |
| 互動式視窗 | R Console 中的語法檢查 | 關閉 | 在 Interactive 視窗中套用語法檢查。 語法檢查可能無法正確運作於多行陳述式。 |
| 大綱 | 程式碼大綱 | 另一 | 自動為多行陳述式等區域建立可摺疊區域。 |
| 語法檢查 | 顯示語法錯誤 | 另一 | 啟用程式碼的自動語法檢查。 |
