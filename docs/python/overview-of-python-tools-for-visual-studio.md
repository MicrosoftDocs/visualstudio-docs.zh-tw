---
title: "Visual Studio 中的 Python 支援概觀 (Windows) | Microsoft Docs"
description: "適用於 Visual Studio 中 Python 之功能 (也稱為「適用於 Visual Studio 的 Python 工具」或 PTVS) 的摘要，包括常見問題集，以及 Visual Studio 版本之間的功能支援對照表。"
ms.custom: 
ms.date: 01/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: hero-article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 067684c7b5064e096849afe69d2f0db1bcc75ea6
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2018
---
# <a name="working-with-python-in-visual-studio-windows"></a>在 Visual Studio 中使用 Python (Windows)

Python 是一種熱門的程式設計語言，不僅可靠、有彈性、容易學習、可在所有作業系統上免費使用，而且也受到強大的開發人員社群和許多免費程式庫支援。 Python 支援所有形式的開發，包括 Web 應用程式、Web 服務傳統型應用程式、指令碼及科學計算，並且許多大學、科學家、業餘開發人員及專業開發人員等都使用它。 您可以從 [python.org (英文)](https://www.python.org) 和[適用於初學者的 Python (英文)](https://www.python.org/about/gettingstarted/) 深入了解此語言。

Windows 上的 Visual Studio 可透過 Python 開發與資料科學工作負載 (Visual Studio 2017) 和免費的「適用於 Visual Studio 的 Python 工具」延伸模組 (Visual Studio 2015 和更舊的版本)，針對 Python 語言提供[開放原始碼](https://github.com/Microsoft/ptvs)支援。 Python 目前在 Visual Studio for Mac 中不予支援，但可透過 Visual Studio Code 在 Mac 和 Linux 上使用 (請參閱[問與答](#questions-and-answers))。

若要開始使用：

- 請遵循[安裝指示](installing-python-support-in-visual-studio.md)，以設定 Python 工作負載。
- 完整瀏覽一或多份快速入門，以建立專案。 如果您不確定從何處著手，請先[從範本建立專案](quickstart-02-project-from-template.md)。
- 請遵循[在 Visual Studio 中使用 Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) 的教學課程，以取得完整的端對端體驗。
- 接著，請使用下表中的連結，探索 Python 相關功能與 Visual Studio 本身的功能。

| 功能 | 描述 | 一般 Visual Studio 文件 |
| --- | --- | --- |
| [Visual Studio 專案系統](managing-python-projects-in-visual-studio.md) | 既能夠以隱含方式讀取 Python 程式碼的資料夾結構，又允許採用明確的控制來識別應用程式程式碼、測試程式碼、網頁、JavaScript、建置指令碼等。 | [Visual Studio 中的方案和專案](../ide/solutions-and-projects-in-visual-studio.md) |
| [專案範本](managing-python-projects-in-visual-studio.md#project-templates) | 快速建立主控台、Web、Azure、資料科學及其他類型專案的專案結構 | [Visual Studio 範本](../ide/creating-project-and-item-templates.md#visual-studio-templates) |
| 多重解譯器支援 | 支援各種版本的 CPython 和 IronPython。 | N/A |
| IPython 支援 | 包含對內嵌繪圖、.NET 及 Windows Presentation Foundation (WPF) 之 REPL 中 IPython/Jupyter 的支援。 | N/A |
| [豐富的編輯、 IntelliSense 及程式碼理解](code-editing.md) | 包含語法色彩標示、所有程式碼和程式庫的自動完成、[程式碼格式設定](code-formatting.md)、簽章說明、類別檢視、移至定義、尋找所有參考、程式碼片段、[重構](code-refactoring.md)、[PyLint](code-pylint.md) 等。 | [在程式碼和文字編輯器中撰寫程式碼](../ide/writing-code-in-the-code-and-text-editor.md) |
| [互動式視窗](interactive-repl.md) | 提供 Python 的快速 REPL 體驗，可讓您輕鬆地醒目提示部分程式碼並將它傳送到 [Interactive Window (互動式視窗)]。 | N/A |
| [功能完整的偵錯](debugging.md) | 可在使用或不使用 Visual Studio 專案的情況下進行偵錯，包括能夠針對現有的可執行檔進行偵錯、進行 [Python/C++ 混合模式偵錯](debugging-mixed-mode.md)、針對 Windows/Linux/Mac 進行[遠端偵錯](debugging-cross-platform-remote.md)、[針對 Azure 進行遠端偵錯](debugging-azure-remote.md)，以及在 [互動式視窗] 內進行偵錯。 | [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md) |
| [具備完整報告的分析工具](profiling.md) | 探索您應用程式內時間的使用情況，包括可讓您比較不同分析執行回合間的效能。 | [分析工具](../profiling/profiling-tools.md) (並非所有 Visual Studio 分析功能都可供 Python 使用) |
| [單元測試工具](unit-testing.md) | 在 Visual Studio [測試總管] 中探索、執行及管理測試，並輕鬆針對單元測試進行偵錯。 | [對程式碼進行單元測試](../test/unit-test-your-code.md) |

Python 工作負載也包含 [Azure SDK for Python](azure-sdk-for-python.md)，此 SDK 可簡化從 Windows、Mac OS X 和 Linux 應用程式使用 Azure 服務。

如需影片介紹，請觀看 Microsoft Virtual Academy 上的 [Python Tools for Visual Studio](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121) (適用於 Visual Studio 的 Python 工具) 簡短課程 (共約 22 分鐘)。 

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567]

## <a name="questions-and-answers"></a>問與答

**問：Visual Studio for Mac 提供 Python 支援嗎？**

答： 目前未提供，但已在 [UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac/suggestions/18670291-python-tools-for-visual-studio-mac) 上要求。 [Visual Studio for Mac](/visualstudio/mac/) 文件可識別它確實支援的目前開發類型。 同時，Windows、Mac 和 Linux 上的 Visual Studio Code [透過可用的延伸模組與 Python 搭配運作良好](https://code.visualstudio.com/docs/languages/python)。

**問：建置 UI 時，我可以使用什麼功能來搭配 Python？**

答： 這方面的主要提供項目是 [Qt 專案](https://www.qt.io/qt-for-application-development/) 及 Python 的繫結，其稱為 [PySide (正式繫結)](http://wiki.qt.io/PySide) (另請參閱 [PySide downloads](https://download.qt.io/official_releases/pyside/.)) (PySide 下載) 和 [PyQt](https://wiki.python.org/moin/PyQt)。 目前，Visual Studio 中的 Python 支援不包含任何特定的 UI 開發工具。

**問：Python 專案是否能產生獨立的可執行檔？**

答： 一般來說，Python 是解譯的語言，並包含可在適當 Python 支援環境 (例如 Visual Studio 和網頁伺服器) 中視需要執行的程式碼。 目前，Visual Studio 本身不提供用來建立獨立可執行檔的工具，因為獨立可執行檔基本上表示內嵌 Python 解譯器的程式。 不過，若要建立可執行檔，Python 社群中提供多種方式，如 [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency) 中所述。 CPython 也支援在原生的應用程式中內嵌，如[使用 CPython 可內嵌的 Zip 檔案](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/)部落格文章中所述。

## <a name="features-matrix"></a>功能對照表

您可以下列版本的 Visual Studio 中安裝 Python 支援，如[安裝指南 (英文)](installing-python-support-in-visual-studio.md) 所述：

- [Visual Studio 2017 (所有版本)](https://www.visualstudio.com/vs/)
- [Visual Studio 2015 (所有版本)] (https://www.visualstudio.com/en-us/downloads/visual-studio-2015-downloads-vs)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express for Web (Update 2 或更新版本)
- Visual Studio 2013 Express for Desktop (Update 2 或更新版本)
- Visual Studio 2013 (Pro 版或更新版本)
- Visual Studio 2012 (Pro 版或更新版本)
- Visual Studio 2010 SP1 (Pro 版或更新版本；需要 .NET 4.5)

依 Visual Studio 版本 (Version 和 Edition) 分類的支援功能：

| Python 支援 | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| 多重解譯器管理 | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
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
| 伺服器總管附加 | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> | &#10007; | &#10007; |
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

- [IIS 與 Python 之間的 WFastCGI 橋接 (英文)](https://pypi.python.org/pypi/wfastcgi) (python.org)
- [Microsoft Virtual Academy 上的免費 Python 課程](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Top Python Questions at Microsoft Virtual Academy](https://aka.ms/mva-top-python-questions) (Microsoft Virtual Academy 的前幾個 Python 問題)
