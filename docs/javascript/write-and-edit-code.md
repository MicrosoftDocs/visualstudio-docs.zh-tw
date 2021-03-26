---
title: JavaScript 開發人員編輯簡介
description: 這個 Visual Studio 程式碼編輯器簡介，說明 Visual Studio 可讓撰寫、巡覽和了解 JavaScript 程式碼更加輕鬆的一些方式。
ms.date: 03/25/2021
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: b1d9fb7cdc850bc54298cd3d82d52786a9e6a639
ms.sourcegitcommit: 00e16b9afe6b22ba0591e4d0d92690544e6d4357
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2021
ms.locfileid: "105616957"
---
# <a name="learn-to-use-the-code-editor-for-javascript"></a>瞭解如何使用 JavaScript 的程式碼編輯器

在這個 Visual Studio 程式碼編輯器簡介中，我們將探討 Visual Studio 讓撰寫、巡覽和了解程式碼更加輕鬆的一些方式。

> [!TIP]
> 如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面免費進行安裝。 根據您執行的應用程式開發類型，您可能需要安裝 Visual Studio 隨附的 **Node.js 開發工作負載**。 如需取得 TypeScript 語言服務的詳細資訊，請參閱 [typescript 支援](../javascript/javascript-in-vs-2019.md#typescript-support)。

本文假設您已熟悉 JavaScript 開發。 如果您不熟悉，建議您先瀏覽教學課程 (例如[建立 Node.js 和 Express 應用程式](../javascript/tutorial-nodejs.md))。

## <a name="add-a-new-project-file"></a>新增專案檔

您可以使用 IDE 將新檔案新增至您的專案。

1. 當您的專案在 Visual Studio 中開啟時，以滑鼠右鍵按一下方案總管 (右窗格) 中的資料夾或專案節點，然後選擇 [**加入**  >  **新專案**]。

1. 在 [新增檔案] 對話方塊的 [一般] 類別下，選擇您要新增的檔案類型 (例如 [JavaScript 檔案])，然後選擇 [開啟]。

    這會將新檔案新增至您的專案，並在編輯器中開啟該檔案。

## <a name="use-intellisense-to-complete-words"></a>使用 IntelliSense 自動完成文字

IntelliSense 是您撰寫程式碼時的重要資源。 它可以顯示類型可用成員的相關資訊，或方法之不同多載的參數詳細資料。 在下列程式碼中，當您鍵入 `Router()` 時，您會看到可傳遞的引數類型。 這稱為簽章說明。

![輸入 JavaScript 程式碼之 Visual Studio 程式碼視窗的螢幕擷取畫面。 會顯示路由器 () 函式的 IntelliSense 資訊。](../javascript/media/write-code-signature-checking.png)

在您鍵入足夠的字元來釐清文字之後，也可以使用 IntelliSense 自動完成文字。 如果您將游標放在下列程式碼中的 `data` 字串後面並鍵入 `get`，IntelliSense 將會顯示稍早在程式碼中定義或在協力廠商程式庫中定義並已新增至專案的函式。

![Visual Studio 程式碼視窗的螢幕擷取畫面，其中會輸入 ' get ' 這個字。 所有以 ' get ' 開頭的函式都會顯示 IntelliSense 資訊。](../javascript/media/write-code-intellisense.png)

當您將滑鼠停留在程式設計項目時，IntelliSense 也會顯示類型的相關資訊。

語言服務可以使用 TypeScript *d.ts* 檔案和 JSDoc 註解來提供 IntelliSense 資訊。 若是最常見的 JavaScript 程式庫，則會自動取得 *d.ts* 檔案。 如需如何取得 IntelliSense 資訊的詳細資訊，請參閱 [JavaScript intellisense](../ide/javascript-intellisense.md?toc=/visualstudio/javascript/toc.json)。 如果您想要在 Visual Studio 中 AngularJS 程式設計，您可以使用 Visual Studio 的 [AngularJS language service 延伸](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio) 模組來取得 IntelliSense。

## <a name="check-syntax"></a>檢查語法

語言服務使用 ESLint 提供語法檢查和 Lint 檢查。 如果您需要在編輯器中設定語法檢查的選項，請選取 [**工具**  >  **選項**  >  **JavaScript/TypeScript**  >  **Linting**]。 [Linting] 選項會將您導向至全域 ESLint 組態檔。

在下列程式碼中，您會看到運算式上的綠色語法醒目提示 (綠色波浪線)。 將滑鼠停留在語法醒目提示上方。

![檢視語法錯誤](../javascript/media/write-code-syntax-checking.png)

此訊息的最後一行告訴您：語言服務必須要有逗號 (`,`)。 綠色波浪線表示警告。 紅色波浪線表示錯誤。

在下方窗格中，您可以按一下 [錯誤清單] 索引標籤來查看警告和描述，以及檔案名稱和行號。

![檢視錯誤清單](../javascript/media/write-code-error-list.png)

您可以在 `"data"` 前面新增逗號 (`,`) 來修正此程式碼。

如需 linting 的詳細資訊，請參閱 [linting](https://github.com/microsoft/JSTSdocs/blob/master/articles/editor/linting.md)。

## <a name="comment-out-code"></a>註解化程式碼

工具列是 Visual Studio 功能表列下的按鈕列，有助您提高撰寫程式碼的效率。 例如，您可以切換 IntelliSense 完成模式 ([IntelliSense](../ide/using-intellisense.md) 是程式碼撰寫的輔助工具，可顯示其他項目中符合的方法清單)，增加或減少行的縮排，也可以為不要編譯的程式碼加上註解。 在本節中，我們會為一些程式碼加上註解。

在編輯器中選取一或多行程式碼，然後選擇工具列上的 [註解選取行] 按鈕 ![加上註解按鈕](../javascript/media/write-code-comment-out.png)。 如果您想要使用鍵盤，請按下 **ctrl** + **K**、 **ctrl** + **C**。

JavaScript 註解字元 `//` 會新增至每個選取行的開頭，為程式碼加上註解。

## <a name="collapse-code-blocks"></a>摺疊程式碼區塊

如果您需要整理某些區域的程式碼檢視，您可以將它摺疊。 選擇函式第一行邊緣中其內有減號的小型灰色方塊。 或者，如果您是鍵盤使用者，請將游標放在函式程式碼中的任何位置，然後按 **ctrl** + **m**、 **ctrl** + **m**。

![大綱摺疊按鈕](../javascript/media/write-code-collapse-code.png)

程式碼區塊只會摺疊到第一行，並且後面接著省略符號 (`...`)。 若要再次展開程式碼區塊，請按一下現在具有加號的相同灰色方塊，或再次按下 **ctrl** + **m**、 **ctrl** + **m** 。 這項功能稱為[大綱](../ide/outlining.md)，而且特別適用於摺疊較長的函式或整個類別。

## <a name="view-definitions"></a>檢視定義

Visual Studio 編輯器可讓您輕鬆檢查類型、函式等的定義。其中一種方式是導覽至包含定義的檔案，例如，在參考程式設計專案的任何位置選擇 [ **移至定義** ]。 不會將焦點移離所處理檔案的較快速方式是使用[查看定義](../ide/go-to-and-peek-definition.md#peek-definition)。 讓我們查看下列範例中 `render` 方法的定義。

以滑鼠右鍵按一下 `render`，然後從操作功能表選擇 [查看定義]。 或者，按 **Alt** + **F12**。

   快顯視窗隨即出現，並內含 `render` 方法的定義。 您可以在快顯視窗內捲動，或甚至查看已查看程式碼中另一種類型的定義。

   ![查看定義視窗](../javascript/media/write-code-peek-definition.png)

選擇快顯視窗右上方含 "x" 的小型方塊，以關閉查看的定義視窗。

## <a name="use-code-snippets"></a>使用程式碼片段

Visual Studio 提供實用的「程式碼片段」，讓您可以用來快速且輕鬆地產生常用的程式碼區塊。 [程式碼片段](../ide/code-snippets.md)適用於不同的程式設計語言 (包括 JavaScript)。 請在程式碼檔案中新增 `for` 迴圈。

將游標放在您想要插入程式碼片段的位置，按一下滑鼠右鍵，然後選擇 [**程式碼片段**  >  **插入代碼** 段]。

![Visual Studio 中的程式碼片段](../javascript/media/write-code-insert-snippet.png)

[插入程式碼片段] 方塊隨即出現在編輯器中。 選擇 [一般]，然後按兩下清單中的 [for] 項目。

![Visual Studio 中的 for 迴圈程式碼片段](../javascript/media/write-code-insert-snippet-for-loop.png)

這會將 `for` 迴圈程式碼片段新增至您的程式碼：

```javascript
for (var i = 0; i < length; i++) {

}
```

您可以選擇 [**編輯**  >  **IntelliSense**  >  **插入程式碼片段**]，然後選擇語言的資料夾，以查看語言的可用程式碼片段。

## <a name="see-also"></a>另請參閱

- [程式碼片段](../ide/code-snippets.md)
- [巡覽程式碼](../ide/navigating-code.md)
- [大綱](../ide/outlining.md)
- [移至定義和查看定義](../ide/go-to-and-peek-definition.md)
- [重構](../ide/refactoring-in-visual-studio.md)
- [使用 IntelliSense](../ide/using-intellisense.md)
