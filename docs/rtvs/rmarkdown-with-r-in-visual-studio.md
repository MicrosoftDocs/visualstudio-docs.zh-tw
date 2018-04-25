---
title: R Markdown
description: 如何在 Visual Studio 中建立 R Markdown 文件，以產生高品質報表、簡報和儀表板。
ms.date: 11/16/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: bc8ffe0f6d3cdc0cd572c39dedb5f059e63525cb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="creating-r-markdown-documents"></a>建立 R Markdown 文件

[R Markdown](https://rmarkdown.rstudio.com/) 是一種文件格式，可將 R 中的分析變成高品質的文件、報告、簡報和儀表板。

Visual Studio R 工具 (RTVS) 提供 R Markdown 項目範本、編輯器支援 (包括編輯器中處理 R 程式碼的 IntelliSense)、檔案產生功能，以及即時預覽。

## <a name="using-r-markdown"></a>使用 R Markdown

1. 關閉 Visual Studio。
1. (僅限一次) 從 [pandoc.org](http://pandoc.org/installing.html) 安裝 `pandoc`。
1. 重新啟動 Visual Studio，應該會挑選 pandoc 安裝。
1. 安裝 `knitr` 和 `rmarkdown` 套件，這可在[互動視窗](interactive-repl-for-r-in-visual-studio.md)中執行：

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. 使用 [檔案] > [新增] > [檔案] 功能表命令，並從清單中選取 [R] > [R Markdown] 來建立新的 R Markdown 檔案。 在專案的內容中，以滑鼠右鍵按一下方案總管中的專案，然後選取 [新增 R Markdown] (或 [新增] > [新增項目...]，然後從清單中選取 [R Markdown])。

1. 新檔案的預設內容如下︰

    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---

    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

    When you click the **R Tools | Publish | Preview** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

    ```{r}
    summary(cars)
    ```

    You can also embed plots, for example:

    ```{r, echo=FALSE}
    plot(cars)
    ```

    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

    ~~~

## <a name="previews"></a>預覽

Visual Studio 2017 版本 15.5 和更新版本會自動提供 R Markdown 的即時預覽。 若要開啟編輯器和預覽之間的自動同步功能，請選取 [R 工具] > [Markdown] > [自動同步] (Ctrl+Shift+Y)。 若您並未使用自動同步，您可以使用 [R 工具] > [Markdown] > [Reload R Markdown Preview] (重新載入 R Markdown 預覽) 來重新整理預覽。

您也可以藉由用滑鼠在編輯器上按右鍵並選取其中一個**預覽**命令來在 HTML、PDF 及 Microsoft Word 格式中預覽檔案。 相同的命令同樣也可以在 [R 工具] > [Markdown] 功能表上找到。 (在舊版的 Visual Studio 中，您可以在 [R 工具] > [發佈] 功能表中找到這些命令。)

![RMarkdown 即時預覽和其他預覽功能表命令](media/rmarkdown-live-preview.png)
