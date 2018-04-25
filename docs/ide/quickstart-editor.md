---
title: 在 Visual Studio 中編輯簡介 | Microsoft Docs
ms.custom: ''
ms.date: 11/30/2017
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 46f627d7157972e277589d2edf07309190c6430d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="quickstart-use-the-code-editor"></a>快速入門：使用程式碼編輯器

在這個 10 分鐘的編輯器簡介中，我們會將程式碼新增至檔案，以查看 Visual Studio 更輕鬆進行撰寫、導覽和了解程式碼的一些方式。

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)頁面免費進行安裝。

本快速入門假設您已熟悉某一種程式設計語言。 如果您還不熟悉，建議您先查看一種程式設計語言的快速入門，例如使用 [Python](../ide/quickstart-python.md) 或 [C#](../ide/tutorial-csharp-aspnet-core.md) 建立 Web 應用程式，或是使用 [Visual Basic](../ide/quickstart-visual-basic-console.md) 或 [C++](../ide/quickstart-cpp.md) 建立主控台應用程式。

## <a name="create-a-new-code-file"></a>建立新的程式碼檔

從建立新檔案並在其中新增一些程式碼開始。 請注意，我們不需要建立專案來取得編輯器所提供的一些優點。

1. 開啟 Visual Studio，然後從功能表列的 [檔案] 功能表中選擇 [新增] > [檔案]。

1. 在 [新增檔案] 對話方塊的 [一般] 類別下，選擇 [Visual C# 類別]，然後選擇 [開啟]。

   使用 C# 類別的基本架構，在編輯器中開啟新的檔案。

## <a name="using-code-snippets"></a>使用程式碼片段

Visual Studio 提供有用的程式碼片段，讓您可以用來快速且輕鬆地產生常用的程式碼區塊。 [程式碼片段](../ide/code-snippets.md)適用於不同的程式設計語言 (包括 C#、Visual Basic 和 C++)。 請在檔案中新增 C# `void Main` 程式碼片段。

1. 將資料指標放在 `Class1` 建構函式的右大括號下方，然後輸入字元 `svm`。

   您會看到所出現的 IntelliSense 對話方塊包含 `svm` 程式碼片段的相關資訊。

   ![IntelliSense 程式碼片段](media/quickstart-intellisense-snippet.png)

1. 按兩次 **Tab** 鍵，以插入程式碼片段。

   您會看到在檔案中新增 `static void Main()` 方法簽章。 `Main()` 方法是 C# 應用程式的進入點。

可用的程式碼片段會因不同語言而異。 您可以依序選擇 [編輯]、[IntelliSense] 和 [插入程式碼片段]，然後選擇您語言的資料夾，以查看程式設計語言的可用程式碼片段。 針對 C#，清單如下：

![C# 程式碼片段清單](media/quickstart-code-snippet-list.png)

此清單所包含的程式碼片段用於建立類別、建構函式、`Console.WriteLine()`、`for` 迴圈、`if` 和 `switch` 陳述式等等。

## <a name="commenting-out-code"></a>將程式碼註解化

工具列提供數個按鈕，讓您與您的程式碼一樣更具生產力。 例如，您可以切換 IntelliSense 完成模式、增加或減少縮排、設定書籤，或將程式碼註解化。 在本節中，我們會將一些不想要編譯的程式碼註解化。

![編輯器工具列](media/quickstart-editor-toolbar.png)

1. 將下列程式碼貼入 `Main()` 方法主體。

    ```csharp
    // _words is a string array that we'll sort alphabetically
    string[] _words = {
        "the",
        "quick",
        "brown",
        "fox",
        "jumps"
    };

    string[] morewords = {
        "over",
        "the",
        "lazy",
        "dog"
    };

    IEnumerable<string> query = from word in _words
                                orderby word.Length
                                select word;
    ```

1. 我們不會使用 `morewords` 變數，但稍後可能會使用它，因此不會想要將它刪除。 相反地，請將這些行註解化。 選取 `morewords` 的整個定義直到結尾分號，然後選擇工具列上的 [註解選取行] 按鈕，或按 **Ctrl**+**K**、**Ctrl**+**C**。

   ![註解化按鈕](media/quickstart-comment-out.png)

   C# 註解字元 `//` 會新增至每個選取行的開頭，以將程式碼註解化。

## <a name="collapsing-code-blocks"></a>摺疊程式碼區塊

我們不想要看到所產生 `Class1` 的空白建構函式，以整理我們的程式碼檢視，那麼讓我們摺疊它。 選擇建構函式第一行邊緣中其內有減號的小型灰色方塊。 或者，如果您是鍵盤使用者，請將資料指標放在建構函式程式碼中的任何位置，然後按 **Ctrl**+**M**、**Ctrl**+**M**。

![大綱摺疊按鈕](media/quickstart-collapse.png)

程式碼區塊只會摺疊到第一行，並且後面接著省略符號 (`...`)。 若要再次展開程式碼區塊，請按一下現在其內有加號的相同灰色方塊，或再次按 **Ctrl**+**M**、**Ctrl**+**M**。 這項功能稱為[大綱](../ide/outlining.md)，而且特別適用於摺疊較長的方法或整個類別。

## <a name="viewing-symbol-definitions"></a>檢視符號定義

Visual Studio 編輯器讓檢查類型、方法等等的定義變得十分輕鬆。其中一種方式是導覽至包含定義的檔案，例如，在參考符號的任何位置選擇 [移至定義]。 不會將焦點移離所處理檔案的較快速方式是使用[查看定義](../ide/go-to-and-peek-definition.md#peek-definition)。 請查看 `string` 的定義。

1. 以滑鼠右鍵按一下任何出現的 `string`，然後從內容功能表中選擇 [查看定義]&mdash; 或按 **Alt**+**F12**。

   快顯視窗隨即出現，並內含 `String` 類別的定義。 您可以在快顯視窗內捲動，或甚至查看已查看程式碼中另一種類型的定義。

   ![查看定義視窗](media/quickstart-peek-definition.png)

1. 選擇快顯視窗右上方含 "x" 的小型方塊，以關閉查看的定義視窗。

## <a name="using-intellisense-to-complete-words"></a>使用 IntelliSense 自動完成文字

[IntelliSense](../ide/using-intellisense.md) 是您撰寫程式碼時的重要資源。 它可以顯示類型可用成員的相關資訊，或方法之不同多載的參數詳細資料。 在您鍵入足夠的字元來釐清文字之後，也可以使用 IntelliSense 自動完成文字。 讓我們新增一行程式碼，以將已排序的字串輸出至主控台視窗。

1. 在 `query` 變數下方，開始鍵入下列程式碼：

   ```csharp
   foreach (string str in qu
   ```

   您會看到 IntelliSense 示範 `query` 符號的 [快速諮詢]。

   ![IntelliSense 文字自動完成](media/quickstart-intellisense-completion-list.png)

1. 若要使用 IntelliSense 的 [自動完成文字] 功能插入 `query` 這個字的其餘部分，請按 **Tab** 鍵。

1. 關閉程式碼區塊，使其看起來如下列程式碼。 您甚至可以再次練習使用程式碼片段，方法是輸入 `cw`，然後按兩次 **Tab** 鍵以產生 `Console.WriteLine` 程式碼。

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactoring-a-name"></a>重構名稱

沒有人第一次就取得正確的程式碼，而且您可能想要變更的其中一個項目就是變數或方法的名稱。 讓我們來試試看 Visual Studio 的[重構](../ide/refactoring-in-visual-studio.md)功能，以將 `_words` 變數重新命名為 `words`。

1. 將資料指標放在 `words` 變數定義上方，然後從右鍵功能表或操作功能表中選擇 [重新命名]，或按 **Ctrl**+**R**、**Ctrl**+**R**。

   快顯 [重新命名] 對話方塊會出現在編輯器右上方。

1. 輸入所需名稱 `words`。 請注意，也會自動重新命名查詢中 `words` 的參考。 按 **Enter** 鍵之前，請選取 [重新命名] 快顯方塊中的 [包括註解] 核取方塊。

   ![重新命名對話方塊](media/quickstart-rename.png)

1. 按 **Enter** 鍵。

   出現的這兩個 `words` 已重新命名，以及程式碼註解中的 `words` 參考。

## <a name="next-steps"></a>後續步驟

您已經完成這個 Visual Studio 編輯器快速入門！ 接下來，您可以試試看一些其他 Visual Studio IDE 快速入門、查看一些[導覽程式碼](../ide/navigating-code.md)的方式，或查看我們所查看功能之相關資訊的連結。 否則，高興撰寫程式碼！

## <a name="see-also"></a>另請參閱

- [快速入門：Visual Studio IDE 初探](../ide/quickstart-ide-orientation.md)
- [快速入門：將 Visual Studio IDE 和編輯器個人化](../ide/quickstart-personalize-the-ide.md)
- [快速入門：專案和方案](../ide/quickstart-projects-solutions.md)
- [程式碼片段](../ide/code-snippets.md)
- [大綱](../ide/outlining.md)
- [移至定義和查看定義](../ide/go-to-and-peek-definition.md)
- [重構](../ide/refactoring-in-visual-studio.md)
- [使用 IntelliSense](../ide/using-intellisense.md)
