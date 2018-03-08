---
ms.technology: vs-ai-tools
ms.openlocfilehash: 73292b9e0c7df23db839a7a13f70dbc2432d564f
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>在 Visual Studio 中複製 Python 程式碼存放庫

在[安裝適用於 AI 的 Visual Studio 工具](installation.md)之後，您可以輕易的複製 Python 程式碼存放庫並從中建立專案。

1. 若要連線至 GitHub 存放庫，請執行 Visual Studio 安裝程式，並選取 [修改]，然後選取 [個別元件] 索引標籤。向下捲動至 [程式碼工具] 區段，並選取 [Visual Studio 的 GitHub 延伸模組]，然後選取 [修改]。

    ![在 Visual Studio 安裝程式中選取 GitHub 延伸模組](media\create-project-repo\installation-github-extension.png)

2. 啟動 Visual Studio。

3. 選取 [檢視] > [Team Explorer...] 以開啟 **Team Explorer** 視窗，您可以從中連線到 GitHub 或 Visual Studio Team Services，或是複製存放庫。

    ![顯示 Visual Studio Team Services 和 GitHub 並複製存放庫的 Team Explorer 視窗](media\create-project-repo\team-explorer.png)

4. 在 [本機 Git 存放庫] 下的 [URL] 欄位中，輸入 `https://github.com/Microsoft/samples-for-ai`，輸入複製檔案的資料夾，然後選取 [複製]。

    > [!Tip]
    > 您在 Team Explorer 中指定的資料夾是用來接收所複製檔案的特定資料夾。 不同於 `git clone` 命令，在 Team Explorer 中建立複製品不會自動使用存放庫的名稱來建立子資料夾。

5. 複製完成時，請按兩下 Team Explorer 底部的存放庫資料夾，以巡覽至存放庫儀表板。 在 [方案] 下，選取 [新增]。

    ![從複製品建立新專案的 Team Explorer 視窗](media\create-project-repo\team-explorer-new-project.png)

6. 在出現的 [新增專案] 對話方塊中，選取 [從現有 Python 程式碼]，並指定專案名稱，再將 [位置] 設定為與存放庫相同的資料夾，然後選取 [確定]。 在出現的精靈中，選取 [完成]。

7. 從功能表中選取 [檢視] > 方案總管。

8. 在方案總管中，展開 `TensorFlow Examples> MNIST` 節點，並以滑鼠右鍵按一下 `convolutional.py`，然後選取 [設定為啟動檔案]。 此步驟會告訴 Visual Studio 在執行專案時應該使用哪個檔案。

10. 按 Ctrl + F5，或是選取 [偵錯] > [啟動但不偵錯]，以執行程式。 如果您看到 `，請重新檢查上一個步驟中的工作目錄設定。


11. 當程式成功執行時，您會看到它開始下載您的訓練及測試資料集，然後訓練模型並輸出您的錯誤率。 通常您會希望錯誤率隨著時間遞減

    ![Pytho MNIST 程式的第一次輸出結果](media\create-project-repo\tensorflow-mnist-running.png)

> 若您使用的是 Anaconda 並收到了遺漏 numpy 的錯誤訊息，則可能需要[將 Python 環境變更為使用 Anaconda](../python/selecting-a-python-environment-for-a-project.md)。

11. 您可以使用 TensorBoard 來視覺化進度。 以滑鼠右鍵按一下您的專案，按一下 [Run TensorBoard] (執行 TensorBoard)，然後選取您輸出 TensorBoard 記錄檔的目錄。

    ![執行 TensorBoard](media\create-project-repo\run-tensorboard.png)

11. 請注意，錯誤已隨著時間遞減，表示品質正在改善

    ![執行 TensorBoard](media\create-project-repo\tensorboard.png)