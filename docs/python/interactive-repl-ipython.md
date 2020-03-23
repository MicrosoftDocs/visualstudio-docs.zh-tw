---
title: IPython REPL (互動式視窗)
description: 在 IPython 模式中使用 Visual Studio 互動式視窗，以取得具有「互動式平行運算」功能且方便使用的互動式開發環境。
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8b4510ed738fdd2b33389ab4242dbde86cffff8c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957722"
---
# <a name="use-ipython-in-the-interactive-window"></a>在互動式視窗中使用 IPython

IPython 模式的 Visual Studio [互動式]**** 視窗，是個進階但容易使用的互動式開發環境，且具有「互動式平行計算」功能。 本文將逐步解說如何在 Visual Studio [互動式]**** 視窗中使用 IPython；該視窗也提供所有的一般[互動式視窗](python-interactive-repl-in-visual-studio.md)功能。

針對此逐步解說，您需要安裝 [Anaconda](https://www.continuum.io) 環境，其中包含 IPython 和必要的程式庫。

> [!Note]
> IronPython 並不支援 IPython，雖然您可以在 [互動式選項]**** 表單中選取它。 如需詳細資訊，請參閱[功能要求](https://github.com/Microsoft/PTVS/issues/84)。

1. 開啟 Visual Studio，切換到 [Python 環境]**** 視窗 ([檢視]**** > [其他視窗]**** > [Python 環境]****)，然後選取 Anaconda 環境。

2. 檢查該環境的 [套件 (Conda)]**** 索引標籤 (這可能會顯示為 [pip]**** 或 [套件]****)，以確定會列出 `ipython` 和 `matplotlib`。 如果沒有，請在這裡安裝它們。 (請參閱 [Python 環境視窗 - 套件索引標籤](python-environments-window-tab-reference.md))。

3. 選擇 **"概述**"選項卡，然後選擇 **"使用 IPython 交互模式**"。 （在 Visual Studio 2015 中，選擇 **"配置互動式選項**"以打開 **"選項**"對話方塊，然後將**互動式模式**設置為**IPython，** 然後選擇 **"確定**"。

4. 選擇 **"打開互動式視窗**"以在 IPython 模式下打開**互動式**視窗。 如果您剛變更互動模式，可能需要重設視窗，如果僅出現 >>> 提示，也可能需要按下 **Enter** 鍵，讓您收到如 **In [2]** 的提示。

    ![IPython 模式的互動式視窗](media/ipython-repl-03.png)

5. 輸入下列程式碼：

   ```python
   import matplotlib.pyplot as plt
   import numpy as np

   x = np.linspace(0, 5, 10)
   y = x ** 2
   plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
   ```

6. 輸入最後一行之後，您應該會看到一個内嵌圖表 (您可以視需要拖曳右下角來調整大小)。

    ![互動式視窗中的內嵌圖表](media/ipython-repl-04.png)

7. 您可以改為在編輯器中編寫代碼、選擇它、按右鍵並選擇"**發送到互動式**"命令（或按**Ctrl**+**Enter）** 而不是鍵入 REPL。 嘗試將下面的代碼粘貼到編輯器中的新檔中，使用**Ctrl**+**A**選擇它，然後發送到**互動式**視窗。 (Visual Studio 將程式碼以單一單位傳送，以避免產生過渡或部分的圖表。 同時，如果您尚未開啟 Python 專案並選取不同的環境，Visual Studio 會為選取的任何環境開啟 [互動式]**** 視窗，作為 [Python 環境]**** 視窗中的預設值。)

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set is colored cyan.
        cs = [c] * len(xs)
        cs[0] = 'c'
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X')
    ax.set_ylabel('Y')
    ax.set_zlabel('Z')
    plt.show()
    ```

    ![將程式碼從編輯器傳送至互動式視窗](media/ipython-repl-05.png)

8. 若要在 [互動式]**** 視窗外查看圖表，請改為使用 [偵錯]**** > [啟動但不偵錯]**** 命令來執行程式碼。

IPython 具有許多其他有用的功能，如轉義到系統外殼、變數替換、捕獲輸出等。有關詳細資訊，請參閱[IPython 文檔](https://ipython.org/documentation.html)。

## <a name="see-also"></a>另請參閱

- 若要輕鬆使用 Jupyter，且不需安裝，請嘗試免費的 [Azure Notebooks 託管服務](https://notebooks.azure.com/)，可讓您保留並與其他人共用您的筆記。

- [Azure 資料科學虛擬機器](/azure/machine-learning/data-science-virtual-machine/overview)也會預先設定為執行 Jupyter Notebook，以及各種其他資料科學工具。
