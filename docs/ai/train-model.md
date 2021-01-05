---
title: 提交作業來定型模型
description: 使用 Azure Batch AI 提交作業來定型模型
ms.custom: SEO-VS-2020
keywords: AI, Visual Studio, 定型模型, 雲端
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: 72f5fa5aab9f9afa6268f8acd737430af0568928
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727355"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>在 Azure Batch AI 中定型 AI 模型

Batch AI 是一項受控服務，可讓資料科學家和 AI 研究人員在 Azure 虛擬機器 (包括具有 GPU 支援的 VM) 叢集上定型 AI 和其他機器學習模型。 您可描述您的作業需求、尋找輸入和儲存輸出的位置，而 Batch AI 會處理其餘部分。 [深入了解 Azure Batch AI](/azure/batch-ai/overview)

它與 Visual Studio Tools for AI 整合，因此您可以在 Azure 中動態相應放大定型模型。  [安裝 Visual Studio Tools for AI](installation.md) 之後，您就可以使用 Azure Machine Learning 範例庫中預先製作的配方，輕鬆建立新的 Python 專案。

1. 啟動 Visual Studio。 開啟 [AI Tools] (AI 工具) 功能表，然後選擇 [選取叢集] 以開啟 **伺服器總管**

    ![叢集選擇器](media/train-model/select-cluster.png)

2. 展開 [AI Tools] (AI 工具)。 系統會自動偵測您所擁有的 Batch AI 資源，並顯示在伺服器總管中。

    ![伺服器總管中 AI 工具展開資料夾樹狀結構的螢幕擷取畫面，其中顯示 Azure Batch AI 和 Azure Machine Learning 的展開子資料夾。](media/train-model/batchai.png)

3. 選取 [檢視] > [Team Explorer...] 以開啟 [Team Explorer] 視窗，您可以從中連線到 GitHub 或 Azure DevOps，或是複製存放庫。

    ![顯示 Azure DevOps 和 GitHub 並複製存放庫的 Team Explorer 視窗](media/train-model/team-explorer-devops.png)

4. 在 [本機 Git 存放庫] 下的 [URL] 欄位中，輸入 `https://github.com/Microsoft/samples-for-ai`，輸入複製檔案的資料夾，然後選取 [複製]。

    > [!Tip]
    > 您在 Team Explorer 中指定的資料夾是用來接收所複製檔案的特定資料夾。 不同於 `git clone` 命令，在 Team Explorer 中建立複製品不會自動使用儲存機制的名稱來建立子資料夾。

5. 複製完成時，按一下 [檔案] > [開啟方案] > [專案/方案]

    ![螢幕擷取畫面，顯示已選取 [開啟] 命令的部分伺服器總管 [檔案] 功能表，以及在操作功能表上選取 [專案/方案]。](media/train-model/open-solution.png)

6. 開啟您複製儲存機制之目錄中的 **samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln**

    ![螢幕擷取畫面，顯示範例-ai 儲存機制的 >samples-for-ai\tensorflowexamples\tensorflowexamples.sln 資料夾內容中所列的方案檔 >samples-for-ai\tensorflowexamples\tensorflowexamples.sln。](media/train-model/tensorflowexamples.png)

7. 將 MNIST 專案設定為 **啟始專案**

    ![顯示方案總管中 MNIST 專案的內容功能表上選取 [設定為啟始專案] 的螢幕擷取畫面。](media/train-model/mnist-startup.png)

8. <strong>以滑鼠右鍵按一下 [MNIST 專案]**、[提交作業]**</strong>

    ![顯示方案總管中 MNIST 專案的內容功能表上選取之提交工作的螢幕擷取畫面。](media/train-model/submit-job.png)
9. 選取您的 **Azure Batch AI** 叢集，然後按一下 [匯入]。 選取 `AzureBatchAI_TF_MNIST.json` 檔案，以快速填入一些預設值，例如要使用哪一個 Docker 映像。 然後按一下 [提交]

    ![[提交作業] 對話方塊的螢幕擷取畫面，其中已填入使用叢集、啟動腳本、作業名稱、映射名稱、StdOutErr 路徑前置詞和 CLI 參數的值。](media/train-model/submit-batch.png)
