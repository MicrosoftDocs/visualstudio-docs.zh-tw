---
title: 字型和格式適用於 Visual Studio |Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f510568c977579fa3e48d57db548040d16dcb574
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335495"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>字型和格式適用於 Visual Studio
## <a name="BKMK_TheEnvironmentFont"></a> 環境字型
 Visual Studio 內的所有字型必須都公開到自訂的使用者。 這主要透過**字型和色彩**頁面**工具 > 選項**對話方塊。 字型設定三種主要分類如下：

- **環境字型**-用於所有的介面項目，包括對話方塊、 功能表、 工具視窗和文件視窗的主要字型 ide （整合式的開發環境）。 根據預設，會繫結至顯示為 9 pt Segoe UI，在目前版本的 Windows 系統字型的環境字型。 所有介面項目的都使用一種字型，可協助確保整個 IDE 有一致的字型的外觀。

- **文字編輯器**-，介面中的程式碼和其他以文字為基礎的編輯器可以自訂在 [文字編輯器] 中的項目頁面**工具 > 選項**。

- **特定集合**-提供使用者自訂其介面項目可能會公開其設計特定字型的設計工具視窗會出現在他們自己設定 頁面中**工具 > 選項**。

### <a name="editor-font-customization-and-resizing"></a>編輯器字型的自訂及調整大小
 使用者通常會放大或縮小的大小和/或根據其喜好設定無關的一般使用者介面編輯器 中的文字色彩。 因為可能會出現在中，或做為編輯器/設計工具的一部分的項目上使用的環境字型，則務必在其中一個這些字型分類變更時，請注意預期的行為。

 在中建立時顯示的 UI 項目編輯器，但不是屬於*內容*，務必要使用的環境字型和文字字型，讓項目調整大小的可預測的方式。

1. 程式碼中的文字編輯器，使用程式碼文字的字型設定調整大小並回應編輯器文字的縮放層級。

2. 介面的所有其他項目應該繫結至環境字型設定，並回應環境中的任何全域變更。 這包括 （但不限於）：

    - 在操作功能表中的文字

    - 文字編輯器透過裝飾，像燈泡功能表文字，快速尋找編輯器窗格中，並瀏覽至窗格

    - 標籤對話方塊中的文字，例如**檔案中尋找**或**重構**

### <a name="accessing-the-environment-font"></a>存取環境字型
 在原生模式或 WinForms 的程式碼，可以存取環境字型所呼叫方法`IUIHostLocale::GetDialogFont`在查詢從介面後`SID_SUIHostLocale`服務。

 針對 Windows Presentation Foundation (WPF) 中，從殼層的衍生對話方塊視窗類別`DialogWindow`類別而不是 WPF 的`Window`類別。

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

 (取代`Microsoft.VisualStudio.Shell.11.0`與目前的 MPF dll 版本。)

 若要顯示對話方塊，請呼叫 「`ShowModal()`"上的類別，透過`ShowDialog()`。 `ShowModal()` 在殼層中設定正確的強制回應狀態，可確保對話方塊會置於父視窗等等。

 程式碼如下所示：

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal` 會傳回 bool？ （可為 null 的布林值） 與`DialogResult`，這可以在需要時。 如果對話方塊已關閉與傳回的值為 true**確定**。

 如果您要顯示某些 WPF UI 的對話方塊，並不裝載在它自己`HwndSource`，例如快顯視窗或 WPF 子視窗的 Win32/WinForms 父視窗，您必須設定`FontFamily`和`FontSize`WPF 項目的根項目上。 (Shell 主視窗中，根據設定的屬性，但無法被繼承過去`HWND`)。 此命令介面提供的資源的屬性可以繫結，就像這樣：

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="BKMK_Formatting"></a> 格式化 （調整/粗體） 參考
 有些對話方塊會需要特定的文字是粗體或以外的環境字型的大小。 先前，大於環境字型的字型編碼為 「`environment font +2`"或類似。 使用提供的程式碼片段，可支援高 DPI 監視器，並確保顯示的文字，一律會出現在正確的大小和重量 （像是 Light 或 semilight 做）。

> **注意：您套用格式之前，請確定您遵循本指南中找到[文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。**

 若要調整環境字型，設定樣式的 TextBlock 或 Label 所示。 每個使用得宜，這些程式碼片段會產生正確的字型，包括適當的尺寸和重量變化。

 其中"`vsui`」 是命名空間的參考`Microsoft.VisualStudio.Shell`:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>375%環境字型 + 細體

**會顯示為：** 34 pt Segoe UI Light

::: moniker range="vs-2017"

**適用於：** （罕見） 唯一品牌的 UI，例如在 [開始] 頁面

::: moniker-end

::: moniker range=">=vs-2019"

**適用於：** （罕見） 的唯一品牌的 UI

::: moniker-end

**程序的程式碼：** 何處`textBlock`是先前定義的 TextBlock 和`label`是先前定義的標籤：

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** 設定樣式的 TextBlock 或標籤所示。

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>310%環境字型 + 細體
 **會顯示為：** 28 pt Segoe UI Light**用於：** 大型的簽章對話方塊標題，主報表中的標題

 **程序的程式碼：** 何處`textBlock`是先前定義的 TextBlock 和`label`是先前定義的標籤：

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** 設定樣式的 TextBlock 或標籤所示。

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>200%環境字型 + 半細體
 **會顯示為：** 18 點 Segoe UI semilight 做**用於：** 子標題、 小型和中型的對話方塊中的標題

 **程序的程式碼：** 何處`textBlock`是先前定義的 TextBlock 和`label`是先前定義的標籤：

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** 設定樣式的 TextBlock 或 Label 所示：

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>155%環境字型
 **會顯示為：** 14 pt Segoe UI**用於：** 文件中的區段標題以及 UI 或報表

 **程序的程式碼：** 何處`textBlock`是先前定義的 TextBlock 和`label`是先前定義的標籤：

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** 設定樣式的 TextBlock 或 Label 所示：

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>133%環境字型
 **會顯示為：** 12 pt Segoe UI**用於：** 簽章對話方塊和文件中較小的子標題以及 UI

 **程序的程式碼：** 何處`textBlock`是先前定義的 TextBlock 和`label`是先前定義的標籤：

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** 設定樣式的 TextBlock 或 Label 所示：

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>122%環境字型
 **會顯示為：** 11 pt Segoe UI**用於：** 區段簽章對話方塊中的標題中前在樹狀結構檢視中，垂直索引標籤瀏覽的節點,

 **程序的程式碼：** 何處`textBlock`是先前定義的 TextBlock 和`label`是先前定義的標籤：

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** 設定樣式的 TextBlock 或 Label 所示：

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>環境字型 + 粗體
 **會顯示為：** 粗體 9 pt Segoe UI**使用：** 標籤和子標頭中的簽章對話方塊、 報表和文件以及 UI

 **程序的程式碼：** 何處`textBlock`是先前定義的 TextBlock 和`label`是先前定義的標籤：

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** 設定樣式的 TextBlock 或 Label 所示：

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>可當地語系化的樣式
 在某些情況下，還需要修改不同的地區設定，例如粗體移除的東亞洲語言文字的字型樣式。 若要進行當地語系化的字型樣式，這些樣式必須是.resx 檔案中。 若要完成這項作業，並仍編輯 Visual Studio 表單設計工具中的字型樣式，最好是明確地在設計階段設定的字型樣式。 雖然這會建立完整的字型物件，並可能中斷的父代字型繼承，只能使用 [fontstyle] 屬性用來將字型設定。

 解決方法是將連結對話方塊表單的`FontChanged`事件。 在 `FontChanged`事件，查核所有控制項，並檢查是否要將它們的字型。 如果設定，請將它變更為新的字型，依據表單的字型和控制項的上一個字型樣式。 這個範例中的程式碼是：

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

 使用下列程式碼，可確保，當更新表單的字型時，將會一併更新控制項的字型。 這個方法應該也從表單的建構函式，呼叫，因為對話方塊可能無法取得的執行個體`IUIService`而`FontChanged`將永遠不會引發事件。 連結`FontChanged`將允許動態挑選新的字型，即使對話方塊已開啟的對話方塊。

### <a name="testing-the-environment-font"></a>測試環境字型
 若要確保您的 UI 會使用環境字型，並採用的大小設定，開啟**工具 > 選項 > 環境 > 字型和色彩**下選取 「 環境字型 」 和 「 顯示設定:"下拉式選單。

 ![[工具] 中的字型和色彩設定&gt;[選項] 對話方塊](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201 a_OptionsFonts")<br />工具 中的字型和色彩設定&gt;選項 對話方塊

 將字型設定為預設值非常不同的項目。 為了讓明顯這並不會更新 UI，選擇使用 （例如"Times New Roman") 有襯線字型並設定非常大的大小。 然後測試您的 UI，以確保它會遵守環境。 以下是使用 [授權] 對話方塊的範例：

 ![不接受環境字型的 UI 文字的範例](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201 b_WrongFontDialog")<br />不接受環境字型的 UI 文字範例

 在此情況下，「 使用者資訊 」 和 「 產品資訊 」 不會採用的字型。 在某些情況下這可能是明確的設計選擇，但如果未指定明確的字型紅線規格的一部分，它可以是 bug。

 若要重設字型，請按一下 「 使用預設值 」 底下**工具 > 選項 > 環境 > 字型和色彩**。

## <a name="BKMK_TextStyle"></a> 文字樣式
 文字樣式是指字型大小、 粗細和大小寫。 如需實作指引，請參閱[環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。

### <a name="text-casing"></a>文字大小寫

#### <a name="all-caps"></a>全部大寫
 請勿使用全部大寫字的項目] 或 [Visual Studio 中的標籤。

#### <a name="all-lowercase"></a>允許小寫
 請勿使用全部小寫的 標題 或 Visual Studio 中的標籤。

#### <a name="sentence-and-title-case"></a>句子和標題的案例
 字首大寫或句子的情況下，視情況而定，應該使用 Visual Studio 中的文字。

|使用字首的大寫：|使用句子大小寫的：|
|-------------------------|----------------------------|
|對話方塊標題|標籤|
|群組方塊|核取方塊|
|功能表項目|選項按鈕|
|操作功能表項目|清單方塊項目|
|按鈕|狀態列|
|資料表標籤||
|資料行標頭||
|工具提示||

##### <a name="title-case"></a>字首大寫
 字首大寫是的樣式，都大寫的大部分或所有內片語的單字的第一個字母。 在 Visual Studio 中，字首大寫用於許多項目，包括：

- **工具提示。** 範例：[預覽選取的項目]

- **資料行標頭。** 範例：「 系統回應 」

- **功能表項目。** 範例：[全部儲存]

  使用 字首大寫，它們何時改成大寫的字，以及何時將它們保留在小寫的方針：

|大寫|註解和範例|
|---------------|---------------------------|
|所有的名詞||
|所有動詞命令|包括 「 是 」 和其他形式的 「 若要為 」|
|所有副詞|包括 「 非 」 和 「 何時 」|
|所有的形容詞|包含"This"和"，"|
|所有的代名詞|包括寫成所有格 「 其 」 也如同"，"的代名詞縮減 [it] 和動詞"is"|
|第一個和最後一個字，無論詞性||
|屬於動詞片語介係詞|"Closing 出所有的 Windows"或者"正在關閉系統 」|
|為縮寫字的所有字母|HTML、 XML、 URL、 IDE、 RGB|
|第二個 word 中複合字，或如果名詞或適當形容詞字有相同的權重|交互參照前的 Microsoft 軟體，讀取/寫入權限，執行階段|

|小寫|範例|
|---------------|--------------|
|中複合字，如果它是另一個詞性或分詞，修改的第一個單字的第二個單字|作法，請採取關閉|
|發行項，除非其中一個是標題中的第一個字|a、 an、 the|
|協調 nor|而且，但是，也不，或|
|介係詞舞文弄墨的四個或更少的字母以外動詞片語|置入，做為 out，在最上層的|
|[到] 用於之不定的片語時|「 如何格式化硬碟 」|

##### <a name="sentence-case"></a>句首大寫
 句首大寫是標準大小寫的方法進行寫入中大寫的第一個字的句子，以及所有專有名詞和代名詞"I"。 一般情況下，句子大小寫會更容易閱讀，特別是當內容將會轉譯機器全球讀者。 使用句子大小寫的：

1. **狀態列訊息。** 這些簡單地說，很簡單，並只提供狀態資訊。 範例：「 正在載入專案檔 」

2. **所有其他 UI 項目**，包括標籤、 核取方塊、 選項按鈕和清單方塊項目。 範例：[選取清單中的所有項目]

### <a name="text-formatting"></a>文字格式設定
 Visual Studio 2013 中的格式設定的預設文字會受到[環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。 這項服務可協助確保整個 IDE （整合式的開發環境），具有一致的字型的外觀，您必須使用它來為您的使用者保證一致的體驗。

 Visual Studio 的字型服務所使用的預設大小是來自 Windows，而會顯示為 9 點。

 您可以將格式套用至環境字型。 本主題涵蓋如何以及在何處使用的樣式。 如需實作資訊，請參閱[環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。

#### <a name="bold-text"></a>粗體的文字
 粗體的文字謹慎使用 Visual Studio 中，且應該是保留供：

- 在精靈中的問題標籤

- 指定使用中的專案，在 方案總管

- 在 [屬性] 工具視窗中的覆寫的值

- 在 Visual Basic 編輯器下拉式清單中的特定事件

- 在文件大綱 中的 web 網頁的伺服器產生的內容

- 在複雜的對話方塊或設計工具 UI 中的區段標頭

#### <a name="italics"></a>斜體
 Visual Studio 不會使用斜體或粗體斜體的文字。

#### <a name="color"></a>色彩

- 藍色是保留的超連結 （導覽及命令），且永遠不會用於方向。

- 針對這些用途，可以彩色較大的標題 （環境字型 x 155%或更高）：

    - 提供至簽章 Visual Studio UI 中的視覺效果

    - 若要提醒您注意到特定的區域

    - 提供從標準暗灰/黑色環境的文字色彩的浮雕

- 標題的色彩應該利用現有 Visual Studio 品牌色彩，主要是主要的紫色，#FF68217A。

- 當使用標題的色彩，您必須遵守[Windows 色彩指導方針](/windows/desktop/uxguide/vis-color)，包括對比比例以及其他協助工具的考量。

### <a name="font-size"></a>Font size
 Visual Studio UI 設計功能較淺的外觀與更多的泛空白字元。 可能的話，chrome 和標題列已降低或移除。 在 Visual Studio 中的需求的資訊密度時，印刷樣式仍然是重要的是，更開放的行距和字型的大小和重量的變化，特別強調。

 下表包含設計詳細資訊和使用 Visual Studio 中的顯示字型的視覺範例。 某些顯示字型的變化有大小和重量，例如 semilight 做或光線，自動程式化成其外觀。

 所有顯示字型的實作程式碼片段位於[格式化 （調整/粗體） 參考](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)。

#### <a name="375-environment-font--light"></a>375%環境字型 + 細體

|||
|-|-|
|**使用方式：** 罕見。 唯一品牌僅限 UI。<br /><br /> **執行動作：**<br /><br /> -使用句子大小寫<br />-一律使用輕量<br /><br /> **沒有此項目：**<br /><br /> 使用 ui 以外的簽章例如起始頁的 UI<br />-粗體、 斜體或粗體斜體<br />使用的內文<br />-使用中工具視窗|**會顯示為：** 34 pt Segoe UI Light<br /><br /> **圖示的範例：**<br /><br /> *目前未使用。可用於 Visual Studio 2017 起始頁。*|

#### <a name="310-environment-font--light"></a>310%環境字型 + 細體

::: moniker range="vs-2017"

|||
|-|-|
|**使用方式：**<br /><br /> 簽章對話方塊中的較大標題<br />-主報表標題<br /><br /> **執行動作：**<br /><br /> -使用句子大小寫<br />-一律使用輕量<br /><br /> **沒有此項目：**<br /><br /> 使用 ui 以外的簽章例如起始頁的 UI<br />-粗體、 斜體或粗體斜體<br />使用的內文<br />-使用中工具視窗|**會顯示為：** 28 pt Segoe UI Light<br /><br /> **圖示的範例：**<br /><br /> ![310%環境字型的範例&#43;淺標題](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202 a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|||
|-|-|
|**使用方式：**<br /><br /> 簽章對話方塊中的較大標題<br />-主報表標題<br /><br /> **執行動作：**<br /><br /> -使用句子大小寫<br />-一律使用輕量<br /><br /> **沒有此項目：**<br /><br /> 使用 ui 以外的簽章 UI<br />-粗體、 斜體或粗體斜體<br />使用的內文<br />-使用中工具視窗|**會顯示為：** 28 pt Segoe UI Light<br /><br /> **圖示的範例：**<br /><br /> ![310%環境字型的範例&#43;淺標題](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202 a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200%環境字型 + 半細體

|||
|-|-|
|**使用方式：**<br /><br /> -子標題<br />-在小型和中型的對話方塊中的項目<br /><br /> **執行動作：**<br /><br /> -使用句子大小寫<br />-一律使用 semilight 做權數<br /><br /> **沒有此項目：**<br /><br /> -粗體、 斜體或粗體斜體<br />使用的內文<br />-使用中工具視窗|**會顯示為：** 18 點 Segoe UI Semillight<br /><br /> **圖示的範例：**<br /><br /> ![200%環境字型的範例&#43;semilight 做](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202 b_EF200")|

#### <a name="155-environment-font"></a>155%環境字型

|||
|-|-|
|**使用方式：**<br /><br /> 在文件中的區段標題以及 UI<br />-報表<br /><br /> **執行動作：** 使用句子大小寫<br /><br /> **沒有此項目：**<br /><br /> -粗體、 斜體或粗體斜體<br />使用的內文<br />-使用標準的 Visual Studio 控制項中<br />-使用中工具視窗|**會顯示為：** 14 pt Segoe UI<br /><br /> **圖示的範例：**<br /><br /> ![155%環境字型標題的範例](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202 c_EF155")|

#### <a name="133-environment-font"></a>133%環境字型

|||
|-|-|
|**使用方式：**<br /><br /> 簽章對話方塊中的小子標題<br />在文件中的小子標題以及 UI<br /><br /> **執行動作：** 使用句子大小寫<br /><br /> **沒有此項目：**<br /><br /> -粗體、 斜體或粗體斜體<br />使用的內文<br />-使用標準的 Visual Studio 控制項中<br />-使用中工具視窗|**會顯示為：** 12 pt Segoe UI<br /><br /> **圖示的範例：**<br /><br /> ![133%環境字型標題的範例](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202 d_EF133")|

#### <a name="122-environment-font"></a>122%環境字型

|||
|-|-|
|**使用方式：**<br /><br /> 簽章對話方塊中的區段標題<br />的樹狀檢視中最上層節點<br />-垂直索引標籤瀏覽<br /><br /> **執行動作：** 使用句子大小寫<br /><br /> **沒有此項目：**<br /><br /> -粗體、 斜體或粗體斜體<br />使用的內文<br />-使用標準的 Visual Studio 控制項中<br />-使用中工具視窗|**會顯示為：** 11 pt Segoe UI<br /><br /> **圖示的範例：**<br /><br /> ![122%環境字型標題的範例](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202 e_EF122")|

#### <a name="environment-font--bold"></a>環境字型 + 粗體

|||
|-|-|
|**使用方式：**<br /><br /> -標籤和簽章對話方塊中的次標題<br />-標籤和子報表中的標頭<br />-標籤和子文件中的標頭以及 UI<br /><br /> **執行動作：**<br /><br /> -使用句子大小寫<br />-使用粗體<br /><br /> **沒有此項目：**<br /><br /> -斜體或粗體斜體<br />使用的內文<br />-使用標準的 Visual Studio 控制項中<br />-使用中工具視窗|**會顯示為：** 粗體 9 pt Segoe UI<br /><br /> **圖示的範例：**<br /><br /> ![環境字型的範例&#43;粗體標題](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202 f_EFB")|

#### <a name="environment-font"></a>環境字型

|||
|-|-|
|**使用方式：** 所有其他的文字<br /><br /> **執行動作：** 使用句子大小寫<br /><br /> **沒有此項目：** 斜體或粗體斜體|**會顯示為：** 9 pt Segoe UI<br /><br /> **圖示的範例：**<br /><br /> ![環境字型的範例](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202 g_EF")|

### <a name="padding-and-spacing"></a>邊框距離和間距
 標題會需要它們以提供適當的強調周圍的空間。 此空間取決於點大小以及其他即將標題，例如水平尺規 」 或 「 環境字型的文字行。

- 理想的邊框距離本身的標題應該是 90%的投資的字元高度空間。 比方說，28 pt Segoe UI Light 標題的 cap 高度是 26 pt 和邊框距離應該大約 23 pt 或大約 31 像素為單位。

- 標題周圍的最小空間應該為大寫的字元高度的 50%。 標題會伴隨其他緊密調整項目或規則時，可能會使用較少的空間。

- 預設高度行距和填補，應該遵循粗體環境字型的文字。

## <a name="see-also"></a>另請參閱

- [MSDN:字型 (Windows)](/windows/desktop/uxguide/vis-fonts)
- [MSDN:使用者介面文字 (Windows)](/windows/desktop/uxguide/text-ui)
