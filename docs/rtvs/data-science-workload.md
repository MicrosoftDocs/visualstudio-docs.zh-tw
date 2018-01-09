---
title: "Visual Studio 中的資料科學與分析應用程式工作負載 | Microsoft Docs"
ms.custom: 
ms.date: 09/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
- devlang-python
- devlang-fsharp
ms.tgt_pltfrm: 
ms.topic: landing-page
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: data-science
ms.openlocfilehash: 97debeab6349fefee48d6c550c39c18c3e516b75
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="data-science-and-analytical-applications-workload"></a>資料科學與分析應用程式工作負載

Visual Studio 中的 資料科學與分析應用程式工作負載結合三種語言和其個別執行階段散發：

- [R 和 Microsoft R Client](../rtvs/index.md)
- [Python 和 Anaconda](../python/python-in-visual-studio.md)
- [含 .NET Framework 的 F#](https://docs.microsoft.com/dotnet/fsharp/)

![Visual Studio 安裝程式中的資料科學與分析應用程式工作負載](media/data-science-workload.png)

R 和 Python 是兩個用於資料科學的主要指令碼語言。 這兩種語言都很容易了解，而且多種套件生態系統都予以支援。 這些套件處理各種案例 (例如資料取得、清理、模型訓練、部署和繪製)。 F# 是一種功能強大的功能優先 .NET 語言，適合各種資料處理工作。

<!--Note link on the image because this one is large -->
[![含 R、Python 和 F# 的 Visual Studio 螢幕擷取畫面](media/data-science-workload-screens.png)](media/data-science-workload-screens.png)

## <a name="workload-options"></a>工作負載選項

根據預設，工作負載會安裝下列選項，而您可以在 Visual Studio 安裝程式中工作負載的 [摘要] 區段內對其進行修改：

- F # 語言支援
- Python：
  - Python 語言支援
  - Python Web 支援
  - [Anaconda3 64 位元](https://www.continuum.io) (包含大量資料科學程式庫和 Python 解譯器的 Python 散發)
  - Cookiecutter 範本支援
- R:
  - R 語言支援
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (Microsoft 的完全相容、社群支援的 R 解譯器與 ScaleR 程式庫，以對單一節點或叢集進行更快速地計算。 您也可以從 [CRAN](https://cran.r-project.org/) 使用任何 R)。
  - R 開發工具的執行階段支援

雖然 F# 隨附數個其他工作負載，而 Python 具有自己的工作負載，但是資料科學與分析應用程式是目前包含 R 的唯一工作負載。與工作負載無關，在安裝程式的 [個別元件] 索引標籤上也可以選取三個 R 元件。 選取 [開發活動] > [R 語言支援]、[開發活動] > [Microsoft R Client] 和 [編譯器、建置工具與執行階段] > [R 開發工具的執行階段支援] 選項。

## <a name="sql-server-integration"></a>SQL Server 整合

SQL Server 支援使用 R 和 Python，以直接在 SQL Server 內執行進階分析。 SQL Server 2016 和更新版本隨附 R 支援；SQL Server 2017 CTP 2.0 和更新版本提供 Python 支援。

執行已有資料的程式碼，有許多優點：

- **不需要移動資料**：您可以在資料庫中建置 R 和 Python 應用程式，而不需要將資料從資料庫移至應用程式或模型。 此功能可消除安全性障礙、合規性、控管、完整性，以及 移動大量資料相關類似問題的主機。 它也可讓您使用無法放入用戶端電腦記憶體的資料集。

- **輕鬆部署**：擁有 R 或 Python 模型之後，將它部署至生產環境表示只在 T-SQL 指令碼中嵌入它。 以任何語言撰寫的任何 SQL 用戶端應用程式接著可以透過預存程序呼叫來運用模型和智慧。 不需要任何特定的 R 或 Python 整合。

- **企業級效能和規模**：您可以使用 SQL Server 的進階功能，例如具有 RevoScaleR 和 RevoScalePy 套件中高效能可擴充 API 的記憶體中資料表和資料行存放區索引。 不需要移動資料也表示在您的資料成長或您想要增加應用程式效能時，避免用戶端記憶體條件約束。

- **豐富的擴充性**：您可以在 SQL Server 上安裝和執行任何最新的開放原始碼 R 或 Python 套件，以對 SQL Server 中的大量資料建置深度學習和 AI 應用程式。 在 SQL Server 中安裝套件，就像在本機電腦上安裝套件一樣簡單。

- **不需額外成本的多可用性**：所有 SQL Server 2017 和更新版本都提供 R 和 Python 整合 (包含 Express Edition)  (SQL Server 2016 和更新版本提供 R 支援)。

若要完整利用 SQL Server 整合，您也應該使用 [SQL Server Data Tools] 選項來安裝**資料儲存和處理**工作負載。 此選項可啟用 SQL IntelliSense、語法醒目提示和部署。

![資料儲存和處理工作負載](media/data-storage-workload.png) &nbsp;&nbsp; &nbsp;&nbsp; ![資料儲存和處理工作負載選項](media/data-storage-workload-options.png)

如需詳細資訊：

- [使用 SQL Server 和 R](../rtvs/sql-server.md)
- [SQL Server 2016 中使用 R 的資料庫中進階分析](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
- [SQL Server 2017 中的 Python：增強式資料庫中機器學習](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>其他服務和 SDK

除了資料科學與分析應用程式工作負載中的直接內容之外，Azure Notebooks 服務和 Azure SDK for Python 也適用於資料科學。

Azure SDK for Python 可讓您更輕鬆地從 Windows、Mac OSX 和 Linux 上執行的應用程式使用及管理 Microsoft Azure 服務。 如需詳細資訊，請參閱 [Azure SDK for Python](../python/azure-sdk-for-python.md)

Azure Notebooks (目前為預覽版本) 可在 Microsoft Azure 上免費線上存取雲端中執行的 Jupyter Notebooks。 此服務會在 Python、R 和 F# 中包含範例筆記本，協助您開始使用。 請瀏覽 [notebooks.azure.com](https://notebooks.azure.com/)。

<!--Note link on the image because this one is large -->
[![含 R 樣本簡介的 Azure Notebooks 螢幕擷取畫面](media/data-science-workload-notebooks.png)](media/data-science-workload-notebooks.png)