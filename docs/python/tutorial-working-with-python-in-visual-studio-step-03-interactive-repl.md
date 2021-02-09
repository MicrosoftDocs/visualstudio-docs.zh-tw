---
title: Visual Studio 中的 Python 教學課程步驟 3，互動式 REPL
titleSuffix: ''
description: 在 Visual Studio 中 Python 功能核心逐步解說的步驟 3，涵蓋 Python 互動式 REPL 視窗。
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c4ae447976798372e049df46552f8383389f7b3e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920775"
---
# <a name="step-3-use-the-interactive-repl-window"></a>步驟 3：使用互動式 REPL 視窗

**上一個步驟：[撰寫並執行程式碼](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

適用于 Python 的 Visual Studio **互動式** 視窗提供豐富的讀取-評估-列印迴圈 (複寫) 體驗，可大幅縮短一般編輯-組建-偵錯工具的週期。 **互動式** 視窗提供 Python 命令列之複寫體驗的所有功能。 它也讓在 Visual Studio 編輯器中與原始程式檔交換程式碼變得極為簡單，而使用命令列來執行此作業則會十分麻煩。

> [!NOTE]
> 針對 REPL 的問題，請務必安裝 `ipython` 和 `ipykernel` 套件，而如需安裝套件的說明，則請參閱 [Python 環境套件索引標籤](./python-environments-window-tab-reference.md#packages-tab)。

1. 以滑鼠右鍵按一下 **方案總管** (中專案的 python 環境，例如舊版圖形) 中的 **python 3.6 (32 位)** ，然後選取 [**開啟互動式視窗]**，開啟 **互動式** 視窗。 您也可以  >  從主要 Visual Studio 功能表中選取 [查看 **其他 windows**  >  **Python 互動式視窗**]。

1. **互動式** 視窗會在編輯器下方以標準 Python 複寫 **>>>** 提示開啟。 [環境] 下拉式清單可讓您選取要使用的特定解譯器。 您通常也會想要讓 **互動式** 視窗變大，只要在兩個視窗之間拖曳分隔符號即可：

    ![Python 互動式視窗並拖曳調整大小](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > 您可以拖曳框線分隔符號，以調整 Visual Studio 中所有視窗的大小。 您也可以單獨將視窗拖出 Visual Studio 框架，不過，您也可以在框架內排列視窗。 如需完整詳細資料，請參閱[自訂視窗版面配置](../ide/customizing-window-layouts-in-visual-studio.md)。

1. 輸入幾個陳述式 (例如 `print("Hello, Visual Studio")`) 和運算式 (例如 `123/456`) 查看立即結果：

    ![Python 互動式視窗立即結果](media/vs-getting-started-python-12-interactive2.png)

1. 當您開始撰寫多行陳述式 (例如函式定義) 時，**互動式** 視窗會顯示繼續執行程式碼行的 Python **...** 提示，不同於命令列 REPL，這會提供自動縮排：

    ![Python 互動式視窗與陳述式接續](media/vs-getting-started-python-13-interactive3.png)

1. **互動式** 視窗會提供您所輸入之所有專案的完整歷程記錄，並可在使用多行歷程記錄專案的命令列複製時改善。 例如，您可以輕鬆地重新呼叫 `f` 函式的整個定義作為單一單位，並輕鬆地將名稱變更為 `make_double`，而非逐行重新建立函式。

1. Visual Studio 可以從編輯器視窗將多行程式碼傳送到 **互動式** 視窗。 這項功能可讓您維護原始程式檔中的程式碼，並輕鬆地將其的選取部分傳送至 **互動式** 視窗。 您接著可以在快速 REPL 環境中使用這類程式碼片段，而不需要執行整個程式。 若要查看此功能，請先將 *PythonApplication1.py* 檔案中的 `for` 迴圈取代為下列項目：

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. `import` `from` 在 .py 檔案中選取、和 `make_dot_string` 函數語句 。 以滑鼠右鍵按一下選取的文字，然後選擇 [**傳送到 Interactive** (或按 **Ctrl** + **enter**) 。 程式碼片段會立即貼入 **互動式** 視窗並執行。 由於程式碼已定義函式，因此您可以藉由呼叫它幾次來快速測試該函式：

    ![將程式碼傳送至互動式視窗並進行測試](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > 在編輯器中使用 **Ctrl** + **Enter** *而沒有* 選取專案，會在 **互動式** 視窗中執行目前的程式程式碼，並自動將插入號放在下一行。 使用這項功能時，重複按下 **Ctrl** + **enter** 可提供便利的方式來逐步執行您的程式碼，並不可能只使用 Python 命令列。 它也可讓您逐步執行程式碼，而不需要執行偵錯工具，也不需要從頭開始啟動您的程式。

1. 您也可以從任何來源（例如下面的程式碼片段）複製多行程式碼，並將其貼到 **互動式** 視窗中，這與 Python 命令列的複製很困難。 貼上時， **互動式** 視窗會執行該程式碼，就像您輸入的一樣：

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![使用互動式傳送貼上多行程式碼](media/vs-getting-started-python-15-interactive5.png)

1. 如您所見，此程式碼會正常運作，但其輸出不怎麼讓人滿意。 `for` 迴圈中的不同步驟值會顯示更多的餘弦波。 幸運的是，因為整個 `for` 迴圈在 REPL 歷程記錄中作為單一單位，所以很容易就能返回，並進行您想要的任何變更，然後再次測試函式。 按向上鍵，先回復 `for` 迴圈。 然後按向左鍵或向右鍵開始在程式碼中巡覽 (在您這麼做之前，向左鍵或向右鍵會繼續循環瀏覽歷程記錄)。 巡覽至 `range` 規格，並將其變更為 `range(0, 360, 12)`。 然後按下 **Ctrl** + **enter** (程式碼) 的任何位置，再次執行整個語句：

    ![在互動式視窗中編輯前一個陳述式](media/vs-getting-started-python-16-interactive6.png)

1. 重複此處理序來試驗不同的步驟設定，直到您找到最喜歡的值。 您也可以延長範圍 (例如，`range(0, 1800, 12)`) 來重複波浪。

1. 當您滿意在 **互動式** 視窗中撰寫的程式碼時，請選取它。 接下來，以滑鼠右鍵按一下程式碼，然後選擇 [**複製程式碼**] (**Ctrl** + **Shift** + **C**) 。 最後，將選取的程式碼貼入編輯器中。 注意此 Visual Studio 特殊功能如何自動省略任何輸出以及 `>>>` 和 `...` 提示。 例如，下圖顯示如何對包含提示和輸出的選取範圍使用 [複製程式碼] 命令：

    ![以提示和輸出對選取範圍的互動式視窗複製程式碼命令](media/vs-getting-started-python-17-interactive7.png)

    當您貼入編輯器時，只會取得程式碼：

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    如果您想要複製 **互動式** 視窗的確切內容（包括提示和輸出），只需要使用標準 **複製** 命令。

1. 您剛才所做的就是使用 **互動式** 視窗的快速複製環境來處理一小段程式碼的詳細資料，然後您就可以輕鬆地將該程式碼新增至專案的原始程式檔。 當您現在使用 **Ctrl** + **F5** (或 **Debug**  >  **Start**) 執行程式碼時，會看到您想要的確切結果。

## <a name="next-step"></a>後續步驟

> [!div class="nextstepaction"]
> [在偵錯工具中執行程式碼](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>深入了解

- [使用互動式視窗](python-interactive-repl-in-visual-studio.md)
- [使用 IPython REPL](interactive-repl-ipython.md)