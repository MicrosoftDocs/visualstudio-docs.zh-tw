---
title: 在程式碼和文字編輯器中撰寫程式碼 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code editor, word wrap
- outlining
- code, editing
- squiggles
- code editor, outlining
- code editor, error and warning markers
- word wrap
- code editor, syntax coloring
- code editor, go to definition
- diff
- code editor [Visual Studio]
- code editor, diff
- error and warning markers
- code editor, navigation bar
- code editor, customizing
- comment selection
- code editor, tabify
- brace matching
- code editor, line numbers
- printing
- code editor, brace matching
- code editor, squiggles
- code editor, features
- line numbers
- go to definition
- syntax coloring
- code editor, navigate to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- navigate to
- line break characters
- code editor, virtual space
- code editor, change tracking
- code editor, comment selection
- code editor, printing
- virtual space
- code editor, line break characters
- code editor, go to line
- code
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: 46
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cb879efdc3370578d57b529194a9a8790c9136dc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487341"
---
# <a name="writing-code-in-the-code-and-text-editor"></a>在程式碼和文字編輯器中撰寫程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[程式碼和文字編輯器中撰寫程式碼](https://docs.microsoft.com/visualstudio/ide/writing-code-in-the-code-and-text-editor)。

Visual Studio 編輯器提供許多功能，讓您能夠更輕鬆地撰寫並管理程式碼。 您可以使用大綱，展開及摺疊程式碼的不同區塊。 您可以使用 IntelliSense、[物件瀏覽器] 及呼叫階層，進一步了解您正在使用的程式碼。 您可以使用像是 [巡覽至] 、[移至定義] 及 [尋找所有參考] 的功能，巡覽您的程式碼。 您可以將程式碼片段插入程式碼區塊，並使用像是 [從使用量產生] 的功能來產生程式碼。 如果您從未使用過 Visual Studio 2015 編輯器，請參閱 [編輯程式碼](https://www.visualstudio.com/features/ide-vs) ，以取得快速概觀。  

 檢視程式碼有許多不同的方法。 若要查看方案的類別檢視，您可以開啟 [類別檢視]  視窗或展開類別檔案下之方案總管  中的節點。  

 您可以搜尋並取代單一或多個檔案的文字。 如需詳細資訊，請參閱[尋找和取代文字](../ide/finding-and-replacing-text.md)。 如果要使用規則運算式，請注意尋找並取代功能現在使用 .NET 規則運算式。 如需詳細資訊，請參閱[在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)。  

 不同的 Visual Studio 語言提供不同的功能集，而在某些情況下，功能在不同的語言下運作方式也會不同。 在功能的描述中有指出許多這些差異，如需詳細資訊，請參閱特定 Visual Studio 語言的各章節。  

> [!IMPORTANT]
>  Visual Studio 的版本及您正在使用的設定，可能會影響 IDE 中的功能。 其可能會與本主題中所述內容有所不同。  

## <a name="editor-features"></a>編輯器功能  

|||  
|-|-|  
|語法著色|部分程式碼的語法元素及標記檔案的色彩不同，以加以區別。 例如，關鍵字 (像是 C# 中的 `using` 及 Visual Basic 中的 `Imports` ) 是一種色彩，但類型 (像是 `Console` 及 `Uri`) 則是另一種色彩。 其他的語法元素也標示有色彩，例如字串常值和註解。 C++ 使用色彩來區別類型、列舉和巨集，及其他語彙基元。<br /><br /> 您可以查看每個類型的預設色彩，也可以變更[選項對話方塊、環境、字型和色彩](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)中任何特定語法項目的色彩，其可從 [工具] 功能表開啟。|  
|錯誤和警告標記|在加入程式碼及建置方案時，會看見 (a) 不同顏色的波浪底線 (又稱為波浪線) 或 (b) 燈泡出現在程式碼中。 紅色波浪線表示語法錯誤，藍色表示編譯器錯誤，綠色表示警告，而紫色則表示其他錯誤。 [燈泡](../ide/perform-quick-actions-with-light-bulbs.md)提供修正問題的建議，並讓您能輕鬆套用修正程式。<br /><br /> 您可以在 [工具]/[選項]/[環境]/[字型和色彩]  對話方塊中，查看每項錯誤及警告波浪線的預設色彩。 尋找 [語法錯誤] 、[編譯器錯誤] 、[警告] 及 [其他錯誤] 。|  
|括號對稱|插入點在程式碼檔案中的左大括號上時，其與右大括號都將反白顯示。 這項功能提供您位置錯誤或遺漏括號的立即回應。 您可以使用 [分隔符號自動反白顯示]  設定 ([工具]/[選項]/[文字編輯器])，開啟或關閉括號對稱。 您可以在 [字型和色彩]  設定中 ([工具]/[選項]/[環境])，變更醒目提示色彩。 尋找 [括號對稱 (反白顯示) ]  或 [括號對稱 (方框)] 。|  
|行號|程式碼視窗的左邊界中可顯示行號。 根據預設，將不顯示行號。 您可以在 [文字編輯器所有語言]  設定中 ([工具]/[選項]/[文字編輯器]/[所有語言])，開啟這個選項。 您可以變更語言的設定來顯示個別程式設計語言的行號 ([工具]/[選項]/[文字編輯器]/[\<語言>])。 若要列印行號，您必須在 [列印]  對話方塊中選取 [包含行號]。|  
|變更追蹤|您可利用左邊界的色彩，追蹤在檔案中所做的變更。 開啟檔案後所做的未儲存變更，將在左邊界以黃色橫條表示 (稱為選取範圍邊界)。 儲存變更後 (但在關閉檔案前)，橫條會變成綠色。 如果您在儲存檔案後復原變更，則橫條會變成橙色。 若要關閉或開啟這項功能，請在 [文字編輯器]  設定中 ([工具]/[選項]/[文字編輯器]  )，變更 [追蹤修訂]選項。|  
|選取程式碼和文字|您可以在標準的連續資料流模式或方塊模式中選取文字，其將為矩形範圍而不是條列的文字。 若要在方塊模式中選取文字，請在按住 ALT 鍵的同時拖曳滑鼠選取範圍 (或按住 ALT+SHIFT+\<方向鍵>)。 選取範圍包含在矩形中 (定義為選取範圍中的第一個及最後一個字元) 的所有字元。 在選取範圍內進行任何輸入或貼上，將插入每一行的相同位置。|  
|縮放|在任何程式碼視窗中都可以放大或縮小，方法是按住 CTRL 鍵並滾動滑鼠滾輪 (或按 CTRL + SHIFT + . 以增加及 CTRL + SHIFT + , 以減少)。 您也可用程式碼視窗左下角的縮放方塊，設定指定的縮放百分比。 縮放功能不適用於工具視窗中。|  
|虛擬空間|根據預設，Visual Studio 編輯器中的行結束於最後一個字元之後，因此若在行尾點選向右鍵，會將游標移至下一行的開頭。 在某些其他編輯器中，最後一個字元之後不是行的結尾，而您可以將游標置於行的任意位置。 您可以透過 [工具]/[選項]/[文字編輯器]/[所有語言]  設定，在編輯器中啟用虛擬空間。 請注意，您可以啟用 [虛擬空間]  或 [自動換行] ，但無法同時啟用兩者。|  
|列印|您可以使用 [列印]  對話方塊中的選項，在列印檔案時包含行號或隱藏程式碼折疊的區域。 在 [版面設定]  對話方塊中，也可以透過選擇 [頁首] 來決定是否要列印檔案的完整路徑及其名稱。<br /><br /> 您可以在 [工具]/[選項]/[環境]/[字型和色彩]  對話方塊中，設定色彩列印選項。 在 [顯示設定]  清單中選取 [印表機]  可自訂彩色列印。 您可以指定列印檔案和編輯檔案使用不同色彩。|  
|全域復原和取消復原|[編輯]  功能表上的 [復原上次的全域動作]  和 [取消復原上次的全域動作]  命令，將復原或取消復原影響多個檔案的全域動作。 全域動作包含重新命名類別或命名空間、針對方案執行尋找並取代作業、重構資料庫，或變更多個檔案的其他動作。 您可以在目前 Visual Studio 工作階段中，對動作套用全域復原和取消復原命令，即使您關閉方案後，動作依然套用其中。|  

## <a name="advanced-editing-features"></a>進階編輯功能  
 您可以在 [編輯]/[進階]  子功能表下找到許多進階功能。 並非所有類型的程式碼檔案都提供所有這些功能。  

|||  
|-|-|  
|格式化文件|設定程式碼適當的行縮排，並移動大括號以分隔文件中的行。|  
|格式化選取範圍|設定程式碼適當的行縮排，並移動大括號以分隔選取範圍中的行。|  
|選取範圍空白鍵轉定位鍵|將前置空格變更至適當的定位點。|  
|選取範圍定位鍵轉空白鍵|將前置定位點變更為空格。 如果您要將檔案中所有空格轉換為定位點 (或轉換所有定位點為空格)，可以使用 `Edit.ConvertSpacesToTabs` 及 `Edit.ConvertTabsToSpaces` comm及s. 在 Visual Studio 功能表中看不到這些命令，但可以透過 [快速存取] 視窗或命令視窗加以呼叫。|  
|設成大寫|將選取範圍中的所有字元變更為大寫；如果沒有選取範圍，則將插入點的字元變更為大寫。|  
|設成小寫|將選取範圍中的所有字元變更為小寫；如果沒有選取範圍，則將插入點的字元變更為小寫。|  
|驗證文件|驗證 JScript 程式碼檔案。|  
|刪除水平空白區|刪除目前行尾的定位點或空格。|  
|檢視空白區|將空格顯示為浮點，定位點則為箭號。 顯示檔案結尾為矩形圖像。 如果選取了 [工具]/[選項]/[文字編輯器]/[所有語言]/[自動換行]/[顯示自動換行的可見圖像]  選項，則該圖像也將顯示。|  
|自動換行|讓文件中的所有行在程式碼視窗中皆可看到。 您可以在 [文字編輯器] 的 [所有語言] 設定中 ([工具]/[選項]/[文字編輯器]/[所有語言])，開啟或關閉自動換行。|  
|取消註解選取範圍|對選取範圍或目前這一行加入註解字元。|  
|註解選取範圍|從選取範圍或目前這一行移除註解字元。|  
|增加行縮排|加入定位點 (或相當的空格) 到選取行或目前這一行。|  
|減少行縮排|從選取行或目前這一行移除定位點 (或相當的空格)。|  
|選取標記|在含有標記的文件 (例如 XML 或 HTML) 中選取標記。|  
|選取標記內容|在含有標記的文件 (例如 XML 或 HTML) 中選取內容。|  

## <a name="navigate-in-the-code-window"></a>在程式碼視窗中巡覽  
 有數種不同的方式可讓您在文件中四處移動。 除了標準作業之外，您可以使用工具列上的 [向後巡覽] \(或 CTRL+減號) 及 [向前巡覽]\ (CTRL+SHIFT+減號) 按鈕，將插入點移至上一個位置或返回使用中文件之最近使用的位置。 這些按鈕會保留插入點的最後 20 個位置。  

 ![[向前巡覽] 及 [向後巡覽] 按鈕](../ide/media/vs2015-nav-buttons.png "VS2015_Nav_buttons")  

 您也可以使用程式碼視窗中的進階捲軸，以取得程式碼的鳥瞰檢視。 在地圖模式中，當您在捲軸上向上及向下移動游標時，可以預覽程式碼。如需詳細資訊，請參閱[如何：自訂捲軸以追蹤程式碼](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)。  

 下列命令是程式碼專屬的巡覽方法：  

|||  
|-|-|  
|移至 \<行號>|([編輯]/[移至] 或 CTRL+G)：移至使用中文件的指定行號。|  
|巡覽至|([編輯]/[巡覽至] 或 CTRL + ,)：在使用中方案內尋找符號或檔案。 其可協助您從查詢中挑選一組適當的相符結果。 您可以使用駝峰式命名法來搜尋包含在符號中的關鍵字，並將字元加底線以將符號分割為關鍵字。|  
|尋找所有參考|(操作功能表)：在方案中尋找選取項目的所有參考。|  
|移至定義|(操作功能表或 F12)：尋找選取項目的定義。|  
|查看定義|(操作功能表或 Alt+F12)：尋找選取項目的定義，並顯示於快顯視窗中。 如需詳細資訊，請參閱[如何：使用查看定義檢視和編輯程式碼 (Alt+F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)。|  
|下一個方法，上一個方法|在 Visual Basic 程式碼檔案中，請使用這些命令 ([編輯]/[下一個方法]、[上一個方法]) 以將插入點移動至不同的方法。|  
|反白顯示參考|當您按一下原始程式碼中的符號時，該符號在文件的所有出現處，都將反白顯示。 反白顯示的符號可能包含宣告和參考，以及許多其他 [尋找所有參考]  會傳回的符號。 其中包括類別、物件、變數、方法和屬性的名稱。 在 Visual Basic 程式碼中，許多控制項結構的關鍵字也會反白顯示。 若要移到下一個或上一個反白顯示的符號，請按 CTRL+SHIFT+向下鍵或 CTRL+SHIFT+向上鍵。 您可以在 [工具]/[選項]/[環境]/[字型和色彩]/[反白顯示的參考] |  
|尋找與程式碼相關的資訊|當您在程式碼編輯器中使用 CodeLens 時，可以尋找特定程式碼的相關資訊，例如變更及進行這些變更的人員、參考、Bug、工作項目、程式碼檢閱和單元測試狀態。 當您使用 Visual Studio Enterprise 與 Team Foundation Server 時，CodeLens 將以類似抬頭顯示方式執行。 請參閱[尋找程式碼變更和其他記錄](../ide/find-code-changes-and-other-history-with-codelens.md)。|  

 您也可以使用 **巡覽列**，也就是顯示在程式碼視窗頂端的兩個下拉式清單方塊，來巡覽程式碼檔案。 您可利用此列直接巡覽至特定類型或某個類型中的其中一位成員。 巡覽列會顯示 Visual Basic、C# 和 C++ 程式碼檔案。  

 若要隱藏巡覽列，請在 [文字編輯器] 的 [所有語言] 設定中 ([工具]/[選項]/[文字編輯器]/[所有語言]  ，或變更各個語言的設定)，變更 [巡覽列]選項。 您可以巡覽下拉式方塊，如下所示：  

-   若要將焦點從程式碼視窗移至巡覽列，請按快速鍵組合 CTRL+F2。  

-   若要將焦點從巡覽列回復到程式碼視窗，請按 ESC 鍵。  

-   若要將焦點從巡覽列的某個項目移至另一個項目，請按 TAB 鍵。  

-   若要選取具有焦點的巡覽列項目並返回 IDE，請按 ENTER 鍵  

-   若要巡覽至類別或類型，請在左側下拉式清單按一下其名稱。  

-   若要直接巡覽至類別中的程序，請在右側下拉式清單中按一下程序。  

 在部分類別中，定義在目前程式碼檔案外部的成員可能會變成灰色。  

## <a name="find-code-using-navigate-to"></a>使用巡覽至來尋找程式碼
Visual Studio 的 [巡覽至] 命令會執行焦點式的搜尋您的程式碼，可協助您在程式碼檔案、 檔案路徑和程式碼符號中找到指定的項目。 與 [尋找] 或 [檔案中尋找] 這類其他文字搜尋不同，[巡覽至] 會將搜尋範圍限制為實際程式碼存在的區域，例如檔案、表單和程式碼模組。 例如，如果您在整個方案中使用 [尋找] 或 [檔案中尋找] 搜尋 ASP.NET Web 應用程式中的字串，則可能會收到數個相符項目，包括程式碼備註中字串的執行個體。 藉由使用瀏覽至，不過，您可能只取得單一函式，並忽略任何程式碼備註中字串的執行個體。

### <a name="navigate-code-using-navigate-to"></a>使用巡覽至來巡覽程式碼

1. 在 Visual Studio 中開啟方案或資料夾。
1. 在主功能表上，依序選擇 [編輯] 和 [巡覽至]，或按 **CTRL + ,**。

    小型文字方塊會出現在程式碼編輯器的上方。
1. 在此文字方塊中，輸入您想要尋找之程式碼項目的名稱。

    ![[巡覽至] 視窗](../ide/media/vside-navigatetowindow.png "[巡覽至] 視窗")

    當您輸入時，結果會出現在文字方塊下方的下拉式清單中。
1. 若要移至項目，請在清單中選擇它。


### <a name="filter-your-search"></a>篩選您的搜尋

若要將搜尋範圍限制為僅限程式碼符號，請在 [巡覽至] 查詢的前面加上 "@" 字元。 例如，如果您搜尋 `@application`，則 [巡覽至] 只會顯示包含 "application" 這個字的類別。

如果您在程式碼中使用駝峰式命名法，則只要輸入程式碼項目名稱的大寫字母，就可以更快速地找到程式碼項目。 例如，如果您的程式碼有一個稱為 `ViewSwitcher` 的元件，則只要在 [巡覽至] 視窗中輸入名稱的大寫字母 (`"VS"`) 就可以找到它。

![[巡覽至] 視窗 - 使用大寫搜尋](../ide/media/vside-capitalsearch.png "[巡覽至] 視窗 - 使用大寫搜尋")

如果您的程式碼名稱很長，這個功能就特別有用。

## <a name="customize-the-editor"></a>自訂編輯器  
 **匯入和匯出設定**：您可以與另一個開發人員共用設定、使設定符合標準，或使用 [工具]  功能表上的 [匯入和匯出設定精靈]  ，將其回復為 Visual Studio 預設設定。 您可以變更一般設定或語言以及專案專屬的設定。  

 **鍵盤對應**：您可以定義新的熱鍵或透過 [工具]/[選項]/[環境]/[鍵盤] 設定，重新定義現有的熱鍵。 如需快速鍵的詳細資訊，請參閱[預設鍵盤快速鍵](../ide/default-keyboard-shortcuts-in-visual-studio.md)。  

 如需語言專屬編輯器選項的相關資訊，請參閱：  

-   [Visual Basic 設定](http://msdn.microsoft.com/library/2712b3b1-18f2-430c-ae91-28468bbf5f32)  

-   [使用 C# 的 Visual Studio 開發環境](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)  

-   [格式、JavaScript、文字編輯器、選項](../ide/reference/options-text-editor-javascript-formatting.md)  

## <a name="in-this-section"></a>本節內容  

-   [尋找和取代文字](../ide/finding-and-replacing-text.md)  

-   [編碼與分行符號](../ide/encodings-and-line-breaks.md)  

-   [大綱](../ide/outlining.md)  

-   [重構](../ide/refactoring-in-visual-studio.md)  

-   [產能的秘訣](../ide/productivity-tips-for-visual-studio.md)  

-   [使用 IntelliSense](../ide/using-intellisense.md)  

-   [自訂編輯器](../ide/customizing-the-editor.md)  

-   [如何：自訂捲軸以追蹤程式碼](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)  

-   [如何：使用查看定義檢視和編輯程式碼 (Alt+F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)  

-   [執行燈泡提示的快速動作](../ide/perform-quick-actions-with-light-bulbs.md)  

-   [程式碼片段](../ide/code-snippets.md)  

-   [使用工具箱](../ide/using-the-toolbox.md)  

-   [檢視程式碼的結構](../ide/viewing-the-structure-of-code.md)  

-   [在程式碼中設定書籤](../ide/setting-bookmarks-in-code.md)  

-   [使用工作清單](../ide/using-the-task-list.md)  

-   [尋找程式碼變更和其他記錄](../ide/find-code-changes-and-other-history-with-codelens.md)  

## <a name="see-also"></a>另請參閱  
 [Visual Studio IDE](../ide/visual-studio-ide.md)


