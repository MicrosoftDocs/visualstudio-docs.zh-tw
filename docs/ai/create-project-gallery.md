---
title: 建立專案
description: 使用 Azure Machine Learning 資源庫中的範例來建立專案
keywords: AI, Visual Studio, Azure Machine Learning
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: a6813e834af00330b4018f16d4a19be945be2be9
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726640"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>在 Visual Studio 中從 Azure Machine Learning 資源庫建立 AI 專案

Azure Machine Learning 與 Visual Studio Tools for AI 整合。 您可以使用它來提交機器學習作業給 Azure 虛擬機器、Spark 叢集等遠端計算目標。 

[安裝 Visual Studio Tools for AI](installation.md) 之後，您就可以使用 Azure Machine Learning 範例庫中預先製作的配方，輕鬆建立新的 Python 專案。

> [!NOTE]
> 您必須安裝 Azure Machine Learning Workbench。 

1. 啟動 Visual Studio。 開啟 [AI Tools] (AI 工具) 功能表，然後選擇 [選取叢集] 以開啟 **伺服器總管**

    ![叢集選擇器](media/create-project-gallery/select-cluster.png)

2. 在伺服器總管中以滑鼠右鍵按一下 [Azure Machine Learning] 節點，然後選取 [登入] 並遵循指示進行，以登入您的 Azure Machine Learning 訂用帳戶。

    ![login](media/create-project-gallery/azureml-login.png)

3. 選取 [AI Tools] (AI 工具) > [Azure Machine Learning 範例庫]。

    ![範例庫](media/create-project-gallery/gallery.png)

4. 針對本快速入門，選取 [MNIST using TensorFlow] (使用 TensorFlow 的 MNIST) 範例，然後按一下 [安裝]。 提供下列項目：

   - **資源群組**：儲存中繼資料的 Azure 資源群組
   - **帳戶**：Azure Machine Learning 測試帳戶
   - **工作區**：Azure Machine Learning 工作區
   - **專案類型**：機器學習架構。 在本例中選擇 [TensorFlow]
   - **至方案**：決定要新增至目前的 Visual Studio 方案，或建立並開啟新的方案
   - **專案路徑**：儲存程式碼的位置
   - **專案名稱**：鍵入 **TensorFlowMNIST**

   ![使用 Python 應用程式範本時所產生的專案](media/create-project-gallery/new-AzureSampleProject.png)

5. Visual Studio 會建立專案檔 (磁碟上的 `.pyproj` 檔) 及範例中定義的其他檔案。 使用 "MNIST" 範本時，專案會包含數個檔案。

    ![Visual Studio 方案總管的螢幕擷取畫面，其中顯示 >tensorflowmnist 專案的檔案。 Tf_mnist 的程式碼會顯示在主視窗中。](media/create-project-gallery/azml-mnist.png)

6. 將作業提交至 Azure Machine Learning。

    ![Visual Studio 方案總管的螢幕擷取畫面，其中顯示 [提交作業 ...] >tensorflowmnist 專案的內容功能表選擇。](media/create-project-gallery/submit-azml.png)

7. 在 Docker 容器中或您的本機電腦上執行

    ![[提交作業] 對話方塊的螢幕擷取畫面，其中使用叢集設定為 "azureml：/local" 和啟動腳本設定為 "tf_mnist .py"。](media/create-project-gallery/azml-local.png)
