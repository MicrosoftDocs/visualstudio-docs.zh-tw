---
title: XAML 程式碼編輯器
description: Visual Studio 中的 XAML 程式碼編輯器導覽
ms.date: 06/16/2020
ms.topic: overview
f1_keywords:
- VS.XamlEditor
monikerRange: vs-2019
ms.custom: contperf-fy21q4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 672bfa6b28e364351f262cb2a2c6e2258ecd9746
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879391"
---
# <a name="xaml-code-editor"></a>XAML 程式碼編輯器

[VISUAL STUDIO IDE](../get-started/visual-studio-ide.md)中的 XAML 程式碼編輯器包含為 Windows 平臺和[Xamarin](/xamarin/xamarin-forms/user-interface/text/editor/)建立 WPF 和 UWP 應用程式所需的所有工具。 本文概述當您開發以 XAML 為基礎的應用程式時，程式碼編輯器所扮演的角色，以及 Visual Studio 2019 中 XAML 程式碼編輯器特有的功能。

首先，讓我們看看 IDE (整合式開發環境) 與開啟的 WPF 專案。 下圖顯示您將在 XAML 程式碼編輯器中使用的幾個主要 IDE 工具。

:::image type="content" source="media/xaml-code-editor-overview-sml.png" alt-text="在 XAML 中使用開放式 WPF 專案的 Visual Studio 2019 IDE" lightbox="media/xaml-code-editor-overview-lrg.png":::

從影像的左下方開始，主要的 IDE 工具如下所示：

- [ **[XAML 程式碼編輯器](#xaml-code-editor-ui)** ] 視窗 &mdash; 是 &mdash; 您建立和編輯程式碼的本文主體。
- 您要在其中設計 UI 的 **[XAML 設計工具](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)** 視窗。
- **[工具箱](../ide/reference/toolbox.md)** 可停駐視窗，您可在其中將控制項加入至 UI。
- [ **[調試](../debugger/debugger-feature-tour.md)** 程式] 按鈕，您可以在其中執行程式碼並進行 Debug 錯。 <br> (您也可以在使用 [XAML 熱重新載入](xaml-hot-reload.md)進行偵錯工具時，即時編輯您的程式碼。 ) 
- **[方案總管](../ide/solutions-and-projects-in-visual-studio.md)**] 視窗，您可以在其中管理檔案、專案和方案。
- [ **[屬性](../ide/reference/properties-window.md)** ] 視窗，您可以在其中變更 ui 的外觀以及 ui 控制項的運作方式。

若要繼續，讓我們深入瞭解 XAML 程式碼編輯器。

## <a name="xaml-code-editor-ui"></a>XAML 程式碼編輯器 UI

XAML 應用程式的 [程式碼編輯器] 視窗會共用某些 UI (使用者介面) 專案也會出現在標準 IDE 中，但它也包含一些獨特的功能，可讓您更輕鬆地開發 XAML 應用程式。

以下是 [XAML 程式碼編輯器] 視窗本身的外觀。

![Visual Studio 中的 XAML 程式碼編輯器視窗](media/xaml-code-editor-window.png "Visual Studio 2019 中 [XAML 程式碼編輯器] 視窗的螢幕擷取畫面")

接下來，讓我們看看程式碼編輯器中每個 UI 元素的函式。

### <a name="first-row"></a>第一個資料列

在 XAML 程式碼視窗頂端的第一個資料列中，左側有一個 [ **設計** ] 索引標籤、[ **交換窗格** ] 按鈕、[ **XAML** ] 索引標籤和 [ **退出 xaml** ] 按鈕。

![Visual Studio 的 XAML 程式碼編輯器視窗中，第一個資料列的第一個資料列，其中第一個資料列的左邊已反白顯示](media/xaml-code-editor-top-row-left.png "Visual Studio 2019 中 XAML 程式碼編輯器視窗中的第一個資料列的螢幕擷取畫面，其中左側的 UI 元素會反白顯示")

其運作方式如下：

- [ **設計** ] 索引標籤會將焦點從 XAML 程式碼編輯器變更為 XAML 設計工具。
- [ **交換窗格** ] 按鈕會在 IDE 中反轉 XAML 設計工具和 XAML 程式碼編輯器的位置。
- [ **Xaml** ] 索引標籤會將焦點變更回 XAML 程式碼編輯器。
- [ **退出 XAML** ] 按鈕會在 IDE 之外建立不同的 XAML 程式碼編輯器視窗。

從右邊繼續，有一個 **垂直分割** 按鈕、 **水準分割** 按鈕和折迭 **窗格** 按鈕。

![Visual Studio 中 XAML 程式碼編輯器視窗中的第一個資料列的第一個，並醒目提示第一個資料列的右側](media/xaml-code-editor-top-row-right.png "Visual Studio 2019 中 XAML 程式碼編輯器視窗的第一個資料列的螢幕擷取畫面，其中會反白顯示右邊的 UI 元素")

其運作方式如下：

- **垂直分割** 按鈕會將 IDE 中的 XAML 設計工具和 XAML 程式碼編輯器的位置，從水準對齊變更為垂直對齊。
- **水準分割** 按鈕會將 IDE 中的 XAML 設計工具和 XAML 程式碼編輯器的位置，從垂直對齊變更為水準對齊。
- [折迭 **窗格]** 按鈕可讓您折迭底部窗格中的內容，不論是程式碼編輯器或設計工具。  (若要還原底部窗格，請再次選擇相同的按鈕，其現在已命名為 **展開窗格** 按鈕。 ) 

<!-- [!TIP]
> You can run two parallel instances of the XAML code editor concurrently by using both the **Pop Out XAML** button and the **Expand Pane** button.
>
> You might find it useful to have one larger window open that reveals more of your code in context and a smaller pane open that has its focus directly on the code that you're working on. -->

### <a name="second-row"></a>第二列

在 XAML 程式碼視窗頂端的第二個數據列中，有兩個視窗下拉式清單。 但是，如果您看到這些 UI 元素的工具提示，則會進一步將其識別為 "Element： Window" 和 "Member： Window"。

![Visual Studio 中 XAML 程式碼編輯器視窗中兩個頂端資料列的第二個數據列，這兩個視窗下拉式清單都是可見的。](media/xaml-code-editor-top-row-windows.png "在 Visual Studio 2019 的 [XAML 程式碼編輯器] 視窗中，第二個頂端資料列的螢幕擷取畫面，其中顯示兩個視窗下拉式清單")

視窗下拉式清單具有不同的功能，如下所示：

- 左邊的 [ **元素：] 視窗** 可協助您查看和導覽至同級或父元素。

  具體來說，它會顯示類似大綱的視圖，以顯示程式碼的標記結構。 當您從清單中選取時，[程式碼編輯器] 中的焦點將會貼齊至包含您所選取之元素的程式程式碼。

    ![Visual Studio 中的 [元素：視窗] 下拉式清單](media/xaml-element-window-dropdown.png "[元素： Visual Studio 2019 中的視窗] 下拉式清單的螢幕擷取畫面")

- 右側的 [ **成員：] 視窗** 可協助您查看和導覽至屬性或子項目。

    具體而言，它會顯示您程式碼中的屬性清單。 當您從清單中選取時，[程式碼編輯器] 中的焦點將會貼齊至包含您所選取之屬性的程式程式碼。

    ![Visual Studio 中的 [成員：視窗] 下拉式清單](media/xaml-member-window-dropdown.png "Visual Studio 2019 中 [成員：視窗] 下拉式清單的螢幕擷取畫面")

### <a name="middle-pane-code-editor"></a>中間窗格，程式碼編輯器

中間窗格是 XAML 程式碼編輯器的「程式碼」部分。 它包含您可以在 [IDE 程式碼編輯器](../get-started/tutorial-editor.md)中找到的大部分功能。 我們將接觸數個可協助您開發 XAML 程式碼的通用 IDE 功能。 我們也會在 IDE 中強調唯一的 XAML 功能。

![XAML 程式碼編輯器（僅限中間窗格） Visual Studio](media/xaml-code-editor-middle.png "XAML 程式碼編輯器的螢幕擷取畫面，僅限中間窗格，在 Visual Studio 2019")

#### <a name="quick-actions"></a>快速動作

您可以使用 [快速動作](../ide/quick-actions.md) 來重構、產生或以其他方式修改具有單一動作的程式碼。

例如，您可以使用 [快速動作] 執行的一項實用工作，就是從 [ **MainWindow** ] 索引標籤中的 c # 程式碼 **移除不必要的 using** 。

方法如下：

1. 將滑鼠停留在 using 語句上，選擇燈泡圖示，然後從下拉式清單中選擇 [ **移除不必要的 using** ]。

    ![[快速動作] 功能表中的 IDE 編輯器的 [移除不必要的 Using] 選項](media/xaml-code-editor-remove-usings.png "[快速動作] 功能表中的 IDE 編輯器 [移除不必要的 Using] 選項的螢幕擷取畫面")

1. 選擇是否要修正 **檔**、 **專案** 或 **方案** 中的所有專案。
1. 查看 [ **預覽** ] 對話方塊， **然後選擇 [** 套用]。

您也可以從功能表列存取這項功能。 若要這樣做，請選擇 [**編輯**  >  **IntelliSense**  >  **移除] 和 [排序 using**]。

如需有關 using 設定的詳細資訊，請參閱 [ [排序 using](../ide/reference/sort-usings.md) ] 頁面。 如需 IntelliSense 的詳細資訊，請參閱 [Visual Studio 頁面中的 intellisense](../ide/using-intellisense.md) 。 而且，如需開發人員使用快速動作之一些一般方式的詳細資訊，請參閱 [一般快速動作](../ide/common-quick-actions.md) 頁面。

#### <a name="change-tracking"></a>變更追蹤

您可利用左邊界的色彩，追蹤在檔案中所做的變更。 色彩與您採取的動作有何關聯：

- 自檔案開啟但未儲存之後所做的變更，會以左邊界上的 **黃色** 橫條表示， (稱為選取範圍邊界) 。

    ![使用黃色橫條圖編輯程式碼編輯器](media/code-editor-edit-yellow.png "程式碼編輯器的螢幕擷取畫面，其中包含在選取範圍邊界內以黃色列標示的變更。")

- 儲存變更之後 (但在關閉檔案) 之前，會變成 **綠色**。

    ![以綠色橫條編輯程式碼編輯器](media/code-editor-edit-green.png "程式碼編輯器的螢幕擷取畫面，其中的變更在選取範圍邊界中標示為綠色橫條。")

若要關閉和開啟此功能，請在 **文字編輯器** 設定 (**工具**   >  **選項**  >  **文字編輯器**]) 中變更 [追蹤變更] 選項。

如需變更追蹤 &mdash; 以包含波浪線的詳細資訊 (也稱為「波浪線」 ) 出現在程式碼字串下， &mdash; 請參閱 [Visual Studio 程式碼編輯器頁面功能](../ide/writing-code-in-the-code-and-text-editor.md)的 **[編輯器功能](../ide/writing-code-in-the-code-and-text-editor.md#editor-features)** 一節。

#### <a name="right-click-context-menu"></a>以滑鼠右鍵按一下快顯功能表

當您在 XAML 程式碼編輯器中編輯程式碼時，您可以使用滑鼠右鍵內容功能表來存取數個功能。 在 Visual Studio IDE 中，大部分的功能都是通用的，有些則是使用程式碼編輯器以及設計視窗的特定功能。

![Visual Studio 2019 中 XAML 程式碼編輯器之滑鼠右鍵內容功能表的螢幕擷取畫面。](media/xaml-code-editor-right-click-menu.png)

以下是每個功能的用途以及其實用程度：

- **View Code** -開啟 [程式設計語言程式碼] 視窗，此視窗通常是預設視圖旁邊的索引標籤，其中包含 [設計] 視窗和 [XAML 程式碼編輯器]。
- **View Designer** -開啟包含設計視窗和 XAML 程式碼編輯器的預設視圖。  (如果您已在預設視圖中，則不會執行任何動作。 ) 
- **快速動作和重構** -重構、產生或以單一動作修改程式碼。 當您將滑鼠停留在程式碼上方時，您會在有快速動作或重構可用時看到燈泡圖示。 <br>另請參閱： [快速動作](../ide/quick-actions.md) 和 [重構程式碼](../ide/refactoring-in-visual-studio.md)。
- **重新命名 ...** -僅重新命名命名空間。 如果您沒有命名空間要重新命名，您會收到錯誤訊息，指出「只有命名空間前置詞可以重新命名」。
- **移除及排序命名空間** -移除未使用的命名空間，然後排序那些保留的命名空間。
- **查看定義** ：預覽類型的定義，而不需要離開編輯器中的目前位置。 <br>另請參閱[](../ide/go-to-and-peek-definition.md#peek-definition) ：[使用查看定義來查看定義和查看及編輯程式碼](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)。
- **移至 [定義** ]-導覽至類型或成員的來源，並在新的索引標籤中開啟結果。 <br>另請參閱： [移至定義](../ide/go-to-and-peek-definition.md#go-to-definition)。
- **環繞于 ...** -使用範圍語句程式碼片段，這會在選取的程式碼區塊周圍加入。 <br>另請參閱： [擴充程式碼片段和範圍語句程式碼片段](../ide/code-snippets.md#expansion-snippets-and-surround-with-snippets)。
- **插入** 程式碼片段-在游標位置插入程式碼片段。
- **剪** 下-一目了然
- **複製** -自我解釋
- **貼** 上-自我解釋
- **大綱** -展開和折迭程式碼區段。 <br>另請參閱： [大綱](../ide/outlining.md)。
- **原始檔控制** -將程式碼投稿的歷程記錄查看至開放原始碼存放庫。

### <a name="middle-pane-scroll-bar"></a>中間窗格、捲軸

捲軸可以執行超過程式碼的捲軸。 您也可以使用它來開啟另一個 [程式碼編輯器] 窗格。 而且，您可以使用捲軸，藉由新增批註或使用不同的顯示模式，來協助您更有效率地撰寫程式碼。

#### <a name="split-the-code-window"></a>分割程式碼視窗

在程式碼編輯器的捲軸中，右上方有一個 **分割** 按鈕。 當您選擇它時，可以開啟另一個程式碼編輯器窗格。 這項功能很有用，因為它們彼此獨立運作，因此您可以使用它們來處理不同位置的程式碼。

![顯示 Visual Studio 2019 中 XAML 程式碼編輯器中間窗格的螢幕擷取畫面，其中的 [分割] 按鈕會反白顯示在窗格的右上角。](media/code-editor-split-window-button.png)

For more information about how to split an editor window, see the [Manage editor windows](../ide/how-to-manage-editor-windows.md) page.

#### <a name="use-annotations-or-map-mode"></a>使用附注或地圖模式

您也可以變更捲軸的外觀，以及它所包含的其他功能。 例如，許多人喜歡將 *批註* 包含在捲軸中，以提供視覺提示，例如程式碼變更、中斷點、書簽、錯誤和插入號位置。

有些人很感謝使用 *地圖模式*，它會在捲軸上顯示縮圖中的程式程式碼。 在檔案中有很多程式碼的開發人員，可能會發現對應模式會比預設捲軸更有效地追蹤程式程式碼。

如需如何變更捲軸預設設定的詳細資訊，請參閱  [自訂捲軸](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md) 頁面。

## <a name="xaml-specific-features"></a>XAML 特定功能

大部分的下列功能在 Visual Studio IDE 中都是通用的，但其中某些功能已加入一些維度，讓 XAML 開發人員更容易撰寫程式碼。

### <a name="xaml-code-snippets"></a>XAML 程式碼片段

程式碼片段是可重複使用的程式碼區塊，您可以使用滑鼠右鍵操作功能表命令 **插入程式碼片段** 或鍵盤快速鍵 (**ctrl** + **K**、 **ctrl** + **X**) 的組合，在程式碼檔案中插入。 我們已增強 [IntelliSense](../ide/using-intellisense.md) ，使其支援顯示 XAML 程式碼片段，此程式碼片段適用于內建程式碼片段，以及您手動新增的任何自訂程式碼片段。 某些現成的 XAML 程式碼片段包括 `#region` 、、 `Column definition` `Row definition` 、 `Setter` 和 `Tag` 。

![XAML 程式碼編輯器與 XAML 程式碼片段選項顯示在 IntelliSense 中](media/xaml-code-snippets.png "XAML 程式碼編輯器的螢幕擷取畫面，其中包含在 IntelliSense 中顯示的 XAML 程式碼片段選項")

如需詳細資訊，請參閱 [程式碼片段](../ide/code-snippets.md) 和 [c # 程式碼片段](../ide/visual-csharp-code-snippets.md) 頁面。

### <a name="xaml-region-support"></a>XAML #region 支援

從 Visual Studio 2015 開始，我們為 WPF 和 UWP 中的 XAML 開發人員提供了 #region 的支援，而且在 [Xamarin](/xamarin/xamarin-forms/user-interface/text/editor/)中也有更新的支援。 在 Visual Studio 2019 中，我們會繼續對 #region 支援進行累加式改進。 例如，在 [16.4 版](/visualstudio/releases/2019/release-notes-v16.4/) 和更新版本中，#region 選項會在您開始輸入時顯示 `<!` 。

![XAML 程式碼編輯器，具有在 IntelliSense 中顯示 #region 選項](media/code-editor-xaml-region.png "XAML 程式碼編輯器的螢幕擷取畫面，其中包含以 IntelliSense 顯示的 #region 選項")

當您想要將您的程式碼區段群組在一起，而您也想要展開或折迭時，可以使用區域。

```xaml
    <!--#region NameOfRegion-->
    Your code is here
    <!--#endregion-->
```

如需區域的詳細資訊，請參閱 [#region (c # 參考) ](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region/) 頁面。 如需展開和折迭程式碼區段的詳細資訊，請參閱 [大綱](../ide/outlining.md) 頁面。

### <a name="xaml-comments"></a>XAML 批註

開發人員通常會偏好使用批註來記錄其程式碼。 您可以利用下列方式，將批註新增至 [ **MainWindow** ] 索引標籤中的 xaml 程式碼：

- 在 `<!--` 批註前面輸入，然後在 `-->` 批註後面加上。
- 輸入 `<!` `!--` 選項清單，然後從選項清單中選擇。

  ![XAML 程式碼編輯器以滑鼠右鍵按一下 [新增批註] 對話方塊](media/xaml-code-editor-comments.png "以滑鼠右鍵按一下內容功能表的螢幕擷取畫面，以在 XAML 程式碼編輯器中新增批註")

- 選取您要用來括住批註的程式碼，然後從 IDE 中的工具列選擇 [ **批註** ] 按鈕。 若要反轉動作，請選擇 [ **取消** 批註] 按鈕。

  ![IDE 工具列中的 [批註] 按鈕和 [取消批註] 按鈕](media/comment-undo-comment-buttons.png "IDE 工具列中 [批註] 按鈕和 [取消批註] 按鈕的螢幕擷取畫面")

- 選取您要用來括住批註的程式碼，然後按下 **ctrl** + **K**、 **ctrl** + **C**。 若要取消選取的程式碼，請按下 **ctrl** + **K**、 **ctrl** + **U**。

如需有關如何在 c # 程式碼中使用 [ **MainWindow** ] 索引標籤中批註的詳細資訊，請參閱 [檔批註](/dotnet/csharp/language-reference/language-specification/documentation-comments/) 頁面。

### <a name="xaml-lightbulbs"></a>XAML 燈泡

出現在 XAML 程式碼中的燈泡圖示，是您可以用來重構、產生或以其他方式修改程式碼的 [快速動作](../ide/quick-actions.md) 的一部分。

以下是一些範例，說明如何能讓您的 XAML 程式碼撰寫體驗受益：

- **移除不必要的命名空間**。 在 XAML 程式碼編輯器中，不必要的命名空間會以灰色文字顯示。 如果您將游標停留在不必要的情況下，將會出現燈泡。 當您從下拉式清單中選擇 [ **移除不必要的命名空間** ] 選項時，您會看到可移除的預覽。

  ![XAML 程式碼編輯器從快速動作燈泡移除不必要的命名空間選項](media/xaml-code-editor-dimmed-namespaces-preview.png "XAML 程式碼編輯器的 [移除不必要的命名空間] 選項的螢幕擷取畫面，此選項會使用 [快速動作] 燈泡顯示")

- **重新命名命名空間**。 這項功能可在您反白顯示命名空間之後，從滑鼠右鍵內容功能表中取得，讓您可以輕鬆地同時變更設定的多個實例。 您也可以使用功能表列、**編輯**  >  **重構**  >  **重新命名**，或是按下 **ctrl** + **r**，再按一次 **ctrl** r， + 來存取這項功能。

  ![以滑鼠右鍵按一下內容功能表中的 [XAML 程式碼編輯器] 的 [重新命名命名空間] 選項](media/code-editor-rename-namespace.png "XAML 程式碼編輯器的 [重新命名命名空間] 選項的螢幕擷取畫面，此選項使用滑鼠右鍵按一下內容功能表來顯示")

  如需詳細資訊，請參閱 [重新命名程式碼符號重構](../ide/reference/rename.md) 頁面。

### <a name="conditional-xaml-for-uwp"></a>UWP 的條件式 XAML

條件式 XAML 提供一種在 XAML 標記中使用 ApiInformation.IsApiContractPresent 方法的方式。 這可讓您在標記中根據 API 是否存在來設定屬性和具現化物件，而不必使用程式碼後置。

如需詳細資訊，請參閱 [條件式 xaml](/windows/uwp/debug-test-perf/conditional-xaml/) 頁面， [桌面應用程式中的主機 UWP XAML 控制項 (XAML 孤島) ](/windows/apps/desktop/modernize/xaml-islands/) 頁面。

### <a name="xaml-structure-visualizer"></a>XAML 結構視覺化

程式碼編輯器中的結構視覺化功能會顯示結構輔助線，這是垂直虛線，表示您程式碼中的開啟和關閉的標記元素相符。 這些垂直線可讓您更輕鬆地查看邏輯區塊的開始和結束位置。

如需詳細資訊，請參閱 [流覽程式碼](../ide/navigating-code.md) 頁面。

### <a name="intellicode-for-xaml"></a>XAML 的 IntelliCode

當您將 XAML 標記新增至您的程式碼時，通常會以左角括弧開頭 `<` 。 當您輸入角括弧時，會出現 [IntelliCode] 功能表，其中列出數個較熱門的 XAML 標記。 選擇您想要快速將它新增至程式碼的檔案。

您可以辨識 IntelliCode 選取專案，因為它們出現在清單頂端，並加星號。

![XAML 文字編輯器的 IntelliCode 清單](media/xaml-intellicode-selection.png "XAML 文字編輯器的 IntelliCode 清單螢幕擷取畫面")

如需詳細資訊，請參閱 IntelliCode 頁面的 [總覽](/visualstudio/intellicode/overview/) 。

### <a name="settings"></a>設定

如需 Visual Studio IDE 中 *所有* 設定的詳細資訊，請參閱程式 [代碼編輯器](../ide/writing-code-in-the-code-and-text-editor.md) 頁面的功能。

## <a name="xaml-optional-settings"></a>XAML 選擇性設定

您可以使用 [ [選項](../ide/reference/options-dialog-box-visual-studio.md) ] 對話方塊來變更 XAML 程式碼編輯器的預設設定。 若要查看設定，請選擇 [**工具**  >  **選項**  >  **文字編輯器**  >  **XAML**]。

![XAML 文字編輯器的選項清單](media/xaml-tools-options.png "XAML 文字編輯器選項清單的螢幕擷取畫面")

> [!NOTE]
> 您也可以使用鍵盤快速鍵來存取 [選項] 對話方塊。 方法如下：按 **Ctrl** + **Q** 搜尋 IDE、輸入 **選項**，然後按 **enter**。 接著，按 **下 Ctrl** + **E** 以搜尋 [選項] 對話方塊、**輸入文字編輯器**、按 **enter**、輸入 **XAML**，然後按 **enter**。
>
> 如需鍵盤快速鍵的詳細資訊，請參閱 Visual Studio 頁面的 [快捷方式提示](../ide/productivity-shortcuts.md#code-editor) 。

### <a name="universal-text-editor-options"></a>通用文字編輯器選項

在 XAML 的 [ [選項](../ide/reference/options-text-editor-xaml-formatting.md) ] 對話方塊中，下列前三個專案通用於 Visual Studio IDE 支援的所有程式設計語言。 請造訪下表中的連結資訊，以深入瞭解這些選項，以及如何使用這些選項。

|Name  |其他資訊  |
|---------|---------|
|一般  | [選項對話方塊：文字編輯器 > 所有語言](../ide/reference/options-text-editor-all-languages.md) |
|捲軸 | [選項、文字編輯器、所有語言、捲軸](../ide/reference/options-text-editor-all-languages-scroll-bars.md) |
|定位點  |  [索引標籤、所有語言、文字編輯器、選項](../ide/reference/options-text-editor-all-languages-tabs.md) |

### <a name="xaml-specific-text-editor-options"></a>XAML 特定的文字編輯器選項

下表列出 [ [選項](../ide/reference/options-text-editor-xaml-formatting.md) ] 對話方塊中的設定，當您開發以 XAML 為基礎的應用程式時，可以增強您的編輯體驗。 請流覽連結的資訊，以深入瞭解這些選項，以及如何使用這些選項。

|Name  |其他資訊  |
|---------|---------|
|格式化 | [選項、文字編輯器、XAML、格式化](../ide/reference/options-text-editor-xaml-formatting.md) |
|其他 |  [選項、文字編輯器、XAML、其他](../ide/reference/options-text-editor-xaml-miscellaneous.md) |

> [!TIP]
> [**其他**] 區段中的 [**大寫事件處理常式方法名稱**] 設定對 XAML 開發人員特別有用。 這項設定預設為 *關閉* ，因為這是新的，但我們建議您將它設為 *on* ，以在您的程式碼中支援適當的大小寫。

## <a name="next-steps"></a>下一步

若要深入瞭解如何在以偵測模式執行應用程式時，即時編輯您的程式碼，請參閱 [XAML 熱重新載入](xaml-hot-reload.md) 頁面。

## <a name="see-also"></a>另請參閱

- [Visual Studio 程式碼編輯器功能](../ide/writing-code-in-the-code-and-text-editor.md)
- [UWP 應用程式中的 XAML](/windows/uwp/xaml-platform/xaml-overview/)
- [Xamarin.Forms 應用程式中的 XAML](/xamarin/xamarin-forms/xaml/)
- [Xamarin 行動應用程式開發 (Mac) ](/visualstudio/mac/xamarin/)
- [適用于 Mac 的 Visual Studio 2019- (Mac) 的 IDE 導覽 ](/visualstudio/mac/ide-tour/)
