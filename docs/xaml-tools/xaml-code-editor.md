---
title: XAML 程式碼編輯器
ms.date: 06/16/2020
ms.topic: conceptual
monikerRange: vs-2019
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: d789ac099e6d0bba7a44f0d6efd7a19beec54c19
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290207"
---
# <a name="xaml-code-editor"></a>XAML 程式碼編輯器

[VISUAL STUDIO IDE](../get-started/visual-studio-ide.md)中的 XAML 程式碼編輯器包含建立適用于 Windows 平臺的 WPF 和 UWP 應用程式所需的所有工具，以及適用于[Xamarin](/xamarin/xamarin-forms/user-interface/text/editor/)的功能。 本文概述當您開發以 XAML 為基礎的應用程式時，程式碼編輯器所扮演的角色，以及 Visual Studio 2019 中 XAML 程式碼編輯器特有的功能。

首先，我們來看一下 IDE （整合式開發環境）與開放式 WPF 專案。 下圖顯示您將搭配 XAML 程式碼編輯器使用的幾個主要 IDE 工具。

:::image type="content" source="media/xaml-code-editor-overview-sml.png" alt-text="在 XAML 中使用 open WPF 專案的 Visual Studio 2019 IDE" lightbox="media/xaml-code-editor-overview-lrg.png":::

從影像的左下方以順時針方向，主要 IDE 工具如下所示：

- [ **[XAML 程式碼編輯器](#xaml-code-editor-ui)**] 視窗是本文的主旨， &mdash; &mdash; 您可以在其中建立和編輯您的程式碼。
- [ **[XAML 設計工具](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)**] 視窗，您可以在其中設計 UI。
- [**[工具箱](../ide/reference/toolbox.md)**] 可停駐視窗，您可以在其中將控制項加入至 UI。
- [ **[Debug](../debugger/debugger-feature-tour.md)** ] 按鈕，您可以在其中執行程式碼並加以調試。 <br>（您也可以在使用[XAML 熱重載](xaml-hot-reload.md)進行偵錯工具時，即時編輯您的程式碼）。
- [**[方案總管](../ide/solutions-and-projects-in-visual-studio.md)**] 視窗，您可以在其中管理檔案、專案和方案。
- [**[屬性](../ide/reference/properties-window.md)**] 視窗，您可以在其中變更 ui 的外觀，以及 ui 控制項的運作方式。

為了繼續進行，讓我們深入瞭解 XAML 程式碼編輯器。

## <a name="xaml-code-editor-ui"></a>XAML 程式碼編輯器 UI

雖然 XAML 應用程式的 [程式碼編輯器] 視窗共用一些也出現在標準 IDE 中的 UI （使用者介面）元素，但它也包含一些獨特的功能，可讓您更輕鬆地開發 XAML 應用程式。

以下是 XAML 程式碼編輯器視窗本身的外觀。

![中的 [XAML 程式碼編輯器] 視窗 Visual Studio](media/xaml-code-editor-window.png "Visual Studio 2019 中 XAML 程式碼編輯器視窗的螢幕擷取畫面")

接下來，我們來看一下程式碼編輯器中每個 UI 元素的功能。

### <a name="first-row"></a>第一個資料列

在 XAML 程式碼視窗頂端的第一個資料列中，左側有一個 [**設計**] 索引標籤、[**交換窗格**] 按鈕、[ **XAML** ] 索引標籤和 [快顯**xaml** ] 按鈕。

![Visual Studio 中 XAML 程式碼編輯器視窗的兩個頂端資料列的第一個，並反白顯示第一個資料列的左邊](media/xaml-code-editor-top-row-left.png "Visual Studio 2019 的 XAML 程式碼編輯器視窗中，第一個資料列的螢幕擷取畫面，左邊的 UI 元素會反白顯示")

其工作方式如下：

- [**設計**] 索引標籤會將焦點從 XAML 程式碼編輯器變更為 XAML 設計工具。
- [**交換窗格**] 按鈕會反轉 XAML 設計工具的位置和 IDE 中的 XAML 程式碼編輯器。
- [ **Xaml** ] 索引標籤會將焦點變更回 XAML 程式碼編輯器。
- [快顯**xaml** ] 按鈕會在 IDE 外部建立個別的 xaml 程式碼編輯器視窗。

從右邊繼續，有**垂直分割**按鈕、**水準分割**按鈕和折迭**窗格**按鈕。

![Visual Studio 中 XAML 程式碼編輯器視窗的兩個頂端資料列的第一個，並反白顯示第一個資料列的右側](media/xaml-code-editor-top-row-right.png "Visual Studio 2019 的 XAML 程式碼編輯器視窗中，第一個資料列的螢幕擷取畫面，右邊的 UI 元素會反白顯示")

其工作方式如下：

- [**垂直分割**] 按鈕會將 IDE 中的 XAML 設計工具和 XAML 程式碼編輯器的位置，從水準對齊變更為垂直對齊。
- **水準分割**按鈕會將 IDE 中 XAML 設計工具和 XAML 程式碼編輯器的位置從垂直對齊變更為水準對齊。
- [折迭**窗格]** 按鈕可讓您折迭底部窗格中的內容，不論這是程式碼編輯器或設計工具。 （若要還原底部窗格，請再次選擇相同的按鈕，這現在已命名為 [**展開窗格]** 按鈕）。

<!-- [!TIP]
> You can run two parallel instances of the XAML code editor concurrently by using both the **Pop Out XAML** button and the **Expand Pane** button.
>
> You might find it useful to have one larger window open that reveals more of your code in context and a smaller pane open that has its focus directly on the code that you're working on. -->

### <a name="second-row"></a>第二列

在 XAML 程式碼視窗頂端的第二列中，有兩個視窗下拉式清單。 不過，如果您看到這些 UI 元素的工具提示，它會進一步將其識別為「元素：視窗」和「成員：視窗」。

![Visual Studio 的 XAML 程式碼編輯器視窗中，兩個頂端的第二個數據列，其中兩個視窗下拉式清單都是可見的](media/xaml-code-editor-top-row-windows.png "Visual Studio 2019 的 XAML 程式碼編輯器視窗中，第二個數據列的螢幕擷取畫面，其中兩個視窗下拉式清單都是可見的")

[視窗] 下拉式清單具有不同的功能，如下所示：

- 左側的 [**元素：] 視窗**可協助您查看和導覽至同輩或父元素。

  具體來說，它會顯示類似大綱的視圖，讓您能夠顯示程式碼的標記結構。 當您從清單中選取時，程式碼編輯器中的焦點會貼齊包含您所選取之元素的程式程式碼。

    ![Visual Studio 中的 [元素：視窗] 下拉式清單](media/xaml-element-window-dropdown.png "Visual Studio 2019 中 [元素：視窗] 下拉式清單的螢幕擷取畫面")

- 右側的 [**成員：] 視窗**可協助您查看和導覽至屬性或子專案。

    具體來說，它會顯示您程式碼中的屬性清單。 當您從清單中選取時，程式碼編輯器中的焦點會貼齊包含所選屬性的程式程式碼。

    ![Visual Studio 中的 [成員：視窗] 下拉式清單](media/xaml-member-window-dropdown.png "Visual Studio 2019 中 [成員：視窗] 下拉式清單的螢幕擷取畫面")

### <a name="middle-pane-code-editor"></a>中間窗格，程式碼編輯器

中間窗格是 XAML 程式碼編輯器的 "code" 部分。 其中包含您可以在[IDE 程式碼編輯器](../get-started/tutorial-editor.md)中找到的大部分功能。 我們將接觸數個可協助您開發 XAML 程式碼的通用 IDE 功能。 我們也會反白顯示 IDE 中的獨特 XAML 功能。

![XAML 程式碼編輯器（僅限中間窗格），位於 Visual Studio](media/xaml-code-editor-middle.png "XAML 程式碼編輯器的螢幕擷取畫面，僅限中間窗格，Visual Studio 2019")

#### <a name="quick-actions"></a>快速動作

您可以使用[快速動作](../ide/quick-actions.md)，以單一動作重構、產生或修改程式碼。

例如，您可以使用 [快速動作] 執行的一個有用工作，就是從 [ **MainWindow.xaml.cs** ] 索引標籤中的 c # 程式碼**移除不必要的 using** 。

方法：

1. 將滑鼠停留在 using 語句上，選擇燈泡圖示，然後從下拉式清單中選擇 [**移除不必要的 using** ]。

    ![IDE 編輯器的 [快速動作] 功能表中的 [移除不必要的 Using] 選項](media/xaml-code-editor-remove-usings.png "[快速動作] 功能表中 IDE 編輯器的 [移除不必要的 Using] 選項的螢幕擷取畫面")

1. 選擇是否要修正**檔**、**專案**或**方案**中的所有出現次數。
1. 查看 [**預覽**] 對話方塊，**然後選擇 [** 套用]。

您也可以從功能表列存取這項功能。 若要這麼做，請選擇 [**編輯**] [IntelliSense] [  >  **IntelliSense**  >  **移除並排序 using**]。

如需有關 using 設定的詳細資訊，請參閱[排序 using](../ide/reference/sort-usings.md)頁面。 如需 IntelliSense 的詳細資訊，請參閱[Visual Studio 頁面中的 intellisense](../ide/using-intellisense.md) 。 而且，如需開發人員使用快速動作之一些一般方式的詳細資訊，請參閱[一般的快速動作](../ide/common-quick-actions.md)頁面。

#### <a name="change-tracking"></a>Change tracking

您可利用左邊界的色彩，追蹤在檔案中所做的變更。 以下是色彩與您所採取之動作的關聯：

- 您在開啟檔案但未儲存檔案之後所做的變更，會以左邊界上的**黃色**橫條表示（也稱為選取範圍邊界）。

    ![以黃色橫條編輯程式碼編輯器](media/code-editor-edit-yellow.png "[程式碼編輯器] 的螢幕擷取畫面，其中包含在選取範圍邊界中以黃色列標示的變更。")

- 儲存變更之後（但在關閉檔案之前），橫條會變成**綠色**。

    ![[程式碼編輯器] 以綠色橫條編輯](media/code-editor-edit-green.png "[程式碼編輯器] 的螢幕擷取畫面，其中具有在選取範圍邊界中以綠色列標示的變更。")

若要關閉和開啟這項功能，請變更**文字編輯器**設定中的 [**追蹤變更**] 選項（[**工具**] [選項] [  >  **Options**  >  **文字編輯器**]）。

如需有關變更追蹤 &mdash; 以包含出現在 [程式碼字串] 底下之波浪線（也稱為 "波浪線"）的詳細資訊， &mdash; 請參閱[[Visual Studio 程式碼編輯器](../ide/writing-code-in-the-code-and-text-editor.md)] 頁面之功能的**[編輯器功能](../ide/writing-code-in-the-code-and-text-editor.md#editor-features)** 一節。

#### <a name="right-click-context-menu"></a>以滑鼠右鍵按一下快顯功能表

當您在 XAML 程式碼編輯器中編輯程式碼時，您可以使用滑鼠右鍵內容功能表來存取數個功能。 大部分的這些功能在 Visual Studio IDE 中都是通用的，而有些則是使用程式碼編輯器和設計視窗所特有。

![XAML 程式碼編輯器的滑鼠右鍵內容功能表，位於 Visual Studio](media/xaml-code-editor-right-click-menu.png "XAML 程式碼編輯器的螢幕擷取畫面，以滑鼠右鍵按一下 Visual Studio 2019 中的快顯功能表")

以下是每項功能的作用和其有用之處：

- **View Code** -開啟程式設計語言程式碼視窗，這通常是預設視圖旁的索引標籤，其中包含 [設計] 視窗和 [XAML 程式碼編輯器]。
- **視圖設計**工具-開啟包含 [設計] 視窗和 [XAML 程式碼編輯器] 的預設視圖。 （如果您已經在預設的視圖中，則不會執行任何操作）。
- **快速動作和重構**-重構、產生，或使用單一動作修改程式碼。 當您將滑鼠停留在程式碼上時，您會在快速動作或重整可供使用時看到燈泡圖示。 <br>另請參閱：[快速動作](../ide/quick-actions.md)和[重構程式碼](../ide/refactoring-in-visual-studio.md)。
- **重新命名 ...**-僅重新命名命名空間。 如果您沒有命名空間可重新命名，您會收到錯誤訊息，指出「只有命名空間前置詞可以重新命名。」
- **移除及排序命名空間**-移除未使用的命名空間，然後排序保留的命名空間。
- **查看定義**-預覽類型的定義，而不將目前的位置保留在編輯器中。 <br>另請參閱：查看[定義](../ide/go-to-and-peek-definition.md#peek-definition)和[使用查看定義來查看和編輯程式碼](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)。
- **移至定義**-流覽至類型或成員的來源，並在新的索引標籤中開啟結果。 <br>另請參閱：[移至定義](../ide/go-to-and-peek-definition.md#go-to-definition)。
- **括住 ...**-使用範圍語句程式碼片段，在選取的程式碼區塊前後加入。 <br>請參閱：[展開程式碼片段和範圍語句程式碼片段](../ide/code-snippets.md#expansion-snippets-and-surround-with-snippets)。
- **插入片段**-在游標位置插入程式碼片段。
- **剪**下一目了然
- **複製**-自我理解
- **貼**上-自我理解
- **大綱**-展開和折迭程式碼區段。 <br>另請參閱：[大綱](../ide/outlining.md)。
- **原始檔控制**-在開放原始碼存放庫中查看程式碼投稿的歷程記錄。

### <a name="middle-pane-scroll-bar"></a>中間窗格、捲軸

捲軸可以執行超過程式碼的動作。 您也可以使用它來開啟另一個 [程式碼編輯器] 窗格。 而且，您可以使用捲軸來協助您更有效率地撰寫程式碼，方法是在其中加入批註，或使用不同的顯示模式。

#### <a name="split-the-code-window"></a>分割程式碼視窗

在程式碼編輯器的捲軸中，右上方有一個 [**分割**] 按鈕。 當您選擇它時，可以開啟另一個 [程式碼編輯器] 窗格。 這項功能很有用，因為它們彼此獨立運作，因此您可以使用它們來處理不同位置的程式碼。

![XAML 程式碼編輯器（僅限中間窗格），位於 Visual Studio](media/code-editor-split-window-button.png "XAML 程式碼編輯器的螢幕擷取畫面，僅限中間窗格，Visual Studio 2019")

如需如何分割編輯器視窗的詳細資訊，請參閱[管理編輯器 windows](../ide/how-to-manage-editor-windows.md)頁面。

#### <a name="use-annotations-or-map-mode"></a>使用批註或對應模式

您也可以變更捲軸的外觀，以及它所包含的其他功能。 例如，許多人喜歡在捲軸中包含*批註*，其中提供了視覺提示，例如程式碼變更、中斷點、書簽、錯誤和插入號位置。

其他人歡迎使用*地圖模式*，這會以縮圖顯示捲軸上的程式程式碼。 在檔案中有大量程式碼的開發人員，可能會發現對應模式比預設捲軸更有效率地追蹤程式程式碼。

如需如何變更捲軸之預設設定的詳細資訊，請參閱[自訂捲軸](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)頁面。

## <a name="xaml-specific-features"></a>XAML 特定功能

大部分的下列功能在 Visual Studio IDE 中都是通用的，但是有一些可讓 XAML 開發人員更容易撰寫程式碼的維度。

### <a name="xaml-code-snippets"></a>XAML 程式碼片段

程式碼片段是可重複使用的程式碼區塊，您可以使用滑鼠右鍵操作功能表命令 [**插入程式碼片段**] 或鍵盤快速鍵（**ctrl** + **K**、 **ctrl** + **X**）的組合，在程式碼檔案中插入。 我們已增強[IntelliSense](../ide/using-intellisense.md) ，使其支援顯示 XAML 程式碼片段，這適用于內建程式碼片段和您手動新增的任何自訂程式碼片段。 一些現成的 XAML 程式碼片段包括 `#region` 、 `Column definition` 、 `Row definition` 、 `Setter` 和 `Tag` 。

![XAML 程式碼編輯器，並在 IntelliSense 中顯示 #region 選項](media/xaml-code-snippets.png "XAML 程式碼編輯器的螢幕擷取畫面，其中包含在 IntelliSense 中顯示的 #region 選項")

如需詳細資訊，請參閱[程式碼片段](../ide/code-snippets.md)和[c # 程式碼片段](../ide/visual-csharp-code-snippets.md)頁面。

### <a name="xaml-region-support"></a>XAML #region 支援

從 Visual Studio 2015 開始，我們為 WPF 和 UWP 中的 XAML 開發人員提供了 #region 支援，而且最近也會在[Xamarin](/xamarin/xamarin-forms/user-interface/text/editor/)中使用。 在 Visual Studio 2019 中，我們會繼續對 #region 支援進行增量改善。 例如，在[16.4 版](/visualstudio/releases/2019/release-notes-v16.4/)和更新版本中，當您開始輸入時，#region 選項會顯示 `<!` 。

![XAML 程式碼編輯器，並在 IntelliSense 中顯示 #region 選項](media/code-editor-xaml-region.png "XAML 程式碼編輯器的螢幕擷取畫面，其中包含在 IntelliSense 中顯示的 #region 選項")

當您想要將您的程式碼區段分組也想要展開或折迭時，可以使用區域。

```xaml
    <!--#region NameOfRegion-->
    Your code is here
    <!--#endregion-->
```

如需區域的詳細資訊，請參閱[#region （c # 參考）](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region/)頁面。 如需展開和折迭程式碼區段的詳細資訊，請參閱[大綱](../ide/outlining.md)頁面。

### <a name="xaml-comments"></a>XAML 批註

開發人員通常偏好使用批註來記錄其程式碼。 您可以透過下列方式，將批註新增至 [ **mainwindow.xaml** ] 索引標籤中的 XAML 程式碼：

- 在 `<!--` 批註前面輸入，然後在 `-->` 批註後面新增。
- 輸入 `<!` ，然後 `!--` 從選項清單中選擇。

  ![XAML 程式碼編輯器以滑鼠右鍵按一下 [加入批註] 對話方塊](media/xaml-code-editor-comments.png "滑鼠右鍵操作功能表的螢幕擷取畫面，用來在 XAML 程式碼編輯器中加入批註")

- 選取您想要用來括住批註的程式碼，然後從 IDE 中的工具列選擇 [**批註**] 按鈕。 若要反轉動作，請選擇 [**取消**批註] 按鈕。

  ![IDE 工具列中的 [批註] 按鈕和 [取消批註] 按鈕](media/comment-undo-comment-buttons.png "[批註] 按鈕的螢幕擷取畫面和 IDE 工具列中的 [取消批註] 按鈕")

- 選取您想要用來括住批註的程式碼，然後按**ctrl** + **K**、 **ctrl** + **C**。 若要取消批註選取的程式碼，請按**ctrl** + **K**、 **ctrl** + **U**。

如需如何在 [ **MainWindow.xaml.cs** ] 索引標籤的 c # 程式碼中使用批註的詳細資訊，請參閱[檔批註](/dotnet/csharp/language-reference/language-specification/documentation-comments/)頁面。

### <a name="xaml-lightbulbs"></a>XAML 燈泡

出現在 XAML 程式碼中的燈泡圖示是[快速動作](../ide/quick-actions.md)的一部分，可供您用來重構、產生或修改程式碼。

以下是幾個範例，說明如何讓您的 XAML 程式碼撰寫體驗受益：

- **移除不必要的命名空間**。 在 XAML 程式碼編輯器中，不必要的命名空間會以灰色文字顯示。 如果您將游標暫留在不必要的 using，燈泡就會出現。 當您從下拉式清單中選擇 [**移除不必要的命名空間**] 選項時，您會看到可移除的預覽。

  ![XAML 程式碼編輯器的 [從快速動作燈泡移除不必要的命名空間] 選項](media/xaml-code-editor-dimmed-namespaces-preview.png "螢幕擷取畫面： XAML 程式碼編輯器的 [移除不必要的命名空間] 選項會使用 [快速動作] 燈泡顯示")

- **重新命名命名空間**。 這項功能可從滑鼠右鍵操作功能表中反白顯示命名空間之後取得，讓您可以輕鬆地一次變更設定的多個實例。 您也可以使用功能表列、**編輯**  >  **重構**  >  **重新命名**，或按**ctrl** + **r**，然後再按一次**ctrl** + **r** ，來存取這項功能。

  ![滑鼠右鍵內容功能表中的 XAML 程式碼編輯器的 [重新命名命名空間] 選項](media/code-editor-rename-namespace.png "使用滑鼠右鍵操作功能表顯示之 XAML 程式碼編輯器的 [重新命名命名空間] 選項的螢幕擷取畫面")

  如需詳細資訊，請參閱[重新命名程式碼符號重構](../ide/reference/rename.md)頁面。

### <a name="conditional-xaml-for-uwp"></a>UWP 的條件式 XAML

條件式 XAML 提供一種在 XAML 標記中使用 ApiInformation.IsApiContractPresent 方法的方式。 這可讓您在標記中根據 API 是否存在來設定屬性和具現化物件，而不必使用程式碼後置。

如需詳細資訊，請參閱[條件式 XAML](/windows/uwp/debug-test-perf/conditional-xaml/)頁面和[桌面應用程式中的主機 UWP XAML 控制項（XAML Islands）](/windows/apps/desktop/modernize/xaml-islands/)頁面。

### <a name="xaml-structure-visualizer"></a>XAML 結構視覺化

[程式碼編輯器] 中的 [結構視覺化] 功能會顯示結構輔助線，這是垂直虛線，表示程式碼中符合的開啟和關閉標記專案。 這些垂直線可讓您更輕鬆地查看邏輯區塊的開始和結束位置。

如需詳細資訊，請參閱[流覽程式碼](../ide/navigating-code.md)頁面。

### <a name="intellicode-for-xaml"></a>適用于 XAML 的 IntelliCode

當您將 XAML 標記新增至程式碼時，通常會以左角括弧開頭 `<` 。 當您輸入該角括弧時，會出現 [IntelliCode] 功能表，其中列出數個較常用的 XAML 標記。 選擇您想要快速將其新增至程式碼的帳戶。

您可以辨識 IntelliCode 的選擇，因為它們會出現在清單的頂端，而且是加星號。

![XAML 文字編輯器的 IntelliCode 清單](media/xaml-intellicode-selection.png "XAML 文字編輯器的 IntelliCode 清單螢幕擷取畫面")

如需詳細資訊，請參閱 IntelliCode 頁面的[總覽](/visualstudio/intellicode/overview/)。

### <a name="settings"></a>設定

如需 Visual Studio IDE 中*所有*設定的詳細資訊，請參閱[[程式碼編輯器](../ide/writing-code-in-the-code-and-text-editor.md)] 頁面的 [功能]。

## <a name="xaml-optional-settings"></a>XAML 選擇性設定

您可以使用 [[選項](../ide/reference/options-dialog-box-visual-studio.md)] 對話方塊來變更 XAML 程式碼編輯器的預設設定。 若要查看設定，請選擇 [**工具**] [選項] [  >  **Options**  >  **文字編輯器**  >  **XAML**]。

![XAML 文字編輯器的選項清單](media/xaml-tools-options.png "XAML 文字編輯器選項清單的螢幕擷取畫面")

> [!NOTE]
> 您也可以使用鍵盤快速鍵來存取 [選項] 對話方塊。 做法如下：按**Ctrl** + **Q**搜尋 IDE、輸入**Options**，然後按**enter**。 接下來，按**Ctrl** + **E**搜尋 [選項] 對話方塊，輸入**文字編輯器**，按**enter**，輸入**XAML**，然後按**enter**。
>  
> 如需有關鍵盤快速鍵的詳細資訊，請參閱[Visual Studio 的快捷方式秘訣](../ide/productivity-shortcuts.md#code-editor)頁面。

### <a name="universal-text-editor-options"></a>通用文字編輯器選項

在 XAML 的 [[選項](../ide/reference/options-text-editor-xaml-formatting.md)] 對話方塊中，下列前三個專案通用於 Visual Studio IDE 支援的所有程式設計語言。 請流覽下表中的連結資訊，以深入瞭解這些選項和使用方式。

|Name  |其他資訊  |
|---------|---------|
|一般  | [選項對話方塊：文字編輯器 > 所有語言](../ide/reference/options-text-editor-all-languages.md) |
|捲軸 | [選項、文字編輯器、所有語言、捲軸](../ide/reference/options-text-editor-all-languages-scroll-bars.md) |
|定位點  |  [索引標籤、所有語言、文字編輯器、選項](../ide/reference/options-text-editor-all-languages-tabs.md) |

### <a name="xaml-specific-text-editor-options"></a>XAML 特定的文字編輯器選項

下表列出在您開發 XAML 應用程式時，可增強編輯體驗的 [[選項](../ide/reference/options-text-editor-xaml-formatting.md)] 對話方塊中的設定。 請造訪連結的資訊，以深入瞭解這些選項及其使用方式。

|Name  |其他資訊  |
|---------|---------|
|格式化 | [選項、文字編輯器、XAML、格式化](../ide/reference/options-text-editor-xaml-formatting.md) |
|其他 |  [選項、文字編輯器、XAML、其他](../ide/reference/options-text-editor-xaml-miscellaneous.md) |

> [!TIP]
> [**其他**] 區段中的 [**大寫事件處理常式方法名稱**] 設定對於 XAML 開發人員而言特別有用。 這項設定預設為*關閉*，因為它是新的，但我們建議您將它設定為*on* ，以在程式碼中支援適當的大小寫。

## <a name="next-steps"></a>後續步驟

若要深入瞭解如何在以「偵測模式」執行應用程式時，即時編輯程式碼，請參閱[XAML 熱重載](xaml-hot-reload.md)頁面。

## <a name="see-also"></a>另請參閱

- [Visual Studio 程式碼編輯器功能](../ide/writing-code-in-the-code-and-text-editor.md)
- [UWP 應用程式中的 XAML](/windows/uwp/xaml-platform/xaml-overview/)
- [Xamarin.Forms 應用程式中的 XAML](/xamarin/xamarin-forms/xaml/)
- [Xamarin 行動應用程式開發（Mac）](/visualstudio/mac/xamarin/)
- [適用于 Mac 的 Visual Studio 2019-IDE 導覽（Mac）](/visualstudio/mac/ide-tour/)
