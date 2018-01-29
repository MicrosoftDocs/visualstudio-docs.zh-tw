---
title: "在 Visual Studio 中使用 Python，步驟 3：互動式 REPL 視窗 | Microsoft Docs"
description: "在 Visual Studio 內使用 Python 之核心教學課程的步驟 3，涵蓋 Python 互動式 REPL 視窗。"
ms.custom: 
ms.date: 10/16/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: cdfcd81108437e611d7ba58f0a612b19931cc654
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2018
---
# <a name="step-3-using-the-interactive-repl-window"></a>步驟 3：使用互動式 REPL 視窗

**上一個步驟：[撰寫和執行程式碼](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

適用於 Python 的 Visual Studio「互動式視窗」提供一個豐富的「讀取、求值、輸出」迴圈 (REPL) 體驗，可大幅縮短一般「編輯-建置-偵錯」循環。 互動式視窗提供 Python 命令列之 REPL 體驗的所有功能。 它也讓在 Visual Studio 編輯器中與原始程式檔交換程式碼變得極為簡單，而使用命令列來執行此作業則會十分麻煩。

1. 在方案總管中以滑鼠右鍵按一下專案的 Python 環境 (例如較早圖形中顯示的 [Python 3.6 (32 位元)])，然後選取 [開啟互動式視窗]，以開啟互動式視窗。 您可以透過互動方式從 Visual Studio 主功能表選取 [檢視] > [其他視窗] > [Python 互動式視窗]。

1. 使用一般 `>>>` Python REPL 提示字元，會在編輯器下方開啟互動式視窗。 您經常會想要讓互動式視窗變大，做法是拖曳兩個視窗之間的分隔符號：

    ![Python 互動式視窗並拖曳調整大小](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > 您可以拖曳框線分隔符號，以調整 Visual Studio 中所有視窗的大小。 您也可以單獨將視窗拖出 Visual Studio 框架，不過，您也可以在框架內排列視窗。 如需完整詳細資料，請參閱[自訂視窗版面配置](../ide/customizing-window-layouts-in-visual-studio.md)。

1. 輸入幾個陳述式 (例如 `print("Hello, Visual Studio")`) 和運算式 (例如 `123/456`) 查看立即結果：

    ![Python 互動式視窗立即結果](media/vs-getting-started-python-12-interactive2.png)

1. 當您開始撰寫多行陳述式 (例如函式定義) 時，互動式視窗會顯示繼續執行程式碼行的 Python `...` 提示，不同於命令列 REPL，這會提供自動縮排：

    ![Python 互動式視窗與陳述式接續](media/vs-getting-started-python-13-interactive3.png)

1. 互動式視窗提供您所輸入之所有資料的完整歷程記錄，並改善包含多行歷程記錄項目的命令列 REPL。 例如，您可以輕鬆地重新呼叫 `f` 函式的整個定義作為單一單位，並輕鬆地將名稱變更為 `make_double`，而非逐行重新建立函式。

1. Visual Studio 可以將多行程式碼從編輯器視窗傳送至互動式視窗。 此功能可讓您維護來源檔案中的程式碼，並輕鬆地將其的選取部分傳送至互動式視窗。 您接著可以在快速 REPL 環境中使用這類程式碼片段，而不需要執行整個程式。 若要查看此功能，請先將 `PythonApplication1.py` 檔案中的 `for` 迴圈取代為下列項目：

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. 僅選取 `.py` 檔案中的 `import` 和 `from` 陳述式，並按一下滑鼠右鍵，然後選取 [傳送到 Interactive] (或按 Ctrl+Enter)。 程式碼片段會立即貼入至互動式視窗並執行。 現在選取 `make_dot_string` 函式，並重複相同的命令，以再次執行該程式碼片段。 因為程式碼定義函式，您可以呼叫該函式數次以快速測試它：

    ![將程式碼傳送至互動式視窗並進行測試](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > 在編輯器中使用 Ctrl+Enter 但「未」選取任何項目，會在互動式視窗中執行目前程式碼行，並自動將插入號放入下一行。 使用此功能，重複按 Ctrl+Enter 可提供便利的方式，來逐步執行無法只使用 Python 命令列執行的程式碼。 它也可讓您逐步執行程式碼，而不需要執行偵錯工具，也不需要從頭開始啟動您的程式。

1. 您也可以從任何來源 (例如下面的程式碼片段) 複製多行程式碼，並將其貼入互動式視窗，但這可能很難使用 Python 命令列 REPL 處理。 貼上時，互動式視窗會執行該程式碼，就像您鍵入它一樣：

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![使用互動式傳送貼上多行程式碼](media/vs-getting-started-python-15-interactive5.png)

1. 如您所見，此程式碼會正常運作，但其輸出不怎麼讓人滿意。 `for` 迴圈中的不同步驟值會顯示更多的餘弦波。 幸運的是，因為整個 `for` 迴圈在 REPL 歷程記錄中作為單一單位，所以很容易就能返回，並進行您想要的任何變更，然後再次測試函式。 按向上鍵，先回復 `for` 迴圈。 然後按向左鍵或向右鍵開始在程式碼中巡覽 (在您這麼做之前，向左鍵或向右鍵會繼續循環瀏覽歷程記錄)。 巡覽至 `range` 規格，並將其變更為 `range(0, 360, 12)`。 然後按 Ctrl+Enter (程式碼中的任何位置) 重新執行整個陳述式：

    ![在互動式視窗中編輯前一個陳述式](media/vs-getting-started-python-16-interactive6.png)

1. 重複此處理序來試驗不同的步驟設定，直到您找到最喜歡的值。 您也可以延長範圍 (例如，`range(0, 1800, 12)`) 來重複波浪。
 
1. 當您滿意在互動式視窗中撰寫的程式碼時，請選取它，並按一下滑鼠右鍵，再選取 [複製程式碼] (Ctrl+Shift+C)，然後貼入編輯器中。 注意此 Visual Studio 特殊功能如何自動省略任何輸出以及 `>>>` 和 `...` 提示。 例如，下圖顯示如何對包含提示和輸出的選取範圍使用 [複製程式碼] 命令：

    ![以提示和輸出對選取範圍的互動式視窗複製程式碼命令](media/vs-getting-started-python-17-interactive7.png)

    當您貼入編輯器時，只會取得程式碼：

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    如果您想要複製互動式視窗的確切內容 (包含提示和輸出)，只需要使用標準 [複製] 命令。

1. 您剛完成的作業是使用互動式視窗的快速 REPL 環境了解一小部分程式碼的詳細資料，然後您可以方便地將該程式碼新增至專案的原始程式檔。 當您現在使用 Ctrl+F5 (或 [偵錯] > [開始但不偵錯]) 再次執行程式碼時，就會看到您想要的確切結果。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [在偵錯工具中執行程式碼](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

### <a name="going-deeper"></a>繼續探討

- [使用互動式視窗](interactive-repl.md)
- [使用 IPython REPL](interactive-repl-ipython.md)
