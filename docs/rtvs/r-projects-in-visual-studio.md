---
title: R 專案
description: 如何在 Visual Studio 中建立管理員 R 專案，包括屬性、專案命令和範本。
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 42cdc6e964d23b5aafdfe225c04d5d35b151cc08
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936401"
---
# <a name="create-r-projects-in-visual-studio"></a>在 Visual Studio 中建立 R 專案

R 專案 (*.rxproj* 檔案) 會識別與您專案建立關聯的所有來源和內容檔案。 它也會包含每個檔案的建置資訊、維護要與來源控制系統整合的資訊，以及協助您將應用程式組織成邏輯元件。 不過，工作區相關資訊 (例如已安裝的套件清單) 會分別在工作區中自行維護。

您一律是在 Visual Studio 的「方案」內管理專案，方案中可以包含任意數目且彼此參考的專案。 請參閱[使用 Visual Studio 中的多個專案類型](#use-multiple-project-types-in-visual-studio)。

## <a name="creating-a-new-r-project"></a>建立新的 R 專案

1. 開啟 Visual Studio。
1. 選擇 [檔案] > [新增] > [專案] (**Ctrl**+**Shift**+**N**)
1. 從 **範本** R 下選取 [r 專案]  >  ****，為專案提供名稱和位置，然後選取 **[確定]**：

    ![Visual Studio R (在 VS2017 中為 RTVS) 的 [新增專案] 對話方塊](media/getting-started-01-new-project.png)

此命令會在編輯器中建立具有已開啟之空 *script.R* 檔案的專案。 請注意，方案總管的專案中也有兩個其他檔案︰

![從範本建立的 R 專案內容](media/projects-template-results.png)

*.Rhistory* 會記錄您在 [R 互動](interactive-repl-for-r-in-visual-studio.md)視窗中輸入的所有命令。 您可以使用 **R 工具**  >  **Windows**  >  **history** 命令開啟專用的歷程記錄視窗。 該視窗具有工具列按鈕和內容功能表項目可清除歷程記錄內容。

*rproject.rproj* 檔案會維護某些本來由 Visual Studio 管理的 R 特定專案設定：

| 屬性 | 預設 | 描述 |
| --- | --- | --- |
| 版本 | 1.0 | 建立專案所使用的 Visual Studio R 工具版本。 |
| RestoreWorkspace | 預設 | 自動從專案目錄的 `.RData` 檔案中載入之前的工作區變數。 |
| SaveWorkspace | 預設 | 關閉專案時，將目前的工作區變數儲存在專案目錄的 `.RData` 檔案。 |
| AlwaysSaveHistory | 預設 | 關閉專案時，將目前的互動式視窗歷程記錄儲存在專案目錄的 `.RHistory` 檔案。 |
| EnableCodeIndexing | 是 | 決定是否執行背景編製索引工作，以加速搜尋程式碼。 |
| UseSpacesForTab | 是 | 決定在編輯器中按下 **tab** 鍵時，是否要插入空格 (Yes) 或 tab 字元 (No) 。 |
| NumSpacesForTab | 2 | 如果 UseSpacesForTab 為 Yes，要插入的空格數目。 |
| 編碼 | UTF-8 | `.R` 檔案的預設編碼。 |
| RnwWeave | Sweave | 編排 Rnw 檔案時要使用的套件。 |
| LaTeX | pdfLaTeX | 將 RMarkdown 轉換為 PDF 時要使用的程式庫。 |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>將檔案資料夾轉換成 R 專案

如果專案中有想要管理的現有 *.R* 檔案資料夾，請執行下列步驟︰

1. 如上節所述，在 Visual Studio 中建立新的專案。
1. 將檔案複製到專案資料夾。
1. 在 [Visual Studio 方案總管中，以滑鼠右鍵按一下專案，選取 [**加入**  >  **現有專案**]，然後流覽至您要新增的檔案。 選取 [確定] 之後，這些檔案就會出現在您的專案樹狀結構中。
1. 若要將程式碼組織到子資料夾，請以滑鼠右鍵按一下專案、選取 [先 **加入**  >  **新資料夾**]，然後將檔案複製到該資料夾，並在步驟3中新增這些現有的專案。

## <a name="project-properties"></a>專案屬性

若要開啟專案屬性頁面，請以滑鼠右鍵按一下 [方案總管] 中的專案，然後選取 [屬性]，或選取 [專案] > [(專案名稱) 屬性] 功能表項目。 開啟的視窗會顯示專案屬性：

| 索引標籤 | 屬性 | 描述 |
| --- | --- | --- |
| 執行 | 啟動檔案 | 使用 **Source startup file** 命令、**F5**、[偵錯] > [開始偵錯] 或 [偵錯] > [啟動但不偵錯] 執行的檔案名稱。 以滑鼠右鍵按一下專案中的檔案，然後選取 [設定為啟動 R 指令碼]，也會將它設定為啟動檔案。 |
| | 重設執行中的 R互動 | 執行專案時，清除互動視窗工作區中的所有變數。 這樣做可以保證沒有前次執行的剩餘工作區內容。 |
| | 遠端專案路徑 | 遠端工作區的路徑。 |
| | 執行時傳輸檔案 | 指出受限於 [Files to transfer]\(要傳輸的檔案) 篩選的專案檔案，是否每一次執行都要複製到遠端工作區。 |
| | 要傳輸的檔案 | 如已選取 [Transfer files on run]\(執行時傳輸檔案)，表示要複製到遠端工作區之特定檔案的檔案名稱和萬用字元。 |
| 設定 | (Settings.R 檔案) | R 專案設定，來自位於專案內的 *Settings.R* 或 *.Settings.R* 檔案。 如果沒有設定檔案，您可以新增變數，並儲存頁面，這樣就會為您建立預設 *Settings.R* 檔案。 您也可以 **透過 [檔案新增**  >  **專案**] 功能表命令，將設定檔新增至專案。 <br/> 在執行其他模組前，設定會先儲存為 R 程式碼，且檔案可以成為來源，因此會以預先定義的設定來填入環境。 |

## <a name="r-specific-project-commands"></a>R 特定專案命令

Visual Studio 專案透過滑鼠右鍵功能表和 [專案] 功能表支援多個一般命令。 如需這些一般功能的詳細資訊，請參閱 [Visual Studio 中的方案和專案](../ide/solutions-and-projects-in-visual-studio.md)。 不過，請記住 Visual Studio R 工具 (RTVS) 會將多個專屬命令新增至 R 專案以及專案中檔案和資料夾的快顯功能表。

| 命令 | 描述 |
| --- | --- |
| 在此設定工作目錄 | 將 [R 互動] 視窗的工作目錄設定為專案資料夾，而專案資料夾也可以用在專案內的任何子資料夾上。 |
| 開啟包含的資料夾 | 在所選檔案位置開啟 Windows 檔案總管。 |
| 新增 R 指令碼 | 以預設名稱建立並開啟新的 *.R* 檔案。 您也可以使用 [**加入**  >  **新專案**] 命令來建立 *。R* 檔案以及其他許多檔案類型。 請參閱 [R 特定項目範本](#r-specific-item-templates)。 |
| 新增 R Markdown | 以預設名稱建立並開啟新的 *.rmd* 文件。 您也可以使用 [**加入**  >  **新專案**] 命令來建立 *rmd* 檔案，以及一些其他檔案類型。 請參閱 [R 特定項目範本](#r-specific-item-templates)。  |
| 發行預存程序 | 啟動發行包含在 R 指令碼中所有預存程序的流程。 請參閱[使用 SQL Server 預存程序](integrating-sql-server-with-r.md#work-with-sql-server-stored-procedures)。 |

## <a name="r-specific-item-templates"></a>R 特定項目範本

RTVS 包含特定檔案類型的多個範本。 您可以用滑鼠右鍵按一下 R 專案並選取 [**加入** 新專案]  >  ****、選取 [**專案**  >  **加入新專案**]，或使用 [檔案新檔案]，   >    >  然後選取 [ **R** ] 索引標籤，以存取範本。探索範本的最佳方式是建立新的專案，並插入每個類型的檔案。

> [!Note]
> [**加入**  >  **新專案**] 命令也會顯示表格中未列出的一般檔案類型， 而 [檔案  >  **新** 檔案] 則  >  是包含這些類型，而不是 [**一般**] 索引標籤。

| 檔案類型 | Description |
| --- | --- |
| R Script | 包含可在 R 命令列輸入之相同命令的文字檔。 |
| R Markdown | 包含 [R Markdown](rmarkdown-with-r-in-visual-studio.md) 文件的檔案。 |
| R 設定 | 保存 R 應用程式設定的檔案。 |
| R 文件 | 僅包含名稱、別名和標題欄位的一般 R 文件檔案。 |
| R 文件 (函式) | 包含許多欄位及描述函式之註解的 R 文件檔案。 |
| R 文件 (資料集) | 包含許多欄位及描述資料集之註解的 R 文件檔案。 |
| SQL 查詢 | 空的 *.sql* 檔。 請參閱[使用 SQL Server 和 R](integrating-sql-server-with-r.md)。 |
| 使用 R 的預存程序 | 具有子系 SQL 查詢和子系預存程序範本檔案的 R 檔案。 請參閱[使用 SQL Server 和 R](integrating-sql-server-with-r.md)。 |

## <a name="use-multiple-project-types-in-visual-studio"></a>使用 Visual Studio 中的多個專案類型

Visual Studio 解決方案提供一個方便的位置，讓您在同一個邏輯位置收集和管理相關的專案。 方案有利於組織程式碼，並加速小組合作。

在下例中，解決方案包含有以 R 建置模組的 R 專案及 Azure Machine Learning、Python/scikit-learn 專案、包含進行密集運算工作模組的 C++ 專案、管理資料的 SQL 專案，以及發行結果網站的 Python/Bottle 專案：

![顯示解決方案中多個相關專案的 Visual Studio 方案總管](media/projects-polyglot.png)

以粗體反白顯示的專案是解決方案的「啟動」專案。若要變更它，請以滑鼠右鍵按一下不同的專案，然後選取 [設定為啟始專案]。

> [!Note]
> 目前，C#/C++ 語言整合沒有任何就緒的明確 R (如為 Python，請參閱[建立適用於 Python 的 C++ 延伸模組](../python/working-with-c-cpp-python-in-visual-studio.md))。  不過有一些可用的文件庫為 R 提供 C# 和 C++ 橋接器。

如需一般管理專案和方案的詳細資訊，請參閱 [Visual Studio 中的方案和專案](../ide/solutions-and-projects-in-visual-studio.md)。
