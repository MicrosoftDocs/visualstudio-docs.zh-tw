---
title: 產能的秘訣 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ccc5e543-7dcf-465c-97dd-e133e869800c
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c56b2a2cd49d164fa55eae472eaa11942bead262
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53928850"
---
# <a name="productivity-tips-for-visual-studio"></a>使用 Visual Studio 提高產能的秘訣
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

遵循下列提示，您可以在 Visual Studio 中更快速、有效率地撰寫、巡覽及偵錯程式碼。 如需常用鍵盤快速鍵的詳細資訊，請參閱[秘訣和訣竅](../ide/tips-and-tricks-for-visual-studio.md)。 如需更完整的清單，請參閱[識別及自訂鍵盤快速鍵](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)和[預設鍵盤快速鍵](../ide/default-keyboard-shortcuts-in-visual-studio.md)。

 本主題包含下列章節：

 [存取 Visual Studio Tools](../ide/productivity-tips-for-visual-studio.md#BKMK_Access)

 [撰寫程式碼](../ide/productivity-tips-for-visual-studio.md#BKMK_Writing)

 [在您的程式碼中巡覽](../ide/productivity-tips-for-visual-studio.md#BKMK_Navigating)

 [更快速地尋找項目](../ide/productivity-tips-for-visual-studio.md#BKMK_Finding)

 [偵錯程式碼](../ide/productivity-tips-for-visual-studio.md#BKMK_Debugging)

 [管理檔案、工具列和視窗](../ide/productivity-tips-for-visual-studio.md#BKMK_Managing)

##  <a name="BKMK_Access"></a> 存取 Visual Studio Tools
 如果釘選至 [開始] 畫面或工作列，您可以更輕鬆地存取開發人員命令提示字元或其他工具。

1.  從 [開始] 畫面，輸入 `Visual Studio Tools`，然後選擇 Enter 鍵。

2.  在檔案總管中，開啟您想要之項目的捷徑功能表：

    -   組建通知

    -   Debuggable Package 管理員

    -   VS2013 開發人員命令提示字元

    -   Microsoft Feedback Client 2013

    -   VS2013 ARM Cross Tools 命令提示字元

    -   VS2013 x64 Cross Tools 命令提示字元

    -   VS2013 x64 Native Tools 命令提示字元

    -   VS2013 x86 Native Tools 命令提示字元

3.  選擇 [釘選到 [開始] 畫面] 或 [釘選到工作列]。

##  <a name="BKMK_Writing"></a> 撰寫程式碼
 您可以使用下列功能，更快速地撰寫程式碼。

-   **使用範例應用程式**。 您可以從 MSDN Code Gallery 下載和安裝範例應用程式，來加速應用程式開發。 您也可以下載和探索該區域的範例套件，學習特定技術或程式設計概念。

-   **使用 IntelliSense**。 當您在編輯器中輸入程式碼時，將會顯示 IntelliSense 資訊，例如列出成員、參數資訊、快速諮詢、簽章說明和自動完成文字。 這些功能支援文字的模糊比對。例如，列出成員的結果清單不僅會包含以您所輸入的字母為開頭的項目，同時也會包含名稱中包含該字母組合的項目。 如需詳細資訊，請參閱[使用 IntelliSense](../ide/using-intellisense.md)。

-   **在您輸入程式碼時變更 IntelliSense 選項的自動插入**。 藉由切換 IntelliSense 至建議模式，您可以規定只有在明確選擇 IntelliSense 選項時，才可以將該選項插入。

     若要啟用建議模式，請選擇 Ctrl+Alt+空格鍵，或在功能表列上依序選擇 [編輯]、[IntelliSense]和 [切換完成模式]。

-   **使用程式碼片段**. 您可以使用內建的程式碼片段或建立自己的程式碼片段。

     若要插入程式碼片段，請在功能表列上依序選擇 [編輯]、[IntelliSense] 和 [插入程式碼片段]，或是開啟檔案中的捷徑功能表，然後選擇 [插入程式碼片段]。 如需詳細資訊，請參閱[程式碼片段](../ide/code-snippets.md)。

-   **修正內嵌程式碼錯誤**。 智慧標籤會在程式碼行底下顯示成藍色或紅色方塊。 您可以指向其中一個方塊或將游標放在程式碼行，並選擇 Ctrl + . (句號) 鍵，來顯示智慧標籤選項。

     藍色方塊提供修正程式碼錯誤的建議。

     圖 1：錯誤智慧標籤

     ![錯誤智慧標籤建議](../ide/media/productivity-bluesmarttags.png "Productivity_BlueSmartTags")

     紅色方塊提供重構程式碼的建議。

     圖 2：重構智慧標籤

     ![重構智慧標籤建議](../ide/media/productivity-redsmarttags.png "Productivity_RedSmartTags")

-   **顯示和編輯程式碼項目的定義**。 您可以快速顯示和編輯定義程式碼項目 (例如成員、變數或區域) 的模組。

     若要在快顯視窗中開啟定義，請反白顯示項目，然後選取 Alt+F12 鍵，或者開啟項目的捷徑功能表，然後選擇 [查看定義]。 若要在不同的程式碼視窗中開啟定義，請開啟項目的捷徑功能表，然後選擇 [移至定義]。

##  <a name="BKMK_Navigating"></a> 在您的程式碼中巡覽
 您可以利用各種技巧，更快速地尋找和移動至程式碼中的某個位置。

-   **將數行程式碼加入書籤**。 您可以利用書籤來快速地巡覽至檔案中的特定幾行程式碼。

     若要設定書籤，請在功能表列上依序選擇 [編輯]、[書籤]和 [切換書籤]。 您可以在 [書籤] 視窗中檢視方案的所有書籤。 如需詳細資訊，請參閱[在程式碼中設定書籤](../ide/setting-bookmarks-in-code.md)。

-   **搜尋檔案中的符號定義**。 您可以在方案中搜尋並找出符號定義和檔名，不過搜尋結果並不會包含名稱空間或區域變數。

     若要存取這項功能，請在功能表列上依序選擇 [編輯] 和 [巡覽至]。

-   **瀏覽程式碼的整體結構**。 在方案總管中，您可以搜尋和瀏覽專案中的類別及其類型和成員。 您也可以搜尋符號，檢閱方法的呼叫階層架構，尋找符號參考和執行其他工作。 如果您在方案總管中選擇程式碼項目，則會在 [預覽] 索引標籤中開啟相關聯的檔案，而游標會移至檔案中的項目。 如需詳細資訊，請參閱[檢視程式碼的結構](../ide/viewing-the-structure-of-code.md)。

##  <a name="BKMK_Finding"></a> 更快速地尋找項目
 除了篩選工具視窗的內容以顯示與您目前的工作有關的資訊以外，您可以在整個 IDE 中搜尋命令、檔案和選項。

-   **篩選工具視窗的內容**。 您可以搜尋 [工具箱]、[屬性] 視窗和方案總管許多這類工具視窗的內容，但只會顯示名稱包含您所指定字元的項目。

-   **只顯示您要處理的錯誤**。 如果您選擇 [錯誤清單] 工具列上的 [篩選] 按鈕，則可以減少 [錯誤清單] 視窗中出現的錯誤數目。 您可以選擇顯示只在目前編輯器開啟之檔案中的錯誤、只在目前檔案中的錯誤或只在目前專案中的錯誤。 您也可以在 [錯誤清單] 視窗中搜尋以找出特定錯誤。

-   **尋找對話方塊、功能表命令和選項**。 在[選項對話方塊、環境、快速啟動](../ide/reference/quick-launch-environment-options-dialog-box.md)方塊中，輸入您要嘗試尋找之項目的關鍵字或片語。 例如，如果您輸入 `new project`，則會出現下列選項︰

     圖 3.快速啟動 結果清單 `new project`

     !['new project' 的快速啟動結果](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

     [快速啟動] 會顯示 [新增專案] 對話方塊、[新增項目] 對話方塊以及 [選項] 對話方塊中的 [專案和方案] 頁面的連結。 快速啟動結果也可以包含專案檔和工具視窗。

##  <a name="BKMK_Debugging"></a> 偵錯程式碼
 偵錯可能會耗用大量的時間，但是下列的技巧可協助您加快處理它們。

-   **在不同瀏覽器中測試相同頁面、應用程式或網站**。 當您偵錯程式碼時，可以輕鬆地切換包括 [Page Inspector (Visual Studio)](http://msdn.microsoft.com/library/65880969-1ad2-47be-85b9-bb12c81bf209) 在內的已安裝網頁瀏覽器，而不需要開啟 [瀏覽方式] 對話方塊。 您可以使用 [偵錯目標] 清單 (位於 [開始偵錯] 按鈕旁的 [標準] 工具列)，快速確認您偵錯或檢視頁面時所使用的瀏覽器。

     ![選取網頁瀏覽器偵錯選項](../ide/media/webbrowserdropdowntoolbar.png "WebBrowserDropDownToolbar")

-   **設定暫時中斷點**。 您可以在目前的程式碼行建立暫時中斷點並同時啟動偵錯工具。 當您執行至該行程式碼時，偵錯工具將進入中斷模式。 如需詳細資訊，請參閱[使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)。

     若要使用這個功能，請選擇 Ctrl + F10 鍵，或為您要設定中斷點的該行程式碼開啟捷徑功能表，然後選擇 [執行至游標處]。

-   **在偵錯期間移動執行點**。 您可以移動目前的執行點至程式碼的其他部分，並從該點重新啟動偵錯。 對於只要偵錯某一區段的程式碼，而不重新建立抵達該部分所需的所有步驟，這個技術非常有用。 如需詳細資訊，請參閱[使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)。

     若要移動執行點，將黃色箭頭拖曳至同一個原始碼檔案中，您想要設定下一個陳述式的位置，並選擇 F5 鍵以繼續偵錯。

-   **擷取變數的值資訊**。 您可以將 DataTip 加入至程式碼中的變數，並釘選它，以便您在偵錯結束後存取變數的最後一個已知值。 如需詳細資訊，請參閱[在資料提示中檢視資料值](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)。

     若要加入 DataTip，偵錯工具必須處於中斷模式。 將游標置於變數，然後選擇 DataTip 上出現的釘選按鈕。 當偵錯停止時，藍色的圖釘圖示會出現在原始碼檔案中包含該變數的程式碼行旁邊。 如果您指向藍色圖釘，將會顯示變數在最近期偵錯階段中的值。

-   **清除即時運算視窗**。 您可以輸入 `>cls` 或 `>Edit.ClearAll`，在設計階段清除[即時運算視窗](../ide/reference/immediate-window.md)的內容。

     如需其他命令的詳細資訊，請參閱 [Visual Studio 命令別名](../ide/reference/visual-studio-command-aliases.md)。

##  <a name="BKMK_Managing"></a> 管理檔案、工具列和視窗
 您可能在開發應用程式的任何時候，同時處理多個程式碼檔案並且在數個工具視窗間移動。 您可以使用下列技巧來保持井然有序。

-   **讓您經常使用的檔案在編輯器中隨時可見**。 您可以將檔案適當地釘選在索引標籤井的左側，使這些檔案不論編輯器中開啟了多少檔案仍隨時可見。

     若要釘選檔案，請選擇檔案的索引標籤，然後選擇 [切換固定狀態] 按鈕。

-   **將文件和視窗移至其他監視器**。 如果您在開發應用程式時使用多個螢幕，您可以透過將開啟於編輯器中的檔案移至其他螢幕，更輕鬆地編輯應用程式的某個部分。 您也可以將偵錯工具視窗等工具視窗移至其他監視器，並將文件和工具視窗停駐在一起以建立「浮動定位」。 如需詳細資訊，請參閱[＜How to：排列和固定視窗](../misc/how-to-arrange-and-dock-windows.md)。

     您也可以建立另一個方案總管執行個體並移至其他監視器，更輕鬆地管理檔案。 若要建立另一個方案總管執行個體，請開啟方案總管中的捷徑功能表，然後選擇 [新增方案總管檢視]。

-   **自訂出現在 Visual Studio 中的字型**。 您可以為 IDE 中使用的文字變更字體、大小和色彩。 例如，您可以為編輯器裏的某一種程式碼項目自訂色彩，以及變更工具視窗或整個 IDE 的字體。 如需詳細資訊，請參閱[＜How to：變更字型和色彩](../ide/how-to-change-fonts-and-colors-in-visual-studio.md)及[如何：在編輯器中變更字型和色彩](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)。

## <a name="see-also"></a>請參閱
 [常用命令的預設鍵盤快速鍵](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md) [How to:自訂功能表和工具列](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)[逐步解說：建立簡單的應用程式](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)[協助工具祕訣和訣竅](../ide/reference/accessibility-tips-and-tricks.md)
