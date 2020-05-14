---
title: Visual Studio 中的 Python 教學課程步驟 5，安裝套件
titleSuffix: ''
description: 在 Visual Studio 中 Python 功能核心逐步解說的步驟 5，示範 Visual Studio 在 Python 環境中管理套件的功能。
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5e2644ccfff0e7c653f4ce2680299aea95a55ef9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "79372901"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>步驟 5：在 Python 環境中安裝套件

**上一步：[在偵錯工具中執行程式碼](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Python 開發人員社群已產生數千個有用的套件，您可以將它們加入自己的專案。 Visual Studio 提供了一個可在 Python 環境中管理套件的 UI。

## <a name="view-environments"></a>檢視環境

1. 選擇"**查看** > **其他 Windows** > **Python 環境**"功能表命令。 **Python 環境**視窗將作為**解決方案資源管理器**的對等方打開，並顯示可供您使用的不同環境。 該清單顯示使用 Visual Studio 安裝程式安裝的環境和單獨安裝的環境。 這包括全域環境、虛擬環境和環境環境。 以粗體顯示的環境是針對新專案使用的預設環境。 有關使用環境的其他資訊，請參閱如何在[Visual Studio 環境中創建和管理 Python 環境](managing-python-environments-in-visual-studio.md)。

   ![[Python Environments (Python 環境)] 視窗](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > 還可以通過按一下"解決方案資源管理器"視窗並使用 Ctrl_K、Ctrl+' 鍵盤快速鍵打開 Python 環境視窗。 如果快捷方式不起作用，並且在功能表中找不到 Python 環境視窗，則可能尚未安裝 Python 工作負荷。 有關如何安裝 Python 的指導，請參閱[如何在視覺化工作室中安裝 Python 支援](installing-python-support-in-visual-studio.md)。

2. 環境的 **"概述"** 選項卡提供對該環境**的互動式**視窗的快速訪問以及環境的安裝資料夾和解譯器。 例如，選擇 **"打開互動式視窗**"，該特定環境**的互動式**視窗將顯示在"視覺工作室"中。

3. 現在，使用**檔** > **新專案** > 創建新**專案**，選擇**Python 應用程式**範本。 在顯示的代碼檔中，粘貼以下代碼，該代碼創建與前面的教程步驟一樣的久元波，但這次只是以圖形方式繪製。 或者，您可以使用以前創建的專案並替換代碼。 

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

4. 打開 Python 專案後，您還可以通過按右鍵 Python 環境並選擇 **"查看所有 Python 環境**"，從解決方案資源管理器打開 Python 環境視窗

   ![環境](media/environments/environments-view-all-2019.png)

5. 查看編輯器視窗時，您會注意到，如果將滑鼠懸停在 未解析`numpy`的`matplotlib`和 導入語句上。 這是因為包尚未安裝到預設的全域環境。

   ![未解析的包導入](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>使用 Python 環境視窗安裝包

1. 在"Python 環境"視窗中，按一下新 Python 專案的預設環境並選擇 **"包**"選項卡。然後，您將看到當前安裝在環境中的包的清單。

   ![環境中安裝的套件](media/environments/environments-installed-packages-2019.png)

2. 通過在`matplotlib`搜索欄位中輸入其名稱，然後選擇 **"運行"命令：點點安裝 matplotlib**選項進行安裝。 這將安裝`matplotlib`，以及它所依賴的任何包（在本例中包括`numpy`）。

   ![在環境中安裝 matplotlib](media/environments/environments-add-matplotlib-2019.png)

5. 如果系統提示您提高權限，請同意這樣做。

6. 安裝包後，它將顯示在**Python 環境**視窗中。 套件右側的 **X** 可用來進行解除安裝。

   ![在環境中完成安裝 matplotlib](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > 環境下方可能會出現一個小進度列，以指示 Visual Studio 正在為新安裝的包構建其 IntelliSense 資料庫。 [IntelliSense]**** 索引標籤也會顯示更詳細的資訊。 請注意，在該資料庫完成之前，IntelliSense 功能（如自動完成和語法檢查）將不會在該包的編輯器中處於活動狀態。
   > 
   > Visual Studio 2017 版本 15.6 及更高版本使用不同且速度更快的方法來使用 IntelliSense，並在**IntelliSense**選項卡上顯示一條有關該效果的消息。

## <a name="run-the-program"></a>執行程式

1. 現在[安裝 matplotlib，](https://matplotlib.org/)使用 （**F5**） 運行程式或沒有調試器 （**Ctrl**+**F5**） 以查看輸出：

   ![matplotlib 範例的輸出](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>後續步驟

> [!div class="nextstepaction"]
> [使用 Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>深入了解

- [Python 環境](managing-python-environments-in-visual-studio.md)
- [了解 Visual Studio 中的 Django](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [了解 Visual Studio 中的 Flask](learn-flask-visual-studio-step-01-project-solution.md)
