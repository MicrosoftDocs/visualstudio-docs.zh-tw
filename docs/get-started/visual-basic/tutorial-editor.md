---
title: Visual Basic 開發人員編輯簡介
description: 這個 10 分鐘的 Visual Studio 程式碼編輯器簡介，說明 Visual Studio 可讓撰寫、巡覽和了解 Visual Basic 程式碼更加輕鬆的一些方式。
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 56f6570b633941c8f7102e245b7668cd31936f83
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308359"
---
# <a name="learn-to-use-the-code-editor-with-visual-basic"></a>瞭解如何使用程式碼編輯器搭配 Visual Basic

在這段10分鐘的程式碼 Visual Studio 編輯器簡介中，我們會將程式碼新增至檔案，以查看 Visual Studio 讓撰寫、流覽和瞭解 Visual Basic 程式碼更容易的一些方式。

::: moniker range="vs-2017"

> [!TIP]
> 如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> 如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2022"

> [!TIP]
> 如果您尚未安裝 Visual Studio Preview，請前往 [Visual Studio 2022 preview 下載](https://visualstudio.microsoft.com/vs/preview/vs2022) 頁面，免費進行安裝。

::: moniker-end

本文假設您已熟悉 Visual Basic。 如果您不熟悉，建議您先瀏覽教學課程 (例如 [Visual Studio 中的 Visual Basic 使用者入門](../../get-started/visual-basic/tutorial-console.md))。

> [!TIP]
> 若要繼續遵循這篇文章，請確定您已為 Visual Studio 選取 Visual Basic 設定。 如需選取整合式開發環境 (IDE) 的設定資訊，請參閱[選取環境設定](visual-studio-ide.md#select-environment-settings)。

## <a name="create-a-new-code-file"></a>建立新的程式碼檔

從建立新檔案並在其中新增一些程式碼開始。

::: moniker range="vs-2017"

1. 開啟 Visual Studio。

::: moniker-end

::: moniker range=">=vs-2019"

1. 開啟 Visual Studio。 在開始視窗中按 **Esc** 或按一下 [不使用程式碼繼續]，以開啟開發環境。

::: moniker-end

2. 從功能表列的 [檔案] 功能表中，選擇 [新增檔案]。

3. 在 [新增檔案] 對話方塊的 [一般] 類別下，選擇 [Visual Basic 類別]，然後選擇 [開啟]。

   使用 Visual Basic 類別的基本架構，在編輯器中開啟新的檔案。 (您可能已注意到不需要建立完整的 Visual Studio 專案，即可享有程式碼編輯器提供的一些優點，例如語法醒目提示。 您只需要一個程式碼檔案！)

   ![Visual Studio 中的 Visual Basic 程式碼檔案](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>使用程式碼片段

Visual Studio 提供實用的「程式碼片段」，讓您可以用來快速且輕鬆地產生常用的程式碼區塊。 [程式碼片段](../../ide/code-snippets.md)適用於不同的程式設計語言 (包括 Visual Basic、C# 和 C++)。 請在檔案中新增 Visual Basic **Sub** 程式碼片段。

1. 將游標放在 `End Class` 行上，然後鍵入 **sub**。

   快顯對話方塊隨即出現，並內含 `Sub` 關鍵字及如何插入 **Sub** 程式碼片段的相關資訊。

   ![Visual Studio 中程式碼片段的 IntelliSense](media/tutorial-intellisense-snippet.png)

1. 按兩次 **Tab** 鍵，以插入程式碼片段。

   Sub 程序 `MySub()` 的大綱會新增至檔案。

可用的程式碼片段會因不同的程式設計語言而異。 您可以選擇 [**編輯**  >  **IntelliSense**  >  **插入程式碼片段** (]，或按 **ctrl** + **K**、 **ctrl** + **X**) ，查看 Visual Basic 的可用程式碼片段。 Visual Basic 的程式碼片段可分為下列類別：

![Visual Basic 程式碼片段清單](media/tutorial-code-snippet-list.png)

這些程式碼片段可用於判斷檔案是否存在電腦上、寫入文字檔、讀取登錄值、執行 SQL 查詢、建立 [For Each...Next 陳述式](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)等。

## <a name="comment-out-code"></a>註解化程式碼

工具列是 Visual Studio 功能表列下的按鈕列，有助您提高撰寫程式碼的效率。 例如，您可以切換 IntelliSense 完成模式、增加或減少行縮排，也可以為不要編譯的程式碼加上註解  ([IntelliSense](../../ide/using-intellisense.md) 是一種程式碼撰寫輔助工具，可顯示相符方法的清單 ) 。在本節中，我們會將某些程式碼標記為批註。

![編輯器工具列按鈕](media/tutorial-editor-toolbar.png)

1. 將下列程式碼貼入 `MySub()` 程序主體。

   ```vb
   ' _words is a string array that we'll sort alphabetically
   Dim _words = New String() {
   "the",
   "quick",
   "brown",
   "fox",
   "jumps"
   }

   Dim morewords = New String() {
   "over",
   "the",
   "lazy",
   "dog"
   }

   Dim query = From word In _words
               Order By word.Length
               Select word
   ```

1. 我們目前不會使用 `morewords` 陣列，但之後可能會用到，所以我們不想要完全將其刪除。 相反地，請將這些行註解化。 選取 `morewords` 的整個定義，直到右大括弧為止，然後選擇工具列上的 [註解選取行] 按鈕。 如果您想要使用鍵盤，請按下 **ctrl** + **K**、 **ctrl** + **C**。

   ![註解化按鈕](media/tutorial-comment-out.png)

   Visual Basic 註解字元 `'` 會新增至每個選取行的開頭，為程式碼加上註解。

## <a name="collapse-code-blocks"></a>摺疊程式碼區塊

您可以摺疊程式碼區段，只著重於您感興趣的一部分。 若要練習，請將 `_words` 陣列摺疊成一行程式碼。 選擇 `Dim _words = New String() {` 行邊緣中其內有減號的小型灰色方塊。 或者，如果您是鍵盤使用者，請將游標放在陣列定義中的任意位置，然後按 **ctrl** + **m**、 **ctrl** + **m**。

![大綱摺疊按鈕](media/tutorial-collapse.png)

程式碼區塊只會摺疊到第一行，並且後面接著省略符號 (`...`)。 若要再次展開程式碼區塊，請按一下現在具有加號的相同灰色方塊，或再次按下 **ctrl** + **m**、 **ctrl** + **m** 。 這項功能稱為「 [大綱](../../ide/outlining.md) 」，當您要折迭較長的方法或整個類別時，這項功能特別有用。

## <a name="view-symbol-definitions"></a>檢視符號定義

Visual Studio 編輯器可讓您輕鬆檢查類型、方法等的定義。其中一種方式是導覽至包含定義的檔案，例如，在參考符號的任何位置選擇 [ **移至定義** ]。 不會將焦點移離所處理檔案的較快速方式是使用[查看定義](../../ide/go-to-and-peek-definition.md#peek-definition)。 讓我們查看 `String` 類型的定義。

1. 以滑鼠右鍵按一下 `String` 一字，然後從操作功能表選擇 [查看定義]。 或者，按 **Alt** + **F12**。

   快顯視窗隨即出現，並內含 `String` 類別的定義。 您可以在快顯視窗內捲動，或甚至查看已查看程式碼中另一種類型的定義。

   ![查看定義視窗](media/tutorial-peek-definition.png)

1. 選擇快顯視窗右上方含 "x" 的小型方塊，以關閉查看的定義視窗。

## <a name="use-intellisense-to-complete-words"></a>使用 IntelliSense 自動完成文字

[IntelliSense](../../ide/using-intellisense.md) 是您撰寫程式碼時的重要資源。 它可以顯示類型可用成員的相關資訊，或方法之不同多載的參數詳細資料。 在您鍵入足夠的字元來釐清文字之後，也可以使用 IntelliSense 自動完成文字。 讓我們新增一行程式碼，將已排序的字串列印至主控台視窗，這是程式輸出的標準目標位置。

1. 在 `query` 變數下方，開始鍵入下列程式碼：

   ```vb
   For Each str In qu
   ```

   您會看到 IntelliSense 示範 `query` 符號的 [快速諮詢]。

   ![Visual Studio 中的 IntelliSense 文字完成](media/tutorial-intellisense-completion-list.png)

1. 若要使用 IntelliSense 的文字完成功能來插入 `query`這個字的其餘部分，請按 **Tab** 鍵。

1. 關閉程式碼區塊，使其看起來如下列程式碼。

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>重構名稱

沒有人第一次就取得正確的程式碼，而且您可能想要變更的其中一個項目就是變數或方法的名稱。 讓我們來試試看 Visual Studio 的[重構](../../ide/refactoring-in-visual-studio.md)功能，以將 `_words` 變數重新命名為 `words`。

1. 將游標放在 `_words` 變數定義上方，然後從右鍵功能表或操作功能表中選擇 [重新命名]。

   快顯 [重新命名] 對話方塊會出現在編輯器右上方。

1. `_words` 仍在選取時，鍵入所需的 **words** 名稱。 請注意，也會自動重新命名查詢中 `words` 的參考。 按 **Enter** 或按一下 [套用] 之前，請選取 [重新命名] 快顯方塊中的 [包括註解] 核取方塊。

   ![重新命名對話方塊](media/tutorial-rename.png)

1. 按 **Enter** 鍵或按一下 [套用]。

   出現的這兩個 `words` 已重新命名，而程式碼註解中的 `words` 參考亦然。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [了解專案與解決方案](tutorial-projects-solutions.md)

## <a name="see-also"></a>另請參閱

- [程式碼片段](../../ide/code-snippets.md)
- [巡覽程式碼](../../ide/navigating-code.md)
- [大綱](../../ide/outlining.md)
- [移至定義和查看定義](../../ide/go-to-and-peek-definition.md)
- [重構](../../ide/refactoring-in-visual-studio.md)
- [使用 IntelliSense](../../ide/using-intellisense.md)
