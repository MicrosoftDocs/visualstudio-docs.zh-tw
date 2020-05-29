---
title: 生產力指南
ms.date: 4/29/2020
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33eb146ce36bfa36dbe28fdcec0f7dfb85daa59b
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184077"
---
# <a name="productivity-guide-for-visual-studio"></a>Visual Studio 的生產力指南

如果您想要在撰寫程式碼時節省時間，您就是在正確的位置。 此生產力指南包含的秘訣可協助您開始使用 Visual Studio、撰寫程式碼、偵錯工具代碼、處理錯誤，以及 &mdash; 在單一頁面上使用鍵盤快速鍵。

如需好用鍵盤快速鍵的詳細資訊，請參閱[生產力快速鍵](../ide/productivity-shortcuts.md)。 如需命令捷徑的完整清單，請參閱[預設鍵盤快速鍵](../ide/default-keyboard-shortcuts-in-visual-studio.md)。

## <a name="get-started"></a>開始使用

藉由快速搜尋您需要的任何專案，包括命令、設定、檔和安裝選項，來節省時間深入探討。 請參閱 Visual Studio 搜尋結果中的命令鍵盤快速鍵，讓您可以更輕鬆地記住它們。 

- **使用工作清單**模擬程式碼。 如果您沒有足夠的需求來完成一段程式碼，請使用工作清單來追蹤使用標記（例如 `TODO` 和 `HACK` ）或自訂標記的程式碼批註，以及管理引導您直接移至程式碼中預先定義位置的快捷方式。 如需詳細資訊，請參閱[使用工作清單](../ide/using-the-task-list.md.)。

- **使用方案總管快捷方式**。 如果您不熟悉 Visual Studio，這些快捷方式將會很有説明，而且當您加速新程式碼基底時，可以節省您的時間。 如需快捷方式的完整清單，請參閱[Visual Studio 中的預設鍵盤快速鍵](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)。

- **[在 Visual Studio 中識別及自訂鍵盤快速鍵](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)**。 您可以識別 Visual Studio 命令的鍵盤快速鍵、自訂這些捷徑，以及將它們匯出以供其他人使用。 您隨時可以在 [選項] 對話方塊中尋找並變更鍵盤快速鍵。

- **讓 Visual Studio 更容易存取**。 Visual Studio 有與螢幕助讀程式和其他輔助技術相容的內建協助工具功能。 如需可用功能的完整清單，請參閱[Visual Studio 的協助工具秘訣和訣竅](../ide/reference/accessibility-tips-and-tricks.md)。 

- **查看 Visual Studio 產品生命週期和服務**。 如需如何取得 Visual Studio 的更新、企業和專業客戶的支援選項、舊版 Visual Studio 的支援，以及 Visual Studio 服務未涵蓋之元件的相關資訊，請參閱[Visual Studio 產品生命週期和服務](https://docs.microsoft.com/visualstudio/releases/2019/servicing)。 

- **在 Visual Studio 中安裝和管理 NuGet 套件**。 Visual Studio 中的 NuGet 套件管理員 UI 可讓您在專案和解決方案中，輕鬆地安裝、解除安裝和更新 NuGet 套件。 如需詳細資訊，請參閱[使用 NuGet 套件管理員在 Visual Studio 中安裝和管理套件](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio)。

## <a name="write-code"></a>撰寫程式碼

您可以使用下列功能，更快速地撰寫程式碼。

- **使用便捷命令**。 Visual Studio 包含各種可協助您更快速完成常用編輯工作的命令。 例如，您可以選擇一個命令來輕鬆複製一行程式碼，而不必先複製程式碼、調整游標位置，然後再將它貼上。 選擇 [**編輯**  >  **重複**] 或按**Ctrl** + **E**、**V**。 您也可以選擇 [**編輯**] [擴充] [  >  **Advanced**  >  **展開選取**] 或 [**編輯**] [  >  **高級**  >  **合約選取**]，或按**shift** + **alt** + **=** 或**shift** + **alt** + **-** ，以快速展開或收縮選取的文字。

- **使用 IntelliSense**。 當您在編輯器中輸入程式碼時，將會顯示 IntelliSense 資訊，例如列出成員、參數資訊、快速諮詢、簽章說明和自動完成文字。 這些功能支援文字的模糊比對;例如，清單成員的結果清單不僅包含以您所輸入的字元開頭的專案，還包括名稱中包含字元組合的專案。 如需詳細資訊，請參閱[使用 IntelliSense](../ide/using-intellisense.md)。

- **在您輸入程式碼時變更 IntelliSense 選項的自動插入**。 藉由切換 IntelliSense 至建議模式，您可以規定只有在明確選擇 IntelliSense 選項時，才可以將該選項插入。

     若要啟用建議模式，請選擇**Ctrl** + **Alt** + **空格鍵**，或在功能表列上選擇 [**編輯**  >  ] [**IntelliSense**  >  **] [切換完成模式]**。

- **使用程式碼片段**。 您可以使用內建的程式碼片段或建立自己的程式碼片段。

     若要插入程式碼片段，請在功能表列上選擇 [**編輯**] [IntelliSense] [  >  **IntelliSense**  >  **插入程式碼片段**] 或 [範圍語句]，或開啟檔案中的快捷方式功能表 **，** 然後選擇 [**片段**  >  **插入代碼**段] 或 [**環繞** 如需詳細資訊，請參閱[程式碼片段](../ide/code-snippets.md)。

- **修正內嵌程式碼錯誤**。 快速動作可讓您輕鬆地重構、產生或用其他方式以單一動作修改程式碼。 您可以使用螺絲起子 ![ 螺絲刀圖示或燈泡燈泡 ](media/screwdriver-icon.png) ![ 圖示 ](media/light-bulb-icon.png) 圖示，或按**Alt** + **enter**或**Ctrl** + **.** 來套用這些動作。 。 如需詳細資訊，請參閱[快速動作](quick-actions.md)。

- **顯示和編輯程式碼項目的定義**。 您可以快速顯示和編輯定義程式碼項目 (例如成員、變數或區域) 的模組。

    若要在快顯視窗中開啟定義，請反白顯示元素，然後選擇**Alt** + **F12**鍵，或開啟專案的快捷方式功能表，然後選擇 [**查看定義**]。 若要在不同的程式碼視窗中開啟定義，請開啟項目的捷徑功能表，然後選擇 [移至定義]****。

- **使用範例應用程式**。 您可以從 [Microsoft Developer Network](https://code.msdn.microsoft.com/) 下載和安裝範例應用程式，來加速應用程式開發。 您也可以下載和探索該區域的範例套件，學習特定技術或程式設計概念。

- **使用格式化/新行變更括弧格式**。 使用 [**格式化**] 選項頁面，即可設定程式碼編輯器中的程式碼格式化選項，包括新行。 如需如何在 c # 中使用這項設定的詳細資訊，請參閱[選項對話方塊：文字編輯器 > c # > 程式碼樣式 > 格式](../ide/reference/options-text-editor-csharp-formatting.md)。 針對 c + +，請參閱[在 Visual Studio 中設定您的 c + + 程式碼偏好](https://docs.microsoft.com/cpp/ide/how-to-set-preferences)。 針對 Python，請參閱[格式化 Python 程式碼](../python/formatting-python-code.md)。

- **使用 Tab 鍵變更縮排**。 使用針對每個程式碼基底量身打造的自訂編輯器設定，針對在不同編輯器和 Ide 上處理相同專案的多個開發人員強制執行一致的編碼樣式。 請確定您的整個小組遵循相同的語言慣例、命名慣例和格式規則。 由於這些自訂設定是可移植的，而且與您的程式碼一起移動，您可以強制執行編碼樣式，甚至是在 Visual Studio 之外。 如需詳細資訊，請參閱[選項、文字編輯器、所有語言、](../ide/reference/options-text-editor-all-languages-tabs.md#tabs)索引標籤。

## <a name="navigate-within-your-code-and-the-ide"></a>在您的程式碼和 IDE 內流覽

您可以利用各種技巧，更快速地尋找和移動至程式碼中的某個位置。 您也可以根據您的喜好設定來變更 Visual Studio 視窗的版面配置。 

- **將數行程式碼加入書籤**。 您可以利用書籤來快速地巡覽至檔案中的特定幾行程式碼。

    若要設定書簽，請在功能表列上選擇 [**編輯**  >  **書簽**] [  >  **切換書簽**]。 您可以在 [書籤]**** 視窗中檢視方案的所有書籤。 如需詳細資訊，請參閱[在程式碼中設定書籤](../ide/setting-bookmarks-in-code.md)。

- **搜尋檔案中的符號定義**。 您可以在方案中搜尋並找出符號定義和檔名，不過搜尋結果並不會包含名稱空間或區域變數。

   若要存取這項功能，請在功能表列上選擇 [**編輯**] [  >  **流覽至**]。

- **瀏覽程式碼的整體結構**。 在方案總管**** 中，您可以搜尋和瀏覽專案中的類別及其類型和成員。 您也可以搜尋符號、檢閱方法的呼叫階層、尋找符號參考和執行其他工作。 如果您在方案總管**** 中選擇程式碼項目，則會在 [預覽]**** 索引標籤中開啟相關聯的檔案，而游標會移至檔案中的項目。 如需詳細資訊，請參閱[檢視程式碼的結構](../ide/viewing-the-structure-of-code.md)。

- **使用對應模式跳至檔案中的位置**。 對應模式會在捲軸上顯示程式碼的行數（以縮為單位）。 如需此顯示模式的詳細資訊，請參閱[如何：自訂捲軸](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md#map-mode)。

- **瞭解 Code Map 的程式碼結構**。 Code map 可協助您將程式碼中的相依性視覺化，並瞭解如何在不需讀取檔案和程式碼的情況下，加以配合。 如需詳細資訊，請參閱[使用 Code Map 來對應相依性](../modeling/map-dependencies-across-your-solutions.md) \(機器翻譯\)。

- **查看常用檔案與編輯/移至最近使用的**檔案。 使用 Visual Studio 中的 [移至] 命令來執行焦點的程式碼搜尋，以協助您快速尋找指定的專案。 如需詳細指示，請參閱[使用移至命令尋找程式碼](../ide/go-to.md)。

- **將[屬性視窗](../ide/reference/properties-window.md)移至右手邊**。 如果您要尋找較熟悉的視窗版面配置，可以按**F4**在 Visual Studio 中移動屬性視窗。

## <a name="find-items-faster"></a>更快速地尋找項目

除了篩選工具視窗的內容以顯示與您目前的工作有關的資訊以外，您可以在整個 IDE 中搜尋命令、檔案和選項。

- **篩選工具視窗的內容**。 您可以搜尋 [工具箱]****、[屬性]**** 視窗和方案總管**** 許多這類工具視窗的內容，但只會顯示名稱包含您所指定字元的項目。

- **只顯示您要處理的錯誤**。 如果您選擇 [錯誤清單]**** 工具列上的 [篩選]**** 按鈕，則可以減少 [錯誤清單]**** 視窗中出現的錯誤數目。 您可以選擇顯示只在目前編輯器開啟之檔案中的錯誤、只在目前檔案中的錯誤或只在目前專案中的錯誤。 您也可以在 [錯誤清單]**** 視窗中搜尋以找出特定錯誤。

- **尋找對話方塊、功能表命令、選項和其他**。 在搜尋方塊中，為您嘗試尋找的項目輸入關鍵字或片語。 例如，如果您輸入**新增專案**，則會出現下列選項︰

   ::: moniker range="vs-2017"

   ![「新增專案」在 [快速啟動] 中的結果](../ide/media/productivity_quicklaunch.png)

   [快速啟動]**** 會顯示建立新專案、將新項目新增至專案，以及 [選項]**** 對話方塊中 [專案和方案]**** 頁面的連結和其他連結。 搜尋結果結果也可以包含專案檔和工具視窗。

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![「新增專案」的搜尋結果](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

   按**Ctrl** + **Q** ，直接跳到搜尋方塊。

## <a name="debug-code"></a>偵錯程式碼

偵錯可能會耗用大量的時間，但是下列的技巧可協助您加快處理它們。

- **使用 Visual Studio 偵錯工具工具**。 在 Visual Studio 內容中，當您在*偵錯工具*時，通常表示您是以偵錯工具模式執行應用程式。 偵錯工具會提供許多方式來查看您的程式碼在執行時所執行的作業。 如需開始使用的指南，請參閱[第一看 Visual Studio 偵錯工具](../debugger/debugger-feature-tour.md)。 

- **在不同瀏覽器中測試相同頁面、應用程式或網站**。 當您偵錯程式碼時，可以輕鬆地切換包括 [Page Inspector (Visual Studio)](https://msdn.microsoft.com/Library/65880969-1ad2-47be-85b9-bb12c81bf209) 在內的已安裝網頁瀏覽器，而不需要開啟 [瀏覽方式]**** 對話方塊。 您可以使用 [**開始調試**] 按鈕旁邊的 [**標準**] 工具列上的 [ **Debug Target** ] 清單，快速確認您在 Debug 或 view 頁面時所使用的瀏覽器。

    ![選取網頁瀏覽器偵錯選項](../ide/media/webbrowserdropdowntoolbar.png)

- **設定暫時中斷點**。 您可以在目前的程式碼行建立暫時中斷點並同時啟動偵錯工具。 當您執行至該行程式碼時，偵錯工具將進入中斷模式。 如需詳細資訊，請參閱[使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)。

    若要使用這項功能，請選擇**Ctrl** + **F10**鍵，或開啟您要中斷之程式程式碼的快捷方式功能表，然後選擇 [**執行至游標處**]。

- **在偵錯期間移動執行點**。 您可以移動目前的執行點至程式碼的其他部分，並從該點重新啟動偵錯。 對於只要偵錯某一區段的程式碼，而不重新建立抵達該部分所需的所有步驟，這個技術非常有用。 如需詳細資訊，請參閱[使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)。

     若要移動執行點，將黃色箭頭拖曳至同一個原始程式檔中，您想要設定下一個陳述式的位置，並選擇 **F5** 鍵以繼續偵錯。

- **擷取變數的值資訊**。 您可以將 DataTip 加入至程式碼中的變數，並釘選它，以便您在偵錯結束後存取變數的最後一個已知值。 如需詳細資訊，請參閱[在資料提示中檢視資料值](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)。

     若要加入 DataTip，偵錯工具必須處於中斷模式。 將游標置於變數，然後選擇 DataTip 上出現的釘選按鈕。 當偵錯停止時，藍色的圖釘圖示會出現在原始碼檔案中包含該變數的程式碼行旁邊。 如果您指向藍色圖釘，將會顯示變數在最近期偵錯階段中的值。

- **清除即時運算視窗**。 您可以輸入 `>cls` 或 `>Edit.ClearAll`，在設計階段清除[即時運算視窗](../ide/reference/immediate-window.md)的內容

     如需其他命令的詳細資訊，請參閱 [Visual Studio 命令別名](../ide/reference/visual-studio-command-aliases.md)。

- **[使用 CodeLens 尋找程式碼變更和其他記錄](../ide/find-code-changes-and-other-history-with-codelens.md)**。 CodeLens 可讓您在了解程式碼發生什麼事時，也能保持專注在工作上，且無須離開編輯器。 您可以尋找程式碼片段的參考、程式碼的變更、已連結的錯誤、工作項目、程式碼檢閱和單元測試。

- **使用 Live Share 來即時與其他人進行調試**。 Live Share 可讓您即時與他人共同編輯和偵錯，不論您使用的程式設計語言或建置的應用程式類型為何。 如需詳細資訊，請參閱[什麼是 Visual Studio Live Share？](https://docs.microsoft.com/visualstudio/liveshare/)

- **使用互動式視窗來撰寫和測試小型程式碼**。 Visual Studio 提供互動式的 [讀取-評估-列印-迴圈（複寫）] 視窗，可讓您輸入任意程式碼並立即查看結果。 這種編碼方式可協助您瞭解 Api 和程式庫並進行實驗，並以互動方式開發要包含在專案中的工作程式碼。 針對 Python，請參閱使用[Python 互動式視窗](../python/python-interactive-repl-in-visual-studio.md)。 互動式視窗功能也適用于 c #。 

## <a name="access-visual-studio-tools"></a>存取 Visual Studio 工具

如果您將開發人員命令提示字元或其他 Visual Studio 工具釘選至 [開始] 功能表或工作列，就可以更輕鬆地存取它。

::: moniker range="vs-2017"

1. 在 Windows 檔案總管中，瀏覽至 *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools*。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 Windows 檔案總管中，瀏覽至 *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*。

::: moniker-end

2. 以滑鼠右鍵按一下 [開發人員命令提示字元]**** 或開啟其快顯功能表，然後選擇 [釘選到 [開始]]**** 或 [釘選到工作列]****。

## <a name="manage-files-toolbars-and-windows"></a>管理檔案、工具列和視窗

您可能在開發應用程式的任何時候，同時處理多個程式碼檔案並且在數個工具視窗間移動。 您可以使用下列技巧讓一切保持井然有序：

- **讓您經常使用的檔案在編輯器中隨時可見**。 您可以將檔案釘選到索引標籤的左側，讓它們保持可見，不論編輯器中開啟了多少檔案。

   若要釘選檔案，請選擇檔案的索引標籤，然後選擇 [**切換 Pin 狀態**] 按鈕。

- **將文件和視窗移至其他監視器**。 如果您在開發應用程式時使用多個螢幕，您可以透過將開啟於編輯器中的檔案移至其他螢幕，更輕鬆地編輯應用程式的某個部分。 您也可以將工具視窗 (例如偵錯工具視窗) 移至其他螢幕，並將文件和工具視窗停駐在一起以建立「浮動定位」。 如需詳細資訊，請參閱[在 Visual Studio 中自訂視窗版面](../ide/customizing-window-layouts-in-visual-studio.md)配置。

   您也可以建立另一個方案總管**** 執行個體並移至其他監視器，更輕鬆地管理檔案。 若要建立另一個方案總管**** 執行個體，請開啟方案總管**** 中的捷徑功能表，然後選擇 [新增方案總管檢視]****。

- **自訂出現在 Visual Studio 中的字型**。 您可以為 IDE 中使用的文字變更字體、大小和色彩。 例如，您可以為編輯器裏的某一種程式碼項目自訂色彩，以及變更工具視窗或整個 IDE 的字體。 如需詳細資訊，請參閱[如何：變更字型和色彩](../ide/how-to-change-fonts-and-colors-in-visual-studio.md)和[如何：在編輯器中變更字型和顏色](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 祕訣和訣竅部落格文章](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [常用命令的預設鍵盤快速鍵](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [如何：自訂功能表和工具列](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [逐步解說：建立簡單的應用程式](../get-started/csharp/tutorial-wpf.md)
- [協助工具祕訣和訣竅](../ide/reference/accessibility-tips-and-tricks.md)
