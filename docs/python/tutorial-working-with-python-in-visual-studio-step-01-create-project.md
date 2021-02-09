---
title: Visual Studio 中的 Python 教學課程步驟 1 來建立專案
titleSuffix: ''
description: 在 Visual Studio 中 Python 功能核心逐步解說的概觀與步驟 1，包含必要條件和建立新的 Python 專案。
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 74259a6e15446d8ca0b07f3b694d0285427f8d9f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861552"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>教學課程：在 Visual Studio 中使用 Python

Python 是一種熱門的程式設計語言，不僅可靠、有彈性、容易學習、可在所有作業系統上免費使用，而且也受到強大的開發人員社群和許多免費程式庫支援。 語言支援所有形式的開發 (包含 Web 應用程式、Web 服務、傳統型應用程式、指令碼和科學計算)，並且許多大學、科學家、業餘開發人員和專業開發人員等都使用它。

Visual Studio 提供 Python 的第一級語言支援。 此教學課程會指導您逐步執行下列步驟：

- [步驟 0：安裝](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [步驟 1：建立 Python 專案 (此文章)](#step-1-create-a-new-python-project)
- [步驟 2：撰寫並執行程式碼以查看運作中的 Visual Studio IntelliSense](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [步驟3：在互動式複製視窗中建立更多程式碼](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [步驟 4：在 Visual Studio 偵錯工具中執行已完成的程式](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [步驟 5：安裝套件以及管理 Python 環境](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [步驟 6：使用 Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>步驟 1：建立新的 Python 專案

「專案」是 Visual Studio 如何管理合併使用以產生單一應用程式的所有檔案 (包含原始程式碼、資源、組態等等)。 專案會正式制定並維護所有專案檔案之間的關聯性，以及多個專案之間共用的外部資源之間的關聯性。 因此，相較於過去只在特定資料夾、指令碼、文字檔中管理專案的關聯性，專案讓應用程式的擴充及成長變得更為容易，在心情上更為輕鬆。

在本教學課程中，您會從包含單一空白程式碼檔案的簡單專案開始。

1. 在 Visual Studio 中，**選取**  >  [檔案 **新增**  >  **專案**] (**Ctrl** + **Shift** + **N**) ，這會顯示 [**新增專案**] 對話方塊。 在這裡，您可以瀏覽不同語言的範本，然後選取您專案的範本，並指定 Visual Studio 放置檔案的位置。

1. 若要查看 Python 範本，請選取左側的 [**已安裝**  >  的 **Python** ]，或搜尋 "Python"。 使用搜尋十分適合在您不記得範本在語言樹狀結構中的位置時來尋找範本。

    ![顯示 Python 專案的新增專案對話方塊](media/vs-getting-started-python-01-new-project.png)

    請注意，Visual Studio 中的 Python 支援如何包含一些專案範本，包含使用 Bottle、Flask 和 Django 架構的 Web 應用程式。 不過，基於本逐步解說的目的，讓我們先從空白專案開始。

1. 選取 [Python 應用程式] 範本，並指定專案的名稱，然後選取 [確定]。

1. 幾分鐘後，Visual Studio 會在方案總管 視窗 (1) 中顯示專案結構。 預設程式碼檔案會在編輯器中開啟 (2)。 [ **屬性** ] 視窗 (3) 也會顯示在 [ **方案總管**] 中所選取之任何專案的其他資訊，包括其在磁片上的確切位置。

    ![方案總管中的 Python 專案](media/vs-getting-started-python-02-windows.png)

1. 請花幾分鐘的時間熟悉 **方案總管**，也就是您在專案中流覽檔案和資料夾的位置。

    ![方案總管已展開以顯示各種功能](media/vs-getting-started-python-03-solution-explorer.png)

    以粗體反白顯示的 (1) 是您的專案，並使用您在 [ **新增專案** ] 對話方塊中提供的名稱。 在磁碟上，此專案是由專案資料夾中的 *.pyproj* 檔案所呈現。

    (2) 最上層是「方案」，預設其名稱與專案相同。 方案 (以磁碟上的 *.sln* 檔案呈現) 是一或多個相關專案的容器。 例如，如果您撰寫 Python 應用程式的 C++ 延伸模組，則該 C++ 專案可能位在相同的方案內。 方案也可以包含 Web 服務的專案，以及專用測試程式的專案。

    (3) 在您的專案下方，您會看到原始程式檔，在此情況下，只是單一 *.py* 檔案。 選取檔案時會在 [ **屬性** ] 視窗中顯示其屬性。 按兩下檔案即會以該檔案適合的方式開啟。

    (4) 在專案下方，也會有 [Python 環境] 節點。 展開時，您會看到您可用的 Python 解譯器。 展開解譯器節點，查看已安裝到該環境 (5) 的程式庫。

    以滑鼠右鍵按一下 **方案總管** 中的任何節點或專案，以存取適用命令的功能表。 例如，**Rename** 命令可讓您變更任何節點或項目的名稱 (包含專案和方案)。

## <a name="next-step"></a>後續步驟

> [!div class="nextstepaction"]
> [撰寫並執行程式碼](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>深入了解

- [Visual Studio 中的 Python 專案](managing-python-projects-in-visual-studio.md)。
- [了解 python.org 上的 Python 語言](https://www.python.org)
- [Python 初學者](https://www.python.org/about/gettingstarted/) (python.org)
