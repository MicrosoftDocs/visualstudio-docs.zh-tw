---
title: 資料科學與分析應用程式工作負載
description: 此 Visual Studio 工作負載結合 Python、F# 及其對應的執行階段發行版本，包括 Anaconda。 (R 僅包含在 Visual Studio 2017 中。)
ms.date: 02/28/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- python
- data-science
ms.openlocfilehash: de86c2021a2abf3cd5346c684199e8f59e2d314e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839184"
---
# <a name="install-data-science-support-in-visual-studio"></a>在 Visual Studio 中安裝資料科學支援

可透過 Visual Studio 安裝程式選取並安裝的資料科學與分析應用程式工作負載，結合了數種語言和其對應的執行階段發行版本：

::: moniker range="vs-2017"
- [Python 和 Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [含 .NET Framework 的 F#](/dotnet/fsharp/)
- [R 和 Microsoft R Client](../rtvs/index.md)
::: moniker-end

::: moniker range="vs-2019"
- [Python](../python/overview-of-python-tools-for-visual-studio.md)
- [含 .NET Framework 的 F#](/dotnet/fsharp/)
::: moniker-end

![Visual Studio 安裝程式中的資料科學與分析應用程式工作負載](media/workload/data-science-workload.png)

::: moniker range="vs-2017"
Python 和 R 是用於資料科學的兩個主要指令碼語言。 這兩種語言都很容易了解，而且多種套件生態系統都予以支援。 這些套件處理各種案例 (例如資料取得、清理、模型訓練、部署和繪製)。 F# 也是一種功能強大的功能優先 .NET 語言，適合各種資料處理工作。
::: moniker-end

::: moniker range="vs-2019"
Python 是用於資料科學的主要指令碼語言。 Python 很容易學習，且支援多種套件生態系統。 這些套件處理各種案例 (例如資料取得、清理、模型訓練、部署和繪製)。 F# 也是一種功能強大的功能優先 .NET 語言，適合各種資料處理工作。 (針對 R 語言，我們建議 [Azure Notebooks](https://notebooks.azure.com)。)
::: moniker-end

<!--Note link on the image because this one is large -->
[![R、Python 和 F Visual Studio 的螢幕擷取畫面#](media/workload/data-science-workload-screens.png)](media/workload/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>工作負載選項

根據預設，工作負載會安裝下列選項，而您可以在 Visual Studio 安裝程式中工作負載的 [摘要] 區段內對其進行修改：

::: moniker range="vs-2019"
- F# 桌面語言支援
- Python：
  - Python 語言支援
  - Python Web 支援
::: moniker-end

::: moniker range="vs-2017"
- F# 語言支援
- Python：
  - Python 語言支援
  - [Anaconda3 64](https://www.continuum.io)位，這是包含大量資料科學程式庫和 python 解譯器的 python 發行版本。
  - Python Web 支援
  - Cookiecutter 範本支援
- R：
  - R 語言支援
  - R 開發工具的執行階段支援
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (Microsoft 的完全相容、社群支援的 R 解譯器與 ScaleR 程式庫，以對單一節點或叢集進行更快速地計算。 您也可以從 [CRAN](https://cran.r-project.org/) 使用任何 R)。
::: moniker-end

## <a name="sql-server-integration"></a>SQL Server 整合

::: moniker range="vs-2017"
SQL Server 支援使用 Python 和 R，以直接在 SQL Server 內執行進階分析。 SQL Server 2016 和更新版本隨附 R 支援；SQL Server 2017 CTP 2.0 和更新版本提供 Python 支援。
::: moniker-end

::: moniker range=">=vs-2019"
SQL Server 支援使用 Python，以直接在 SQL Server 內執行進階分析。 SQL Server 2017 CTP 2.0 和更新版本提供 Python 支援。
::: moniker-end

執行已有資料的程式碼將會有下列優點：

- **消除資料移動**：您可以在資料庫中建立應用程式，而不是將資料從資料庫移至應用程式或模型。 此功能可消除安全性障礙、合規性、控管、完整性，以及 移動大量資料相關類似問題的主機。 您也可以使用無法放入用戶端電腦記憶體的資料集。

- **輕鬆部署**：當您準備好模型之後，將它部署至生產環境，就可以簡單地將它內嵌在 t-sql 腳本中。 以任何語言撰寫的任何 SQL 用戶端應用程式接著可以透過預存程序呼叫來運用模型和智慧。 不需要任何特定的語言整合。

- **企業級效能和規模**：您可以使用 SQL Server 的 advanced 功能，例如記憶體內部資料表和資料行存放區索引，以及 RevoScale 套件中高效能可擴充的 api。 不需要移動資料也表示在您的資料成長或您想要增加應用程式效能時，避免用戶端記憶體條件約束。

- **豐富** 的擴充性：您可以在 SQL Server 中安裝並執行任何最新的開放原始碼套件，以在 SQL Server 的大量資料上建立深度學習和 AI 應用程式。 在 SQL Server 中安裝套件，就像在本機電腦上安裝套件一樣簡單。

- 完全免費且 **不需額外費用**：語言整合適用于所有版本的 SQL Server 2017 和更新版本（包括 Express edition）。

若要完整利用 SQL Server 整合，請使用 Visual Studio 安裝程式，透過 [SQL Server Data Tools] 選項來安裝 [資料儲存和處理] 工作負載。 後述選項可啟用 SQL IntelliSense、語法醒目提示和部署。

![資料儲存和處理工作負載](media/workload/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![資料儲存和處理工作負載選項](media/workload/data-storage-workload-options.png)

其他資訊：

::: moniker range="vs-2017"
- [使用 SQL Server 和 R](../rtvs/integrating-sql-server-with-r.md)
- [SQL Server 2016 中使用 R 的資料庫中進階分析 (部落格)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/) \(英文\)
::: moniker-end
- [SQL Server 2017 中的 Python：增強式資料庫中機器學習 (部落格)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/) \(英文\)

## <a name="additional-services-and-sdks"></a>其他服務和 SDK

除了資料科學與分析應用程式工作負載中的直接內容之外，Azure Notebooks 服務和 Azure SDK for Python 也適用於資料科學。

Azure SDK for Python 可讓您更輕鬆地從 Windows、Mac 和 Linux 上所執行的應用程式使用及管理 Microsoft Azure 服務。 如需詳細資訊，請參閱 [適用于 Python 的 AZURE SDK](/azure/python/)。

Azure Notebooks (目前為預覽版本) 可在 Microsoft Azure 上免費線上存取雲端中執行的 Jupyter Notebooks。 此服務會在 Python、R 和 F# 中包含範例筆記本，協助您開始使用。 請瀏覽 [notebooks.azure.com](https://notebooks.azure.com/)。

<!--Note link on the image because this one is large -->
[![簡介 R 範例 Azure Notebooks 的螢幕擷取畫面](media/workload/data-science-workload-notebooks.png)](media/workload/data-science-workload-notebooks.png#lightbox)
