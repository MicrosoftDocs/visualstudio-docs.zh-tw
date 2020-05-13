---
title: 步驟 7：讓配對保持可見
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eeca594849625b548857a23b9d5c8e278dcdf07c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579288"
---
# <a name="step-7-keep-pairs-visible"></a>步驟 7：讓配對保持可見
只要玩家僅選擇不相符的圖示配對，遊戲都可以運作良好。 但是，請考慮當玩家選擇相符的配對時會發生的情況。 遊戲不用藉由啟動計時器使圖示消失 (使用 <xref:System.Windows.Forms.Timer.Start> 方法)，而是應該本身進行重設，如此它就不會再使用 `firstClicked` 和 `secondClicked` 參考變數來追蹤任何標籤，但不需要重設已選擇之兩個標籤的色彩。

## <a name="to-keep-pairs-visible"></a>若要讓配對保持可見

1. 將下列 `if` 陳述式加入至 `label_Click()` 事件處理常式方法，位置靠近您啟動計時器之陳述式正上方的程式碼那一端。 將程式碼加入至程式時，請仔細觀察該程式碼。 請考慮程式碼的運作方式。

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

       > [!IMPORTANT]
       > Use the programming language control at the top right of this page to view either the C# code snippet or the Visual Basic code snippet.<br><br>![Programming language control for Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     您剛才加入的 `if` 陳述式的第一行會檢查玩家所選擇的第一個標籤中的圖示是否與第二個標籤中的圖示相同。 如果圖示相同，程式即執行在 C# 中大括號之間或 Visual Basic 中 `if` 陳述式內的三個陳述式。 前兩個陳述式會重設 `firstClicked` 和 `secondClicked` 參考變數，如此他們便不會再追蹤任何的標籤  （可以從計時器<xref:System.Windows.Forms.Timer.Tick>的事件處理常式中識別這兩個語句。第三個語句是`return`一個語句，它告訴程式跳過方法中其餘語句而不執行它們。

     如果在 C# 中程式設計，您可能已經注意到某些代碼使用單個等號 （），`=`而其他語句使用兩個等號 （）。`==` 請考慮為何某些地方使用 `=`，而其他地方使用 `==`。

     這是一個顯示差異的好範例。 請仔細觀察 `if` 陳述式中括號之間的程式碼。

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     然後，再仔細查看 `if` 陳述式之後程式碼區塊中的第一個陳述式。

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     這兩個陳述式中的第一個會檢查兩個圖示是否相同。 由於正在比較兩個值，因此 C# 程式`==`使用相等運算子。 第二個陳述式會實際變更值 (稱為「指派」**)，方法是將 `firstClicked` 參考變數設為等於 `null` 以進行重設。 這就是它為何改用 `=` 指派運算子的緣故。 C#`=`用於設置值並`==`比較它們。 Visual Basic 則是使用 `=` 來進行變數指派和比較。

2. 儲存並執行程式，然後開始在表單中選擇圖示。 如果您選擇不相符的配對，計時器的 Tick 事件觸發器和這兩個圖示都會消失。 如果選擇匹配對，則執行新`if`語句，並且 return 語句會導致該方法跳過啟動計時器的代碼，因此圖示保持可見，如下圖所示。

     ![您在本教學課程中建立的遊戲](../ide/media/express_finishedgame.png)<br/>
***匹配****帶有可見圖示對*的遊戲

## <a name="to-continue-or-review"></a>若要繼續或檢視

- 要轉到下一個教程步驟，請參閱**[步驟 8：添加一種方法來驗證玩家是否獲勝](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)**。

- 若要返回上一個教學課程步驟，請參閱[步驟 6：新增計時器](../ide/step-6-add-a-timer.md)。
