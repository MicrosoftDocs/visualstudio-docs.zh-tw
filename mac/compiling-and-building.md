---
title: 編譯和建置
description: 本文描述如何在 Visual Studio for Mac 中編譯和建置專案與方案
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2021
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: a24c57907afedb4f02068a071d2c9f81eb8962bb
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2021
ms.locfileid: "108640970"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>在 Visual Studio for Mac 中編譯和建置

Visual Studio for Mac 可用來在專案開發期間建置應用程式和建立組件。 頻繁地建置您的程式碼以允許快速識別類型不符、易發生錯誤的語法、拼錯的關鍵字與其他編譯時間錯誤非常重要。 透過建置並偵錯，您也可以尋找並修正執行階段錯誤，例如邏輯、IO 與除以零錯誤。

成功的建置表示原始程式碼包含正確的語法，而且對程式庫、組件與其他元件的所有靜態參考都能成功解析。 建置程序會產生應用程式可執行檔。 這個可執行檔接著可透過偵錯與其他類型的手動與自動測試來驗證程式碼品質。 完整測試您的應用程式之後，您便能編譯發行版本以部署到您的客戶。

在 Mac 上，您可以使用下列任何一種方法來建立您的應用程式： Visual Studio for Mac、MSBuild 命令列工具或 Azure Pipelines。

| 建置方法 | 優點 |
| --- |--- | --- |
| Visual Studio for Mac |- 立即建立組建並在偵錯工具中加以測試。<br />- 對 C# 專案執行多處理器組建。<br />- 自訂建置系統的不同層面。 |
| MSBuild 命令列| - 無須安裝 Visual Studio for Mac 即可建置專案。<br />- 對所有專案類型執行多處理器建置。<br />- 自訂建置系統大部分的區域。|
| Azure Pipelines | - 將建置流程自動化，這是持續整合/持續傳遞管線的一部分。<br />- 在每個組建套用自動化的測試。<br />- 在建置流程採用幾乎不受限制的雲端式資源。<br />- 修改建置工作流程，以及建立建置活動以執行深入自訂的工作。|

本節文件進一步說明使用 IDE 的建置流程詳細資料。 若要從命令列建立應用程式，而不安裝 Visual Studio for Mac，您可以安裝最新的 [.NET Core SDK](https://dotnet.microsoft.com/download)。 如需有關透過命列列建置應用程式的詳細資訊，請參閱 [MSBuild](/visualstudio/msbuild/msbuild)。 如需有關使用 Azure Pipelines 來建置應用程式的詳細資訊，請參閱 [Azure Pipelines](/azure/devops/pipelines)。


> [!NOTE]
> 本主題適用於 Visual Studio for Mac。 針對 Windows 上的 Visual Studio，請參閱[在 Visual Studio 中編譯與建置](/visualstudio/ide/compiling-and-building-in-visual-studio)。


## <a name="building-from-the-ide"></a>從 IDE 建置

Visual Studio for Mac 可讓您立即建立和執行組建，同時仍然能夠控制組建功能。 當您建立專案時，Visual Studio for Mac 會定義預設建置設定 (這會設定建置的上下文)。 您可以編輯預設建置設定，而且也可以建立您自己的建置設定。 建立或修改這些組態會自動更新專案檔，MSBuild 之後會使用該檔案來建置專案。

如需如何在 IDE 中建立專案和方案的詳細資訊，請參閱[建置和清除專案與方案](building-and-cleaning-projects-and-solutions.md)指南。

Visual Studio for Mac 也可用來執行下列作業：

* 變更輸出路徑。 這是在您的專案選項中進行編輯：

    ![變更輸出路徑](media/compiling-and-building-image4.png)

* 變更組建輸出的詳細資訊：

    ![變更組建的詳細資訊](media/compiling-and-building-image5.png)

* 在建置或清除之前、期間或之後加入自訂命令：

    ![新增自訂命令](media/compiling-and-building-image6.png)


## <a name="see-also"></a>另請參閱

- [編譯與建置 (Windows 上的 Visual Studio)](/visualstudio/ide/compiling-and-building-in-visual-studio)
