---
title: 適用於 Python 的選項和設定
description: Visual Studio 中與 Python 程式碼和專案相關的各種設定參考。
ms.date: 03/13/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Diagnostics
- VS.ToolsOptionsPages.Python_Tools.Experimental
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 08501d71400a0df139022f04e68573d0dd1449d1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302746"
---
# <a name="options-for-python-in-visual-studio"></a>Visual Studio 中 Python 的選項

要查看 Python 選項，請使用 **"工具** > **選項"** 功能表命令，確保**顯示所有設置**已選中，然後導航到**Python**：

::: moniker range="vs-2017"
![Python 選項對話方塊、一般索引標籤](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python 選項對話方塊、一般索引標籤](media/options-general-2019.png)
::: moniker-end

**文字編輯器** > **Python** > **高級**選項卡和**文字編輯器****組中的環境** > **字體和顏色**選項卡上還有其他特定于 Python 的選項。

> [!Note]
> **實驗**群組包含仍在開發中功能的選項，因此不在此處記錄。 它們通常見於 [Microsoft 部落格 Python 工程](https://devblogs.microsoft.com/python/)的討論文章中。

## <a name="general-options"></a>一般選項

（**工具** > **選項** > **Python**選項卡。

| 選項 | 預設 | 描述 |
| --- | --- | --- |
| **建立虛擬環境時顯示輸出視窗**| 另一 | 清除以防止出現**輸出**視窗。 |
| **安裝或移除套件時顯示輸出視窗** | 另一 | 清除以防止出現**輸出**視窗。 |
| **顯示建立環境的通知列** | 另一 | *僅限 Visual Studio 2019。* 當設定這個選項且使用者開啟包含 *requirements.txt* 或 *environment.yml* 檔案的專案時，Visual Studio 會顯示資訊列，其中包含個別建立虛擬環境或 conda 環境，而不是使用預設全域環境的建議。 |
| **顯示安裝套件的通知列** | 另一 | *僅限 Visual Studio 2019。* 當設定這個選項且使用者開啟包含 *requirements.txt* 檔案的專案 (且沒有使用預設全域環境) 時，Visual Studio 會比較那些需求與目前環境中已安裝的套件。 如果遺失任何套件，Visual Studio 會顯示安裝那些相依項目的提示。 |
| **一律以系統管理員身分執行套件管理員** | 關閉 | 一律提高所有環境的 `pip install` 和類似套件管理員作業的權限。 安裝套件時，如果環境位在檔案系統的受保護區域 (例如 *c:\Program Files*)，則 Visual Studio 會提示需要系統管理員權限。 您可以在該提示中選擇一律只針對該環境提高安裝命令的權限。 請參閱["包"選項卡](python-environments-window-tab-reference.md#packages-tab)。 |
| **第一次使用時自動產生完成 DB** | 另一 | 適用於 Visual Studio 2017 15.5 版及較舊版本，也適用於使用 IntelliSense 資料庫的較新版本。** 當您撰寫使用程式庫的程式碼時，系統會優先完成該程式庫的資料庫。 如需詳細資訊，請參閱 [IntelliSense 索引標籤](python-environments-window-tab-reference.md?view=vs-2017#intellisense-tab)。 |
| **略過全系統的 PYTHONPATH 變數** | 另一 | 因為 Visual Studio 提供更多直接方法來指定環境和專案中的搜尋路徑，所以預設會略過 PYTHONPATH。 如需詳細資訊，請參閱[搜尋路徑](search-paths.md)。 |
| **新增連結的檔案時更新搜尋路徑** | 另一 | 設置後，將[連結檔](managing-python-projects-in-visual-studio.md#linked-files)添加到專案會更新[搜索路徑](search-paths.md)，以便 IntelliSense 可以在其完成資料庫中包含連結檔資料夾的內容。 清除此選項，可從完成資料庫排除這類內容。 |
| **找不到匯入的模組時發出警告** | 另一 | 清除此選項，可在您知道匯入的模組目前不可用但不會影響程式碼作業時隱藏警告。 |
| **回報不一致的縮排為** | **警告** | 因為 Python 解譯器大量取決於正確的縮排來判斷範圍，所以 Visual Studio 預設會在偵測到可能指出程式碼錯誤的不一致縮排時發出警告。 設定為 Errors**** 甚至更為嚴格，在這類情況下會結束程式。 若要完全停用此行為，請選取 [不]****。 |
| **查看是否有問卷/新聞** | **一週一次** | *視覺工作室 2017 及更早版本。* 設定您允許 Visual Studio 開啟所含網頁具有 Python 相關問卷和新聞項目 (如果有的話) 之視窗的頻率。 選項為 [永不]****、[一天一次]****、[一週一次]**** 和 [一個月一次]****。 |
| **重置所有永久隱藏的對話方塊**按鈕 | n/a | 不同的對話方塊會提供 [不要再顯示]**** 這類選項。 使用此按鈕，可清除這些選項，並重新顯示對話方塊。 |

::: moniker range="vs-2017"
![Python 選項對話方塊、一般索引標籤](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python 選項對話方塊、一般索引標籤](media/options-general-2019.png)
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="conda-options"></a>Conda 選項

([工具]** [選項]** > ** [Python]** > ** [Conda]** > **** 索引標籤。)

| 選項 | 預設 | 描述 |
| --- | --- | --- |
| **Conda 可執行檔路徑** | (空白) | 請指定 *conda.exe* 可執行檔的確切路徑，而不要依賴 Python 工資負載隨附的預設 Miniconda 安裝。 如果在這裡指定另一個路徑，其優先順序會高於預設安裝和登錄中指定的任何其他 conda.exe 可執行檔。 如果手動安裝較新版本的 Anaconda 或 Miniconda，或想要使用 32 位元發行版本，而不是預設的 64 位元發行版本，您可以變更此設定。 |

![Python 選項對話方塊、語言伺服器索引標籤](media/options-conda.png)

::: moniker-end

## <a name="debugging-options"></a>偵錯選項

（**工具** > **選項** > **Python** > **調試**選項卡。

| 選項 | 預設 | 描述 |
| --- | --- | --- |
| **發生錯誤時於執行前提示** | 另一 | 設定時，系統會提示您確認您想要執行包含錯誤的程式碼。 清除此選項，可停用警告。 |
| **處理序異常結束時等候輸入**<br/><br/>**處理序正常結束時等候輸入** | 開啟 (針對兩者) | 從 Visual Studio 啟動的 Python 程式會執行它自己的主控台視窗中。 視窗預設會在關閉之前等待您按任一鍵，不論程式的結束方式為何。 若要移除該提示，並自動關閉視窗，請清除其中任一或兩個選項。 |
| **將 Tee 程式輸出至偵錯輸出視窗** | 另一 | 在單獨的主控台視窗和視覺化工作室輸出視窗中顯示程式**輸出**。 清除此選項，只在不同的主控台視窗中顯示輸出。 |
| **發生 SystemExit 例外狀況時中斷，結束代碼為零** | 關閉 | 如果設定，請停止此例外狀況的偵錯工具。 清除時，會結束偵錯工具，而不中斷。 |
| **啟用 Python 標準程式庫的偵錯** | 關閉 | 可在偵錯時逐步執行標準程式庫原始程式碼，但會增加啟動偵錯工具所花費的時間。|
| **顯示函數傳回值** | 另一 | *僅限 Visual Studio 2019。* 在偵錯工具 (F10) 中逐步執行函式呼叫時，[區域]**** 視窗中會顯示函數傳回值 |
| **使用舊版偵錯工具** | 關閉 | *僅限 Visual Studio 2019。* 會指示 Visual Studio 預設使用舊版偵錯工具。 如需詳細資訊，請參閱 [偵錯 - 使用舊版偵錯工具](debugging-python-in-visual-studio.md#use-the-legacy-debugger)。 |

::: moniker range="vs-2017"
![Python 選項對話方塊、偵錯索引標籤](media/options-debugging.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python 選項對話方塊、偵錯索引標籤](media/options-debugging-2019.png)
::: moniker-end

## <a name="diagnostics-options"></a>診斷選項

（**工具** > **選項** > **Python** > **診斷**選項卡。

| 選項 | 預設 | 描述 |
| --- | --- | --- |
| **包括分析記錄檔** | 另一 | 使用按鈕將診斷儲存到檔案，或將它們複製到剪貼簿時，包含與已安裝 Python 環境分析相關的詳細記錄檔。 此選項可能會大幅增加所產生檔案的大小，但通常是診斷 IntelliSense 問題時所需的項目。 |
| **將診斷保存到檔**按鈕 | n/a | 提示輸入檔案名稱，然後將記錄檔儲存到文字檔。 |
| **將診斷複製到剪貼簿**按鈕 | n/a | 將完整的記錄檔放到剪貼簿；這項作業可能需要一些時間，視記錄檔的大小而定。 |

![Python 選項對話方塊、診斷索引標籤](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>互動式視窗選項

（**工具** > **選項** > **Python** > **互動式視窗**選項卡。

| 選項 | 預設 | 描述 |
| --- | --- | --- |
| **腳本** | n/a | 指定用於啟動腳本的通用資料夾，以便應用於所有環境的**互動式**視窗。 請參閱[啟動腳本](python-environments-window-tab-reference.md#startup-scripts)。 不過，請注意，這項功能目前無法運作。 |
| **按向上鍵/向下鍵巡覽歷程記錄** | 另一 | 使用方向鍵在 **"互動式"** 視窗中瀏覽歷程記錄。 清除此設置以使用方向鍵在**互動式**視窗的輸出中導航。 |
| **完成模式** | **只評估沒有函式呼叫的運算式** | 確定**互動式**視窗中運算式上的可用成員的過程可能需要評估當前未完成的運算式，這可能導致多次調用副作用或函數。 預設設定 [只評估沒有函式呼叫的運算式]**** 會排除呼叫函式的運算式，但會評估其他運算式。 例如，它會評估 `a.b`，但不會評估 `a().b`。  [一律不評估運算式]**** 可防止所有副作用，並建議僅使用標準 IntelliSense 引擎。 [評估所有運算式]**** 會評估整個運算式來取得建議，不論副作用為何。 |
| **隱藏靜態分析建議** | 關閉 | 設定時，只會顯示評估運算式所取得的建議。 如果與 [完成模式]**** 值 [一律不評估運算式]**** 合併使用，則**互動式**視窗中不會出現任何有用的完成。 |

![Python 選項對話方塊、互動式視窗索引標籤](media/options-interactive-windows.png)

::: moniker range=">=vs-2019"
## <a name="language-server-options"></a>語言伺服器選項

([工具]** [選項]** > ** [Python]** > ** [語言伺服器]** > **** 索引標籤。)

| 選項 | 預設 | 描述 |
| --- | --- | --- |
| **停用從 Typeshed 自動完成** | 關閉 | Visual Studio IntelliSense 通常會使用 Typeshed 的配套版本 (一組 *.pyi * 檔案) ，以尋找 Python 2 和 Python 3 的標準程式庫和協力廠商程式庫類型提示。 設定此選項會停用配套的 TypeShed 行為。 |
| **自訂 Typeshed 路徑** | (空白) | 如果設定，Visual Studio 會使用此路徑的 Typeshed 檔案，而不是其配套版本。 如果設定了**停用從 Typeshed 自動完成**，則會忽略。 |

![Python 選項對話方塊、語言伺服器索引標籤](media/options-language-server.png)

::: moniker-end

## <a name="advanced-python-editor-options"></a>進階 Python 編輯器選項

（**工具** > **選項** > **文字編輯器** > **Python** > **高級**選項卡。

### <a name="completion-results"></a>完成結果

| 選項 | 預設 | 描述 |
| --- | --- | --- |
| **成員完成會顯示成員的交集** | 關閉 | 設定時，只會顯示所有可能類型所支援的完成。 |
| **根據搜尋字串篩選清單** | 另一 | 在您鍵入時，套用完成建議的篩選 (預設為核取)。 |
| **自動顯示所有識別碼的完成** | 另一 | 清除此選項可禁用編輯器和**互動式**視窗中的完成。 |

### <a name="selection-in-completion-list"></a>完成清單中的選取範圍

| 選項 | 預設 | 描述 |
| --- | --- | --- |
| **輸入下列字元予以認可** | **{}\[\]（）：：;*-/%&&#124;=<>#@\\** | 這些字元一般會接在可從完成清單中選取的識別碼後面，因此只要鍵入字元就可以輕易地認可完成。 您可以視需要在清單中移除或新增特定字元。  |
| **按 Enter 認可目前的完成** | 另一 | 設置後 **，"Enter"** 鍵選擇並應用當前選定的完成，與上面的字元一樣（當然 **，Enter**沒有字元，因此它不能直接進入該清單！ |
| **在完整鍵入字的結尾處按 Enter 來新增新行** | 關閉 | 預設情況下，如果鍵入"完成"快顯視窗中顯示的整個單詞，然後按**Enter**，則提交該完成。 通過設置此選項，在鍵入識別碼後有效地提交完成，以便**Enter**插入新行。 |

### <a name="miscellaneous-options"></a>其他選項

| 選項 | 預設 | 描述 |
| --- | --- | --- |
| **檔案開啟時進入大綱模式** | 另一 | 開啟 Python 程式碼檔案時，會自動開啟編輯器中的 Visual Studio 大綱功能。 |
| **貼上已移除的 REPL 提示** | 另一 | 從**>>>** 粘貼的文本中刪除和 **...** ，允許輕鬆地將代碼從**互動式**視窗傳輸到編輯器。 如果您在從其他來源貼上時需要保留這些字元，請清除此選項。 |
| **根據類型為名稱上色** | 另一 | 啟用 Python 程式碼中的語法著色。 |

![Python 編輯器選項對話方塊、進階索引標籤](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>字型與色彩選項

（**文本** > **編輯器**組中的環境**字體和顏色**選項卡。

Python 選項的名稱都預綴在**Python**中，並且不言自明。 所有 Visual Studio 色彩佈景主題都是 10pt Consolas regular (非粗體)。 預設色彩會因佈景主題而異。 一般而言，使用者會在無法順利閱讀預設設定的文字時，變更其字型或色彩。

![Python 字型和色彩選項](media/options-fonts-and-colors.png)
