---
title: "使用 Visual Studio R 工具的 R Markdown | Microsoft Docs"
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac955b2-b6e1-4d32-b1a4-2882c93311fc
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: b29ae0240a29616edcdf2ae0dced7a9fca0f9584
ms.contentlocale: zh-tw
ms.lasthandoff: 07/12/2017

---

# <a name="creating-r-markdown-documents"></a>建立 R Markdown 文件

[R Markdown](https://rmarkdown.rstudio.com/) 是一種文件格式，可將 R 中的分析變成高品質的文件、報告、簡報和儀表板。

Visual Studio R 工具 (RTVS) 提供 R Markdown 項目範本、編輯器支援 (包括編輯器中處理 R 程式碼的 IntelliSense)，以及檔案產生功能。

使用 R Markdown：

1. 關閉 Visual Studio。
1. (僅限一次) 從 [pandoc.org](http://pandoc.org/installing.html) 安裝 `pandoc`。
1. 重新啟動 Visual Studio，應該會挑選 pandoc 安裝。
1. 安裝 `knitr` 和 `rmarkdown` 套件，這可在[互動視窗](interactive-repl.md)中執行：

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. 建立新的 R Markdown 檔案：使用 [檔案] > [新增] 功能表命令，從清單中選取 [R Markdown]，或以滑鼠右鍵按一下方案總管中的專案，然後選取 [新增 R Markdown]\(或 [新增] > [新增項目...]，然後從清單中選取 [R Markdown])。

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

1. 在編輯期間的任何時間，以滑鼠右鍵按一下編輯器，然後選取 [預覽]，其有 [HTML]、[PDF] 和 [Microsoft Word] 選項。 在該預覽中，您可將檔案另存為您選擇的合適格式。

