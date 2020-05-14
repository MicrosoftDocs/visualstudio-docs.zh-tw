---
title: 複製存放庫
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: d146d801a1519d3282b4e2c5dd72fd23b0df7206
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638636"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>在 Visual Studio 中複製 Python 程式碼存放庫

在[安裝適用於 AI 的 Visual Studio 工具](installation.md)之後，您可以輕易的複製 Python 程式碼存放庫並從中建立專案。

1. 要連線到 GitHub 儲存函式庫,請執行 Visual Studio 安裝程式,選擇 **「修改**」,然後選擇 **「單個元件**」選項卡。 往您捲動到 **「代碼工具」** 部分,為 Visual Studio 選擇**GitHub 擴充**名,然後選擇 **「 修改**」 。

    ![在 Visual Studio 安裝程式中選取 GitHub 延伸模組](media/create-project-repo/installation-github-extension.png)

2. 啟動 Visual Studio。

3. 選擇 **「檢視>團隊資源管理員**」 以開啟**團隊資源管理員**視窗,您可以在該視窗中連接到 GitHub 或 Azure DevOps,或複製儲存庫。

    ![顯示 Azure DevOps 和 GitHub 並複製存放庫的 Team Explorer 視窗](media/create-project-repo/team-explorer-devops.png)

4. 在 [本機 Git 存放庫]**** 下的 [URL] 欄位中，輸入 `https://github.com/Microsoft/samples-for-ai`，輸入複製檔案的資料夾，然後選取 [複製]****。

    > [!Tip]
    > 您在 Team Explorer 中指定的資料夾是用來接收所複製檔案的特定資料夾。 不同於 `git clone` 命令，在 Team Explorer 中建立複製品不會自動使用儲存機制的名稱來建立子資料夾。

5. 複製完成時，請按兩下 Team Explorer 底部的存放庫資料夾，以巡覽至存放庫儀表板。 在 [解決方案]**** 下，選取 [新增]****。

    ![從複製品建立新專案的 Team Explorer 視窗](media/create-project-repo/team-explorer-new-project.png)

6. 在顯示**的「新項目**」對話框中,選擇「**從現有 Python 代碼**」,指定項目的名稱,將**位置**設定為與儲存庫相同的資料夾,然後選擇 **「確定**」。 在出現的精靈中，選取 [完成]****。

7. 從功能表中選取 [檢視] > 方案總管****。

8. 在解決方案資源管理器中`TensorFlow Examples> MNIST`,展開節點,右鍵單`convolutional.py`擊 ,然後選擇「**設定為啟動檔**」。 此步驟會告訴 Visual Studio 在執行專案時應該使用哪個檔案。

9. 按**Ctrl**+**F5**或選擇**調試>無需調試即可**運行程式。 如果您看到錯誤，請重新檢查上一個步驟中的工作目錄設定。

10. 當程式成功執行時，您會看到它開始下載您的訓練及測試資料集，然後訓練模型並輸出您的錯誤率。 通常您會希望錯誤率隨著時間遞減

    ![Pytho MNIST 程式的第一次輸出結果](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > 若您使用的是 Anaconda 並收到了遺漏 numpy 的錯誤訊息，則可能需要[將 Python 環境變更為使用 Anaconda](../python/selecting-a-python-environment-for-a-project.md)。

11. 您可以使用 TensorBoard 來視覺化進度。 以滑鼠右鍵按一下您的專案，按一下 [Run TensorBoard] (執行 TensorBoard)****，然後選取您輸出 TensorBoard 記錄檔的目錄。

   ![執行 TensorBoard](media/create-project-repo/run-tensorboard.png)

12. 請注意，錯誤已隨著時間遞減，表示品質正在改善。

   ![執行 TensorBoard](media/create-project-repo/tensorboard.png)
