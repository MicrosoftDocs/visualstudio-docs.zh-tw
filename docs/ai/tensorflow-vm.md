---
title: 在雲端中執行 TensorFlow 模型
description: 在 Azure 深度學習 VM 中執行 TensorFlow 模型
keywords: AI, Visual Studio, 深度學習虛擬機器
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: tutorial
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 8f6aef2d0cf8fe727036dda91256ac0330e15d37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841311"
---
# <a name="train-a-tensorflow-model-in-the-cloud"></a>在雲端中定型 TensorFlow 模型

在本教學課程中，我們將在 Azure [深度學習](/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview)虛擬機器上，使用 [MNIST 資料集](http://yann.lecun.com/exdb/mnist/)來定型 TensorFlow 模型。

MNIST 資料庫具有 60,000 個範例的定型集，以及 10,000 個手寫數字範例的測試集。

## <a name="prerequisites"></a>必要條件
開始之前，請確定您已安裝並設定下列項目：

### <a name="setup-azure-deep-learning-virtual-machine"></a>設定 Azure 深度學習虛擬機器

> [!NOTE]
> 將 [OS 類型] 設定為 Linux。

您可以在[這裡](/azure/machine-learning/data-science-virtual-machine/provision-deep-learning-dsvm)找到設定深度學習虛擬機器的指示。

### <a name="remove-comment-in-parens"></a>移除括弧中的註解

```bash
echo -e ". /etc/profile\n$(cat ~/.bashrc)" > ~/.bashrc
```

### <a name="download-sample-code"></a>下載範例程式碼

下載這個 [GitHub 存放庫](https://github.com/Microsoft/samples-for-ai)，其中包含深度學習 TensorFlow、CNTK、Theano 等使用者入門範例。

## <a name="open-project"></a>開啟專案

- 啟動 Visual Studio，然後選取 [檔案] > [開啟] > [專案/方案]。

- 從下載的範例存放庫中選取 **TensorFlow 範例** 資料夾，然後開啟 **TensorflowExamples.sln** 檔案。

   ![開啟專案](media/tensorflow-local/open-project.png)

   ![開啟方案](media/tensorflow-local/open-solution.png)

## <a name="add-azure-remote-vm"></a>新增 Azure 遠端 VM

在伺服器總管中，以滑鼠右鍵按一下 [AI Tools] (AI 工具) 節點下的 [遠端機器] 節點，然後選取 [新增…]。 輸入遠端電腦的顯示名稱、IP 主機、SSH 連接埠、使用者名稱及密碼/金鑰檔案。

![新增遠端電腦](media/tensorflow-vm/add-remote-vm.png)

## <a name="submit-job-to-azure-vm"></a>對 Azure VM 提交作業
在 **方案總管** 中，以滑鼠右鍵按一下 MNIST 專案，然後選取 [提交作業]。

![對遠端電腦提交作業](media/tensorflow-vm/job-submission.png)

在提交視窗中：

- 在 [使用叢集] 清單中，選取要提交作業的目標遠端電腦 (字首為 "rm:")。

- 輸入 **作業名稱**。

- 按一下 [提交]  。

## <a name="check-status-of-job"></a>檢查作業的狀態
若要查看作業的狀態和詳細資料：在 **伺服器總管** 中展開您提交作業的目標虛擬機器。 按兩下 [作業]。

![作業瀏覽器](media/tensorflow-vm/job-browser.png)

## <a name="clean-up-resources"></a>清除資源

如果您計劃在不久的未來使用它，請停止 VM。 如果您已完成本教學課程，請執行下列命令來清除資源：

```azurecli-interactive
az group delete --name myResourceGroup
```
