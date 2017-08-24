---
title: "Visual Studio 中的 R 工具選項 | Microsoft Docs"
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
f1_keywords:
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
ms.topic: article
ms.assetid: 554dc602-ecad-4cd0-8e6f-a60bb8a2328f
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 8a544bd1e1242bb6fabe00f7842ac33ed9d9d444
ms.openlocfilehash: a2f0421ff622483fb53795dac527bb8db3c689e2
ms.contentlocale: zh-tw
ms.lasthandoff: 08/14/2017

---

# <a name="r-tools-for-visual-studio-options"></a>Visual Studio R 工具選項
 
設定的存取方式是透過 [R 工具] > [選項] 功能表，或透過 [工具] > [選項] 並捲動到 [R 工具]：
 
  ![R 工具的 [選項] 對話方塊](media/options-dialog.png)

下列各節描述此頁面上可用的不同選項。

> [!Note]
> 透過一般 [工具] > [選項] 功能表存取選項時，您可能需要選取底部的 [顯示所有設定] 方塊，[R 工具] 頁面才會顯示。

<a name="data-scientist-layout"</a>

[R 工具] > [資料科學設定] 功能表項目也可使用針對資料科學家需求最佳化的配置來設定 Visual Studio IDE。 具體而言，此選項會開啟[互動式](interactive-repl.md)、[變數總管](variable-explorer.md)和[工作區](workspaces.md)視窗：

![Visual Studio 中的資料科學家視窗版面配置](media/installation-data-scientist-layout-result.png)

> [!Important]      
> 若要在稍後還原其他 Visual Studio 設定，請先使用 [工具] > [匯入和匯出設定] 命令，並選取 [匯出選取的環境設定]，然後指定檔案名稱。 若要還原這些設定，請使用相同的命令，並選取 [匯入選取的環境設定]。 如果您變更資料科學家版面配置，並稍後想要還原，而不是直接使用 [資料科學設定] 命令，則也可以使用相同的命令。

## <a name="debugging"></a>偵錯

這些選項控制[變數總管](variable-explorer.md)和偵錯工具視窗 (如監看式和區域變數) 中的值處理方式 (請參閱[偵錯](debugging.md))。

| 選項 | 預設值 | 說明 | 
| --- | --- | --- |
| 評估使用中繫結 | `True` | 為 `True` 時，確保您在檢查變數和屬性時一律會看到最新值。 根據實作方式，風險是評估運算式可能會造成副作用。 |
| 顯示以點為前置字元的變數 | `False` | 指定是否顯示前面加上 `.` 的變數。 |

## <a name="general"></a>一般

| 選項 | 預設值 | 說明 | 
| --- | --- | --- |
| 調查/新聞檢查 | `Once a week` | 指定 R 工具應檢查伺服器上是否有新聞和調查更新的頻率。 | 

## <a name="help"></a>說明

| 選項 | 預設值 | 說明 | 
| --- | --- | --- |
| F1 網頁瀏覽器 | `Internal` | 控制使用 Ctrl+F1 搜尋詞彙時的說明顯示方式。 設定為 `Internal` 時，說明是呈現在 Visual Studio 的工具視窗內。 設定為 `External` 時，說明會顯示在預設網頁瀏覽器中。 | 
| F1 Web 搜尋字串 | `R site:stackoverflow.com` | 控制在編輯器中對詞彙按 Ctrl+F1 時，如何將搜尋詞彙傳遞至搜尋引擎。 字串預設是 `R site:stackoverflow.com`，這是將 `R` 附加至搜尋詞彙。 `site:stackoverflow.com` 是搜尋引擎的指示詞，告知將搜尋範圍設為 `stackoverflow.com` 網域內的頁面。 | 
| R 說明瀏覽器 | `Automatic` | 控制使用 F1、`?` 或 `??` 搜尋 R 文件時的說明顯示方式。 設定為 `Automatic` 時，說明會呈現在適當的視窗中。 例如，HTML 說明出現在 Visual Studio 工具視窗內，而 PDF 出現在預設 PDF 程式中。 設定為 `External` 時，說明會呈現在預設網頁瀏覽器中。 |

## <a name="history"></a>歷程

| 選項 | 預設值 | 說明 | 
| --- | --- | --- |
| 一律儲存歷程記錄 | `True` | 控制只要關閉專案，RTVS 是否就會將命令歷程記錄寫入工作目錄中的 `.RHistory` 檔案。 即使您在結束前未儲存專案，還是會儲存歷程記錄。 |
| 重設搜尋篩選 | `True` | 判斷 [歷程記錄] 視窗是否可以篩選命令歷程記錄，只顯示子字串與 [R 歷程記錄] 對話方塊中篩選詞彙相符的命令。 此設定可決定是否只要執行新命令就重設歷程記錄搜尋篩選，或切換至新專案，這樣會觸發載入不同的 `.RHistory` 檔案。 如果您使用篩選集來執行命令，並且納悶剛剛執行的命令為什麼未顯示在 [歷程記錄] 中，則預設設定 `True` 可將驚喜降至最低。 |
| 使用多行選取範圍 | `True` | 指定是否可以只按一下就在 [歷程記錄] 中選取多行陳述式。 也會透過陳述式而非行來啟用互動式視窗中的向上/向下箭號巡覽。 |

## <a name="html"></a>HTML

| 選項 | 預設值 | 說明 | 
| --- | --- | --- |
| HTML 網頁瀏覽器 | `External` | 判斷是否呈現 `ggvis` 繪圖或 `shiny` 應用程式這類內容。 `Internal` 會在 Visual Studio 的工具視窗內顯示 HTML 輸出；`External` 會在預設瀏覽器中顯示 HTML 輸出。 | 

## <a name="logging"></a>記錄

| 選項 | 預設值 | 說明 | 
| --- | --- | --- |
| 記錄事件 | `Normal` | 控制用於 RTVS 診斷的記錄詳細程度。 預設設定 `Normal` 會在 `TEMP` 目錄中建立記錄檔。 設定為 `Traffic` 時，RTVS 會記錄所有命令以及工作階段中的回應。 這些記錄檔絕不會離開您的電腦，但可能有助於診斷 RTVS 中的問題。 |

## <a name="markdown"></a>Markdown

| 選項 | 預設值 | 說明 | 
| --- | --- | --- |
| Markdown 預覽瀏覽器 | `External` | 判斷顯示 RMarkdown HTML 輸出的位置。 `Internal` 會在 Visual Studio 的工具視窗內顯示 RMarkdown HTML 文件；`External` 會使用預設瀏覽器顯示 RMarkdown HTML。 | 

## <a name="r-engine"></a>R 引擎

| 選項 | 預設值 | 說明 | 
| --- | --- | --- |
| 字碼頁 | `(OS Default)` | 設定 R 的字碼頁 (地區設定)。預設會使用作業系統的基礎地區設定。 | 
| CRAN 鏡像 | `(Use .Rprofile)` | 設定預設 CRAN 鏡像來進行套件安裝。 預設設定 `Use .Rprofile` 使用 `.RProfile` 檔案中的 CRAN 鏡像設定。 |
| 工作目錄 | 使用者特定資料夾 | Sets 是目前的工作目錄，一般只要開啟專案就會予以設定。 |

## <a name="workspace"></a>工作區

| 選項 | 預設值 | 說明 | 
| --- | --- | --- |
| 在專案開啟時載入工作區 | `No` | 設定為 `Yes` 會在開啟專案時，將工作階段資料從 `.RData` 檔案載入至全域環境。 |
| 在重設時提示儲存工作區 | `Yes` | 設定為 `No` 會在您按一下 [互動式視窗] 中的 [重設] 按鈕時停用提示儲存工作區。 |
| 在專案關閉時儲存工作區 | `No` | 設定為 `Yes` 會在關閉專案時，將全域環境儲存至 `.RData` 檔案。 |
| 在切換工作區前顯示確認對話方塊 | `Yes` | 設定為 `No` 會在切換不同的工作區時停止提示使用者進行確認。 請參閱[切換工作區](workspaces.md#switching-between-workspaces)。 |
 

