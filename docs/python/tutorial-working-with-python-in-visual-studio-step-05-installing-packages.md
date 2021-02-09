---
title: Visual Studio 中的 Python 教學課程步驟 5，安裝套件
titleSuffix: ''
description: 在 Visual Studio 中 Python 功能核心逐步解說的步驟 5，示範 Visual Studio 在 Python 環境中管理套件的功能。
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c47eacf0c9977e7342bfda17e03ea53728ee9215
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901152"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>步驟 5：在 Python 環境中安裝套件

**上一步：[在偵錯工具中執行程式碼](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Python 開發人員社群已產生數千個有用的套件，您可以將它們加入自己的專案。 Visual Studio 提供了一個可在 Python 環境中管理套件的 UI。

## <a name="view-environments"></a>檢視環境

1. 選取 [**查看**  >  **其他 Windows**  >  **Python 環境**] 功能表命令。 [ **Python 環境** ] 視窗會開啟成為 **方案總管** 的對等，並顯示可供您使用的不同環境。 此清單會顯示您使用 Visual Studio 安裝程式安裝的環境，以及您另外安裝的環境。 這包括全域、虛擬和 conda 環境。 以粗體顯示的環境是針對新專案使用的預設環境。 如需有關使用環境的詳細資訊，請參閱 [如何在 Visual Studio 環境中建立和管理 Python 環境](managing-python-environments-in-visual-studio.md)。

   ![[Python Environments (Python 環境)] 視窗](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > 您也可以選取方案總管視窗，然後使用 **ctrl + K、ctrl +** 鍵盤快速鍵，來開啟 [Python 環境] 視窗。 如果快速鍵無法運作，而且您在功能表中找不到 [Python 環境] 視窗，則可能尚未安裝 Python 工作負載。 如需如何安裝 Python 的指引，請參閱 [如何在 Visual Studio 中安裝 python 支援](installing-python-support-in-visual-studio.md) 。

2. 環境的 **[總覽** ] 索引標籤可讓您快速存取該環境的 **互動式** 視窗，以及環境的安裝資料夾和解譯器。 例如，選取 [ **開啟互動式視窗]** ，該特定環境的 **互動式** 視窗會出現在 Visual Studio 中。

3. 現在，使用 [檔案新增專案] 建立 **新的專案**  >    >  ****，然後選取 [ **Python 應用程式**] 範本。 在出現的程式碼檔案中，貼上下列程式碼，此程式碼會建立類似先前教學課程步驟的余弦波，而只有這段時間以圖形方式繪製。 或者，您可以使用先前建立的專案，並取代程式碼。

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

4. 當 Python 專案開啟時，您也可以在 [ **Python 環境**] 上按一下滑鼠右鍵，然後選取 [**查看所有 python 環境**]，從方案總管開啟 [python 環境] 視窗。

   ![環境](media/environments/environments-view-all-2019.png)

5. 查看編輯器視窗時，您會注意到，如果您將滑鼠停留在上方 `numpy` 並匯 `matplotlib` 入語句，則不會加以解析。 這是因為封裝尚未安裝至預設的全域環境。

   ![未解析的套件匯入](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>使用 Python 環境視窗安裝套件

1. 從 [Python 環境] 視窗中，選取新 Python 專案的預設環境，然後選擇 [ **封裝** ] 索引標籤。然後，您會看到目前安裝在環境中的套件清單。

   ![環境中安裝的套件](media/environments/environments-installed-packages-2019.png)

2. 在 `matplotlib` [搜尋] 欄位中輸入其名稱，然後選取 [ **執行命令： pip install matplotlib** ] 選項以進行安裝。 這將會安裝 `matplotlib` ，以及它所相依的任何套件 (在此案例中包含 `numpy`) 。

   ![在環境中安裝 matplotlib](media/environments/environments-add-matplotlib-2019.png)

5. 如果系統提示您提高權限，請同意這樣做。

6. 安裝套件之後，它會出現在 [ **Python 環境** ] 視窗中。 套件右側的 **X** 可用來進行解除安裝。

   ![在環境中完成安裝 matplotlib](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > 環境下方可能會出現一個小的進度列，指出 Visual Studio 正在為新安裝的套件建立其 IntelliSense 資料庫。 [IntelliSense] 索引標籤也會顯示更詳細的資訊。 請注意，在該資料庫完成之前，編輯器中的 IntelliSense 功能（例如自動完成和語法檢查）不會在該封裝的編輯器中作用。
   >
   > Visual Studio 2017 15.6 版和更新版本會使用不同且更快速的方法來處理 IntelliSense，並在 [ **intellisense** ] 索引標籤上顯示該效果的訊息。

## <a name="run-the-program"></a>執行程式

1. 現在已安裝 [matplotlib](https://matplotlib.org/) ，請使用 (**F5**) 執行程式，或不使用偵錯工具 (**Ctrl** + **F5**) 以查看輸出：

   ![matplotlib 範例的輸出](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>後續步驟

> [!div class="nextstepaction"]
> [使用 Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>深入了解

- [Python 環境](managing-python-environments-in-visual-studio.md)
- [了解 Visual Studio 中的 Django](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [了解 Visual Studio 中的 Flask](learn-flask-visual-studio-step-01-project-solution.md)
