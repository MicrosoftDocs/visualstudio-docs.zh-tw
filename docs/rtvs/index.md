---
title: "Visual Studio R 工具 | Microsoft Docs"
ms.custom: 
ms.date: 6/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: hero-article
ms.assetid: 11324501-ceb6-47a2-ae13-e9e992d3603e
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 80a10c710aac8413bd59b53bb61de7a982c09952
ms.contentlocale: zh-tw
ms.lasthandoff: 07/12/2017

---

# <a name="working-with-r-in-visual-studio"></a>在 Visual Studio 中使用 R

R 專供統計運算與圖形設計之用，是高可延伸性的語言及環境。 它是依據 GNU General Public License 免費散發、享有堅強的社群支援，且以能夠產生出版物水平的繪圖 (包括數學符號和公式) 而聞名。 您可以透過 [r-project.org (英文)](https://www.r-project.org/about.html) 和[簡介 R (英文)](https://cran.r-project.org/doc/manuals/r-release/R-intro.html) 深入了解 R。

Visual Studio R 工具 (RTVS) 為適用於 Visual Studio 2017 和 Visual Studio 2015 Update 3 (或更新版本) 的免費[開放原始碼 (英文)](https://github.com/microsoft/RTVS) 擴充功能，並依據 MIT 授權發行。 (另一個會連結至 R 解譯器二進位檔，稱為 [RHost (英文)](https://github.com/microsoft/R-Host) 的開放原始碼元件，是依據 GNU Public License V2 發行)。

在 Visual Studio 中體驗 R：

- [安裝 R 工具](installation.md)。
- 遵循[開始使用](getting-started-with-r.md)指南，同時參考[範例](getting-started-samples.md)和[取得協助](getting-started-help.md)主題。

然後隨著連結深入了解 R 的相關功能，以及更加熟悉 Visual Studio 本身的一般功能。

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

下列影片也提供 R 工具功能的簡短 (5 分 48 秒) 檢閱：

> [!VIDEO https://www.youtube.com/embed/RcSDEfMgUvU]

## <a name="frequently-asked-questions"></a>常見問題集

**問：RTVS 是否可以搭配 Visual Studio Express 各版本使用？**

答： 否。

**問：RTVS 可以搭配哪種 R 解譯器使用？**

答： [CRAN R](https://cran.r-project.org/)、[Microsoft R Client 及 Microsoft R Server](https://msdn.microsoft.com/microsoft-r/)

**問：我可以從何處下載這些解譯器？**

答： 請參閱[安裝](installation.md)。

**問：我是否可以搭配 RTVS 使用 Visual Studio 擴充功能？**

答： 當然可以。 說到這個，以下是使用 R 的人員最愛使用的幾個擴充功能。

- [適用於 Vim 金鑰繫結的 VsVim (英文)](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub (英文)](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [具有即時預覽的 Markdown 編輯器 (英文)](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

請造訪 [Visual Studio Marketplace (英文)](https://marketplace.visualstudio.com/) 以尋找更多擴充功能。

**問：由於 RTVS 位於 Visual Studio 中，這是否代表 R 可以輕鬆搭配 C#、C++ 及其他 Microsoft 語言使用？**

答： 否。 RTVS 是開發 R 程式碼的工具，並會使用標準的原生 R 解譯器。 目前不支援 R 與其他語言互通。

**問：我找不到某個功能，但 RStudio 有該功能！**

答： 適用於 R 的 RStudio 是一個優秀且成熟的 IDE，且已經開發多年。 RTVS 正在努力包含所有您成功所需的重要功能。 請參與 [RTVS 問卷 (英文)](https://www.surveymonkey.com/r/RTVS1)，以協助我們決定後續作業的優先順序。

**問：RTVS 是否能運作於 OS X 或 Linux 上？**

答： 否，RTVS 是以 Visual Studio 為基礎建置，而 Visual Studio 為僅限 Windows 的實作。 話雖如此，Microsoft 仍在考慮以其所擁有的熱門跨平台編輯器 [Visual Studio Code](https://code.visualstudio.com/) 作為基礎，建置一組新的工具。

**問：我是否能為 RTVS 做出貢獻？**

答： 當然可以！ 原始程式碼位於 [GitHub (英文)](https://github.com/microsoft/RTVS) 上。 使用問題追蹤器提交 Bug，以及對已歸檔的 Bug 提出註解。

也歡迎您參與編輯這份文件&mdash;，只要選取任一頁面右上角的 [編輯] 命令，即可開始編輯文件。 我們也歡迎您在文件上提出註解，您可以在任何頁面的底部加入註解。

**問：RTVS 是否可以搭配我的原始檔控制系統使用？**

答： 是，您可以使用任何與 Visual Studio 整合的原始檔控制系統。

**問：RTVS 是否能運作在非英語地區設定上？**

答： RTVS 的 1.0 版僅支援英文。 1.1 版將會針對和 Visual Studio 本身相同的語言集進行當地語系化。 在此期間，請使用[適用於 Visual Studio 2015 的英文語言套件](https://www.microsoft.com/download/details.aspx?id=48157)。針對 Visual Studio 2017，請執行安裝程式，並在 [語言套件] 索引標籤中選取 [英文]。

![適用於 Visual Studio 2017 的國際設定](media/FAQ-international-settings.png)

**問：RTVS 是否能搭配 32 位元版本的 R 運作？**

答： 否，RTVS 僅支援在 Windows 64 位元版本上執行之 R 的 64 位元版本。

**問：我很喜歡我目前的 Visual Studio 設定，但我想要嘗試新的資料科學設定。我該怎麼做？**

答： 請使用 [工具] > [匯入和匯出設定] 儲存目前的 Visual Studio 設定，然後切換至資料科學設定。 若要還原已儲存的設定，請再次使用 [匯入和匯出設定] 命令。

**問：針對 RTVS 專案所建議的 `.gitignore` 設定為何？**

答： GitHub 有維護建議之 `.gitignore` 檔案的主要存放庫。 您可以在此查看它：[R .gitignore (英文)](https://github.com/github/gitignore/blob/master/R.gitignore)

**問：我是否可以將 Visual Studio 專案儲存在網路共用上？**

答： 否，Visual Studio 不支援從網路共用載入專案。

## <a name="send-us-your-feedback"></a>將您的意見反應傳送給我們！

1. **GitHub 問題**：連絡 RTVS 小組的最佳方式，是[在 GitHub 上提出問題 (英文)](https://github.com/Microsoft/RTVS/issues)，或使用 [R 工具] > [意見反應] 功能表。

1. **傳送笑臉 / 苦臉**：[R 工具] > [意見反應] 功能表可快速傳送意見反應，並附加 RTVS 記錄檔以協助診斷您的問題。 (記錄會寫入 `%temp%/RTVSlogs.zip`，以防您要分別傳送它們)。若是透過 [說明] > [意見反應] > [設定] 功能表命令，或是於安裝期間退出 Visual Studio 遙測，即會停用記錄。

1. **電子郵件**：您可以透過 *rtvsuserfeedback (at) microsoft.com*，將意見反應直接傳送給小組。

