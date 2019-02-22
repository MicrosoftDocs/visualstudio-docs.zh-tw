---
title: 適用於 Python 的選項和設定
description: Visual Studio 中與 Python 程式碼和專案相關的各種設定參考。
ms.date: 02/11/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Diagnostics
- VS.ToolsOptionsPages.Python_Tools.Experimental
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 3589447cdc9451a52dcffb4653a31f188b33c634
ms.sourcegitcommit: 61dc40d6c707f8c79779ec1091b296530d5a7b81
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987388"
---
# <a name="options-for-python-in-visual-studio"></a>Visual Studio 中 Python 的選項

若要檢視 Python 選項，請使用 [工具] > [選項] 功能表命令，並確定選取 [顯示所有設定]，然後瀏覽 至 [Python 工具]：

![Python 選項對話方塊、一般索引標籤](media/options-general.png)

在 [文字編輯器] > [Python] > [進階] 索引標籤上以及 [文字編輯器] 群組內的 [環境] > [字型和色彩] 索引標籤上，也有其他 Python 特定選項。

> [!Note]
> **實驗**群組包含仍在開發中功能的選項，因此不在此處記錄。 它們通常見於 [Microsoft 部落格 Python 工程](https://blogs.msdn.microsoft.com/pythonengineering/)的討論文章中。

## <a name="general-options"></a>一般選項

([工具] > [選項] > [Python] 索引標籤。)

| 選項 | 預設 | 描述 |
| --- | --- | --- |
| **建立虛擬環境時顯示輸出視窗**| 開啟 | 清除即可防止 [輸出] 視窗出現。 |
| **安裝或移除套件時顯示輸出視窗** | 開啟 | 清除即可防止 [輸出] 視窗出現。 |
| **一律以系統管理員身分執行 pip** | Off | 一律提高所有環境的 `pip install` 作業。 安裝套件時，如果環境位在檔案系統的受保護區域 (例如 *c:\Program Files*)，則 Visual Studio 會提示需要系統管理員權限。 在該提示中，您可以選擇一律只提高該環境的 `pip install`。 請參閱[套件索引標籤](python-environments-window-tab-reference.md#packages-tab)。 |
| **第一次使用時自動產生完成 DB** | 開啟 | 適用於 Visual Studio 2017 15.5 版及較舊版本，也適用於使用 IntelliSense 資料庫的較新版本。 當您撰寫使用程式庫的程式碼時，系統會優先完成該程式庫的資料庫。 如需詳細資訊，請參閱 [IntelliSense 索引標籤](python-environments-window-tab-reference.md#intellisense-tab)。 |
| **略過全系統的 PYTHONPATH 變數** | 開啟 | 因為 Visual Studio 提供更多直接方法來指定環境和專案中的搜尋路徑，所以預設會略過 PYTHONPATH。 如需詳細資訊，請參閱[搜尋路徑](search-paths.md)。 |
| **新增連結的檔案時更新搜尋路徑** | 開啟 | 設定時，將[連結的檔案](managing-python-projects-in-visual-studio.md#linked-files)新增至專案更新[搜尋路徑](search-paths.md)，讓 IntelliSense 可以將所連結檔案資料夾的內容包含在完成資料庫中。 清除此選項，可從完成資料庫排除這類內容。 |
| **找不到匯入的模組時發出警告** | 開啟 | 清除此選項，可在您知道匯入的模組目前不可用但不會影響程式碼作業時隱藏警告。 |
| **回報不一致的縮排為** | **警告** | 因為 Python 解譯器大量取決於正確的縮排來判斷範圍，所以 Visual Studio 預設會在偵測到可能指出程式碼錯誤的不一致縮排時發出警告。 設定為 Errors 甚至更為嚴格，在這類情況下會結束程式。 若要完全停用此行為，請選取 [不]。 |
| **查看是否有問卷/新聞** | **一週一次** | 設定您允許 Visual Studio 開啟所含網頁具有 Python 相關問卷和新聞項目 (如果有的話) 之視窗的頻率。 選項為 [永不]、[一天一次]、[一週一次] 和 [一個月一次]。 |
| **重設所有永久隱藏的對話方塊**按鈕 | N/A | 不同的對話方塊會提供 [不要再顯示] 這類選項。 使用此按鈕，可清除這些選項，並重新顯示對話方塊。 |

![Python 選項對話方塊、一般索引標籤](media/options-general.png)

## <a name="debugging-options"></a>偵錯選項

([工具] > [選項] > [Python] > [偵錯] 索引標籤。)

| 選項 | 預設 | 描述 |
| --- | --- | --- |
| **發生錯誤時於執行前提示** | 開啟 | 設定時，系統會提示您確認您想要執行包含錯誤的程式碼。 清除此選項，可停用警告。 |
| **處理序異常結束時等候輸入**<br/><br/>**處理序正常結束時等候輸入** | 開啟 (針對兩者) | 從 Visual Studio 啟動的 Python 程式會執行它自己的主控台視窗中。 視窗預設會在關閉之前等待您按任一鍵，不論程式的結束方式為何。 若要移除該提示，並自動關閉視窗，請清除其中任一或兩個選項。 |
| **將 Tee 程式輸出至偵錯輸出視窗** | 開啟 | 在不同的主控台視窗和 Visual Studio [輸出] 視窗中，顯示程式輸出。 清除此選項，只在不同的主控台視窗中顯示輸出。 |
| **發生 SystemExit 例外狀況時中斷，結束代碼為零** | Off | 如果設定，請停止此例外狀況的偵錯工具。 清除時，會結束偵錯工具，而不中斷。 |
| **啟用 Python 標準程式庫的偵錯** | Off | 可在偵錯時逐步執行標準程式庫原始程式碼，但會增加啟動偵錯工具所花費的時間。|

![Python 選項對話方塊、偵錯索引標籤](media/options-debugging.png)

## <a name="diagnostics-options"></a>診斷選項

([工具] > [選項] > [Python] > [診斷] 索引標籤。)

| 選項 | 預設 | 描述 |
| --- | --- | --- |
| **包括分析記錄檔** | 開啟 | 使用按鈕將診斷儲存到檔案，或將它們複製到剪貼簿時，包含與已安裝 Python 環境分析相關的詳細記錄檔。 此選項可能會大幅增加所產生檔案的大小，但通常是診斷 IntelliSense 問題時所需的項目。 |
| **將診斷儲存到檔案**按鈕 | N/A | 提示輸入檔案名稱，然後將記錄檔儲存到文字檔。 |
| **將診斷複製到剪貼簿**按鈕 | N/A | 將完整的記錄檔放到剪貼簿；這項作業可能需要一些時間，視記錄檔的大小而定。 |

![Python 選項對話方塊、診斷索引標籤](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>互動式視窗選項

([工具] > [選項] > [Python] > [互動式視窗] 索引標籤。)

| 選項 | 預設 | 描述 |
| --- | --- | --- |
| **指令碼** | N/A | 指定啟動指令碼的一般資料夾，以套用至所有環境的**互動式**視窗。 請參閱[啟動指令碼](python-environments-window-tab-reference.md#startup-scripts)。 不過，請注意，這項功能目前無法運作。 |
| **按向上鍵/向下鍵瀏覽歷程記錄** | 開啟 | 使用方向鍵，在**互動式**視窗中瀏覽歷程記錄。 清除此設定，可改為使用方向鍵在**互動式**視窗的輸出中進行瀏覽。 |
| **完成模式** | **只評估沒有函式呼叫的運算式** | 決定**互動式**視窗中運算式可用成員的程序，可能需要評估目前未完成的運算式，這樣可能會導致副作用或多次呼叫函式。 預設設定 [只評估沒有函式呼叫的運算式] 會排除呼叫函式的運算式，但會評估其他運算式。 例如，它會評估 `a.b`，但不會評估 `a().b`。  [一律不評估運算式] 可防止所有副作用，並建議僅使用標準 IntelliSense 引擎。 [評估所有運算式] 會評估整個運算式來取得建議，不論副作用為何。 |
| **隱藏靜態分析建議** | Off | 設定時，只會顯示評估運算式所取得的建議。 如果與 [完成模式] 值 [一律不評估運算式] 合併使用，則**互動式**視窗中不會出現任何有用的完成。 |

![Python 選項對話方塊、互動式視窗索引標籤](media/options-interactive-windows.png)

## <a name="advanced-python-editor-options"></a>進階 Python 編輯器選項

([工具] > [選項] > [文字編輯器] > [Python] > [進階] 索引標籤。)

### <a name="completion-results"></a>完成結果

| 選項 | 預設 | 描述 |
| --- | --- | --- |
| **成員完成會顯示成員的交集** | Off | 設定時，只會顯示所有可能類型所支援的完成。 |
| **根據搜尋字串篩選清單** | 開啟 | 在您鍵入時，套用完成建議的篩選 (預設為核取)。 |
| **自動顯示所有識別碼的完成** | 開啟 | 清除此選項，可停用編輯器和**互動式**視窗中的完成。 |

### <a name="selection-in-completion-list"></a>完成清單中的選取範圍

| 選項 | 預設 | 描述 |
| --- | --- | --- |
| **輸入下列字元予以認可** | **{}\[\]().,:;+-*/%&&#124;^~=<>#@\\** | 這些字元一般會接在可從完成清單中選取的識別碼後面，因此只要鍵入字元就可以輕易地認可完成。 您可以視需要在清單中移除或新增特定字元。  |
| **按 Enter 認可目前的完成** | 開啟 | 設定時，Enter 鍵會選擇並套用目前選取的完成，與上面字元相同 (但是，當然，沒有 Enter 的字元，因此無法直接進入該清單！)。 |
| **在完整輸入的字結尾處按 ENTER 時新增行** | Off | 根據預設，如果您鍵入完成快顯視窗中所顯示的整個單字，然後按 Enter，則會認可該完成。 設定此選項，即可在完成輸入識別碼時有效地認可完成，因此 Enter 會插入新行。 |

### <a name="miscellaneous-options"></a>其他選項

| 選項 | 預設 | 描述 |
| --- | --- | --- |
| **檔案開啟時進入大綱模式** | 開啟 | 開啟 Python 程式碼檔案時，會自動開啟編輯器中的 Visual Studio 大綱功能。 |
| **貼上已移除的 REPL 提示** | 開啟 | 從貼上的文字中移除 **>>>** 與 **...**，允許將程式碼從**互動式**視窗輕鬆傳送至編輯器。 如果您在從其他來源貼上時需要保留這些字元，請清除此選項。 |
| **根據類型為名稱上色** | 開啟 | 啟用 Python 程式碼中的語法著色。 |

![Python 編輯器選項對話方塊、進階索引標籤](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>字型與色彩選項

([文字編輯器] 群組內的 [環境] > [字型和色彩] 索引標籤。)

Python 選項名稱的前面都會加上 **Python**，而且您可以輕鬆透過名稱了解其功能。 所有 Visual Studio 色彩佈景主題都是 10pt Consolas regular (非粗體)。 預設色彩會因佈景主題而異。 一般而言，使用者會在無法順利閱讀預設設定的文字時，變更其字型或色彩。

![Python 字型和色彩選項](media/options-fonts-and-colors.png)
