---
title: 範例 R 專案
description: 可讓您開始搭配使用 R 和 Visual Studio 的範例集合索引。
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 0ed322a03d056f72ac2246e96d3aaeefa8f557c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967016"
---
# <a name="r-tools-for-visual-studio-sample-projects"></a>Visual Studio R 工具範例專案

此範例集合能讓您開始使用 R、Visual Studio R 工具 (RTVS) 和 Microsoft Machine Learning Server：

1. 下載[ ZIP 檔案範例](https://github.com/Microsoft/RTVS-docs/archive/master.zip)並解壓縮至您選擇的資料夾。
1. 開啟 `examples/Examples.sln` 即可看到專案中的兩個資料夾︰

    - *初探 R* 為 R 新手提供合適的簡介。
    - *MRS 和機器學習服務* 提供如何使用 R 和 Microsoft Machine Learning Server 進行機器學習服務的範例。

## <a name="a-first-look-at-r"></a>初探 R

這個範例透過兩個原始程式檔中的大量註解，提供 R 的深入介紹。 為獲得最佳體驗，請將游標放在檔案最上方，然後按 Ctrl + Enter 逐步傳送程式碼行到 [R 互動] 視窗。 (安裝套件的行可能需要一兩分鐘的時間才能完成。)

- `1-Getting Started with R.R` 涵蓋許多 R 基本概念，包括使用套件、載入和分析資料，以及繪製。

    ![1-Getting Started with R.R 範例的範例輸出](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` 介紹 ggplot2 圖形套件，它是以視覺效果豐富的繪圖和簡單的語法而知名。 這個範例可以視覺化斐濟的地震資料。

    ![2-Introduction to ggplot2.R 範例的範例輸出](media/samples-ggplot-output.png)

## <a name="microsoft-machine-learning-server-and-machine-learning"></a>Microsoft Machine Learning Server 和機器學習服務

此範例集合示範如何使用 R 建立機器學習服務模型，以及如何充分利用 [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server)。

如同所有範例，請開啟檔案、將游標放在最上方，然後以 **Ctrl** Enter 逐行執行程式程式碼 + ****。 每個資料夾中的 Markdown 檔案也包含其他詳細資料。

- `Benchmarks` 會執行許多密集、平行的線性代數運算，顯示透過使用 Microsoft R Open 和 Intel 數學核心程式庫 (MKL) 而可能會提升的效能。 使用模擬資料，基準測試特別比較在一與兩個執行緒上的矩陣計算。

    ![範例基準測試繪圖](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS` 會建立單車出租的需求預測模型，這是使用 Microsoft Machine Learning Server，並以歷程記錄資料集為基礎。

- `Data_Exploration` 包含三個指令碼：

  - `Import Data from URL.R` 示範如何將 URL 識別資料檔案載入到 R。
  - `Import Data from URL to xdf.R` 示範如何將 URL 識別資料檔案作為 xdf 載入到 Microsoft Machine Learning Server。
  - `Using ggplot2.R` 是 `A First Look at R/2-Introduction to ggplot2.R` 範例的延伸模組，提供更豐富的 ggplot2 功能教學課程，包括互動式 3D 繪圖。

      ![Using ggplot2.R 範例的輸出](media/samples-3d-interactive.png)

- `Datasets` 包含其他範例所使用的三個 *.csv* 檔案
- `Flight_Delays_Prediction_with_R` 和 `Flight_Delays_Prediction_with_MRS` 示範如何使用 R、機器學習服務和歷史準點率和天候資料預測航班誤點。
- `Machine learning` 含有三個範例，學習預測航班延誤、住宅價格和自行車租金。 這些範例一起示範 R 和 Microsoft Machine Learning Server 的真實問題應用。 它們還要告訴您如何使用數個常用的機器學習模型，並使用 [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/) 工作區將其部署為 Azure Web 服務。

- `R_MRO_MRS_Comparison` 是六個部分的比較，顯示 R、Microsoft R Open 和 Microsoft Machine Learning Server 在命令、語法、建構和效能方面的相似性和差異。

## <a name="whats-special-about-microsoft-r-open-and-microsoft-ml-server"></a>Microsoft R Open 與 Microsoft Machine Learning Server 有什麼特別之處？

[Microsoft R Open](https://mran.revolutionanalytics.com/download/)，是 Microsoft 的 R 發行版本，它與 [CRAN R](https://cran.r-project.org/) 的不同有兩個重要的方面︰

1. 搭配 [Intel Math Kernel Library](https://software.intel.com/intel-mkl) (Intel 數學核心程式庫) 使用時[計算效能較高](https://mran.revolutionanalytics.com/rro/#intelmkl1)。 程式庫可以從 Microsoft 免費下載，以便搭配 Microsoft R Open 使用。

1. [可重製的 R 工具箱](https://mran.revolutionanalytics.com/rro/#reproducibility)能確保您用來建置 R 程式的程式庫一律能供想要重製您作品的其他人使用。

[Microsoft Machine Learning Server (MLS)](/machine-learning-server/what-is-machine-learning-server) 是可讓您處理更多資料，並更快速處理的 R 延伸模組。 它提供 R 兩項強大的功能︰

1. 較大的資料集，沒有 RAM 限制。 Machine Learning Server 可以處理來自各種來源的記憶體不足資料，包括 Hadoop 叢集、資料庫和資料倉儲。

1. 平行、多核心處理程序。 MLS 可以有效率地將計算分散到它能用的所有計算資源。 在您的個人工作站或遠端叢集上，MLS 會更快獲得解答。

下列比較顯示在特定矩陣計算方面，MLS 和具有 MKL 的 MRO 計算效能明顯優於 R 和沒有 MKL 的 MRO。 這項計算中，會使用模擬的資料︰

![比較 MLS 和使用 MKL 的 MRO，以及 R 和沒有 MKL 的 MRO](media/samples-speed-comparison.png)

如需 R 與 MRO 和 MLS 的技術比較，請參閱 [Lixun Zhang 關於這主題的詳細討論](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html)。

然後，下圖比較建立使用羅吉斯迴歸模型來預測航班延遲超過 15 分鐘時，耗用的時間 (以秒為單位)。  當增加少量的資料列時，CRAN R 中使用的已耗用時間會大幅增加，而 MLS 則只增加大約兩倍。 如需此基準測試的詳細資料，請參閱 *Benchmarks/rxGlm_benchmark.R* 範例。

![rxGlm 基準測試](media/samples-rxGLM-benchmark.png)
