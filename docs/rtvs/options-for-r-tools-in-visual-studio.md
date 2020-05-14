---
title: R 工具選項
description: Visual Studio 中 R 語言的選項和相關功能的參考。
ms.date: 12/04/2017
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: c7c2cb57dc96d7bb0df09248eb7a877820e50521
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302704"
---
# <a name="r-tools-for-visual-studio-options"></a>Visual Studio R 工具選項

通過**R 工具** > **選項**功能表或通過**工具** > **選項**和滾動到**R 工具**訪問設置：

  ![R 工具的 [選項] 對話方塊](media/options-dialog.png)

您可以使用下列方法存取 R 專用的選項及設定。 您必須選取位於 [選項]**** 對話方塊底部的 [顯示所有設定]**** 方塊，才能顯示這些區段。

- 程式碼格式設定選項 (請參閱[編輯器選項](editing-r-code-in-visual-studio.md#editor-options))：[工具]**** > [選項]**** 功能表，然後選取 [文字編輯器]**** > [R]**** > [格式設定]****
- Linter 選項 (請參閱 [Linter](linting-r-code.md))：[工具]**** > [選項]**** 功能表，然後選取 [文字編輯器]**** > [R]**** > [Lint]****
- 進階編輯器選項 ([於本文中描述](#text-editor--r--advanced-options))：[工具]**** > [選項]**** 功能表，然後選取 [文字編輯器]**** > [R]**** > [進階]****
- 行為選項 ([於本文中描述](#r-tools--advanced-options))：[R 工具]**** > [選項]**** 功能表，或 [工具]**** > [選項]****，然後捲動至 [R 工具]****。

**R Tools** > **資料科學設置命令**還影響 Visual Studio 中許多不同的設置。 下一節將描述此命令。

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>[R 工具] > [資料科學設定]

[R 工具] > [資料科學設定]**** 功能表項目可使用針對資料科學家需求最佳化的配置來設定 Visual Studio IDE。 具體而言，此選項會開啟[互動式](interactive-repl-for-r-in-visual-studio.md)、[變數總管](variable-explorer.md)和[工作區](r-workspaces-in-visual-studio.md)視窗：

![Visual Studio 中的資料科學家視窗版面配置](media/installation-data-scientist-layout-result.png)

要稍後還原到其他 Visual Studio 設置，請首先使用 **"工具** > **導入和匯出設置"** 命令，選擇 **"匯出選定的環境設置**"並指定檔案名。 若要還原這些設定，請使用相同的命令並選取 [匯入選取的環境設定]****。 如果您變更資料科學家版面配置，並稍後想要還原，而不是直接使用 [資料科學設定]**** 命令，則也可以使用相同的命令。

## <a name="text-editor--r--advanced-options"></a>[文字編輯器] > [R] > [進階選項]

這些選項可控制 R 格式設定、IntelliSense、大綱、縮排和語法檢查的行為。

![R 文字編輯器進階選項中的選項對話方塊](media/options-dialog-advanced-text-editor.png)

每個選項都可設為 [開啟] 或 [關閉] 來控制發生疑問時的行為。 如需每個選項造成之影響的詳細資料，請參閱對話方塊底部的說明窗格。 請注意，您可以拖曳該說明窗格的頂部來放大窗格。

![展開之 R 文字編輯器進階選項對話方塊的說明窗格](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>[R 工具] > [進階選項]

**"R 工具** > **選項"** 功能表命令將 **"選項"** 對話方塊打開到 R 選項：

  ![R 工具的 [選項] 對話方塊](media/options-dialog.png)

下列各節描述此頁面上可用的不同選項。

### <a name="debugging"></a>偵錯

這些選項控制[變數總管](variable-explorer.md)和偵錯工具視窗 (如監看式和區域變數) 中的值處理方式 (請參閱[對 R 程式碼進行偵錯](debugging-r-in-visual-studio.md))。

| 選項 | 預設值 | 描述 |
| --- | --- | --- |
| 評估使用中繫結 | `True` | 為 `True` 時，確保您在檢查變數和屬性時一律會看到最新值。 根據實作方式，風險是評估運算式可能會造成副作用。 |
| 顯示以點為前置字元的變數 | `False` | 指定是否顯示前面加上 `.` 的變數。 |

### <a name="grid-view"></a>格線檢視

| 選項 | 預設值 | 描述 |
| --- | --- | --- |
| 動態評估 | `False` | 根據預設，`View(<expression>)` 函式會擷取資料的快照集作為資料框架，而該資料框架會儲存大型資料集並消耗大量的記憶體。 將此選項設為 `True`，表示運算式會在格線更新並僅擷取要顯示的資料時進行評估。 然而，若運算式發生變更，則資料同時也會發生變更。此舉可能不適合 dplyr pip 運算式。 |

### <a name="help"></a>説明

| 選項 | 預設值 | 描述 |
| --- | --- | --- |
| F1 網頁瀏覽器 | `Internal` | 控制使用**Ctrl**+**F1**搜索術語時説明的顯示方式。 設定為 `Internal` 時，說明是呈現在 Visual Studio 的工具視窗內。 設定為 `External` 時，說明會顯示在預設網頁瀏覽器中。 |
| F1 Web 搜尋字串 | `R site:stackoverflow.com` | 控制在編輯器中按**Ctrl**+**F1**上的字詞時，如何將搜索詞傳遞到搜尋引擎。 字串預設是 `R site:stackoverflow.com`，這是將 `R` 附加至搜尋詞彙。 `site:stackoverflow.com` 是搜尋引擎的指示詞，告知將搜尋範圍設為 `stackoverflow.com` 網域內的頁面。 |
| R 說明瀏覽器 | `Automatic` | 控制使用**F1** **、？** 或 **？** 搜索 R 文檔時顯示説明的方式。 設定為 `Automatic` 時，說明會呈現在適當的視窗中。 例如，HTML 說明出現在 Visual Studio 工具視窗內，而 PDF 出現在預設 PDF 程式中。 設定為 `External` 時，說明會呈現在預設網頁瀏覽器中。 |

### <a name="history"></a>記錄

| 選項 | 預設值 | 描述 |
| --- | --- | --- |
| 一律儲存歷程記錄 | `True` | 控制只要關閉專案，RTVS 是否就會將命令歷程記錄寫入工作目錄中的 *.RHistory* 檔案。 即使您在結束前未儲存專案，還是會儲存歷程記錄。 |
| 重設搜尋篩選 | `True` | 判斷 [歷程記錄] 視窗是否可以篩選命令歷程記錄，只顯示子字串與 [R 歷程記錄] 對話方塊中篩選詞彙相符的命令。 此設定可決定是否只要執行新命令就重設歷程記錄搜尋篩選，或切換至新專案，這樣會觸發載入不同的 *.RHistory* 檔案。 如果您使用篩選集來執行命令，並且納悶剛剛執行的命令為什麼未顯示在 [歷程記錄] 中，則預設設定 `True` 可將驚喜降至最低。 |
| 使用多行選取範圍 | `True` | 指定是否可以只按一下就在 [歷程記錄] 中選取多行陳述式。 也會透過陳述式而非行來啟用互動式視窗中的向上/向下箭號巡覽。 |

### <a name="html"></a>HTML

| 選項 | 預設值 | 描述 |
| --- | --- | --- |
| HTML 網頁瀏覽器 | `External` | 判斷是否呈現 `ggvis` 繪圖或 `shiny` 應用程式這類內容。 `Internal` 會在 Visual Studio 的工具視窗內顯示 HTML 輸出；`External` 會在預設瀏覽器中顯示 HTML 輸出。 |

### <a name="logging"></a>記錄

| 選項 | 預設值 | 描述 |
| --- | --- | --- |
| 記錄事件 | `Normal` | 控制用於 RTVS 診斷的記錄詳細程度。 預設設定 `Normal` 會在 `TEMP` 目錄中建立記錄檔。 設定為 `Traffic` 時，RTVS 會記錄所有命令以及工作階段中的回應。 這些記錄檔絕不會離開您的電腦，但可能有助於診斷 RTVS 中的問題。 |

### <a name="markdown"></a>Markdown

| 選項 | 預設值 | 描述 |
| --- | --- | --- |
| Markdown 預覽瀏覽器 | `External` | 判斷顯示 RMarkdown HTML 輸出的位置。 `Internal` 會在 Visual Studio 的工具視窗內顯示 RMarkdown HTML 文件；`External` 會使用預設瀏覽器顯示 RMarkdown HTML。 |

### <a name="r-engine"></a>R 引擎

| 選項 | 預設值 | 描述 |
| --- | --- | --- |
| 字碼頁 | `(OS Default)` | 設定 R 的字碼頁 (地區設定)。預設會使用作業系統的基礎地區設定。 |
| CRAN 鏡像 | `(Use .Rprofile)` | 設定預設 CRAN 鏡像來進行套件安裝。 預設設定 `Use .Rprofile` 使用 *.RProfile* 檔案中的 CRAN 鏡像設定。 |

### <a name="workspace"></a>工作區

| 選項 | 預設值 | 描述 |
| --- | --- | --- |
| 在專案開啟時載入工作區 | `No` | 設定為 `Yes` 會在開啟專案時，將工作階段資料從 *.RData* 檔案載入至全域環境。 |
| 在重設時提示儲存工作區 | `Yes` | 設定為 `No` 會在您按一下 [互動式視窗] 中的 [重設] 按鈕時停用提示儲存工作區。 |
| 在專案關閉時儲存工作區 | `No` | 設定為 `Yes` 會在關閉專案時，將全域環境儲存至 *.RData* 檔案。 |
| 在切換工作區前顯示確認對話方塊 | `Yes` | 設定為 `No` 會在切換不同的工作區時停止提示使用者進行確認。 請參閱[切換工作區](r-workspaces-in-visual-studio.md#switch-between-workspaces) |
| 顯示機器負載指示器 | `False` | 控制狀態列中 CPU/記憶體/網路負載指示器的可見度。 由於指示器會產生網路流量，在遠端計量的案例中，將其設為 `False` 可能會有所幫助。 變更此選項需要重新啟動 Visual Studio。 |
