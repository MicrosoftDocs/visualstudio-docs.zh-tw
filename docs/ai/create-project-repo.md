---
title: 複製存放庫
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 73f1595e0e6c8f182f0bedcece51011390964ed2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "62539615"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>在 Visual Studio 中複製 Python 程式碼存放庫

在[安裝適用於 AI 的 Visual Studio 工具](installation.md)之後，您可以輕易的複製 Python 程式碼存放庫並從中建立專案。

1. 要連接到 GitHub 存儲庫，請運行 Visual Studio 安裝程式，選擇 **"修改**"，然後選擇 **"單個元件**"選項卡。 向下滾動到 **"代碼工具"** 部分，為 Visual Studio 選擇**GitHub 擴展**名，然後選擇"**修改**"。

    ![在 Visual Studio 安裝程式中選取 GitHub 延伸模組](media/create-project-repo/installation-github-extension.png)

2. 啟動 Visual Studio。

3. 選擇 **"查看>Team 總管**以打開**Team 總管**視窗，您可以在該視窗中連接到 GitHub 或 Azure DevOps，或克隆存儲庫。

    ![顯示 Azure DevOps 和 GitHub 並複製存放庫的 Team Explorer 視窗](media/create-project-repo/team-explorer-devops.png)

4. 在 [本機 Git 存放庫]**** 下的 [URL] 欄位中，輸入 `https://github.com/Microsoft/samples-for-ai`，輸入複製檔案的資料夾，然後選取 [複製]****。

    > [!Tip]
    > 您在 Team Explorer 中指定的資料夾是用來接收所複製檔案的特定資料夾。 不同於 `git clone` 命令，在 Team Explorer 中建立複製品不會自動使用儲存機制的名稱來建立子資料夾。

5. 複製完成時，請按兩下 Team Explorer 底部的存放庫資料夾，以巡覽至存放庫儀表板。 在 [解決方案]**** 下，選取 [新增]****。

    ![從複製品建立新專案的 Team Explorer 視窗](media/create-project-repo/team-explorer-new-project.png)

6. 在顯示**的"新專案**"對話方塊中，選擇"**從現有 Python 代碼**"，指定專案的名稱，將**位置**設置為與存儲庫相同的資料夾，然後選擇 **"確定**"。 在出現的精靈中，選取 [完成]****。

7. 從功能表中選取 [檢視] > 方案總管****。

8. 在解決方案資源管理器中`TensorFlow Examples> MNIST`，展開節點，按右鍵`convolutional.py`，然後選擇"**設置為開機檔案**"。 此步驟會告訴 Visual Studio 在執行專案時應該使用哪個檔案。

9. 按**Ctrl**+**F5**或選擇**調試>無需調試即可**運行程式。 如果您看到錯誤，請重新檢查上一個步驟中的工作目錄設定。

10. 當程式成功執行時，您會看到它開始下載您的訓練及測試資料集，然後訓練模型並輸出您的錯誤率。 通常您會希望錯誤率隨著時間遞減

    ![Pytho MNIST 程式的第一次輸出結果](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > 若您使用的是 Anaconda 並收到了遺漏 numpy 的錯誤訊息，則可能需要[將 Python 環境變更為使用 Anaconda](../python/selecting-a-python-environment-for-a-project.md)。

11. 您可以使用 TensorBoard 來視覺化進度。 以滑鼠右鍵按一下您的專案，按一下 [Run TensorBoard] (執行 TensorBoard)****，然後選取您輸出 TensorBoard 記錄檔的目錄。

   ![執行 TensorBoard](media/create-project-repo/run-tensorboard.png)

12. 請注意，錯誤已隨著時間遞減，表示品質正在改善。

   ![執行 TensorBoard](media/create-project-repo/tensorboard.png)
