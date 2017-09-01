---
title: "開始在 Visual Studio 中使用 Python | Microsoft Docs"
ms.custom: 
ms.date: 7/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: a9087b19-275b-4cc1-8d0c-f9c4356c9ce8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: d0a5b44962b0cfbe549453b1760a38237de7e6ab
ms.openlocfilehash: 420af3d78a514a7e6b6ded186c204ad8301c4c85
ms.contentlocale: zh-tw
ms.lasthandoff: 08/16/2017

---

# <a name="getting-started-with-python-in-visual-studio"></a>開始在 Visual Studio 中使用 Python

一旦 Visual Studio 已安裝 Python 工作負載 (Visual Studio 2017) 或者適用於 Visual Studio 的 Python 工具 (Visual Studio 2015 與更早版本)，您就準備好探索 Python 開發體驗。 (若有需要，請參閱[安裝](installation.md))。

本逐步解說引導您建立一個新的空白 Python 應用程式、選擇要使用的 Python 環境，然後撰寫一些程式碼，以在工作中查看 IntelliSense。 然後，您將短暫使用互動式 REPL 視窗建立更多程式碼，接著完成程式，並單獨執行程式或在偵錯工具中執行程式。

> [!Note]
> 本逐步解說將探討 Visual Studio 2017 中的 Python 體驗；其他版本非常類似，但一些細節上可能有所不同。

## <a name="create-a-new-python-project"></a>建立新的 Python 專案

Visual Studio 中的 Python 支援包含一些[專案範本](python-projects.md)，可讓您開始使用不同類型的專案，包括使用 Bottle、Flask 及 Django 架構搭配 Azure 雲端服務的 Web 應用程式。 不過，基於本逐步解說的目的，讓我們先從空白專案開始。

1. 在 Visual Studio 中，選取 [檔案] > [新增專案] 啟動 [新增專案] 對話方塊。 在這裡您可以瀏覽和選取範本，以及指定在哪個資料夾中建立專案的位置。

1. 您可以在左側的 [範本] > [其他語言] > [Python] 底下找到 Python 範本，或者搜尋 "Python"：

    ![顯示 Python 專案的新增專案對話方塊](media/getting-started-new-project.png)

1. 選取 [Python 應用程式] 範本、指定專案的資料夾，並選取 [確定]。 (如果您想要立刻建立專案的本機存放庫，也請選取 [加入至原始檔控制] 選項)。

    > [!Tip]
    > [從現有 Python 程式碼] 範本可讓您從已包含 Python 程式碼的資料夾快速建立 Visual Studio 專案，而不是建立新的空白專案並將現有的程式碼匯入。

1. 幾分鐘後，專案會在 Visual Studio [方案總管] 視窗中開啟。 您可以在這裡瀏覽專案中的檔案和資料夾，以及管理環境。

    ![方案總管中的 Python 專案](media/getting-started-solution-explorer-1.png)

1. 展開 [Python 環境] 節點，您會看到此專案目前預設的 Python 解譯器。 如果您也展開該解譯器節點，您會看到該環境中可以使用的程式庫清單︰

    ![方案總管中顯示 Python 環境](media/getting-started-solution-explorer-2.png)

1. 如果您使用的是 Visual Studio 2015 或更早版本，依預設則不會安裝 Python 解譯器。 針對此程序，請參閱[選取並安裝 Python 解譯器](python-environments.md#selecting-and-installing-python-interpreters)。

### <a name="going-deeper"></a>繼續探討

- [Visual Studio 中的 Python 專案](python-projects.md)。
- [Web 專案範本](template-web.md)
- [Django Web 專案範本](template-django.md)
- [Azure 雲端服務範本](template-azure-cloud-service.md)

## <a name="writing-and-running-code"></a>撰寫和執行程式碼

1. 建立新的「Python 應用程式」專案之後，Visual Studio 編輯器中會開啟名稱為 `PythonApplication1.py` 的預設空白檔案。 若要將它重新命名，在 [方案總管] 中以滑鼠右鍵按一下檔案，然後選取 [重新命名]，並將名稱變更為 `hello.py`。

1. 開始輸入 `print("Hello world")`，並注意 Visual Studio IntelliSense 在過程中如何顯示自動完成選項。 下拉式清單中含外框的選項是您按下 Tab 鍵時使用的預設自動完成選項。 涉及到較長的陳述式或識別項時，完成最有幫助。

    ![IntelliSense 自動完成快顯視窗](media/getting-started-coding-1.png)

1. IntelliSense 會根據您所使用的陳述式、所呼叫的函式等等，顯示不同的資訊。 使用 `print` 函式，輸入 `(` 進行呼叫會快顯該函式的完整使用方式資訊，以粗體顯示目前您需要提供的引數 (如下所示的 **value**)：

    ![函式的 IntelliSense 自動完成快顯視窗](media/getting-started-coding-2.png)

1. 完成陳述式，使它符合下列內容︰

  ```python
  print("Hello world")
  ```

1. 若要執行程式碼，請按 F5 或選取 [偵錯] > [開始偵錯] 功能表項目。

    > [!Note]
    > 如果您在 Visual Studio 2015 或更早版本中看到沒有任何解譯器的訊息，請參閱[選取並安裝 Python 解譯器](python-environments.md#selecting-and-installing-python-interpreters)，因為預設未安裝解譯器。

1. Visual Studio 將使用專案中的預設環境執行程式碼，並在命令視窗中顯示結果。 按任意鍵關閉該視窗，並結束偵錯工作階段。

    ![偵錯工具列上的 [開始] 按鈕](media/getting-started-coding-4.png)

1. 除了陳述式和函式以外，IntelliSense 會提供 `import` 陳述式的自動完成選項。 匯入完成可協助您輕鬆地找出哪些模組可用於您的環境，以及該模組中可使用的成員。 在編輯器中，刪除 `print` 行，並開始輸入 `import`。 會出現一份模組清單︰

    ![IntellSense 顯示 import 陳述式可用的模組](media/getting-started-coding-5.png)

1. 輸入或選取 `sys` 完成行。

1. 在下一行中，再次輸入 `from` 以查看模組清單：

    ![IntellSense 顯示 from 陳述式可用的模組](media/getting-started-coding-6.png)

1. 選取或輸入 `math`，然後繼續輸入空格與 `import`，其中顯示模組成員︰

    ![IntellSense 顯示模組成員](media/getting-started-coding-7.png)

1. 透過匯入 `sin`、`cos` 和 `radians` 成員來完成，注意每個成員可用的自動完成選項。 當您完成時，您的程式碼應該會如下所示︰

  ```python
  import sys  
  from math import sin, cos, radians          
  ```

> [!Tip]
> 當您輸入時，自動完成選項會與子字串搭配使用，比對部分字組、字組開頭的字母，甚至是略過的字元。 如需詳細資訊，請參閱[編輯程式碼 - 自動完成](code-editing.md#completions)。

在下一個步驟中，我們將使用互動式 REPL 視窗撰寫可以立即測試，而不用執行偵錯工具的一些程式碼。

### <a name="going-deeper"></a>繼續探討

- [編輯程式碼](code-editing.md)
- [格式化程式碼](code-formatting.md)
- [重構程式碼](code-refactoring.md)
- [使用 PyLint](code-pylint.md)


## <a name="using-the-interactive-repl-window"></a>使用互動式 REPL 視窗

適用於 Python 的 Visual Studio 互動式視窗提供一個豐富的讀取-評估-輸出-循環 (REPL) 體驗，可大幅縮短一般編輯-建置-偵錯的循環。 它類似於 Python 命令列的 REPL 體驗，但是提供一些如此處所示範的其他功能。

1. 透過從 Visual Studio 主功能表選取 [檢視] > [其他視窗] > [Python 互動式視窗]，開啟互動式視窗。 隨即開啟一般 >>> Python REPL 提示字元視窗。 請注意，您可以使用工具列上的下拉式選單，隨時變更環境︰

    ![Python 互動式視窗](media/getting-started-interactive-1.png)

1. 輸入幾個陳述式 (例如 `print("hello")`) 和運算式 (例如 `123/567`) 查看立即結果：

    ![Python 互動式視窗立即結果](media/getting-started-interactive-2.png)

1. 當您開始撰寫多行陳述式 (例如函式定義) 時，互動式視窗會顯示繼續執行程式碼行的 ... 提示，不同於命令列 REPL，這會提供自動縮排：

    ![Python 互動式視窗與陳述式接續](media/getting-started-interactive-3.png)

1. 互動式視窗提供您所輸入之所有資料的完整歷程記錄，並改善包含多行歷程記錄項目的命令列 REPL。 例如，您可以輕鬆地重新叫用上述整個 `f` 函式的定義做為單一單位，並輕鬆地將名稱變更為 `make_double`，而非逐行重新建立函式。

1. 另一個有用的功能是能快速地將多行程式碼從編輯器視窗傳送至互動式視窗中，其中您可在快速 REPL 環境中使用它，而不用撰寫其他程式碼在偵錯工具中執行。 若要查看功能，請先將下列程式碼新增至您已在編輯器中開啟的 hello.py 檔案︰

  ```python
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'
  ```

1. 選取 hello.py 中的所有程式碼 (包括 `import` 陳述式)、按一下滑鼠右鍵，然後選取 [傳送到 Interactive] (Ctrl+Enter)。 程式碼會立即貼入到互動式視窗中並執行。 因為程式碼定義函式，您可以呼叫該函式數次以快速測試它：

    ![將程式碼傳送至互動式視窗](media/getting-started-interactive-4.png)

1. 在編輯器中使用 Ctrl + Enter 搭配在單一行使用插入號，也是一個簡單的方式來逐步執行程式碼。 Ctrl + Enter 會在互動式視窗中執行目前這一行，然後自動將插入號設定到下一行。 重複按下 Ctrl + Enter，您便可以執行檔案中的所有程式碼。

1. 在 Visual Studio 2017 您可以直接將多行貼到互動式視窗 (在舊版，您需要將這些行貼到編輯器視窗、選取它們，並接著使用 [傳送到 Interactive])。 貼上時，互動式視窗會執行該程式碼，如下所示：

  ```python
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

    ![使用互動式傳送貼上多行程式碼](media/getting-started-interactive-5.png)

1. 因為函式定義在 REPL 歷程記錄中是作為單一單位，很容易就能返回並進行您想要的任何變更，並接著再測試一次函式。

1. 當您滿意在互動式視窗中撰寫的程式碼時，您可以選取程式碼、按一下滑鼠右鍵、選取 [複製程式碼]，然後貼入編輯器中。 [複製程式碼] 命令會自動省略任何輸出以及 >>> 和 ... 提示文字。 例如，搭配如下所示的選取範圍使用命令：

  ![互動式視窗複製程式碼命令](media/getting-started-interactive-6.png)

  只會貼上下列程式碼：

  ```python
  make_dot_string(180)
  make_dot_string(135)
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

1. 最後，互動式視窗會提供一些可載入檔案、重設環境而不遺失歷程資料，以及在您進行時插入註解的中繼命令。 如需詳細資訊，請參閱[互動式視窗 - 中繼命令](interactive-repl.md#meta-commands)。

### <a name="going-deeper"></a>繼續探討

- [使用互動式視窗](interactive-repl.md)
- [使用 IPython REPL](interactive-repl-ipython.md)

## <a name="running-code-in-the-debugger"></a>在偵錯工具中執行程式碼

除了管理專案、提供豐富的編輯體驗以及互動式視窗以外，Visual Studio 還針對 Python 程式碼提供其完整功能的偵錯支援。

1. 編輯您 hello.py 檔案中的程式碼，以符合下列：

  ```python  
  from math import sin, cos, radians  
  import sys  
    
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
    
  def main():  
      for i in range(360 * 5):
          s = make_dot_string(i)  
          print(s)  
            
  main()
  ```  

1. 按下 F5，或選取 [偵錯] > [開始偵錯] 功能表命令，檢查程式碼運作是否正常。 此命令會在偵錯工具中執行程式碼，但因為您沒有設定任何中斷點，它只會輸出反覆幾次的波浪圖樣。 此時按下任意鍵會關閉輸出視窗。

    > [!Tip]
    > 若要在程式完成時自動關閉輸出視窗，請使用下列程式碼取代 `main()` 呼叫：
    >
    > ```python    
    > if __name__ == "__main__":  
    >     sys.exit(int(main() or 0))      
    > ```
    > 
    > 或者，如果您遇到輸出視窗自動關閉，但您不想要如此的情況，請以滑鼠右鍵按一下專案、依序選取 [屬性][偵錯] 索引標籤，然後新增 `-i` 至 [解譯器引數] 欄位。 此引數會導致解譯器在程式完成之後進入互動模式，並在您輸入 Ctrl+Z、Enter 以結束之前保持視窗開啟。

1. 在 `main` 函式第一行上設定中斷點，方法是按一下該行旁左側灰色邊界，或者將插入點放在該行，並使用 [偵錯] > [切換中斷點] 命令 (F9)。 灰色邊界會出現紅點，表示中斷點 (如下方藍色箭號所註)：

    ![設定中斷點](media/getting-started-debugging-1.png)

1. 重新啟動偵錯工具，您會看到執行中的程式碼停在含有該中斷點的行。 這裡您可以檢查呼叫堆疊，並檢查 [區域變數] 視窗中的區域變數：

    ![Python 的中斷點 UI 體驗](media/getting-started-debugging-2.png)

1. 使用 F10、[偵錯] > [不進入函式] 命令，或 [不進入函式] 工具列按鈕，逐行進行 `for` 迴圈的幾個反覆項目。 不進入函式表示偵錯工具會執行 `make_dot_string` 的每個呼叫，但不會在該函式內停止 (除非您設定中斷點)。

1. 在工具列中，下方顯示的三個逐步執行按鈕 (由左至右) 為：[逐步執行]、[不進入函式] 和 [跳離函式]：

    ![逐步執行工具列按鈕](media/getting-started-debugging-3.png)

1. 現在使用 [逐步執行] 命令 (F11) 逐步執行 `make_dot_string`。 看到您從 `for` 迴圈逐步執行該函式。 再次逐步執行會回到 `for` 迴圈中，但是如果函式內有其他行，您必須逐一執行它們。 如果您在函式中，且想要執行其程式碼行的其餘部分，並返回呼叫的程式碼，請使用 [跳離函式] (Shift+F11)。

1. 若要繼續執行程式碼直到下一個中斷點 (或程式結束) 為止，再次按下 F5 或選取 [繼續] 工具列按鈕或 [偵錯] > [繼續]。 因為您在 `for` 迴圈中有中斷點，將會在下一個反覆項目中斷。

1. 逐步執行數百個迴圈的反覆項目可能會非常繁瑣，因此您可以針對稍早設定的中斷點新增條件，只在 `i` 的值超過特定值 (例如 1600) 時才中斷。 若要設定條件，以滑鼠右鍵按一下中斷點紅點，然後選取 [條件]。在出現的 [中斷點設定] 視窗中，輸入 `i > 1600` 做為運算式，並選取 [關閉]。 現在，按下 F5 繼續，監看程式在再次中斷前會執行一段時間。 

    ![設定中斷點條件](media/getting-started-debugging-4.png)

1. 若要完成程式，您可以再次切換中斷點，然後按 F5。 偵錯完成時，Visual Studio 會回到其編輯模式。

### <a name="going-deeper"></a>繼續探討

- [偵錯](debugging.md)。
- 如需 Visual Studio 偵錯功能的完整文件，另請參閱 [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md)。

## <a name="next-steps"></a>後續步驟

除了稍早提供的 [繼續探討] 連結以外，下列主題涵蓋 Visual Studio 中 Python 體驗的其他功能：

- 若要查看 Visual Studio 如何連接到 Azure App Service，請參閱[將 Python Web 應用程式發行至 Azure](publishing-to-azure.md)
- 若要探索如何同時全域以及針對個別專案管理不同環境 (包含虛擬環境)，請參閱 [Python 環境](python-environments.md)。
- Visual Studio 提供在遠端伺服器上偵錯您的應用程式的功能，如[跨平台遠端偵錯](debugging-cross-platform-remote.md)和 [Azure 遠端偵錯](debugging-azure-remote.md)中所述。
- 您可以使用 [Visual Studio 程式碼剖析](profiling.md)評估您的 Python 程式碼的效能。
- 以 Python 撰寫的單元測試會直接與 Visual Studio 測試總管整合，如[單元測試](unit-testing.md)中所討論。
- [Microsoft Virtual Academy 上的免費 Python 課程](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Top Python Questions at Microsoft Virtual Academy](https://aka.ms/mva-top-python-questions) (Microsoft Virtual Academy 的前幾個 Python 問題)

