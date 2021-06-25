---
title: Visual Studio 的字型和格式 |Microsoft Docs
description: 瞭解您針對 Visual Studio 所設計之新功能的字型和格式，包括如何使用環境字型。
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e6e26b18c838fc240d7fab398f8626890eed0d31
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901678"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>適用於 Visual Studio 的字型和格式設定
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a> 環境字型
 Visual Studio 內的所有字型都必須向使用者公開，才能進行自訂。 這主要是透過 [**工具 > 選項**] 對話方塊中的 [字型 **和色彩**] 頁面完成。 字型設定的三個主要類別是：

- **環境字型** -IDE 的主要字型 (整合式開發環境) ，用於所有介面元素，包括對話方塊、功能表、工具視窗和文件視窗。 根據預設，環境字型會系結至在目前的 Windows 版本中顯示為 9 pt Segoe UI 的系統字型。 針對所有介面元素使用一個字型有助於確保整個 IDE 中的字型外觀一致。

- **文字編輯器** -在 [ **工具 > 選項**] 的 [文字編輯器] 頁面中，可以自訂程式碼和其他以文字為基礎之編輯器中的元素。

- **特定集合** -提供使用者介面專案自訂的設計工具視窗，可能會在 [ **工具] > 選項**] 的 [設定] 頁面中，公開其設計介面的特定字型。

### <a name="editor-font-customization-and-resizing"></a>編輯器字型自訂和調整大小
 使用者通常會根據其喜好設定（與一般使用者介面無關）來放大或縮放編輯器中的文字大小和（或）色彩。 由於環境字型是用於可能出現在編輯器/設計工具內或作為一部分的元素，因此當這些字型分類的其中一個變更時，請務必注意預期的行為。

 當您建立出現在編輯器中，但不是 *內容* 一部分的 UI 專案時，請務必使用環境字型，而不是文字字型，讓元素能以可預測的方式調整大小。

1. 針對編輯器中的程式碼文字，請使用程式碼文字字型設定來調整大小，並回應編輯器文字的縮放層級。

2. 介面的所有其他元素應系結至環境字型設定，並回應環境中的任何全域變更。 其中包括 (但不限於)：

    - 內容功能表中的文字

    - 編輯器裝飾中的文字，例如燈泡功能表文字、快速尋找編輯器窗格，然後流覽至窗格

    - 對話方塊中的標籤文字，例如檔案 **中尋找** 或 **重構**

### <a name="accessing-the-environment-font"></a>存取環境字型
 在原生或 WinForms 程式碼中，您可以在 `IUIHostLocale::GetDialogFont` 從服務查詢介面之後呼叫方法來存取環境字型 `SID_SUIHostLocale` 。

 針對 Windows Presentation Foundation (WPF) ，請從 shell 的類別衍生您的交談視窗類別， `DialogWindow` 而不是從 WPF 的類別 `Window` 。

 XAML 中的程式碼看起來像這樣：

```xaml
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>
```

程式碼後置於：

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

  (取代 `Microsoft.VisualStudio.Shell.11.0` 為目前的 MPF dll 版本。 ) 

 若要顯示對話方塊，請 `ShowModal()` 在類別上呼叫 "" `ShowDialog()` 。 `ShowModal()` 在 shell 中設定正確的強制回應狀態，以確保對話方塊在父視窗中置中，依此類推。

 程式碼如下所示：

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal` 傳回 bool？ 使用可為 null 的布林值)  (`DialogResult` ，可在需要時使用。 如果對話方塊以 **[確定**] 關閉，則傳回值為 true。

 如果您需要顯示不是對話方塊且裝載于其本身的 WPF UI （ `HwndSource` 例如快顯視窗或 Win32/WinForms 父視窗的 WPF 子視窗），您必須在 WPF 專案的 `FontFamily` `FontSize` 根項目上設定和。  (shell 會在主視窗上設定屬性，但是它們不會被繼承過 `HWND`) 。 Shell 提供可系結屬性的資源，如下所示：

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a> (調整/粗體) 參考的格式
 某些對話方塊要求特定文字必須是粗體或非環境字型的大小。 先前，大於環境字型的字型會編碼為「」 `environment font +2` 或類似。 使用提供的程式碼片段將會支援高 DPI 的監視器，並確保顯示文字一律會以正確的大小和權數顯示 (例如淺色或 Semilight 做) 。

> [!NOTE]
> 套用格式之前，請確定您遵循 [文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)中所找到的指引。 * *

 若要調整環境字型，請依指示設定 TextBlock 或標籤的樣式。 這些程式碼片段的每個正確使用都會產生正確的字型，包括適當的大小和權數變化。

 其中 " `vsui` " 是命名空間的參考 `Microsoft.VisualStudio.Shell` ：

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>375% 環境字型 + 淺色

**顯示為：** 34 Pt Segoe UI Light

::: moniker range="vs-2017"

**適用于：** (罕見) 唯一品牌的 UI，例如 [開始] 頁面

::: moniker-end

::: moniker range=">=vs-2019"

**適用于：** (罕見) 唯一品牌的 UI

::: moniker-end

程式性程式 **代碼：** 其中 `textBlock` 是先前定義的 TextBlock，而且 `label` 是先前定義的標籤：

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML：** 設定 TextBlock 或標籤的樣式，如下所示。

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>310% 環境字型 + 淺色
 **顯示為：** 28 Pt Segoe UI 淺色 **使用：** 大型特徵標記對話方塊標題、報表中的主要標題

 程式性程式 **代碼：** 其中 `textBlock` 是先前定義的 TextBlock，而且 `label` 是先前定義的標籤：

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML：** 設定 TextBlock 或標籤的樣式，如下所示。

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>200% 環境字型 + Semilight 做
 **顯示為：** 18 Pt Segoe UI semilight 做 **Use for：** 副標題、小型和中型對話方塊中的標題

 程式性程式 **代碼：** 其中 `textBlock` 是先前定義的 TextBlock，而且 `label` 是先前定義的標籤：

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML：** 設定 TextBlock 或標籤的樣式，如下所示：

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>155% 環境字型
 **顯示為：** 14 pt Segoe UI **適用于：** 檔妥善 UI 或報表中的區段標題

 程式性程式 **代碼：** 其中 `textBlock` 是先前定義的 TextBlock，而且 `label` 是先前定義的標籤：

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML：** 設定 TextBlock 或標籤的樣式，如下所示：

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>133% 環境字型
 **顯示為：** 12 Pt Segoe UI **用於：** 簽章對話方塊中較小的子標題，以及檔的適當 UI

 程式性程式 **代碼：** 其中 `textBlock` 是先前定義的 TextBlock，而且 `label` 是先前定義的標籤：

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML：** 設定 TextBlock 或標籤的樣式，如下所示：

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>122% 環境字型
 **顯示為：** 11 Pt Segoe UI **用於：** 簽章對話方塊中的區段標題、樹狀檢視中的最上層節點、垂直索引標籤流覽

 程式性程式 **代碼：** 其中 `textBlock` 是先前定義的 TextBlock，而且 `label` 是先前定義的標籤：

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML：** 設定 TextBlock 或標籤的樣式，如下所示：

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>環境字型 + 粗體
 **顯示為：** 粗體 9 Pt Segoe UI **用於：** 簽章對話方塊、報表和檔的 UI 中的標籤和 subheads

 程式性程式 **代碼：** 其中 `textBlock` 是先前定義的 TextBlock，而且 `label` 是先前定義的標籤：

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML：** 設定 TextBlock 或標籤的樣式，如下所示：

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>可當地語系化的樣式
 在某些情況下，當地語系化人員將需要修改不同地區設定的字型樣式，例如從東亞語言的文字中移除粗體。 若要對字型樣式進行當地語系化，則這些樣式必須在 .resx 檔案內。 在 [Visual Studio 表單設計工具] 中完成這項工作的最佳方式，以及仍然編輯字型樣式，是在設計階段明確設定字型樣式。 雖然這樣會建立完整字型物件，而且可能會中斷父字型的繼承，但是只有 FontStyle 屬性會用來設定字型。

 解決方法是將對話表單的事件連結在一起 `FontChanged` 。 在此 `FontChanged` 事件中，請流覽所有控制項，並檢查其字型是否已設定。 如果已設定，則會根據表單的字型和控制項的先前字型樣式，將其變更為新字型。 在程式碼中的範例如下：

```csharp
private void Form1_FontChanged(object sender, System.EventArgs e)
{
          SetFontStyles();
}

/// <summary>
/// SetFontStyles - This function will iterate all controls on a page
/// and recreate their font with the desired fontstyle.
/// It should be called in the OnFontChanged handler (and also in the constructor
/// in case the IUIService is not available so OnFontChange doesn't fire).
/// This way, when the VS shell font is given to us the controls that have
/// a different style for the font (bolded for example) will recreate their font
/// and use the VS shell font but with a style variation (bolded ...).
/// </summary>
protected void SetFontStyles()
{
     SetFontStyles(this, this, this.Font);
}

protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)
{
     foreach(Control c in parent.Controls)
     {
          if (c.Controls != null && c.Controls.Count > 0) {
               SetFontStyles(topControl, c, referenceFont);
          }
          if (c.Font != topControl.Font) {
               c.Font = new Font(referenceFont, c.Font.Style);
          }
     }
}
```

 使用此程式碼可保證當表單的字型更新時，控制項的字型也會更新。 您也應該從表單的函式呼叫這個方法，因為對話方塊可能無法取得的實例， `IUIService` 而且 `FontChanged` 永遠不會引發事件。 `FontChanged`即使對話方塊已經開啟，還是會讓對話方塊動態地取得新的字型。

### <a name="testing-the-environment-font"></a>測試環境字型
 為確保您的 UI 使用環境字型，並遵循大小設定，請開啟 [ **工具] > [選項] > 環境] > 字型和色彩** ，然後選取 [顯示設定：] 下拉式功能表底下的 [環境字型]。

 ![[工具 &gt; 選項] 對話方塊中的字型和色彩設定](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />[工具 &gt; 選項] 對話方塊中的字型和色彩設定

 將字型設定為與預設值非常不同的字型。 若要清楚指出哪個 UI 未更新，請選擇具有襯線的字型 (例如 "Times New Roman" ) 並設定非常大的大小。 然後測試您的 UI，以確保其遵迴圈境。 以下是使用 [授權] 對話方塊的範例：

 ![不遵守環境字型的 UI 文字範例](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />不遵守環境字型的 UI 文字範例

 在此情況下，「使用者資訊」和「產品資訊」不會遵守字型。 在某些情況下，這可能是明確的設計選擇，但如果未指定明確字型作為紅線規格的一部分，則可能會是錯誤。

 若要重設字型，請在 [工具 > 選項] 下，按一下 [使用預設值]， **> 環境 > 字型和色彩**。

## <a name="text-style"></a><a name="BKMK_TextStyle"></a> 文字樣式
 文字樣式指的是字型大小、粗細和大小寫。 如需執行指導方針，請參閱 [環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。

### <a name="text-casing"></a>文字大小寫

#### <a name="all-caps"></a>全部大寫
 請勿在 Visual Studio 中使用標題或標籤的全部大寫。

#### <a name="all-lowercase"></a>全部小寫
 請勿在 Visual Studio 的標題或標籤中使用全部小寫。

#### <a name="sentence-and-title-case"></a>句子和標題大小寫
 Visual Studio 中的文字應該使用標題案例或句子大小寫（視情況而定）。

|針對下列專案使用標題案例：|使用句子案例：|
|-------------------------|----------------------------|
|對話方塊標題|標籤|
|群組方塊|核取方塊|
|功能表項目|選項按鈕|
|操作功能表項目|清單方塊專案|
|按鈕|狀態列|
|資料表標籤||
|資料行標題||
|工具提示||

##### <a name="title-case"></a>字首大寫
 標題案例是一種樣式，其中片語中的最多或所有字組的第一個字母都是大寫。 在 Visual Studio 中，有許多專案使用標題案例，包括：

- **提示。** 範例：「預覽選取的專案」

- **資料行標頭。** 範例：「系統回應」

- **功能表項目。** 範例：「全部儲存」

  使用標題案例時，這些是要將字組大寫的時機，以及何時要讓它們保持小寫的指導方針：

|大寫|批註和範例|
|---------------|---------------------------|
|所有名詞||
|所有動詞命令|包含 "是" 和其他形式的 "to"|
|所有副詞|包含 "&" 和 "When"|
|所有形容詞|包括 "This" 和 "This"|
|所有代名詞|包括所有格「其」以及「它是」，縮減的代詞「it」和動詞「是」|
|第一個和最後一個字組，無論語音的各部分||
|屬於動詞片語一部分的介係詞|「關閉所有視窗」或「關閉系統」|
|縮寫的所有字母|HTML、XML、URL、IDE、RGB|
|複合單字中的第二個單字，如果是名詞或適當的形容詞，或單字的加權相等|交叉參考，預先 Microsoft 軟體，讀取/寫入存取，Run-Time|

|小寫|範例|
|---------------|--------------|
|複合單字中的第二個單字，如果是語音的另一個部分，或修改了第一個單字的分詞|How to、Take|
|文章，除非其中一個是標題中的第一個單字|a、an、the|
|座標結合|and、or、for、or 或|
|在動詞片語之外以四個或更少字母的文字介係詞|into、移至、移出|
|在不定片語中使用時的 "To"|「如何格式化硬碟」|

##### <a name="sentence-case"></a>句子案例
 句子大小寫是標準的大小寫方法，只要句子的第一個單字是大寫的，再加上任何適當的名詞和代詞的 "I" 即可。 一般情況下，句子案例較容易閱讀，尤其是當電腦將內容轉譯時。 使用句子案例：

1. **狀態列訊息。** 這些都是簡單、簡短且僅提供狀態資訊。 範例：「正在載入專案檔」

2. **所有其他 UI 元素**，包括標籤、核取方塊、選項按鈕和清單方塊專案。 範例：「選取清單中的所有專案」

### <a name="text-formatting"></a>文字格式
 Visual Studio 2013 中的預設文字格式是由 [環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)所控制。 這種服務可協助確保整個 IDE 中的一致字型外觀 (整合式開發環境) ，而且您必須使用它來確保使用者的一致體驗。

 Visual Studio 字型服務所使用的預設大小來自于 Windows，並顯示為 9 pt。

 您可以將格式套用至環境字型。 本主題涵蓋使用樣式的方式和位置。 如需執行資訊，請參閱 [環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。

#### <a name="bold-text"></a>粗體文字
 粗體文字會在 Visual Studio 中謹慎使用，應保留給：

- 在嚮導中的問題標籤

- 在方案總管中指定現用專案

- 屬性工具視窗中的覆寫值

- Visual Basic 編輯器下拉式清單中的特定事件

- 網頁檔大綱中的伺服器產生內容

- 複雜對話方塊或設計工具 UI 中的區段標頭

#### <a name="italics"></a>斜體
 Visual Studio 不會使用斜體或粗體的斜體文字。

#### <a name="color"></a>Color

- 藍色是針對 (流覽和命令) 的超連結所保留，絕對不能用於方向。

- 較大的標題 (環境字型 x 155% 或更高的) 可能會以下列用途為色彩：

  - 提供視覺效果吸引 Visual Studio UI 的簽章

  - 若要注意特定區域

  - 提供標準深色灰色/黑色環境文字色彩的降低

- 標題中的色彩應該利用現有的 Visual Studio 品牌色彩，主要是紫色的 #FF68217A。

- 在標題中使用色彩時，您必須遵守 [Windows 色彩指導方針](/windows/desktop/uxguide/vis-color)，包括對比比例和其他協助工具考慮。

### <a name="font-size"></a>字型大小
 Visual Studio UI 設計有更多空白字元的較淺外觀。 可能的話，已減少或移除 chrome 和標題列。 雖然資訊密度是 Visual Studio 的需求，但印刷樣式仍然很重要，並強調更多開放的行間距以及字型大小和權數的變化。

 下表包含 Visual Studio 中使用之顯示字型的設計詳細資料和視覺範例。 某些顯示字型的變化會將大小和粗細（例如 Semilight 做或淺色）編碼為其外觀。

 您可以在 [格式化 (縮放/粗體) 參考](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)中，找到所有顯示字型的執行程式碼片段。

#### <a name="375-environment-font--light"></a>375% 環境字型 + 淺色

|使用方式|外觀|
|-|-|
|**使用方式：** 罕見。 僅限唯一品牌的 UI。<br /><br /> **任務**<br /><br /> -使用句子大小寫<br />-一律使用輕量<br /><br /> **不要：**<br /><br /> -用於簽章 UI 以外的 UI，例如起始頁<br />-粗體、斜體或粗體斜體<br />-用於主體文字<br />-在工具視窗中使用|**顯示為：** 34 Pt Segoe UI Light<br /><br /> **Visual 範例：**<br /><br /> *目前未使用。可以在 Visual Studio 2017 起始頁中使用。*|

#### <a name="310-environment-font--light"></a>310% 環境字型 + 淺色

::: moniker range="vs-2017"

|使用方式|外觀|
|-|-|
|**使用方式：**<br /><br /> -簽章對話方塊中較大的標題<br />-主報表標題<br /><br /> **任務**<br /><br /> -使用句子大小寫<br />-一律使用輕量<br /><br /> **不要：**<br /><br /> -用於簽章 UI 以外的 UI，例如起始頁<br />-粗體、斜體或粗體斜體<br />-用於主體文字<br />-在工具視窗中使用|**顯示為：** 28 Pt Segoe UI 淺色<br /><br /> **Visual 範例：**<br /><br /> ![310% 環境字型 &#43; 淺色標題的範例](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|使用方式|外觀|
|-|-|
|**使用方式：**<br /><br /> -簽章對話方塊中較大的標題<br />-主報表標題<br /><br /> **任務**<br /><br /> -使用句子大小寫<br />-一律使用輕量<br /><br /> **不要：**<br /><br /> -用於簽章 UI 以外的 UI<br />-粗體、斜體或粗體斜體<br />-用於主體文字<br />-在工具視窗中使用|**顯示為：** 28 Pt Segoe UI 淺色<br /><br /> **Visual 範例：**<br /><br /> ![310% 環境字型 &#43; 淺色標題的範例](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200% 環境字型 + Semilight 做

|使用方式|外觀|
|-|-|
|**使用方式：**<br /><br /> -子標題<br />-小型和中型對話中的標題<br /><br /> **任務**<br /><br /> -使用句子大小寫<br />-一律使用 Semilight 做權數<br /><br /> **不要：**<br /><br /> -粗體、斜體或粗體斜體<br />-用於主體文字<br />-在工具視窗中使用|**顯示為：** 18 Pt Segoe UI Semillight<br /><br /> **Visual 範例：**<br /><br /> ![200% 環境字型 &#43; Semilight 做的範例](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>155% 環境字型

|使用方式|外觀|
|-|-|
|**使用方式：**<br /><br /> -檔妥善 UI 中的區段標題<br />-報表<br /><br /> **執行：** 使用句子大小寫<br /><br /> **不要：**<br /><br /> -粗體、斜體或粗體斜體<br />-用於主體文字<br />-在標準 Visual Studio 控制項中使用<br />-在工具視窗中使用|**顯示為：** 14 pt Segoe UI<br /><br /> **Visual 範例：**<br /><br /> ![155% 環境字型標題的範例](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>133% 環境字型

|使用方式|外觀|
|-|-|
|**使用方式：**<br /><br /> -簽章對話方塊中較小的子標題<br />-檔妥善 UI 中較小的子標題<br /><br /> **執行：** 使用句子大小寫<br /><br /> **不要：**<br /><br /> -粗體、斜體或粗體斜體<br />-用於主體文字<br />-在標準 Visual Studio 控制項中使用<br />-在工具視窗中使用|**顯示為：** 12 pt Segoe UI<br /><br /> **Visual 範例：**<br /><br /> ![133% 環境字型標題的範例](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>122% 環境字型

|使用方式|外觀|
|-|-|
|**使用方式：**<br /><br /> -簽章對話方塊中的區段標題<br />-樹狀檢視中的最上層節點<br />-垂直索引標籤流覽<br /><br /> **執行：** 使用句子大小寫<br /><br /> **不要：**<br /><br /> -粗體、斜體或粗體斜體<br />-用於主體文字<br />-在標準 Visual Studio 控制項中使用<br />-在工具視窗中使用|**顯示為：** 11 pt Segoe UI<br /><br /> **Visual 範例：**<br /><br /> ![122% 環境字型標題的範例](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>環境字型 + 粗體

|使用方式|外觀|
|-|-|
|**使用方式：**<br /><br /> -簽章對話方塊中的標籤和 subheads<br />-報表中的標籤和 subheads<br />-檔中的標籤和 subheads 正確 UI<br /><br /> **任務**<br /><br /> -使用句子大小寫<br />-使用粗體粗細<br /><br /> **不要：**<br /><br /> -斜體或粗體斜體<br />-用於主體文字<br />-在標準 Visual Studio 控制項中使用<br />-在工具視窗中使用|**顯示為：** 粗體 9 pt Segoe UI<br /><br /> **Visual 範例：**<br /><br /> ![環境字型 &#43; 粗體標題的範例](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>環境字型

|使用方式|外觀|
|-|-|
|**使用方式：** 所有其他文字<br /><br /> **執行：** 使用句子大小寫<br /><br /> **不要：** 斜體或粗體斜體|**顯示為：** 9 pt Segoe UI<br /><br /> **Visual 範例：**<br /><br /> ![環境字型的範例](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>填補和間距
 標題周圍需要有空格，以提供適當的強調。 此空間會根據點大小以及標題附近的其他內容而有所不同，例如水準規則或環境字型中的文字行。

- 標題本身的理想填補應該是大寫字元高度空間的90%。 例如，28 pt Segoe UI 淺色標題的最高寬度為 26 pt，而填補應大約 23 pt 或大約31圖元。

- 標題周圍的最小空間應該是大寫字元高度的50%。 當標題伴隨著規則或其他緊密調整的元素時，可能會使用較少的空間。

- 粗體的環境字型文字應遵循預設的線條高度間距和邊框距離。

## <a name="see-also"></a>另請參閱

- [Windows)  (字型 ](/windows/desktop/uxguide/vis-fonts)
- [消費者介面文字 (Windows) ](/windows/desktop/uxguide/text-ui)
