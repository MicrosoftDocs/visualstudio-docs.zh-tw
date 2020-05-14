---
title: Visual Studio 中的 Python 教學課程步驟 3，互動式 REPL
titleSuffix: ''
description: 在 Visual Studio 中 Python 功能核心逐步解說的步驟 3，涵蓋 Python 互動式 REPL 視窗。
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 51723d22cd72de8333fca9b83c1643117a7413e5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "72986220"
---
# <a name="step-3-use-the-interactive-repl-window"></a>步驟 3：使用互動式 REPL 視窗

**上一個步驟：[撰寫並執行程式碼](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

Python 的視覺化工作室**互動式**視窗提供了豐富的讀取評估列印迴圈 （REPL） 體驗，大大縮短了通常的編輯生成-調試週期。 **互動式**視窗提供 Python 命令列的 REPL 體驗的所有功能。 它也讓在 Visual Studio 編輯器中與原始程式檔交換程式碼變得極為簡單，而使用命令列來執行此作業則會十分麻煩。

> [!NOTE]
> 針對 REPL 的問題，請務必安裝 `ipython` 和 `ipykernel` 套件，而如需安裝套件的說明，則請參閱 [Python 環境套件索引標籤](/en-us/visualstudio/python/python-environments-window-tab-reference#packages-tab)。

1. 通過在**解決方案資源管理器**中按右鍵專案的 Python 環境（如早期圖形中顯示的 Python **3.6（32 位））** 並選擇 **"打開互動式視窗"，打開互動式視窗**。 **Interactive** 您可以從主視覺化工作室功能表中交替選擇 **"查看** > **其他 Windows** > **Python 互動式 Windows"。**

1. **使用**標準**>>>** Python REPL 提示符在編輯器下方打開互動式視窗。 [環境]**** 下拉式清單可讓您選取要使用的特定解譯器。 通常，您還希望使**互動式**視窗變大，您可以通過在兩個視窗之間拖動分隔符號來執行此操作：

    ![Python 互動式視窗並拖曳調整大小](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > 您可以拖曳框線分隔符號，以調整 Visual Studio 中所有視窗的大小。 您也可以單獨將視窗拖出 Visual Studio 框架，不過，您也可以在框架內排列視窗。 如需完整詳細資料，請參閱[自訂視窗版面配置](../ide/customizing-window-layouts-in-visual-studio.md)。

1. 輸入幾個陳述式 (例如 `print("Hello, Visual Studio")`) 和運算式 (例如 `123/456`) 查看立即結果：

    ![Python 互動式視窗立即結果](media/vs-getting-started-python-12-interactive2.png)

1. 當您開始撰寫多行陳述式 (例如函式定義) 時，**互動式**視窗會顯示繼續執行程式碼行的 Python **...** 提示，不同於命令列 REPL，這會提供自動縮排：

    ![Python 互動式視窗與陳述式接續](media/vs-getting-started-python-13-interactive3.png)

1. **互動式**視窗提供您輸入的所有內容的完整歷史記錄，並在具有多行歷史記錄項的命令列 REPL 上改進。 例如，您可以輕鬆地重新呼叫 `f` 函式的整個定義作為單一單位，並輕鬆地將名稱變更為 `make_double`，而非逐行重新建立函式。

1. Visual Studio 可以從編輯器視窗向**互動式**視窗發送多行代碼。 此功能允許您在原始檔案中維護代碼，並輕鬆地將其中的某些部分發送到**互動式**視窗。 您接著可以在快速 REPL 環境中使用這類程式碼片段，而不需要執行整個程式。 若要查看此功能，請先將 *PythonApplication1.py* 檔案中的 `for` 迴圈取代為下列項目：

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. 選擇`import`*.py* `make_dot_string`檔中 的 和`from`， 按右鍵， 並選擇"**發送到互動式**"（或按**Ctrl**+**Enter**）。 代碼片段立即粘貼到**互動式**視窗中並運行。 由於代碼定義了函數，因此可以通過調用該函數幾次來快速測試該函數：

    ![將程式碼傳送至互動式視窗並進行測試](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > *在沒有選擇的情況下*在編輯器中使用**Ctrl**+**Enter**將運行 **"互動式"** 視窗中的當前程式碼，並自動將插入者放在下一行上。 使用此功能，按**Ctrl**+**Enter**反復按下提供了一種只需使用 Python 命令列才能單一步驟代碼的便捷方法。 它也可讓您逐步執行程式碼，而不需要執行偵錯工具，也不需要從頭開始啟動您的程式。

1. 您還可以從任何源（如下面的程式碼片段）將多行代碼複製並粘貼到**互動式**視窗中，這與 Python 命令列 REPL 很難執行。 粘貼後，**互動式**視窗將運行該代碼，就像鍵入該代碼一樣：

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![使用互動式傳送貼上多行程式碼](media/vs-getting-started-python-15-interactive5.png)

1. 如您所見，此程式碼會正常運作，但其輸出不怎麼讓人滿意。 `for` 迴圈中的不同步驟值會顯示更多的餘弦波。 幸運的是，因為整個 `for` 迴圈在 REPL 歷程記錄中作為單一單位，所以很容易就能返回，並進行您想要的任何變更，然後再次測試函式。 按向上鍵，先回復 `for` 迴圈。 然後按向左鍵或向右鍵開始在程式碼中巡覽 (在您這麼做之前，向左鍵或向右鍵會繼續循環瀏覽歷程記錄)。 巡覽至 `range` 規格，並將其變更為 `range(0, 360, 12)`。 然後按**Ctrl**+**Enter（** 代碼中的任何位置）再次運行整個語句：

    ![在互動式視窗中編輯前一個陳述式](media/vs-getting-started-python-16-interactive6.png)

1. 重複此處理序來試驗不同的步驟設定，直到您找到最喜歡的值。 您也可以延長範圍 (例如，`range(0, 1800, 12)`) 來重複波浪。

1. 當您對在 **"交互"** 視窗中編寫的代碼感到滿意時，選擇它，按右鍵並選擇**複製代碼****（Ctrl**+**Shift**+**C），** 然後粘貼到編輯器中。 注意此 Visual Studio 特殊功能如何自動省略任何輸出以及 `>>>` 和 `...` 提示。 例如，下圖顯示如何對包含提示和輸出的選取範圍使用 [複製程式碼]**** 命令：

    ![以提示和輸出對選取範圍的互動式視窗複製程式碼命令](media/vs-getting-started-python-17-interactive7.png)

    當您貼入編輯器時，只會取得程式碼：

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    如果要複製**互動式**視窗的確切內容（包括提示和輸出），只需使用標準**Copy**命令。

1. 您剛剛完成的工作是使用**互動式**視窗的快速 REPL 環境來制定一小塊代碼的詳細資訊，然後方便地將該代碼添加到專案的原始檔案中。 現在使用**Ctrl**+**F5（****或不** > **調試啟動**）再次運行代碼時，可以看到所需的確切結果。

## <a name="next-step"></a>後續步驟

> [!div class="nextstepaction"]
> [在偵錯工具中執行程式碼](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>深入了解

- [使用互動式視窗](python-interactive-repl-in-visual-studio.md)
- [使用 IPython REPL](interactive-repl-ipython.md)
