---
title: 編譯/建置
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7681ad9cd109dbc8da266721d9d8382d3552eda6
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "53062589"
---
# <a name="compile-and-build-in-visual-studio"></a>在 Visual Studio 中編譯與建置

當您建置原始程式碼時，建置引擎會建立組件和可執行的應用程式。 不同專案類型 (如 Windows、ASP.NET、行動裝置及其他類型) 進行的建置流程大致上都很相似。 不同的程式語言 (如 C#、Visual Basic、C++ 和 F#) 也進行類似的建置流程。

經常建置程式碼讓您可以迅速識別編譯錯誤，例如語法不正確、關鍵字拼字錯誤和類型不相符。 您也可以藉由建置和執行程式碼的偵錯版本，偵測並修正執行階段錯誤，例如邏輯錯誤和語意錯誤。

成功的組建會驗證應用程式的原始程式碼包含了正確語法，而且所有對程式庫、組件及其他元件的靜態參考均可解析。 如此會產生可執行的應用程式，不僅可在[偵錯環境](../debugger/index.md)中測試其正常運作，也可透過各種手動和自動測試來[驗證程式碼品質](../test/improve-code-quality.md)。 應用程式一經完整測試，您便可編譯發行版本以部署到您的客戶。 如需此流程的簡介，請參閱[逐步解說：建置應用程式](../ide/walkthrough-building-an-application.md)。

您可以使用下列任一種方法來建置應用程式：Visual Studio IDE、MSBuild 命令列工具，以及 Azure Pipelines：

| 建置方法 | 優點 |
| --- |--- | --- |
| IDE |- 立即建立組建並在偵錯工具中加以測試。<br />- 對 C++ 和 C# 專案執行多處理器組建。<br />- 自訂建置系統的不同層面。 |
| MSBuild 命令列| - 無須安裝 Visual Studio 即可建置專案。<br />- 對所有專案類型執行多處理器建置。<br />- 自訂建置系統大部分的區域。|
| Azure Pipelines | - 將建置流程自動化，這是持續整合/持續傳遞管線的一部分。<br />- 在每個組建套用自動化的測試。<br />- 在建置流程採用幾乎不受限制的雲端式資源。<br />- 修改建置工作流程，以及建立建置活動以執行深入自訂的工作。|

本節文件進一步說明使用 IDE 的建置流程詳細資料。 如需其他方法的詳細資訊，請分別參閱 [MSBuild](../msbuild/msbuild.md) 和 [Azure Pipelines](/azure/devops/pipelines/index?view=vsts)。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[在 Visual Studio for Mac 中編譯與建置](/visualstudio/mac/compiling-and-building)。

## <a name="overview-of-building-from-the-ide"></a>從 IDE 建置的概觀

當您建立專案時，Visual Studio 為專案及包含該專案的解決方案建立了預設組建組態。  這些組態定義了解決方案和專案建置及部署的方式。 針對目標平台 (例如 Windows 或 Linux) 和組建類型 (例如偵錯或發行)，專案組態更必須具備唯一性。 您可以自由編輯這些組態，也可視需要建立自己的組態。

若要了解在 IDE 中建置的初步簡介，請參閱[逐步解說：建置應用程式](walkthrough-building-an-application.md)。

之後，請參閱[在Visual Studio 中建置和清除專案與方案](building-and-cleaning-projects-and-solutions-in-visual-studio.md)來了解可對流程自訂的不同層面。 自訂包括[變更輸出目錄](how-to-change-the-build-output-directory.md)、[指定自訂建置事件](specifying-custom-build-events-in-visual-studio.md)、[管理專案相依性](how-to-create-and-remove-project-dependencies.md)、[管理組建記錄檔](how-to-view-save-and-configure-build-log-files.md)和[隱藏編譯器警告](how-to-suppress-compiler-warnings.md)。

您可以從中探索其他各種工作：
- [了解建置組態](understanding-build-configurations.md)
- [了解建置平台](understanding-build-platforms.md)
- [管理專案及解決方案屬性](managing-project-and-solution-properties.md)。
- 使用 [C#](how-to-specify-build-events-csharp.md) 和 [Visual Basic](how-to-specify-build-events-visual-basic.md) 指定建置事件。
- [設定建置選項](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [平行建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)。

## <a name="see-also"></a>另請參閱

- [建置 (編譯) 網站專案](https://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)
- [編譯與建置 (Visual Studio for Mac)](/visualstudio/mac/compiling-and-building)