---
title: Windows 上 Visual Studio 中的 Python 支援概觀
description: Visual Studio 中 Python 功能的摘要，這些功能使它成為 Windows 上最佳的 Python IDE (也稱為「適用於 Visual Studio 的 Python 工具」(PTVS))。
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 587517bdeabf9755e2678b03206059ef5b403255
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="working-with-python-in-visual-studio-on-windows"></a>在 Windows 的 Visual Studio 中使用 Python

Python 是一種熱門的程式設計語言，不僅可靠、有彈性、容易學習、可在所有作業系統上免費使用，而且也受到強大的開發人員社群和許多免費程式庫支援。 Python 支援各式各樣的開發，包括 Web 應用程式、Web 服務、傳統型應用程式、指令碼及科學計算，並且許多大學、科學家、業餘開發人員及專業開發人員等都使用它。 您可以從 [python.org (英文)](https://www.python.org) 和[適用於初學者的 Python (英文)](https://www.python.org/about/gettingstarted/) 深入了解此語言。

Visual Studio 是 Windows 上功能強大的 Python IDE。 Visual Studio 可透過「Python 開發與資料科學工作負載」(Visual Studio 2017) 和免費的「適用於 Visual Studio 的 Python 工具」延伸模組 (Visual Studio 2015 和更舊的版本)，針對 Python 語言提供[開放原始碼](https://github.com/Microsoft/ptvs)支援。

Python 目前在 Visual Studio for Mac 中不予支援，但可透過 Visual Studio Code 在 Mac 和 Linux 上使用 (請參閱[問與答](#questions-and-answers))。

若要開始使用：

- 依照[安裝指示](installing-python-support-in-visual-studio.md)設定 Python 工作負載。
- 透過本文中的各節熟悉 Visual Studio 的 Python 功能。 您也可以[觀看 Visual Studio 中的 Python 簡介影片系列 (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121) (總長 22 分鐘)。
- 完整瀏覽一或多份快速入門，以建立專案。 如果您不確定從何處著手，請從[使用 Flask 來建立 Web 應用程式](../ide/quickstart-python.md?context=visualstudio/python/default)開始著手。
- 請遵循[在 Visual Studio 中使用 Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) 的教學課程，以取得完整的端對端體驗。

## <a name="support-for-multiple-interpreters"></a>支援多重解譯器

Visual Studio 的 [Python 環境] 視窗 (在下方顯示為寬型的展開檢視) 提供您一個單一位置來管理所有全域 Python 環境、Conda 環境及虛擬環境。 Visual Studio 會自動偵測標準位置中的 Python 安裝，並允許您設定自訂安裝。 針對每個環境，您可以輕鬆管理套件、開啟該環境的互動式視窗，以及存取環境資料夾。

![[Python 環境] 視窗的展開檢視](media/environments-expanded-view.png)

如需詳細資訊：

- 影片 (2 分 35 秒)：[管理 Python 環境](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567)
- 文件：[管理 Python 環境](managing-python-environments-in-visual-studio.md)
- 文件：[Python 環境視窗參考](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>豐富的編輯功能、IntelliSense 及程式碼理解

Visual Studio 提供最優質的 Python 編輯器，包括語法色彩標示、所有程式碼和程式庫的自動完成、程式碼格式設定、簽章說明、重構、Lint 處理 (如下所示) 和類型提示。 Visual Studio 也提供獨一無二的功能，例如類別檢視、[移至 定義]、[尋找所有參考] 及程式碼片段。 與[互動式視窗](#interactive-window)的整合可協助您快速開發已經儲存在檔案中的 Python 程式碼。

![Visual Studio 中 Python 程式碼的程式碼完成](media/code-editing-completions-simple.png)

如需詳細資訊：

- 應面 (2 分 30 秒)：[編輯 Python 程式碼](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=r2iQH5LWE_4605918567)
- 文件：[編輯 Python 程式碼](editing-python-code-in-visual-studio.md)
- 文件：[程式碼格式設定](formatting-python-code.md)
- 文件：[重構](refactoring-python-code.md)
- 文件：[Lint 處理](linting-python-code.md)
- 一般 Visual Studio 功能文件：[程式碼編輯器的功能](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>互動式視窗

針對 Visual Studio 已知的每個 Python 環境，您可以直接從 Visual Studio 內輕鬆開啟相同的 Python 解譯器互動式 (REPL) 環境，而無須使用個別的命令提示字元。 您也可以在環境之間輕鬆切換。

![Visual Studio 中的 Python 互動式視窗](media/interactive-window.png)

Visual Studio 也提供 Python 程式碼編輯器與互動式視窗之間的緊密整合。 **Ctrl+Enter** 鍵盤快速鍵可方便您將編輯器中目前的程式碼行 (或程式碼區塊) 傳送至互動式視窗，然後移至下一行 (或區塊)。 **Ctrl+Enter** 可讓您輕鬆逐步執行程式碼，而無須執行偵錯工具。 您也可以使用相同的按鍵將選取的程式碼傳送至互動式視窗，以及輕鬆地將程式碼從互動式視窗貼到編輯器中。 這些功能一起搭配可讓您在互動式視窗中發展出某個程式碼區段的詳細資料，然後在編輯器中輕鬆地將結果儲存在檔案中。

Visual Studio 也支援 REPL 中 IPython/Jupyter，包括內嵌繪圖、.NET 及 Windows Presentation Foundation (WPF)。

如需詳細資訊：

- 影片 (2 分 22 秒)：[Python 互動式視窗](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=gJYKY5LWE_4605918567)
- 文件：[互動式視窗](python-interactive-repl-in-visual-studio.md)
- 文件：[Visual Studio 中的 IPython](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>專案系統以及專案和項目範本

Visual Studio 可協助您管理專案隨時間發展衍生出的複雜性。 專案遠比資料夾結構複雜：它包括了解不同檔案的使用方式，以及它們之間的關聯性。 Visual Studio 可協助您區別應用程式程式碼、測試程式碼、網頁、JavaScript、建置指令碼等，這些會接著啟用檔案適當的功能。 此外，Visual Studio 方案還可協助您管理多個相關的專案，例如 Python 專案和 C++ 延伸模組專案。

![同時包含 Python 和 C++ 專案的 Visual Studio 方案](media/projects-solution-explorer-two-projects.png)

專案和項目範本可將設定不同類型專案和檔案的流程自動化，不僅可節省您寶貴的時間，還能讓您不必再管理錯綜複雜又容易出錯的細節。 Visual Studio 提供適用於 Web、Azure、資料科學、主控台及其他類型專案的範本，還提供適用於檔案的範本，例如 Python 類別、單元測試、Azure Web 設定、HTML 及甚至是 Django 應用程式。

[![Visual Studio 中的 Python 專案和項目範本](media/project-and-item-templates.png)](media/project-and-item-templates.png)

如需詳細資訊：

- 文件：[管理 Python 專案](managing-python-projects-in-visual-studio.md)
- 文件：[項目範本參考](python-item-templates.md)
- 文件：[Python 專案範本](managing-python-projects-in-visual-studio.md#project-templates)
- 文件：[使用 C++ 和 Python](working-with-c-cpp-python-in-visual-studio.md)
- 一般 Visual Studio 功能文件：[專案和項目範本](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- 一般 Visual Studio 功能文件：[Visual Studio 中的方案和專案](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>功能完整的偵錯

Visual Studio 的其中一個優點是功能強大的偵錯工具。 特別是針對 Python，Visual Studio 包括可進行 Python/C++ 混合模式偵錯、對 Linux 進行遠端偵錯、對 Azure 進行遠端偵錯、在「互動式視窗」內進行偵錯，以及對 Python 單元測試進行偵錯。

![顯示例外狀況快顯的 Visual Studio Python 偵錯工具](media/debugging-exception-popup.png)

如需詳細資訊：

- 影片 (3 分 32 秒)：[對 Python 進行偵錯](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=Ep5dp5LWE_3805918567)
- 文件：[對 Python 進行偵錯](debugging-python-in-visual-studio.md)
- 文件：[Python/C++ 混合模式偵錯](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- 文件：[對 Linux 進行遠端偵錯](debugging-python-code-on-remote-linux-machines.md)
- 文件：[對 Azure 進行遠端偵錯](debugging-remote-python-code-on-azure.md)
- 一般 Visual Studio 功能文件：[Visual Studio 偵錯工具的功能導覽](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>具備完整報告功能的分析工具

分析功能會探索您應用程式中的時間使用情況。 Visual Studio 支援使用 CPython 型解譯器來進行分析，並且包含了可比較不同分析執行回合之間效能的功能。

[![Python 專案的 Visual Studio 分析工具結果](media/profiling-results.png)](media/profiling-results.png)

如需詳細資訊：

- 影片 (3 分 00 秒)：[分析 Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=s6FoC6LWE_1005918567)
- 文件：[Python 分析工具](profiling-python-code-in-visual-studio.md)
- 一般 Visual Studio 功能文件：[分析功能導覽](../profiling/profiling-feature-tour.md)。 (並非所有 Visual Studio 分析功能都可供 Python 使用)。

## <a name="unit-testing-tools"></a>單元測試工具

在 Visual Studio [測試總管] 中探索、執行及管理測試，並輕鬆針對單元測試進行偵錯。

![在 Visual Studio 中進行 Python 單元測試偵錯](media/unit-test-debugging.png)

如需詳細資訊：

- 影片 (2 分 31 秒)：[測試 Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=hb46k6LWE_405918567)
- 文件：[適用於 Python 的單元測試工具](unit-testing-python-in-visual-studio.md)
- 一般 Visual Studio 功能文件：[對您的程式碼進行單元測試](../test/unit-test-your-code.md)。

## <a name="publishing-to-azure-and-azure-sdk-for-python"></a>發佈至 Azure 和適用於 Python 的 Azure SDK

Visual Studio 提供整合式支援，可將 Web 應用程式和雲端服務發佈至 Azure。 Visual Studio 包含適用於動態和靜態內容的必要 `web.config` 項目範本。 Python 工作負載也包含「適用於 Python 的 Azure SDK」，此 SDK 可簡化從 Windows、Mac OS X 及 Linux 應用程式使用 Azure 服務的流程。

![在 Visual Studio 中將 Python 應用程式發佈至 Azure](media/azure-publish-dialog.png)

如需詳細資訊：

- 文件：[發佈至 Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
- 文件：[適用於 Python 的 Azure SDK](azure-sdk-for-python.md)

## <a name="python-training-on-microsoft-virtual-academy"></a>Microsoft Virtual Academy 上的 Python 訓練

|   |   |
|---|---|
| ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片") | <ul><li>[使用 Python 設計程式的簡介](https://mva.microsoft.com/en-US/training-courses/introduction-to-programming-with-python-8360?l=lqhuMxFz_8904984382)</li><li>[Python 初學者：字串和函式](https://mva.microsoft.com/en-US/training-courses/python-beginner-strings-and-functions-18015)</li><li>[Python 基本概念：清單和迴圈](https://mva.microsoft.com/en-US/training-courses/python-fundamentals-lists-and-loops-18019)</li><li>[前幾大 Python 問題](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121)</li></ul> |

## <a name="questions-and-answers"></a>問與答

**問：Visual Studio for Mac 提供 Python 支援嗎？**

答： 目前沒有提供，但您可以在 [UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac/suggestions/18670291-python-tools-for-visual-studio-mac) 上對該要求投贊成票。 [Visual Studio for Mac](/visualstudio/mac/) 文件可識別它確實支援的目前開發類型。 同時，Windows、Mac 和 Linux 上的 Visual Studio Code [透過可用的延伸模組與 Python 搭配運作良好](https://code.visualstudio.com/docs/languages/python)。

**問：建置 UI 時，我可以使用什麼功能來搭配 Python？**

答： 這方面的主要提供項目是 [Qt 專案](https://www.qt.io/qt-for-application-development/) 及 Python 的繫結，其稱為 [PySide (正式繫結)](http://wiki.qt.io/PySide) (另請參閱 [PySide downloads](https://download.qt.io/official_releases/pyside/.)) (PySide 下載) 和 [PyQt](https://wiki.python.org/moin/PyQt)。 目前，Visual Studio 中的 Python 支援不包含任何特定的 UI 開發工具。

**問：Python 專案是否能產生獨立的可執行檔？**

答： 一般來說，Python 是解譯的語言，並包含可在適當 Python 支援環境 (例如 Visual Studio 和網頁伺服器) 中視需要執行的程式碼。 目前，Visual Studio 本身不提供用來建立獨立可執行檔的工具，因為獨立可執行檔基本上表示內嵌 Python 解譯器的程式。 不過，若要建立可執行檔，Python 社群中提供多種方式，如 [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency) 中所述。 CPython 也支援在原生的應用程式中內嵌，如[使用 CPython 可內嵌的 Zip 檔案](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/)部落格文章中所述。

## <a name="features-matrix"></a>功能對照表

您可用下列版本的 Visual Studio 安裝 Python 功能，如[安裝指南](installing-python-support-in-visual-studio.md)所述：

- [Visual Studio 2017 (所有版本)](https://www.visualstudio.com/vs/)
- Visual Studio 2015 (所有版本)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express for Web (Update 2 或更新版本)
- Visual Studio 2013 Express for Desktop (Update 2 或更新版本)
- Visual Studio 2013 (Pro 版或更新版本)
- Visual Studio 2012 (Pro 版或更新版本)
- Visual Studio 2010 SP1 (Pro 版或更新版本；需要 .NET 4.5)

Visual Studio 2015 及更早版本位於 [visualstudio.com/vs/older-downloads/](https://www.visualstudio.com/vs/older-downloads/)。

> [!Important]
> 只有最新版本的 Visual Studio 具備功能的完整支援與維護。 功能在較舊版本中依然可用，但不會主動維護。

| Python 支援 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 管理多重解譯器 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 自動偵測熱門的解譯器 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 新增自訂解譯器 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 虛擬環境 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Pip/簡易安裝 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| 專案系統 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 來自現有程式碼的新專案 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 顯示所有檔案 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 原始檔控制 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Git 整合 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004;<sup>1</sup> | &#10007; |
<br/>

| 編輯 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 語法醒目提示 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 自動完成 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 簽章說明 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 快速諮詢 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 物件瀏覽器/類別檢視 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 巡覽列 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 移至定義 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 導覽至 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 尋找所有參考 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 自動縮排 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 程式碼格式設定 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 重構 - 重新命名 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 重構 - 擷取方法 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 重構 - 新增/移除匯入 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| PyLint | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| 互動式視窗 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 互動式視窗 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 具有內嵌圖形的 IPython | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| 桌面 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 主控台/Windows 應用程式 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IronPython WPF (含 XAML 設計工具) | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IronPython Windows Forms | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Web | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Django Web 專案 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Bottle Web 專案 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Flask Web 專案 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| 一般 Web 專案 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Azure | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 部署至網站 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004;<sup>2</sup> |
| 部署至 Web 角色 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| 部署至背景工作角色 | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| 在 Azure 模擬器中執行 | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| 遠端偵錯 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> | &#10007; |
| 附加伺服器總管 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> | &#10007; | &#10007; |
<br/>

| Django 範本 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 偵錯 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| 自動完成 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004; | &#10004; |
| CSS 和 JavaScript 的自動完成 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007; | &#10007; |
<br/>

| 偵錯 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 偵錯 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 在不使用檔案的情況下進行偵錯 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| 偵錯 - 附加至編輯 | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| 混合模式偵錯 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| 遠端偵錯 (Windows、Mac OS X、Linux) | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| 偵錯互動式視窗 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

<a name="matrix-profiling"></a>

| 程式碼剖析 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 程式碼剖析 | &#10004; | &#10004; | &#10004; | &#10007; | &#10007; | &#10004; | &#10004; | &#10004; |
<br/>

| 測試 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 測試總管 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| 執行測試 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| 偵錯測試 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
<br/>

1. [Visual Studio 組件庫](http://visualstudiogallery.msdn.microsoft.com/abafc7d6-dcaa-40f4-8a5e-d6724bdb980c) \(英文\) 上提供的 Visual Studio Tools for Git 延伸模組中有針對 Visual Studio 2012 的 Git 支援。

1. 部署到 Azure 網站需要 [Azure SDK for .NET 2.1 - Visual Studio 2010 SP1](http://go.microsoft.com/fwlink/?LinkId=313855)。 較新的版本不支援 Visual Studio 2010。

1. 對 Azure「Web 角色」和「背景工作角色」的支援需要 [Azure SDK for .NET 2.3 - VS 2012](http://go.microsoft.com/fwlink/?LinkId=323511) 或更新版本。

1. 對 Azure「Web 角色」和「背景工作角色」的支援需要 [Azure SDK for .NET 2.3 - VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) 或更新版本。

1. Visual Studio 2013 中的 Django 範本編輯器有一些已知的問題，這些問題可透過安裝 Update 2 來解決。

1. 需要 Windows 8 或更新版本。 Visual Studio 2013 Express for Web 並沒有 [附加至處理序] 對話方塊，但透過使用 [伺服器總管] 中的 [附加偵錯工具] (Python) 命令，仍然可以進行「Azure 網站」遠端偵錯。 遠端偵錯需要 [Azure SDK for .NET 2.3 - Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkId=323510) 或更新版本。

1. 需要 Windows 8 或更新版本。 [伺服器總管] 中的 [附加偵錯工具] (Python) 命令需要 [Azure SDK for .NET 2.3 - Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkId=323510) 或更新版本。

1. 需要 Windows 8 或更新版本。

## <a name="additional-resources"></a>其他資源

- [WFastCGI bridge between IIS and Python](https://pypi.org/p/wfastcgi) (IIS 與 Python 之間的 WFastCGI 橋接) (pypi.org)
- [Microsoft Virtual Academy 上的免費 Python 課程](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Top Python Questions at Microsoft Virtual Academy](https://aka.ms/mva-top-python-questions) (Microsoft Virtual Academy 的前幾個 Python 問題)
