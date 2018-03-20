---
title: "在 Visual Studio 中使用 Python，步驟 1：建立專案 | Microsoft Docs"
description: "在 Visual Studio 內使用 Python 之核心教學課程的步驟 1，提供整個教學課程的大鋼、描述必要條件，並逐步介紹建立新 Python 專案的程序。"
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 469494b2c0c4704ac1eab42d36934657adc2313d
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="working-with-python-in-visual-studio"></a>在 Visual Studio 中使用 Python

Python 是一種熱門的程式設計語言，不僅可靠、有彈性、容易學習、可在所有作業系統上免費使用，而且也受到強大的開發人員社群和許多免費程式庫支援。 語言支援所有形式的開發 (包含 Web 應用程式、Web 服務、傳統型應用程式、指令碼和科學計算)，並且許多大學、科學家、業餘開發人員和專業開發人員等都使用它。

Visual Studio 提供 Python 的第一級語言支援。 此教學課程會指導您逐步執行下列步驟：

- [步驟 0：安裝](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [步驟 1：建立 Python 專案 (本文章)](#step-1-create-a-new-python-project)
- [步驟 2：撰寫和執行程式碼以查看運作中的 Visual Studio IntelliSense](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [步驟 3：在互動式 REPL 視窗中建立其他程式碼](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [步驟 4：在 Visual Studio 偵錯工具中執行已完成的程式](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [步驟 5：安裝套件以及管理 Python 環境](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [步驟 6：使用 Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="prerequisites"></a>必要條件

- 已安裝 Python 工作負載的 Visual Studio 2017。 如需指示，請參閱[步驟 0](tutorial-working-with-python-in-visual-studio-step-00-installation.md)。

## <a name="step-1-create-a-new-python-project"></a>步驟 1：建立新的 Python 專案

「專案」是 Visual Studio 如何管理合併使用以產生單一應用程式的所有檔案 (包含原始程式碼、資源、組態等等)。 專案會正式制定並維護所有專案檔案之間的關聯性，以及多個專案之間共用的外部資源之間的關聯性。 因此，專案可讓您應用程式的展開和成長比只管理特定資料夾、指令碼、文字檔甚至您自己的考量中的專案關聯性更為簡單。

在本教學課程中，您會從包含單一空白程式碼檔案的簡單專案開始。

1. 在 Visual Studio 中，選取 [檔案] > [新增] > [專案] (Ctrl+Shift+N) 以啟動 [新增專案] 對話方塊。 在這裡，您可以瀏覽不同語言的範本，然後選取您專案的範本，並指定 Visual Studio 放置檔案的位置。

1. 若要檢視 Python 範本，請選取左側的 [已安裝] > [Python]，或搜尋 "Python"。 使用搜尋十分適合在您不記得範本在語言樹狀結構中的位置時來尋找範本。

    ![顯示 Python 專案的新增專案對話方塊](media/vs-getting-started-python-01-new-project.png)

    請注意，Visual Studio 中的 Python 支援如何包含一些專案範本，包含使用 Bottle、Flask 和 Django 架構的 Web 應用程式。 不過，基於本逐步解說的目的，讓我們先從空白專案開始。

1. 選取 [Python 應用程式] 範本，並指定專案的名稱，然後選取 [確定]。

1. 幾分鐘後，Visual Studio 會在方案總管 視窗 (1) 中顯示專案結構。 預設程式碼檔案會在編輯器中開啟 (2)。 也會出現屬性視窗 (3)，以顯示方案總管中所選取之任何項目的其他資訊 (包含其在磁碟上的確切位置)。

    ![方案總管中的 Python 專案](media/vs-getting-started-python-02-windows.png)

1. 需要一些時間來熟悉方案總管，您可以在其中瀏覽專案中的檔案和資料夾。

    ![方案總管已展開以顯示各種功能](media/vs-getting-started-python-03-solution-explorer.png)

    (1) 以粗體反白顯示的項目就是您的專案，並使用您在 [新增專案] 對話方塊中所指定的名稱。 在磁碟上，此專案是由專案資料夾中的 `.pyproj` 檔案所呈現。

    (2) 最上層是「方案」，預設其名稱與專案相同。 方案 (以磁碟上的 `.sln` 檔案呈現) 是一或多個相關專案的容器。 例如，如果您撰寫 Python 應用程式的 C++ 延伸模組，則該 C++ 專案可能位在相同的方案內。 方案也可以包含 Web 服務的專案，以及專用測試程式的專案。 

    (3) 在您的專案下方，您會看到原始程式檔，在此情況下，只是單一 `.py` 檔案。 選取檔案時會在 [屬性] 視窗中顯示其屬性。 按兩下檔案即會以該檔案適合的方式開啟。

    (4) 在專案下方，也會有 [Python 環境] 節點。 展開時，您會看到您可用的 Python 解譯器。 展開解譯器節點，查看已安裝到該環境 (5) 的程式庫。

    以滑鼠右鍵按一下方案總管中的任何節點或項目，以存取適用命令的功能表。 例如，**Rename** 命令可讓您變更任何節點或項目的名稱 (包含專案和方案)。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [撰寫和執行程式碼](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="going-deeper"></a>繼續探討

- [Visual Studio 中的 Python 專案](managing-python-projects-in-visual-studio.md)。
- [了解 python.org 上的 Python 語言](https://www.python.org)
- [Python 初學者](https://www.python.org/about/gettingstarted/) (python.org)
- [Microsoft Virtual Academy 上的免費 Python 課程](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Top Python Questions at Microsoft Virtual Academy](https://aka.ms/mva-top-python-questions) (Microsoft Virtual Academy 的前幾個 Python 問題)
