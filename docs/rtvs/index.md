---
title: "Visual Studio R 工具 | Microsoft Docs"
ms.custom: 
ms.date: 11/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: hero-article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 1ff32914b523b2b515a3d4175e4b3f76ad7ecefd
ms.sourcegitcommit: ae9450e81c4167b3fbc9ee5d1992fc693628eafa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2017
---
# <a name="working-with-r-in-visual-studio"></a>在 Visual Studio 中使用 R

R 專供統計運算與圖形設計之用，是高可延伸性的語言及環境。 它是依據 GNU General Public License 免費散發、享有堅強的社群支援，且以能夠產生出版物水平的繪圖 (包括數學符號和公式) 而聞名。 您可以透過 [r-project.org (英文)](https://www.r-project.org/about.html) 和[簡介 R (英文)](https://cran.r-project.org/doc/manuals/r-release/R-intro.html) 深入了解 R。

Visual Studio R 工具 (RTVS) 為適用於 Visual Studio 2017 和 Visual Studio 2015 Update 3 (或更新版本) 的免費[開放原始碼 (英文)](https://github.com/microsoft/RTVS) 擴充功能，並依據 MIT 授權發行。 (另一個會連結至 R 解譯器二進位檔，稱為 [RHost (英文)](https://github.com/microsoft/R-Host) 的開放原始碼元件，是依據 GNU Public License V2 發行)。

> [!Note]
> 目前只有 Windows 上的 Visual Studio 支援 RTVS，Visual Studio for Mac 則不支援。

在 Visual Studio 中體驗 R：

- [安裝 R 工具](installation.md)。
- 遵循[開始使用](getting-started-with-r.md)指南，同時參考[範例](getting-started-samples.md)和[取得協助](getting-started-help.md)主題。

然後遵循下列連結以深入了解 R 的相關功能，以及 Visual Studio 本身的一般功能。

| 功能 | 描述 | 一般 Visual Studio 文件 | 
| --- | --- | --- |
| [Visual Studio 專案系統](projects.md) | 在便利的結構中組織並管理相關檔案，並利用適用於各種項目 (例如 R 程式碼、R 文件、R Markdown、SQL 查詢及預存程序) 的有用範本。 同時也能運用[套件管理員](package-manager.md)和 [SQL Server 整合](sql-server.md)。  | [Visual Studio 中的方案和專案](../ide/solutions-and-projects-in-visual-studio.md) |
| [工作區](workspaces.md) | RTVS 可繫結至本機及遠端工作區，讓您能夠使用更小的資料集於本機開發 R 程式碼，然後輕鬆地利用更大的資料集在更為強大的雲端電腦上執行程式碼。 | N/A |
| [R 工具選項](options.md) | 控制 RTVS 的各個層面。 | [選項對話方塊](../ide/reference/options-dialog-box-visual-studio.md) |
| [豐富的編輯、IntelliSense 及程式碼片段](code-editing.md) | 包含語法色彩標示、適用所有程式碼和程式庫的 [IntelliSense](code-intellisense.md)、程式碼格式設定、簽章說明、移至定義、尋找所有參考、[程式碼片段](code-snippets.md)等。 | [在程式碼和文字編輯器中撰寫程式碼](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown.md) | R Markdown 文件可協助您共用資料結果，Markdown 程式碼區塊內將具有整合的 R 程式碼。 | N/A |
| [互動式視窗](interactive-repl.md) | 針對 R 提供完整的 REPL 體驗，並能夠輕鬆地在互動式視窗中執行來源檔案中的程式碼。 | N/A |
| [視覺化資料](visualizing-data.md) | 繪圖是 R 體驗不可或缺的一部分，而 RTVS 支援多種獨立的繪圖視窗，每個視窗都擁有自己的記錄，並可以在視窗之間移動繪圖。 繪圖可以儲存為點陣圖或 PDF 檔案，或是以點陣圖或中繼檔的形式複製到剪貼簿。  | N/A |
| [變數總管](variable-explorer.md) | 以全域或套件特定的範圍檢視變數，並能夠檢視可排序的資料表，以及匯出為 CSV。 | N/A |
| [功能完整的偵錯](debugging.md) | 包含與互動式視窗的整合。 | [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md) |

另請參閱[常見問題集](faq.md)。

下列影片也提供 R 工具功能的簡短 (5 分 48 秒) 檢閱：

> [!VIDEO https://www.youtube.com/embed/RcSDEfMgUvU]

## <a name="send-us-your-feedback"></a>將您的意見反應傳送給我們！

1. **GitHub 問題**：連絡 RTVS 小組的最佳方式，是[在 GitHub 上提出問題 (英文)](https://github.com/Microsoft/RTVS/issues)，或使用 [R 工具] > [意見反應] 功能表。

1. **傳送笑臉 / 苦臉**：[R 工具] > [意見反應] 功能表可快速傳送意見反應，並附加 RTVS 記錄檔以協助診斷您的問題。 (記錄會寫入 `%temp%/RTVSlogs.zip`，以防您要分別傳送它們)。若是透過 [說明] > [意見反應] > [設定] 功能表命令，或是於安裝期間退出 Visual Studio 遙測，即會停用記錄。

1. **電子郵件**：您可以透過 *rtvsuserfeedback (at) microsoft.com*，將意見反應直接傳送給小組。
