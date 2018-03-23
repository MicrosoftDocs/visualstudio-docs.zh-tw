---
title: 字型及格式設定適用於 Visual Studio |Microsoft 文件
ms.custom: ''
ms.date: 04/26/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 83c1d4e20dd372d3b76362b9f06ee894b045333c
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="fonts-and-formatting-for-visual-studio"></a>字型及格式設定適用於 Visual Studio
##  <a name="BKMK_TheEnvironmentFont"></a> 環境字型
 在 Visual Studio 中的所有字型必須都公開給可自訂的使用者。 這主要透過完成**字型和色彩**頁面**工具 > 選項**對話方塊。 字型設定的三個主要類別如下：  
  
-   **環境字型**-用於所有介面項目，包括對話方塊、 功能表、 工具視窗和文件視窗的主要字型 ide （整合式的開發環境）。 根據預設，環境字型繫結會顯示為 9 點 Segoe UI，在目前版本的 Windows 系統字型。 使用一種字型的所有介面項目有助於確保整個 IDE 的一致字型外觀。  
  
-   **文字編輯器**-，介面中的程式碼和其他以文字為基礎的編輯器可以自訂在文字編輯器中的項目頁面**工具 > 選項**。  
  
-   **特定集合**-在他們自己設定 頁面中的設計工具提供使用者介面項目的的自訂可能會公開其設計特定字型的 windows 介面**工具 > 選項**。  
  
### <a name="editor-font-customization-and-resizing"></a>編輯器的字型自訂和調整大小  
 使用者通常會放大或縮放的大小和/或根據他們的喜好設定，獨立於一般使用者介面編輯器中的文字色彩。 因為可能內或編輯器/設計工具的一部分顯示的項目上有使用環境字型，所以這些字型分類的其中一個變更時，請注意預期的行為。  
  
 建立時顯示的 UI 項目編輯器但不是屬於*內容*，請務必使用環境字型和文字字型，讓項目調整大小的可預測的方式。  
  
1.  對於程式碼編輯器中的文字，與程式碼的文字字型設定調整大小，並回應編輯器文字的縮放層級。  
  
2.  介面的其他所有項目應該繫結至環境字型設定，以及回應環境中的任何全域變更。 這包括 （但不限於）：  
  
    -   內容功能表中的文字  
  
    -   文字編輯器裝飾，像燈泡功能表文字，快速尋找編輯器窗格中，並瀏覽窗格  
  
    -   類似的標籤文字 對話方塊中的**檔案中尋找**或**重構**  
  
### <a name="accessing-the-environment-font"></a>存取環境字型  
 可以呼叫的方法來存取原生模式或 WinForms 程式碼中環境字型`IUIHostLocale::GetDialogFont`之後查詢從介面`SID_SUIHostLocale`服務。  
  
 為 Windows Presentation Foundation (WPF) 中，從介面衍生對話方塊視窗類別`DialogWindow`類別而不是 WPF 的`Window`類別。  
  
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
  
 (取代`Microsoft.VisualStudio.Shell.11.0`MPF dll 的目前版本。)  
  
 若要顯示對話方塊，請呼叫 「`ShowModal()`」 透過在類別上`ShowDialog()`。 `ShowModal()` 在介面中設定正確的強制回應狀態，可確保對話方塊置於父視窗等等。  
  
 程式碼如下所示：  
  
```csharp
MyWindow window = new MyWindow();  
window.ShowModal()  
```
  
 `ShowModal` 傳回 bool？ （可為 null 的布林值） 與`DialogResult`，必要時可使用。 如果關閉對話方塊時，如果有傳回值為 true**確定**。  
  
 如果您要顯示在它自己的某些 WPF UI，不是一個對話方塊，而裝載`HwndSource`，例如快顯視窗或 WPF 視窗的子視窗 Win32/WinForms 父視窗，您必須設定`FontFamily`和`FontSize`WPF e 根項目上lement。 (在 shell 主視窗中，根據設定的屬性，但不是會繼承過去`HWND`)。 此命令介面提供的資源的內容可以繫結，就像這樣：  
  
```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
```
  
###  <a name="BKMK_Formatting"></a> 格式化 （調整/粗體） 參考  
 有些對話方塊則需要為粗體的特定文字或以外的環境字型的大小。 先前，大於環境字型的字型已編碼為"`environment font +2`」 或類似。 使用提供的程式碼片段，將支援高 DPI 顯示器，並確保顯示的文字一律會顯示在正確的大小和粗細 （像 Light 或半細體）。  
  
> **注意： 您套用格式之前，請確定您要遵照中找到的指導方針[文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。**  
  
 若要調整規模的環境字型，請設定樣式的 TextBlock 或指示的標籤。 每個正確使用，這些程式碼片段會產生正確的字型，包括適當的尺寸和重量變化。  
  
 其中"`vsui`」 是命名空間的參考`Microsoft.VisualStudio.Shell`:  

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0" 
```
  
#### <a name="375-environment-font--light"></a>375%環境字型 + 細體  
 **會顯示為：** 34 pt Segoe UI Light  
 **適用於：** （罕見） 唯一品牌 UI，例如在 [開始] 頁面

 **程序程式碼：**其中`textBlock`是先前定義的 TextBlock 和`label`是先前定義的標籤：  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
```
  
 **XAML:**設定樣式的 TextBlock 或標籤所示。  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
```
  
#### <a name="310-environment-font--light"></a>310%環境字型 + 細體  
 **會顯示為：** 28 pt Segoe UI Light   
 **適用於：**大型的簽章對話方塊標題，主報表中的標題  
  
 **程序程式碼：**其中`textBlock`是先前定義的 TextBlock 和`label`是先前定義的標籤：  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);    
```
  
 **XAML:**設定樣式的 TextBlock 或標籤所示。  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>     
```
  
#### <a name="200-environment-font--semilight"></a>200%環境字型 + 半細體  
 **會顯示為：** 18 pt Segoe UI semilight 做    
 **適用於：**子標題、 小型及中型 對話方塊中的標題  
  
 **程序程式碼：**其中`textBlock`是先前定義的 TextBlock 和`label`是先前定義的標籤： 
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);    
```
  
 **XAML:**設定樣式的 TextBlock 或標籤所示：  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>    
```
  
#### <a name="155-environment-font"></a>155%環境字型  
 **會顯示為：** 14 pt Segoe UI    
 **適用於：** UI 或報表，以及文件中的區段標題  
  
 **程序程式碼：**其中`textBlock`是先前定義的 TextBlock 和`label`是先前定義的標籤：  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);    
```
  
 **XAML:**設定樣式的 TextBlock 或標籤所示：  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
```
  
#### <a name="133-environment-font"></a>133%環境字型  
 **會顯示為：** 12 點 Segoe UI    
 **適用於：**簽章對話方塊和文件中較小的子標題以及 UI  
  
 **程序程式碼：**其中`textBlock`是先前定義的 TextBlock 和`label`是先前定義的標籤：  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);    
```
  
 **XAML:**設定樣式的 TextBlock 或標籤所示：  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>    
```
  
#### <a name="122-environment-font"></a>122%環境字型  
 **會顯示為：** 11 pt Segoe UI    
 **適用於：**區段中的簽章對話方塊標題中，排名最前面的節點在樹狀結構檢視中，垂直索引標籤瀏覽  
  
 **程序程式碼：**其中`textBlock`是先前定義的 TextBlock 和`label`是先前定義的標籤：  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);    
```
  
 **XAML:**設定樣式的 TextBlock 或標籤所示：  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>    
```
  
#### <a name="environment-font--bold"></a>環境字型 + 粗體  
 **會顯示為：**粗體 9 點 Segoe UI    
 **適用於：**標籤和簽章對話方塊、 報表和文件中的次良好的 UI  
  
 **程序程式碼：**其中`textBlock`是先前定義的 TextBlock 和`label`是先前定義的標籤：  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironmentBoldStyleKey);    
```
  
 **XAML:**設定樣式的 TextBlock 或標籤所示：  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>    
```
  
### <a name="localizable-styles"></a>可當地語系化的樣式  
 在某些情況下，當地語系化人員將需要修改不同的地區設定，例如粗體移除東亞語言的文字的字型樣式。 若要進行當地語系化的字型樣式，這些樣式必須是.resx 檔案中。 若要完成這項作業，並仍然編輯 Visual Studio 表單設計工具中的字型樣式，最好是在設計階段中明確設定的字型樣式。 雖然這會建立完整的字型物件，並中斷繼承的父系字型可能不按照，只能使用 FontStyle 屬性用來設定字型。  
  
 解決方法是連接對話方塊表單`FontChanged`事件。 在`FontChanged`事件，查核所有控制項，並檢查是否要將它們的字型。 如果設定，請將它變更為根據表單的字型和前一個字型樣式的控制項的新字型。 這個範例中程式碼是：  
  
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
  
 使用此程式碼，可保證，更新表單的字型時，會一併更新控制項的字型。 呼叫此方法也會從表單的建構函式，因為對話方塊可能無法取得的執行個體`IUIService`和`FontChanged`將永遠不會引發事件。 攔截`FontChanged`將允許動態收取新字型，即使對話方塊已開啟的對話方塊。  
  
### <a name="testing-the-environment-font"></a>測試環境字型  
 為了確保您的 UI 使用環境字型，而且尊重大小設定，開啟**工具 > 選項 > 環境 > 字型和色彩**下選取 」 環境字型 」 和 「 顯示設定:"下拉式選單。  
  
 ![[工具] 中的字型和色彩設定&gt;選項 對話方塊](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201 a_OptionsFonts")<br />工具 中的字型和色彩設定&gt;選項 對話方塊
  
 為預設值非常不同的項目設定的字型。 更明顯這不會更新 UI，請選擇截 （例如"Times New Roman") 的字型，並設定非常大的大小。 然後測試您的 UI，以確保它尊重環境。 以下是使用 [授權] 對話方塊的範例：  
  
 ![不會遵守環境字型的 UI 文字範例](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201 b_WrongFontDialog")<br />不會遵守環境字型的 UI 文字範例
  
 在此情況下，「 使用者資訊 」 和 「 產品資訊 」 不會尊重字型。 在某些情況下，這可能是明確的設計選擇，但是如果未指定明確的字型紅線規格的一部分，它可以是 bug。  
  
 若要重設字型，請按一下 「 使用預設值"下**工具 > 選項 > 環境 > 字型和色彩**。  
  
##  <a name="BKMK_TextStyle"></a> 文字樣式  
 文字樣式是指字型大小、 加權和大小寫。 如需實作指引，請參閱[環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。  
  
### <a name="text-casing"></a>文字大小寫  
  
#### <a name="all-caps"></a>全部大寫  
 請勿使用全部大寫字標題或 Visual Studio 中的標籤。  
  
#### <a name="all-lowercase"></a>所有小寫  
 請勿使用全部小寫的標題或 Visual Studio 中的標籤。  
  
#### <a name="sentence-and-title-case"></a>句子和標題大小寫  
 字首大寫或句子的情況下，視情況，應該使用 Visual Studio 中的文字。  
  
|使用字首的大寫：|使用句子大小寫：|  
|-------------------------|----------------------------|  
|對話方塊標題|標籤|  
|群組方塊|核取方塊|  
|功能表項目|選項按鈕|  
|內容功能表項目|清單方塊項目|  
|按鈕|狀態列|  
|資料表標籤||  
|資料行標頭||  
|工具提示||  
  
##### <a name="title-case"></a>字首大寫  
 字首大寫為的樣式，都大寫的大部分或所有片語單字的第一個字母。 在 Visual Studio 中，字首大寫用於許多項目，包括：  
  
-   **工具提示。** 範例: 「 預覽選取的項目 」  
  
-   **資料行標頭。** 範例: 「 系統回應 」  
  
-   **功能表項目。** 範例: 「 儲存所有 」  
  
 當使用字首大寫，改成大寫的文字和時機將其保留大小寫方針如下：  
  
|大寫|註解和範例|  
|---------------|---------------------------|  
|所有的名詞||  
|所有動詞命令|包括 「 是 」 以及其他形式的"至 be"|  
|所有副詞|包括 「 非 」 和 「 時機 」|  
|所有的形容詞|包括"This"和"，"|  
|所有代名詞|包括寫成所有格 「 其 」 以及原狀 」，「 代名詞的縮減"它"和動作 「 不 」|  
|第一個和最後一個單字，不論詞性的||  
|屬於動詞片語介系詞|「 結束所有的 Windows"或者"以將系統關機 」|  
|為縮寫字的所有字母|HTML、 XML、 URL、 IDE、 RGB|  
|第二個 word 中的複合字是名詞或適當形容詞，或者單字有相同的權重|交互參照前的 Microsoft 軟體，讀取/寫入存取，執行階段|  
  
|小寫|範例|  
|---------------|--------------|  
|如果它是另一個的一部份或分詞，修改的第一個單字的複合字中的第二個字|作法，請採取關閉|  
|發行項，除非其中一個是標題中的第一個單字|a、 an、 the|  
|協調 nor|而且，但是，也不，或|  
|含有文字的四個或更少的字母之外動詞片語介系詞|執行到，做為 out，在最上層的|  
|"To"用於不定的片語時|< 如何格式化硬碟 >|  
  
##### <a name="sentence-case"></a>句子大小寫  
 句子大小寫是寫入在句子的第一個單字大寫，以及任何的專有名詞和代名詞標準大小寫的方法"I"。 一般情況下，句子的案例是更容易閱讀，尤其是當內容將會轉譯機器全球市場。 使用句子大小寫：  
  
1.  **狀態列訊息。** 這些簡單地說，很簡單，並只提供狀態資訊。 範例: 「 正在載入專案檔案 」  
  
2.  **所有其他 UI 項目**，包括標籤、 核取方塊、 選項按鈕和清單方塊項目。 範例: 「 在清單中選取所有項目 」  
  
### <a name="text-formatting"></a>文字格式設定  
 Visual Studio 2013 中的格式設定的預設文字由[環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。 此服務可協助確保整個 IDE （整合式的開發環境） 有一致的字型的外觀，您必須使用它來確保一致的經驗，為您的使用者。  
  
 Visual Studio 字型服務所使用的預設大小是來自於 Windows，且會顯示為 9 點。  
  
 您可以將格式套用至環境字型。 本主題涵蓋如何及在何處使用樣式。 實作的詳細資訊，請參閱[環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。  
  
#### <a name="bold-text"></a>粗體文字  
 粗體文字盡量少用用於 Visual Studio 中，以及應該保留為：  
  
-   在精靈中的問題標籤  
  
-   指定使用中的專案，在 方案總管  
  
-   覆寫屬性的 [工具] 視窗中的值  
  
-   在 Visual Basic 編輯器下拉式清單中的特定事件  
  
-   web 網頁的文件大綱 中的伺服器產生的內容  
  
-   在複雜的對話方塊或設計工具 UI 區段標頭  
  
#### <a name="italics"></a>斜體  
 Visual Studio 不會使用粗體或斜體斜體文字。  
  
#### <a name="color"></a>色彩  
  
-   藍色是保留的超連結 （瀏覽和命令），且絕不會用於方向。  
  
-   針對這些用途可著色較大的標題 （環境字型 155 %5x 或以上版本）：  
  
    -   提供 Visual Studio UI 簽章的視覺效果  
  
    -   若要醒目提示的特定區域  
  
    -   提供從標準暗灰色/黑色環境的文字色彩的 relief  
  
-   標題的色彩應該利用現有 Visual Studio 品牌色彩，主要是主要紫色 #FF68217A。  
  
-   當標題中使用色彩，您必須遵守[Windows 色彩指導方針](https://msdn.microsoft.com/en-us/library/dn742482.aspx)，包括對比比例以及其他協助工具的考量。  
  
### <a name="font-size"></a>Font size  
 Visual Studio UI 設計功能有較多空白空間較淡的外觀。 如果可行，chrome 和標題列已減少或移除。 雖然資訊密度是 Visual Studio 中的需求，印刷樣式仍然是很重要，特別強調更開啟行距和各式各樣的字型大小和加權。  
  
 下表包含設計詳細資料和視覺範例的 Visual Studio 中使用的顯示字型。 某些顯示字型變數有大小和粗細，例如 Semilight 或光線，自動程式化成其外觀。  
  
 所有顯示字型的實作程式碼片段位於[格式 （調整/粗體） 參考](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)。  
  
#### <a name="375-environment-font--light"></a>375%環境字型 + 細體  
  
|||  
|-|-|  
|**使用方式：**罕見。 Unique 只品牌 UI。<br /><br /> **執行動作：**<br /><br /> -使用句子大小寫<br />一律使用輕量<br /><br /> **不要：**<br /><br /> 使用 ui 以外簽章 UI，例如起始頁<br />-粗體、 斜體或粗體斜體<br />本文的使用<br />-使用中工具視窗|**會顯示為：** 34 pt Segoe UI Light<br /><br /> **Visual 範例：**<br /><br /> *目前未使用。可用於起始頁。*|  
  
#### <a name="310-environment-font--light"></a>310%環境字型 + 細體  
  
|||  
|-|-|  
|**使用方式：**<br /><br /> 規模較大的標題，在簽章對話方塊<br />-主報表標題<br /><br /> **執行動作：**<br /><br /> -使用句子大小寫<br />一律使用輕量<br /><br /> **不要：**<br /><br /> 使用 ui 以外簽章 UI，例如起始頁<br />-粗體、 斜體或粗體斜體<br />本文的使用<br />-使用中工具視窗|**會顯示為：** 28 pt Segoe UI Light<br /><br /> **Visual 範例：**<br /><br /> ![310%環境字型的範例&#43;淺色標題](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202 a_EF310")|  
  
#### <a name="200-environment-font--semilight"></a>200%環境字型 + 半細體  
  
|||  
|-|-|  
|**使用方式：**<br /><br /> -子標題<br />的小型和中型 對話方塊中標題<br /><br /> **執行動作：**<br /><br /> -使用句子大小寫<br />一律使用半細體權數<br /><br /> **不要：**<br /><br /> -粗體、 斜體或粗體斜體<br />本文的使用<br />-使用中工具視窗|**會顯示為：** 18 pt Segoe UI Semillight<br /><br /> **Visual 範例：**<br /><br /> ![200%環境字型的範例&#43;Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202 b_EF200")|  
  
#### <a name="155-environment-font"></a>155%環境字型  
  
|||  
|-|-|  
|**使用方式：**<br /><br /> 在文件中的區段標頭以及 UI<br />-報表<br /><br /> **操作方法：**使用句子大小寫<br /><br /> **不要：**<br /><br /> -粗體、 斜體或粗體斜體<br />本文的使用<br />-使用標準 Visual Studio 控制項中<br />-使用中工具視窗|**會顯示為：** 14 pt Segoe UI<br /><br /> **Visual 範例：**<br /><br /> ![155%環境字型標題的範例](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202 c_EF155")|  
  
#### <a name="133-environment-font"></a>133%環境字型  
  
|||  
|-|-|  
|**使用方式：**<br /><br /> 簽章對話方塊中的小子標題<br />文件中的小子標題以及 UI<br /><br /> **操作方法：**使用句子大小寫<br /><br /> **不要：**<br /><br /> -粗體、 斜體或粗體斜體<br />本文的使用<br />-使用標準 Visual Studio 控制項中<br />-使用中工具視窗|**會顯示為：** 12 點 Segoe UI<br /><br /> **Visual 範例：**<br /><br /> ![133%環境字型標題的範例](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202 d_EF133")|  
  
#### <a name="122-environment-font"></a>122%環境字型  
  
|||  
|-|-|  
|**使用方式：**<br /><br /> 簽章對話方塊中的區段標題<br />的樹狀檢視中最上層節點<br />-垂直 tab 導覽<br /><br /> **操作方法：**使用句子大小寫<br /><br /> **不要：**<br /><br /> -粗體、 斜體或粗體斜體<br />本文的使用<br />-使用標準 Visual Studio 控制項中<br />-使用中工具視窗|**會顯示為：** 11 pt Segoe UI<br /><br /> **Visual 範例：**<br /><br /> ![122%環境字型標題的範例](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202 e_EF122")|  
  
#### <a name="environment-font--bold"></a>環境字型 + 粗體  
  
|||  
|-|-|  
|**使用方式：**<br /><br /> -標籤和子標頭中的簽章對話方塊<br />-標籤和子報表中的標頭<br />-標籤和子文件中的標頭以及 UI<br /><br /> **執行動作：**<br /><br /> -使用句子大小寫<br />-使用粗體的加權<br /><br /> **不要：**<br /><br /> -斜體或粗體斜體<br />本文的使用<br />-使用標準 Visual Studio 控制項中<br />-使用中工具視窗|**會顯示為：**粗體 9 點 Segoe UI<br /><br /> **Visual 範例：**<br /><br /> ![環境字型的範例&#43;粗體標題](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202 f_EFB")|  
  
#### <a name="environment-font"></a>環境字型  
  
|||  
|-|-|  
|**使用方式：**所有其他文字<br /><br /> **操作方法：**使用句子大小寫<br /><br /> **不要：**斜體或粗體斜體|**會顯示為：** 9 點 Segoe UI<br /><br /> **Visual 範例：**<br /><br /> ![環境字型的範例](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202 g_EF")|  
  
### <a name="padding-and-spacing"></a>填補和間距  
 標題會需要它們，讓它們有適當的強調周圍的空間。 此空間會根據點大小和還有什麼是附近的標題，例如水平尺規或一行文字中的環境字型而有所不同。  
  
-   單獨使用時的標題的理想邊框間距應該是 90%的大寫字元高度空間。 例如，28 pt Segoe UI，細體標題的 cap 高度是 26 pt 而且填補應該大約 23 pt 或大約 31 像素為單位。  
  
-   標題周圍的最小空間應該是大寫字元高度的 50%。 標題會伴隨的規則或其他緊密調整項目時，可能會使用較少的空間。  
  
-   預設高度行距和填補，應遵循粗體字顯示環境字型的文字。  
  
## <a name="see-also"></a>另請參閱  
 [MSDN： 字型 (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [MSDN： 使用者介面文字 (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)