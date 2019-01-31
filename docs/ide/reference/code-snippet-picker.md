---
title: 程式碼片段選擇器
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edf1bdc8de559cc5728a119ecdbec972ac9d0733
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021919"
---
# <a name="code-snippet-picker"></a>程式碼片段選擇器

Visual Studio 程式碼編輯器提供了 [程式碼片段選擇器]，讓您只需按幾下滑鼠即可將現成的程式碼區塊插入至使用中文件。

顯示 [程式碼片段選擇器] 的程序會根據所使用的語言而有所不同。

- Visual Basic - 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著選取 [插入程式碼片段]。

- C# -- 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著按一下 [插入程式碼片段] 或 [範圍陳述式]。

- C++ - 無法使用 [程式碼片段選擇器]。

- F# - 無法使用 [程式碼片段選擇器]。

- JavaScript - 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著按一下 [插入程式碼片段] 或 [範圍陳述式]。

- XML - 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著按一下 [插入程式碼片段] 或 [範圍陳述式]。

- HTML - 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著按一下 [插入程式碼片段] 或 [範圍陳述式]。

- SQL - 以滑鼠右鍵按一下 [程式碼編輯器] 中所需的任何位置，即可顯示捷徑功能表，接著按一下 [插入程式碼片段]。

在大部分的 Visual Studio 開發語言中，您可以使用 [程式碼片段管理員] 將資料夾新增至資料夾清單，[程式碼片段選擇器] 會掃描那些資料夾中是否有 XML程式碼片段檔案。 您也可以建立自己的程式碼片段並新增至清單。 如需詳細資訊，請參閱[逐步解說：建立程式碼片段](../../ide/walkthrough-creating-a-code-snippet.md)。

## <a name="uielement-list"></a>UIElement 清單

項目名稱

可編輯的文字欄位，它會顯示 [項目清單] 中已選取項目的名稱。 若要累加搜尋您想要的項目，請在這個欄位開始鍵入項目名稱。 繼續新增字母，直到 [項目清單] 中選取了所需項目為止。

項目清單

可供插入的程式碼片段清單，或是含有程式碼片段的資料夾清單。 若要插入程式碼片段或展開資料夾，請選取您要的項目並按 Enter。

## <a name="see-also"></a>另請參閱

- [使用程式碼片段的最佳作法](../../ide/best-practices-for-using-code-snippets.md)
- [Visual Basic IntelliSense 程式碼片段](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [在程式碼中設定書籤](../../ide/setting-bookmarks-in-code.md)
- [如何：使用範圍陳述式程式碼片段](../../ide/how-to-use-surround-with-code-snippets.md)