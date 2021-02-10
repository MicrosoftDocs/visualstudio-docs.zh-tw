---
title: 適用於 Visual Studio 的 R 工具
description: Visual Studio 2017 R 工具 (RTVS) 是免費的開放原始碼延伸模組，提供許多語言功能，包括 IntelliSense、偵錯及遠端工作區。
ms.date: 11/13/2017
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 76230555defd9367800f6c3c4e5ea0fe24a5195d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946341"
---
# <a name="work-with-r-in-visual-studio"></a>在 Visual Studio 中使用 R

R 專供統計運算與圖形設計之用，是高可延伸性的語言及環境。 它是依據 GNU General Public License 免費散發、享有堅強的社群支援，且以能夠產生出版物水平的繪圖 (包括數學符號和公式) 而聞名。 您可以透過 [r-project.org (英文)](https://www.r-project.org/about.html) 和[簡介 R (英文)](https://cran.r-project.org/doc/manuals/r-release/R-intro.html) 深入了解 R。

Visual Studio R 工具 (RTVS) 為適用於 Visual Studio 2017 和 Visual Studio 2015 Update 3 (或更新版本) 的免費[開放原始碼 (英文)](https://github.com/microsoft/RTVS) 擴充功能，並依據 MIT 授權發行。 (另一個會連結至 R 解譯器二進位檔，稱為 [RHost (英文)](https://github.com/microsoft/R-Host) 的開放原始碼元件，是依據 GNU Public License V2 發行)。

> [!Note]
> 目前只有 Windows 上的 Visual Studio 2017 支援 RTVS，Visual Studio for Mac 則不支援。 Visual Studio 2019 無法使用此延伸模組。

在 Visual Studio 中體驗 R：

- [安裝 R 工具](installing-r-tools-for-visual-studio.md)。
- 請遵循[快速入門](getting-started-with-r.md)指南、[範例](getting-started-samples.md)及[取得說明](getting-started-help.md)等文章中的指示作業。

然後遵循下列連結以深入了解 R 的相關功能，以及 Visual Studio 本身的一般功能。

| 功能 | 描述 | 一般 Visual Studio 文件 |
| --- | --- | --- |
| [Visual Studio 專案系統](r-projects-in-visual-studio.md) | 在便利的結構中組織並管理相關檔案，並利用適用於各種項目 (例如 R 程式碼、R 文件、R Markdown、SQL 查詢及預存程序) 的有用範本。 同時也能運用[套件管理員](r-package-manager-in-visual-studio.md)和 [SQL Server 整合](integrating-sql-server-with-r.md)。  | [Visual Studio 中的方案和專案](../ide/solutions-and-projects-in-visual-studio.md) |
| [工作區](r-workspaces-in-visual-studio.md) | RTVS 可繫結至本機及遠端工作區，讓您能夠使用更小的資料集於本機開發 R 程式碼，然後輕鬆地利用更大的資料集在更為強大的雲端電腦上執行程式碼。 | n/a |
| [R 工具選項](options-for-r-tools-in-visual-studio.md) | 控制 RTVS 的各個層面。 | [選項對話方塊](../ide/reference/options-dialog-box-visual-studio.md) |
| [豐富的編輯、IntelliSense 及程式碼片段](editing-r-code-in-visual-studio.md) | 包含語法色彩標示、適用所有程式碼和程式庫的 [IntelliSense](r-intellisense.md)、程式碼格式設定、簽章說明、移至定義、尋找所有參考、[程式碼片段](code-snippets-for-r.md)等。 | [程式碼編輯器的功能](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown-with-r-in-visual-studio.md) | R Markdown 文件可協助您共用資料結果，Markdown 程式碼區塊內將具有整合的 R 程式碼。 | n/a |
| [互動式視窗](interactive-repl-for-r-in-visual-studio.md) | 針對 R 提供完整的 REPL 體驗，並能夠輕鬆地在互動式視窗中執行來源檔案中的程式碼。 | n/a |
| [視覺化資料](visualizing-data-with-r-in-visual-studio.md) | 繪圖是 R 體驗不可或缺的一部分，而 RTVS 支援多種獨立的繪圖視窗，每個視窗都擁有自己的記錄，並可以在視窗之間移動繪圖。 繪圖可以儲存為點陣圖或 PDF 檔案，或是以點陣圖或中繼檔的形式複製到剪貼簿。  | n/a |
| [變數總管](variable-explorer.md) | 以全域或套件特定的範圍檢視變數，並能夠檢視可排序的資料表，以及匯出為 CSV。 | n/a |
| [功能完整的偵錯](debugging-r-in-visual-studio.md) | 包含與互動式視窗的整合。 | [Visual Studio 偵錯](../debugger/debugger-feature-tour.md) |

另請參閱[常見問題集](faq.md)。

![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片")[觀看影片 (youtube.com)](https://www.youtube.com/watch?v=dll3IS1bfWQ) 以概覽 Visual Studio R 工具 (12 分 36 秒)。 另請觀看[其他 R 工具影片](https://www.youtube.com/results?search_query=R+Tools+for+visual+studio)。

## <a name="send-us-your-feedback"></a>將您的意見反應傳送給我們！

1. **GitHub Issues**：連絡 RTVS 小組的最佳方式，就是 [在 GitHub 上提問](https://github.com/Microsoft/RTVS/issues)，或是使用 [R 工具] >  [意見反應] 功能表。

1. **傳送笑臉/苦臉**：[R 工具] >  [意見反應] 功能表是快速傳送意見反應，以及附加 RTVS 記錄檔，協助診斷問題最快的方式  (若您想要個別傳送記錄檔，其位於 *%temp%/RTVSlogs.zip* 之中)。若透過 [說明] >  [意見反應] >  [設定] 功能表命令或在是安裝期間選擇退出 Visual Studio 遙測，將會停用記錄。

1. **電子郵件**：您可以透過 *rtvsuserfeedback (at) microsoft.com*，將意見反應直接傳送給小組。
