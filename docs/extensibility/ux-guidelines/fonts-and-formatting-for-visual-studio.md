---
title: Visual Studio 的字型和格式 |Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd2e8a41ef4b9708df079e94bcac8b8c06189116
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536106"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>適用於 Visual Studio 的字型和格式設定
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a>環境字型
 Visual Studio 內的所有字型都必須公開給使用者進行自訂。 這主要是透過 [**工具] > [選項**] 對話方塊中的 [字型**和色彩**] 頁面來完成。 字型設定的三個主要類別為：

- **環境字型**-IDE （整合式開發環境）的主要字型，用於所有介面元素，包括對話方塊、功能表、工具視窗和文件視窗。 根據預設，環境字型會系結至目前 Windows 版本中顯示為 9 pt Segoe UI 的系統字型。 所有介面元素都使用一個字型，有助於確保整個 IDE 都具有一致的字型外觀。

- **文字編輯器**-可以在 [**工具] > 選項**] 的 [文字編輯器] 頁面中，自訂以程式碼和其他以文字為基礎之編輯器中的元素。

- **特定集合**-提供使用者自訂其介面專案的設計工具視窗，可能會在 [**工具] > 選項**] 的 [設定] 頁面中，公開其設計介面特有的字型。

### <a name="editor-font-customization-and-resizing"></a>編輯自訂字型和調整大小
 使用者通常會根據其喜好設定來放大或縮放編輯器中的文字大小和（或）色彩，而與一般使用者介面無關。 因為環境字型是在可能出現在編輯器/設計工具中或做為一部分的元素上使用，所以當其中一個字型分類變更時，請務必注意預期的行為。

 建立出現在編輯器中但不屬於*內容*一部分的 UI 專案時，請務必使用環境字型，而不是文字字型，讓元素以可預測的方式調整大小。

1. 針對編輯器中的程式碼文字，使用 [程式碼文字] 字型設定來調整大小，並回應編輯器文字的縮放層級。

2. 介面的所有其他元素都應該系結至環境字型設定，並回應環境中的任何全域變更。 這包括（但不限於）：

    - 內容功能表中的文字

    - 編輯器裝飾中的文字，例如燈泡功能表文字、快速尋找編輯器窗格，以及流覽至窗格

    - 在對話方塊中標記文字，例如**在**檔案中尋找或**重構**

### <a name="accessing-the-environment-font"></a>存取環境字型
 在原生或 WinForms 程式碼中，您可以在 `IUIHostLocale::GetDialogFont` 從服務中查詢介面之後呼叫方法來存取環境字型 `SID_SUIHostLocale` 。

 若是 Windows Presentation Foundation （WPF），請從 shell 的 `DialogWindow` 類別（而不是 wpf 的類別）衍生您的交談視窗類別 `Window` 。

 在 XAML 中，程式碼看起來像這樣：

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

程式碼後置：

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 （ `Microsoft.VisualStudio.Shell.11.0` 以 MPF dll 的目前版本取代。）

 若要顯示對話方塊，請呼叫 `ShowModal()` 類別上的 "" `ShowDialog()` 。 `ShowModal()`在 shell 中設定正確的強制回應狀態，確保對話方塊會在父視窗中置中，依此類推。

 程式碼如下所示：

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal`傳回 bool？ （可為 null 的布林值） `DialogResult` ，包含，可在需要時使用。 如果對話方塊已關閉但有 **[確定**]，則傳回值為 true。

 如果您需要顯示一些不是對話方塊且裝載于其本身的 WPF UI （ `HwndSource` 例如，快顯視窗或 Win32/WinForms 父視窗的 WPF 子視窗），您必須在 `FontFamily` `FontSize` WPF 元素的根項目上設定和。 （Shell 會在主視窗上設定屬性，但不會繼承過去 `HWND` ）。 Shell 會提供可系結屬性的資源，如下所示：

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a>格式化（縮放/粗體）參考
 有些對話方塊需要特定文字為粗體，或是環境字型以外的大小。 先前，大於環境字型的字體會編碼為 " `environment font +2` " 或類似。 使用提供的程式碼片段將支援高 DPI 監視器，並確保顯示文字一律會以正確的大小和粗細（例如光源或 Semilight 做）顯示。

> [!NOTE]
> 套用格式之前，請確定您遵循的是[文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)中的指引。 * *

 若要調整環境字型，請依指示設定 TextBlock 或標籤的樣式。 這些程式碼片段的每個正確使用，都會產生正確的字型，包括適當的大小和權數變化。

 其中 " `vsui` " 是命名空間的參考 `Microsoft.VisualStudio.Shell` ：

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>375% 環境字型 + 淺色

**顯示為：** 34 Pt Segoe UI Light

::: moniker range="vs-2017"

用於 **：** （罕見）唯一品牌的 UI，例如起始頁中的

::: moniker-end

::: moniker range=">=vs-2019"

用於 **：** （罕見）唯一品牌的 UI

::: moniker-end

程式性程式**代碼：** 其中 `textBlock` 是先前定義的 TextBlock，而 `label` 是先前定義的標籤：

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
 **顯示為：** 28 Pt Segoe UI 輕用於 **：** 大型簽章對話方塊標題，報表中的主要標題

 程式性程式**代碼：** 其中 `textBlock` 是先前定義的 TextBlock，而 `label` 是先前定義的標籤：

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
 **顯示為：** 18 Pt Segoe UI semilight 做用於：子標題、小型和中型對話方塊中**的**標題

 程式性程式**代碼：** 其中 `textBlock` 是先前定義的 TextBlock，而 `label` 是先前定義的標籤：

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
 在檔功能良好的 UI 或報表中，**顯示為：** 14 pt Segoe UI 用於 **：** 區段標題

 程式性程式**代碼：** 其中 `textBlock` 是先前定義的 TextBlock，而 `label` 是先前定義的標籤：

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
 **顯示為：** 12 Pt Segoe UI**用於：** 簽章對話方塊中較小的子標題和檔良好的 UI

 程式性程式**代碼：** 其中 `textBlock` 是先前定義的 TextBlock，而 `label` 是先前定義的標籤：

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
 **顯示為：** 11 Pt Segoe UI**用於：** 簽章對話方塊中的區段標題、樹狀檢視中的前幾個節點、垂直索引標籤導覽

 程式性程式**代碼：** 其中 `textBlock` 是先前定義的 TextBlock，而 `label` 是先前定義的標籤：

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
 **顯示為：** 粗體 9 pt Segoe UI 用於：簽章對話方塊、報表和檔良好 UI 中**的**標籤和 subheads

 程式性程式**代碼：** 其中 `textBlock` 是先前定義的 TextBlock，而 `label` 是先前定義的標籤：

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
 在某些情況下，當地語系化人員將需要修改不同地區設定的字型樣式，例如從東亞語言的文字中移除 [粗體]。 為了能夠當地語系化字型樣式，這些樣式必須在 .resx 檔案中。 在 [Visual Studio 表單設計工具] 中完成這項工作並繼續編輯字型樣式的最佳方式，就是在設計階段明確設定字型樣式。 雖然這會建立完整的字型物件，而且看起來可能會中斷父字型的繼承，但是只會使用 FontStyle 屬性來設定字型。

 解決方法是攔截對話表單的 `FontChanged` 事件。 在 `FontChanged` 事件中，請流覽所有控制項，並檢查其字型是否已設定。 如果已設定，請根據表單的字型和控制項的上一個字型樣式，將它變更為新字型。 在程式碼中的範例如下：

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

 使用此程式碼可確保當表單的字型更新時，控制項的字型也會一併更新。 這個方法也應該從表單的「函式」呼叫，因為對話可能無法取得的實例 `IUIService` ，而且 `FontChanged` 永遠不會引發事件。 `FontChanged`如果對話方塊已開啟，則會允許對話動態地取得新的字型。

### <a name="testing-the-environment-font"></a>測試環境字型
 為確保您的 UI 使用環境字型，並遵循大小設定，請開啟 [**工具] > 選項 > 環境 > 字型和色彩**]，然後選取 [顯示設定：] 下拉式功能表底下的 [環境字型]。

 ![[工具 &gt; 選項] 對話方塊中的字型和色彩設定](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />[工具 &gt; 選項] 對話方塊中的字型和色彩設定

 將字型設定為與預設值非常不同的內容。 若要讓它顯而易見，哪個 UI 不會更新，請選擇具有襯線的字型（例如「Times New Roman」）並設定非常大的大小。 然後測試您的 UI，以確保其遵迴圈境。 以下是使用 [授權] 對話方塊的範例：

 ![不遵守環境字型的 UI 文字範例](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />不遵守環境字型的 UI 文字範例

 在此情況下，「使用者資訊」和「產品資訊」並不尊重字型。 在某些情況下，這可能是明確的設計選擇，但如果未指定明確字型做為紅線規格的一部分，則會是 bug。

 若要重設字型，請按一下 [工具] **> > 選項**] 下的 [使用預設值] > 字型和色彩]。

## <a name="text-style"></a><a name="BKMK_TextStyle"></a>文字樣式
 文字樣式指的是字型大小、權數和大小寫。 如需執行指引，請參閱[環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。

### <a name="text-casing"></a>文字大小寫

#### <a name="all-caps"></a>全部大寫
 請勿在 Visual Studio 中使用標題或標籤的全部大寫。

#### <a name="all-lowercase"></a>全部小寫
 Visual Studio 中的標題或標籤不全部使用小寫。

#### <a name="sentence-and-title-case"></a>句子和標題案例
 視情況而定，Visual Studio 中的文字應該使用標題大小寫或句子案例。

|將標題案例用於：|使用的句子案例：|
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
 「標題大小寫」是一種樣式，其中片語中大部分或所有單字的前幾個字母都是大寫。 在 Visual Studio 中，標題案例會用於許多專案，包括：

- **提示.** 範例：「預覽選取的專案」

- **資料行標頭。** 範例：「系統回應」

- **功能表項目。** 範例：「全部儲存」

  使用標題案例時，這些是何時要將文字大寫，以及何時將其保持小寫的指導方針：

|大寫|批註和範例|
|---------------|---------------------------|
|所有名詞||
|所有動詞命令|包括 "Is" 和其他形式的 "to"|
|所有 adverbs|包含「超過」和「時間」|
|所有形容詞|包括「此」和「那」|
|所有代名詞|包括所有格「它」以及「它是」，縮減的代詞「it」和動詞「是」|
|第一個和最後一個字組，不論語音的部分為何||
|屬於動詞片語的介係詞|「關閉所有視窗」或「關閉系統」|
|縮寫的所有字母|HTML、XML、URL、IDE、RGB|
|複合字組中的第二個單字（如果它是名詞或適當形容詞），或如果單字具有相等的權數|交互參照，Microsoft 預先軟體，讀取/寫入存取，執行時間|

|小寫|範例|
|---------------|--------------|
|複合字組中的第二個單字（如果它是語音的另一個部分或分詞修改第一個單字）|使用說明，請停用|
|文章，除非其中一個是標題中的第一個單字|a、an、the|
|座標連接詞|和，但適用于、或|
|在動詞片語外部以四個或更少字母的文字介係詞|into，移至，在|
|在不定片語中使用時的 "To"|「如何格式化硬碟」|

##### <a name="sentence-case"></a>句子案例
 句子大小寫是標準的大寫方法，其中只有句子的第一個單字是大寫，以及任何適當名詞和代詞「I」。 在一般情況下，句子較容易閱讀，特別是當電腦轉譯內容時。 使用的句子案例：

1. **狀態列訊息。** 這些只是簡單、簡短，而且只提供狀態資訊。 範例：「正在載入專案檔」

2. **所有其他 UI 元素**，包括標籤、核取方塊、選項按鈕和清單方塊專案。 範例：「選取清單中的所有專案」

### <a name="text-formatting"></a>文字格式
 Visual Studio 2013 中的預設文字格式是由[環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)所控制。 此服務有助於確保整個 IDE （整合式開發環境）中的字型外觀一致，而且您必須使用它來保證使用者的一致體驗。

 Visual Studio 字型服務所使用的預設大小來自 Windows，並顯示為 9 pt。

 您可以將格式套用至環境字型。 本主題涵蓋使用樣式的方式和位置。 如需執行資訊，請參閱[環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。

#### <a name="bold-text"></a>粗體文字
 粗體文字會在 Visual Studio 中謹慎使用，且應保留給：

- 在嚮導中的問題標籤

- 在方案總管中指定現用專案

- [屬性] 工具視窗中的覆寫值

- [Visual Basic 編輯器] 下拉式清單中的特定事件

- 網頁檔大綱中伺服器產生的內容

- 複雜對話方塊或設計工具 UI 中的區段標頭

#### <a name="italics"></a>斜體
 Visual Studio 不會使用斜體或粗體的斜體文字。

#### <a name="color"></a>Color

- 藍色會保留給超連結（導覽和命令），而且永遠不應用於方向。

- 較大的標題（環境字型 x 155% 或更新版本）可用於下列用途：

  - 對簽章 Visual Studio UI 提供視覺效果歡迎

  - 若要呼叫特定區域的注意力

  - 從標準深色灰階/黑色環境文字色彩中提供浮雕

- 標題中的色彩應該利用現有的 Visual Studio 品牌色彩，主要為紫色，#FF68217A。

- 在標題中使用色彩時，您必須遵守[Windows 色彩方針](/windows/desktop/uxguide/vis-color)，包括對比比例和其他協助工具考慮。

### <a name="font-size"></a>字型大小
 Visual Studio UI 設計具有更多空白字元的較淡外觀。 可能的話，已減少或移除 chrome 和標題列。 雖然資訊密度是 Visual Studio 的需求，但印刷樣式仍然很重要，著重于更多的開放行間距以及字型大小和權數的變化。

 下表包含 Visual Studio 中使用之顯示字型的設計詳細資料和視覺效果範例。 某些顯示字型變化的大小和粗細，例如 Semilight 做或淺色，會編碼成其外觀。

 所有顯示字型的執行程式碼片段都可以在[格式化（縮放/粗體）參考](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)中找到。

#### <a name="375-environment-font--light"></a>375% 環境字型 + 淺色

|使用方式|外觀|
|-|-|
|**使用方式：** 比較. 唯一的品牌化 UI。<br /><br /> **對**<br /><br /> -使用句子案例<br />-一律使用輕量<br /><br /> **不要：**<br /><br /> -用於簽章 UI 以外的 UI，例如起始頁<br />-粗體、斜體或粗體斜體<br />-用於本文文字<br />-在工具視窗中使用|**顯示為：** 34 Pt Segoe UI Light<br /><br /> **視覺效果範例：**<br /><br /> *目前未使用。可用於 Visual Studio 2017 起始頁。*|

#### <a name="310-environment-font--light"></a>310% 環境字型 + 淺色

::: moniker range="vs-2017"

|使用方式|外觀|
|-|-|
|**使用方式：**<br /><br /> -簽章對話方塊中的較大標題<br />-主報表標題<br /><br /> **對**<br /><br /> -使用句子案例<br />-一律使用輕量<br /><br /> **不要：**<br /><br /> -用於簽章 UI 以外的 UI，例如起始頁<br />-粗體、斜體或粗體斜體<br />-用於本文文字<br />-在工具視窗中使用|**顯示為：** 28 Pt Segoe UI 淺色<br /><br /> **視覺效果範例：**<br /><br /> ![310% 環境字型的範例 &#43; 淺色標題](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|使用方式|外觀|
|-|-|
|**使用方式：**<br /><br /> -簽章對話方塊中的較大標題<br />-主報表標題<br /><br /> **對**<br /><br /> -使用句子案例<br />-一律使用輕量<br /><br /> **不要：**<br /><br /> -用於簽章 UI 以外的 UI<br />-粗體、斜體或粗體斜體<br />-用於本文文字<br />-在工具視窗中使用|**顯示為：** 28 Pt Segoe UI 淺色<br /><br /> **視覺效果範例：**<br /><br /> ![310% 環境字型的範例 &#43; 淺色標題](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200% 環境字型 + Semilight 做

|使用方式|外觀|
|-|-|
|**使用方式：**<br /><br /> -子標題<br />-小型和中型對話方塊中的標題<br /><br /> **對**<br /><br /> -使用句子案例<br />-一律使用 Semilight 做權數<br /><br /> **不要：**<br /><br /> -粗體、斜體或粗體斜體<br />-用於本文文字<br />-在工具視窗中使用|**顯示為：** 18 Pt Segoe UI Semillight<br /><br /> **視覺效果範例：**<br /><br /> ![200% 環境字型的範例 &#43; Semilight 做](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>155% 環境字型

|使用方式|外觀|
|-|-|
|**使用方式：**<br /><br /> -檔良好 UI 中的區段標題<br />-報表<br /><br /> **Do：** 使用句子案例<br /><br /> **不要：**<br /><br /> -粗體、斜體或粗體斜體<br />-用於本文文字<br />-在標準 Visual Studio 控制項中使用<br />-在工具視窗中使用|**顯示為：** 14 pt Segoe UI<br /><br /> **視覺效果範例：**<br /><br /> ![155% 環境字型標題的範例](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>133% 環境字型

|使用方式|外觀|
|-|-|
|**使用方式：**<br /><br /> -簽章對話方塊中較小的子標題<br />-檔良好 UI 中較小的子標題<br /><br /> **Do：** 使用句子案例<br /><br /> **不要：**<br /><br /> -粗體、斜體或粗體斜體<br />-用於本文文字<br />-在標準 Visual Studio 控制項中使用<br />-在工具視窗中使用|**顯示為：** 12 pt Segoe UI<br /><br /> **視覺效果範例：**<br /><br /> ![133% 環境字型標題的範例](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>122% 環境字型

|使用方式|外觀|
|-|-|
|**使用方式：**<br /><br /> -簽章對話方塊中的區段標題<br />-樹狀檢視中的最上層節點<br />-垂直 tab 導覽<br /><br /> **Do：** 使用句子案例<br /><br /> **不要：**<br /><br /> -粗體、斜體或粗體斜體<br />-用於本文文字<br />-在標準 Visual Studio 控制項中使用<br />-在工具視窗中使用|**顯示為：** 11 pt Segoe UI<br /><br /> **視覺效果範例：**<br /><br /> ![122% 環境字型標題的範例](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>環境字型 + 粗體

|使用方式|外觀|
|-|-|
|**使用方式：**<br /><br /> -簽章對話方塊中的標籤和 subheads<br />-報表中的標籤和 subheads<br />-檔功能良好的 UI 中的標籤和 subheads<br /><br /> **對**<br /><br /> -使用句子案例<br />-使用粗體權數<br /><br /> **不要：**<br /><br /> -斜體或粗體斜體<br />-用於本文文字<br />-在標準 Visual Studio 控制項中使用<br />-在工具視窗中使用|**顯示為：** 粗體 9 pt Segoe UI<br /><br /> **視覺效果範例：**<br /><br /> ![環境字型 &#43; 粗體標題的範例](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>環境字型

|使用方式|外觀|
|-|-|
|**使用方式：** 所有其他文字<br /><br /> **Do：** 使用句子案例<br /><br /> **不要：** 斜體或粗體斜體|**顯示為：** 9 pt Segoe UI<br /><br /> **視覺效果範例：**<br /><br /> ![環境字型的範例](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>填補和間距
 標題周圍需要一些空間，以提供適當的強調。 這個空間會根據點大小和其他在標題附近的內容而有所不同，例如水準規則或環境字型中的文字行。

- 標題本身的理想填補應該是大寫字元高度空間的90%。 例如，28 pt Segoe UI 淺色標題的端點高度為 26 pt，而填補應大約為 23 pt，或約31圖元。

- 標題周圍的最小空間應為大寫字元高度的50%。 當標題伴隨規則或其他緊密調整元素時，可能會使用較少的空間。

- 粗體的環境字型文字應遵循預設行高度間距和填補。

## <a name="see-also"></a>另請參閱

- [字型（Windows）](/windows/desktop/uxguide/vis-fonts)
- [使用者介面文字（Windows）](/windows/desktop/uxguide/text-ui)
