---
title: 可視化工作室的字體和格式 |微軟文件
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf1550026fb5c9d9395d931f21d48bc4739ea8c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698586"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>適用於 Visual Studio 的字型和格式設定
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a>環境字型
 Visual Studio 中的所有字體都必須向使用者公開以進行自定義。 這主要通過「**工具>選項**」 對話方塊中的「**字型和顏色**」 頁完成。 字型設定的三個主要類別是:

- **環境字型**- IDE(整合式開發環境)的主字型,用於所有介面元素,包括對話框、功能表、工具視窗和文件視窗。 預設情況下,環境字型綁定到當前版本的 Windows 中顯示為 9 pt Segoe UI 的系統字體。 對所有介面元素使用一種字體有助於確保在整個 IDE 中保持一致的字體外觀。

- **文字編輯器**─ 在「**工具>選項**」 的文字編輯器頁面中,可以在代碼和其他基於文字的編輯器中顯示的元素進行自訂。

- **特定集合**- 設計器視窗,提供使用者自定義其介面元素可能會公開特定於其設計表面的字體在**工具>選項**的自己的設置頁。

### <a name="editor-font-customization-and-resizing"></a>編輯器字型自訂和調整大小
 使用者通常會根據使用者偏好放大或縮放編輯器中文本的大小和/或顏色,而與一般使用者介面無關。 由於環境字體用於可能出現在編輯器/設計器內部或作為編輯器/設計器的一部分的元素,因此在更改這些字體分類之一時注意預期行為非常重要。

 創建出現在編輯器中但不是*內容*一部分的 UI 元素時,使用環境字型而不是文本字體非常重要,以便元素以可預測的方式調整大小。

1. 對於編輯器中的代碼文本,請使用代碼文字字體設置調整大小,並回應編輯器文本的縮放級別。

2. 介面的所有其他元素應綁定到環境字體設置,並回應環境中的任何全域更改。 這包括(但不限於):

    - 內容選單中的文字

    - 編輯器修飾中的文字,如燈泡菜單文字、快速搜尋編輯器窗格以及瀏覽到窗格

    - 在對話框中標記文本,如 **"在檔中尋找**"或 **"重構"**

### <a name="accessing-the-environment-font"></a>存取環境字型
 在本機或 WinForms 代碼中,`IUIHostLocale::GetDialogFont``SID_SUIHostLocale`可以通過從服務查詢介面後調用 方法來訪問環境字體。

 對於 Windows 演示文稿基礎 (WPF),`DialogWindow`從 shell 的類派生對話框視窗類`Window`,而不是 WPF 的 類。

 在 XAML 中,代碼如下所示:

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

代碼後面:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (替換為`Microsoft.VisualStudio.Shell.11.0`MPF dll 的當前版本。

 要顯示對話框,請對`ShowModal()`類`ShowDialog()`上調用""。 `ShowModal()`在 shell 中設置正確的模態狀態,確保對話框在父視窗中居中,等等。

 程式碼如下所示：

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal`還一頭野豬? (空布爾)與`DialogResult`,如果需要,可以使用。 如果對話框以 **「確定」** 關閉,則返回值為 true。

 如果需要顯示一些不是對話框並在其自己的`HwndSource`中託管的 WPF UI,例如 Win32/WinForms 父視窗的彈出視窗或 WPF 子視窗,則需要`FontFamily`設定`FontSize`WPF 元素的根 元素和 。 (shell 在主視窗中設定屬性,但不會繼承`HWND`經過 。 shell 提供可以綁定屬性的資源,如下所示:

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a>格式 (縮放/ 粗體) 參考
 某些對話框要求特定文本為粗體或環境字體以外的大小。 以前,大於環境字型的字體被編碼為"`environment font +2`或類似。 使用提供的程式碼段將支援高 DPI 監視器,並確保顯示文本始終以正確的大小和重量顯示(如"光"或"半光")。

> [!NOTE]
> 在應用格式設置之前,請確保遵循[文本樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).* 中的指南。

 要縮放環境字型,可以按指示設定 TextBlock 或 Label 的樣式。 正確使用的每個代碼段都將生成正確的字體,包括適當的大小和重量變化。

 其中「"`vsui`是對命名`Microsoft.VisualStudio.Shell`空間的引用:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>375% 環境字型 + 淺色

**顯示為:** 34 pt 塞戈 UI 燈

::: moniker range="vs-2017"

**用於:(** 罕見)唯一品牌 UI,如"起始頁"

::: moniker-end

::: moniker range=">=vs-2019"

**用於:(** 罕見)唯一品牌 UI

::: moniker-end

**程式碼:** 以前`textBlock`定義的 TextBlock`label`是以前定義的標籤:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** 設置文本塊或標籤的樣式,如圖所示。

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>310% 環境字型 + 淺色
 **顯示為:** 28 pt Segoe UI 燈**用途:** 大簽名對話框標題, 報表中的主標題

 **程式碼:** 以前`textBlock`定義的 TextBlock`label`是以前定義的標籤:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** 設置文本塊或標籤的樣式,如圖所示。

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>200% 環境字型 + 半光
 **顯示為:** 18 pt Segoe UI 半光**用於:** 副標題, 標題在中小型對話框

 **程式碼:** 以前`textBlock`定義的 TextBlock`label`是以前定義的標籤:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** 設定文字塊或標籤的樣式,如下所示:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>155% 環境字型
 **顯示為:** 14 pt Segoe UI**用於:** 文件井 UI 或報表中的節標題

 **程式碼:** 以前`textBlock`定義的 TextBlock`label`是以前定義的標籤:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** 設定文字塊或標籤的樣式,如下所示:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>133% 環境字型
 **顯示為:** 12 pt Segoe UI**用於:** 簽名對話框中較小的副標題與文件井 UI

 **程式碼:** 以前`textBlock`定義的 TextBlock`label`是以前定義的標籤:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** 設定文字塊或標籤的樣式,如下所示:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>122% 環境字型
 **顯示為:** 11 pt Segoe UI**用於:** 簽名對話框中的節標題、樹狀圖中的頂部節點、垂直選項卡導航

 **程式碼:** 以前`textBlock`定義的 TextBlock`label`是以前定義的標籤:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** 設定文字塊或標籤的樣式,如下所示:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>環境字型 = 粗體
 **顯示為:** 粗體 9 pt Segoe UI**用於:** 簽名對話框、報表和文件中的標記與子頭

 **程式碼:** 以前`textBlock`定義的 TextBlock`label`是以前定義的標籤:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** 設定文字塊或標籤的樣式,如下所示:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>可本地化樣式
 在某些情況下,當地語系化人員需要修改不同區域設置的字體樣式,例如從東亞語言的文本中刪除粗體。 為了使字體樣式的當地語系化成為可能,這些樣式必須存在於 .resx 檔中。 在 Visual Studio 窗體設計器中實現此目的並仍在編輯字體樣式的最佳方法是在設計時顯式設置字體樣式。 儘管這將創建一個完整的字體物件,並且似乎可能會破壞父字體的繼承,但只有 FontStyle 屬性用於設置字體。

 解決方案是掛接對話框表單的事件`FontChanged`。 在這種情況下,`FontChanged`請遍歷所有控制項並檢查其字型是否已設置。 如果已設置,則根據窗體的字體和控制項以前的字體樣式將其更改為新字體。 代碼中這方面的一個範例是:

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

 使用此代碼可確保在更新窗體的字體時,控制件的字體也將更新。 還應從窗體的建構函數調用此方法,因為對話框可能無法獲取的`IUIService`實例,`FontChanged`並且事件永遠不會觸發。 鉤`FontChanged`將允許對話框動態選取新字體,即使對話框已打開也是如此。

### <a name="testing-the-environment-font"></a>測試環境字型
 為確保 UI 使用環境字型並尊重大小設定,請打開 **「工具>選項>環境>字體和顏色**」,並在「顯示設定」下拉菜單下選擇「環境字體」。

 ![「工具&gt;選項」對話框中的字型與顏色設定](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />「工具&gt;選項」對話框中的字型與顏色設定

 將字體設置為與預設值非常不同的內容。 為了明顯哪個 UI 不更新,請選擇帶有襯線(如"時代新羅馬")的字體,並設置非常大的大小。 然後測試UI以確保它尊重環境。 下面是使用授權對話框的範例:

 ![不尊重環境字型的 UI 文字範例](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />不尊重環境字型的 UI 文字範例

 在這種情況下,「使用者資訊」和「產品資訊」不尊重字體。 在某些情況下,這可能是一個明確的設計選擇,但如果顯式字體未指定為紅線規範的一部分,則可能是一個錯誤。

 要重置字型,請按下 **「工具>選項 >>字體和顏色」** 下「使用預設值」。

## <a name="text-style"></a><a name="BKMK_TextStyle"></a>文字樣式
 文本樣式是指字體大小、粗細和大小寫。 有關實現指南,請參閱[環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。

### <a name="text-casing"></a>文字大小寫

#### <a name="all-caps"></a>全部大寫
 請勿在視覺工作室中對標題或標籤使用所有大寫字母。

#### <a name="all-lowercase"></a>所有小寫
 請勿對視覺工作室中的標題或標籤使用所有小寫。

#### <a name="sentence-and-title-case"></a>句子和標題案例
 Visual Studio 中的文本應使用標題案例或句子案例,具體取決於具體情況。

|使用標題案例:|使用句子案例:|
|-------------------------|----------------------------|
|對話框標題|標籤|
|群組盒|核取方塊|
|功能表項目|選項按鈕|
|操作功能表項目|清單盒項目|
|按鈕|狀態列|
|表標籤||
|資料行標題||
|工具提示||

##### <a name="title-case"></a>字首大寫
 標題大小寫是一種樣式,其中短語中大多數或所有單詞的第一個字母大寫。 在 Visual Studio 中,標題案例用於許多專案,包括:

- **提示。** 示例:"預覽所選專案"

- **列標題。** 示例:"系統回應"

- **功能表項。** 示例:"全部保存"

  使用標題大小寫時,以下是何時對單詞進行大寫以及何時保留小寫字母的準則:

|大寫|評論和範例|
|---------------|---------------------------|
|所有名詞||
|所有動詞命令|包括"是"和其他形式的"要"|
|所有副詞|包括"Than"和"何時"|
|所有形容詞|包括"這個"和"那個"|
|所有代詞|包括佔有性的「它」和「它是」,代詞「它」和動詞」是「的收縮|
|第一個單詞和最後一個單詞,無論演講的哪個部分||
|作為動詞短語一部分的介詞|關閉所有視窗"或"關閉系統"|
|第一字母縮圖的所有字母|HTML, XML, URL, IDE, RGB|
|複合詞中的第二個單詞,如果是名詞或適當的形容詞,或者單詞具有相等的權重|交叉引用,微軟前軟體,讀/寫訪問,運行時|

|小寫|範例|
|---------------|--------------|
|複合詞中的第二個單詞,如果它是語音的另一部分或修改第一個單詞的分詞|如何,起飛|
|文章,除非標題中的第一個單字|a、an、the|
|座標連合|和,但是,也不,或|
|動詞短語之外有四個或更少字母的單詞的介詞|到,至於,出,在上面|
|在不定式短語中使用時的"To"|"如何格式化硬碟"|

##### <a name="sentence-case"></a>判刑案例
 句子案例是書寫的標準大寫方法,其中只有句子的第一個單詞大寫,以及任何正確的名詞和代詞"I"。 通常,對於全球受眾來說,句子案例更容易閱讀,尤其是當內容將由機器翻譯時。 使用句子案例:

1. **狀態欄消息。** 這些操作簡單、簡短,僅提供狀態資訊。 示例:"載入專案檔"

2. **所有其他 UI 元素**,包括標籤、複選框、單選按鈕和清單框項。 示例:"選擇清單中的所有專案"

### <a name="text-formatting"></a>文字格式
 Visual Studio 2013 中的預設文本格式由[環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)控制。 此服務有助於確保在整個 IDE(整合式開發環境)中保持一致的字體外觀,您必須使用它來保證用戶獲得一致的體驗。

 Visual Studio 字型服務使用的預設大小來自 Windows,顯示為 9 磅。

 您可以將格式應用於環境字型。 本主題介紹如何使用樣式以及在哪裡使用樣式。 有關實作資訊,請參閱[環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。

#### <a name="bold-text"></a>粗體文字
 粗體文本在視覺工作室中謹慎使用,應保留為:

- 匯出匯中的問題分頁

- 在解決方案資源管理員中指定活動項目

- 「屬性」工具視窗中的重寫值

- 視覺化基本編輯器下拉清單中的某些事件

- 網頁文件大綱中的伺服器產生的內容

- 複雜對話框或設計器 UI 中的節標題

#### <a name="italics"></a>斜體
 Visual Studio 不使用斜體或粗體斜體文本。

#### <a name="color"></a>Color

- 藍色保留為超連結(導航和命令),絕不應用於方向。

- 出於以下目的,可以著色較大的標題(環境字體 x 155% 或更高):

  - 為簽名視覺工作室 UI 提供視覺吸引力

  - 呼籲關注特定區域

  - 提供從標準深灰色/黑色環境文字顏色的緩解

- 標題中的顏色應利用現有的 Visual Studio 品牌顏色,主要是主要的紫色、#FF68217A。

- 在標題中使用顏色時,必須遵守[Windows 顏色準則](/windows/desktop/uxguide/vis-color),包括對比度和其他輔助功能注意事項。

### <a name="font-size"></a>字型大小
 Visual Studio UI 設計具有更輕的外觀和更多的空白空間。 在可能的情況下,鉻和標題條已減少或刪除。 雖然資訊密度是 Visual Studio 中的一項要求,但排版仍然很重要,重點是更開放的線條間距和字體大小和權重的變化。

 下表包括 Visual Studio 中使用的顯示字體的設計詳細資訊和可視化範例。 某些顯示字體變體的大小和權重(如半光或輕)已編碼到其外觀中。

 所有顯示字型的實現代碼段都可以在[格式(縮放/粗體)引用](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)中找到。

#### <a name="375-environment-font--light"></a>375% 環境字型 + 淺色

|||
|-|-|
|**用法:** 罕見。 僅具有唯一品牌 UI。<br /><br /> **執行:**<br /><br /> - 使用句子案例<br />- 始終使用重量輕<br /><br /> **不要:**<br /><br /> - 用於簽署 UI 以外的 UI,如起始頁<br />- 粗體、斜體或粗斜體<br />- 用於正文文字<br />- 在工具視窗中使用|**顯示為:** 34 pt 塞戈 UI 燈<br /><br /> **視覺範例:**<br /><br /> *當前未使用。可在視覺工作室 2017 起始頁中使用。*|

#### <a name="310-environment-font--light"></a>310% 環境字型 + 淺色

::: moniker range="vs-2017"

|||
|-|-|
|**使用:**<br /><br /> - 簽名對話框中較大的標題<br />- 主要報告標題<br /><br /> **執行:**<br /><br /> - 使用句子案例<br />- 始終使用重量輕<br /><br /> **不要:**<br /><br /> - 用於簽署 UI 以外的 UI,如起始頁<br />- 粗體、斜體或粗斜體<br />- 用於正文文字<br />- 在工具視窗中使用|**顯示為:** 28 pt 塞戈 UI 燈<br /><br /> **視覺範例:**<br /><br /> ![310% 環境字型&#43;光標題的範例](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|||
|-|-|
|**使用:**<br /><br /> - 簽名對話框中較大的標題<br />- 主要報告標題<br /><br /> **執行:**<br /><br /> - 使用句子案例<br />- 始終使用重量輕<br /><br /> **不要:**<br /><br /> - 用於簽署 UI 以外的 UI<br />- 粗體、斜體或粗斜體<br />- 用於正文文字<br />- 在工具視窗中使用|**顯示為:** 28 pt 塞戈 UI 燈<br /><br /> **視覺範例:**<br /><br /> ![310% 環境字型&#43;光標題的範例](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200% 環境字型 + 半光

|||
|-|-|
|**使用:**<br /><br /> - 副標題<br />- 中小型對話框中的標題<br /><br /> **執行:**<br /><br /> - 使用句子案例<br />- 始終使用半輕重量<br /><br /> **不要:**<br /><br /> - 粗體、斜體或粗斜體<br />- 用於正文文字<br />- 在工具視窗中使用|**顯示為:** 18 pt 塞戈 UI 塞米萊特<br /><br /> **視覺範例:**<br /><br /> ![200% 環境字型&#43;半光的範例](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>155% 環境字型

|||
|-|-|
|**使用:**<br /><br /> - 文件井 UI 中的節標題<br />- 報告<br /><br /> **執行:** 使用句子案例<br /><br /> **不要:**<br /><br /> - 粗體、斜體或粗斜體<br />- 用於正文文字<br />- 在標準視覺工作室控制項中使用<br />- 在工具視窗中使用|**顯示為:** 14 pt 塞戈 UI<br /><br /> **視覺範例:**<br /><br /> ![155% 環境字型標題的範例](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>133% 環境字型

|||
|-|-|
|**使用:**<br /><br /> - 簽署對話框中的較小子標題<br />- 文件井 UI 中的較小子標題<br /><br /> **執行:** 使用句子案例<br /><br /> **不要:**<br /><br /> - 粗體、斜體或粗斜體<br />- 用於正文文字<br />- 在標準視覺工作室控制項中使用<br />- 在工具視窗中使用|**顯示為:** 12 pt 塞戈 UI<br /><br /> **視覺範例:**<br /><br /> ![133% 環境字型標題的範例](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>122% 環境字型

|||
|-|-|
|**使用:**<br /><br /> - 簽署對話框中的節標題<br />- 樹狀圖中的頂端節點<br />- 垂直選項卡導覽<br /><br /> **執行:** 使用句子案例<br /><br /> **不要:**<br /><br /> - 粗體、斜體或粗斜體<br />- 用於正文文字<br />- 在標準視覺工作室控制項中使用<br />- 在工具視窗中使用|**顯示為:** 11 pt Segoe UI<br /><br /> **視覺範例:**<br /><br /> ![122% 環境字型標題的範例](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>環境字型 = 粗體

|||
|-|-|
|**使用:**<br /><br /> - 簽署對話框中的標籤與子頭<br />- 報表中的標籤與子頭<br />- 文件井 UI 的標籤與子頭<br /><br /> **執行:**<br /><br /> - 使用句子案例<br />- 使用粗體重量<br /><br /> **不要:**<br /><br /> - 斜體或粗斜體<br />- 用於正文文字<br />- 在標準視覺工作室控制項中使用<br />- 在工具視窗中使用|**顯示為:** 粗體 9 pt Segoe UI<br /><br /> **視覺範例:**<br /><br /> ![環境字型&#43;粗體標題的範例](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>環境字型

|||
|-|-|
|**用法:** 所有其他文字<br /><br /> **執行:** 使用句子案例<br /><br /> **不要:** 斜體或粗斜體|**顯示為:** 9 pt Segoe UI<br /><br /> **視覺範例:**<br /><br /> ![環境字型的範例](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>填滿與間距
 標題需要圍繞它們的空間來給予適當的強調。 此空間因點大小和標題附近的其他內容而異,例如水準規則或環境字體中的一行文本。

- 標題本身的理想填充應為大寫字元高度空間的 90%。 例如,28 pt Segoe UI Light標題的上限高度為 26 磅,填充高度應約為 23 pt,即大約 31 圖元。

- 標題周圍的最小空間應為大寫字元高度的 50%。 當標題附帶規則或其他緊密擬合元素時,可以使用較少的空間。

- 帶粗體環境字體文本應遵循預設行高度間距和填充。

## <a name="see-also"></a>另請參閱

- [MSDN: 字型 (視窗)](/windows/desktop/uxguide/vis-fonts)
- [MSDN:使用者介面文字(視窗)](/windows/desktop/uxguide/text-ui)
