---
title: R Markdown
description: 如何在 Visual Studio 中建立 R Markdown 文件，以產生高品質報表、簡報和儀表板。
ms.date: 11/16/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 4e74966e71a7d440aed918e8aa609eeb8e68c355
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851877"
---
# <a name="create-r-markdown-documents"></a>建立 R Markdown 文件

[R Markdown](https://rmarkdown.rstudio.com/) 是一種文件格式，可將 R 中的分析變成高品質的文件、報告、簡報和儀表板。

Visual Studio R 工具 (RTVS) 提供 R Markdown 項目範本、編輯器支援 (包括編輯器中處理 R 程式碼的 IntelliSense)、檔案產生功能，以及即時預覽。

## <a name="using-r-markdown"></a>使用 R Markdown

1. 關閉 Visual Studio。
1. (僅限一次) 從 [pandoc.org](https://pandoc.org/installing.html) 安裝 `pandoc`。
1. 重新啟動 Visual Studio，應該會挑選 pandoc 安裝。
1. 安裝 `knitr` 和 `rmarkdown` 套件，這可在[互動視窗](interactive-repl-for-r-in-visual-studio.md)中執行：

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```

1. 使用 **[檔案**  >  **新增** 檔案]  >  功能表命令，並從清單中選取 **R**  >  **R Markdown** ，以建立新的 R Markdown 檔案。 在專案的內容中，以滑鼠右鍵按一下 [方案總管] 中的專案，然後選取 [新增 R Markdown] (或 [新增] > [新增項目]，然後從清單中選取 [R Markdown])。

1. 新檔案的預設內容如下︰

    <!-- markdownlint-disable MD048 -->
    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---

    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

    When you select the **R Tools | Publish | Preview** button, a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

    ```{r}
    summary(cars)
    ```

    You can also embed plots, for example:

    ```{r, echo=FALSE}
    plot(cars)
    ```

    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

    ~~~
    <!-- markdownlint-disable MD048 -->

## <a name="previews"></a>預覽

Visual Studio 2017 版本 15.5 和更新版本會自動提供 R Markdown 的即時預覽。 若要開啟編輯器與預覽之間的自動同步處理，請選取 [ **R 工具**]  >  **Markdown**[  >  **自動同步** 處理] (**Ctrl** + **Shift** + **Y**) 。 如果您未使用自動同步處理，您可以使用 **R 工具**  >  **Markdown**  >  **重載 R Markdown 預覽版來重新** 整理預覽。

您也可以藉由用滑鼠在編輯器上按右鍵並選取其中一個 **預覽** 命令來在 HTML、PDF 及 Microsoft Word 格式中預覽檔案。 您也可以在 [ **R 工具**  >  **Markdown** ] 功能表上取得相同的命令。 在舊版的中 (Visual Studio 在 [ **R 工具** 發佈] 功能表上找到這些命令  >   。 ) 

![RMarkdown 即時預覽和其他預覽功能表命令](media/rmarkdown-live-preview.png)
