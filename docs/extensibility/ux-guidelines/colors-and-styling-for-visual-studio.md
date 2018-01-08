---
title: "色彩和樣式設定適用於 Visual Studio |Microsoft 文件"
ms.custom: 
ms.date: 07/31/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 40e795238e46885707cfd6eff715a27a5f53f85c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="colors-and-styling-for-visual-studio"></a>色彩和樣式設定適用於 Visual Studio
## <a name="using-color-in-visual-studio"></a>使用 Visual Studio 中的色彩  
在 Visual Studio 中，色彩做為主要通訊工具，如同裝飾。 最少使用的色彩，並保留您想要的情況下：  
  
-   通訊意義或關係 （例如，平台或語言修飾詞）  
  
-   吸引注意 （例如，表示狀態變更）  
  
-   改善可讀性，並提供地標巡覽 UI  
  
-   增加符合度  
  
有數個選項在 Visual Studio 中的 UI 項目來指派色彩。 有時候很難圖哪一個選項時您應該要使用，或如何正確使用它。 本主題將協助您：  
  
1.  了解不同的服務和系統用來定義 Visual Studio 中的色彩。  
  
2.  選取正確的選項，針對指定的項目。  
  
3.  正確地使用您選擇的選項。  
  
> **注意：**從未硬編碼十六進位、 RGB 或系統色彩，您的 UI 項目。 使用服務可以調整色調的彈性。 此外，沒有服務，您將無法利用的佈景主題切換功能[VSColor 服務](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。
  
### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Visual Studio 介面項目來指派色彩的方法  
選擇最適合您的 UI 元素的方法。  
  
| 您的 UI | 方法 | 它們是什麼？ |  
| --- | --- | --- |  
| 具有內嵌或獨立的對話方塊。 | **系統色彩** | 允許定義的色彩及外觀的 UI 項目中，作業系統的系統名稱，例如通用對話方塊控制項。 |
| 自訂 UI，您想要與整體的 VS 環境一致且有符合的類別目錄和共用的語彙基元的語意的 UI 項目。 | **常見共用的色彩** | 現有的預先定義的色彩語彙基元名稱特定的 UI 元素 |
| 您有個別的功能的群組，而且沒有任何共用類似的項目色彩。 | **自訂色彩** | 色彩語彙基元名稱特定區域並不是用來與其他 UI 共用 |
| 您想要讓使用者自訂 UI 或內容 （例如，適用於文字編輯器或特製化的設計工具視窗）。 | **使用者自訂**<br /><br />**(工具&gt;選項 對話方塊)** | 設定"字型和色彩 」 頁面中定義**工具&gt;選項**對話方塊或一個 UI 功能的特定的頁面。 |
  
### <a name="visual-studio-themes"></a>Visual Studio 佈景主題  
Visual Studio 功能的三個不同的色彩佈景主題當中： 亮色、 暗色，及藍色。 它也會偵測高對比模式，這是專為協助工具設計全系統色彩佈景主題。  
  
使用者會提示您選取的佈景主題的 Visual Studio 的第一次使用時，可以稍後移至切換主題**工具&gt;選項&gt;環境&gt;一般**並選擇從新的佈景主題[色彩佈景主題] 下拉功能表中。  
  
使用者也可以使用控制台中，切換到一個數個高對比佈景主題的整個系統。 如果使用者選取 高對比佈景主題，然後 Visual Studio 色彩佈景主題選取器不會再影響色彩在 Visual Studio 中，雖然任何佈景主題變更會儲存為當使用者結束高對比模式。 如需高對比模式的詳細資訊，請參閱[選擇高對比色彩](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)。
  
### <a name="the-vscolor-service"></a>VSColor 服務  
Visual Studio 提供的環境色彩服務，稱為 「 VSColor 服務，可讓您將您的 UI 元素的色彩值繫結至具名的項目，其中包含每個 Visual Studio 佈景主題色彩值。 這可確保您的色彩會自動將變更以反映目前使用者選取的佈景主題或系統高對比模式。 使用服務表示的色彩佈景主題相關的所有變更的實作在一個地方，處理，而且如果您使用從服務的常見共用的色彩，您的 UI 會自動反映在未來版本的 Visual Studio 中的新主題。  
  
### <a name="implementation"></a>實作  
Visual Studio 原始程式碼包含數個封裝定義檔包含的語彙基元名稱以及每個主題的個別色彩值清單。 色彩服務讀取 VSColors 這些封裝定義檔中定義。 這些色彩是 XAML 標記中，或在程式碼中參考，然後透過載入`IVsUIShell5.GetThemedColor`方法或 DynamicResource 對應。  
  
### <a name="system-colors"></a>系統色彩  
通用控制項參考預設系統色彩。 如果您想要您的 UI 使用系統色彩，例如當您建立內嵌或獨立的對話方塊，您不需要執行任何動作。  
  
### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor 服務中的常見共用的色彩  
您的介面項目應該會反映整體 Visual Studio 環境。 重複使用適用於您正在設計的 UI 元件的常見共用的色彩，您可以確保您的介面與其他 Visual Studio 的介面，一致，且當新增或更新佈景主題色彩將會自動更新。  
  
之前使用常見共用的色彩，請確定您了解如何正確使用它們。 常見共用色彩的用法不正確可能會導致不一致，令人沮喪，或令人混淆的經驗，為您的使用者。  
  
### <a name="user-customizable-colors"></a>使用者可自訂的色彩  
請參閱：[適用於一般使用者公開色彩](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
有時候，您會想要允許使用者自訂 UI，例如當您建立程式碼編輯器或設計介面。 可自訂的 UI 元件位於**字型和色彩**區段**工具&gt;選項**對話方塊中，使用者可以選擇變更的前景色彩、 背景色彩，或兩者。  
  
![工具&gt;選項 對話方塊](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301 a_ToolsOptionsDialog")<br />工具&gt;選項 對話方塊
  
##  <a name="BKMK_TheVSColorService"></a>VSColor 服務  
Visual Studio 提供的環境色彩服務，也稱為 VSColor 服務或 shell 色彩服務。 此服務可讓您繫結至集，其中包含每個佈景主題色彩的名稱 / 值色彩的 UI 元素的色彩值。 VSColor 服務必須用於所有 UI 項目，使色彩會自動變更以反映目前使用者選取的佈景主題，並使 UI 繫結至環境色彩服務將會整合新的佈景主題在未來版本的 Visual Studio。  
  
### <a name="how-the-service-works"></a>服務的運作方式  
環境色彩服務讀取 VSColors UI 元件.pkgdef 中所定義。 這些 VSColors 被用在 XAML 標記或程式碼會載入及透過`IVsUIShell5.GetThemedColor`或`DynamicResource`對應。  
  
![環境色彩服務架構](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302 a_EnvironmentColorServiceArchitecture")<br />環境色彩服務架構
  
### <a name="accessing-the-service"></a>存取服務
有幾種不同方式 VSColor 服務，根據哪種色彩語彙基元您正在使用的存取權與您所擁有的程式碼類型為何。  

#### <a name="predefined-environment-colors"></a>預先定義的環境色彩  
  
##### <a name="from-native-code"></a>從原生程式碼  
在命令介面提供的服務，可讓`COLORREF`的色彩。 服務介面為：  
  
```  
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)  
```  
  
在檔案 VSShell80.idl，列舉`__VSSYSCOLOREX`具有殼層色彩常數。 若要使用它，請傳入做為索引值從值的其中一個`enum __VSSYSCOLOREX`記載在 MSDN 或一般的索引編號，Windows 系統應用程式開發介面， `GetSysColor`，接受。 如此一來取得回應該在第二個參數中使用的色彩的 RGB 值。  
  
如果儲存的畫筆或筆刷，新的色彩，您必須`AdviseBroadcastMessages`（從 Visual Studio shell) 和接聽`WM_SYSCOLORCHANGE`和`WM_THEMECHANGED`訊息。  
  
  
若要存取原生程式碼中的色彩服務，您將進行呼叫，看起來像這樣： 

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);    
```  

> **注意：** `COLORREF`所傳回的值`GetVSSysColorEx()`包含只 R、 G B 的佈景主題色彩的元件。 如果佈景主題的項目使用的透明度，alpha 色板值會被捨棄，再傳回。 因此，如果您感興趣的環境色彩需要用於重要透明通道所在的位置，您應該使用`IVsUIShell5.GetThemedColor`而不是`IVsUIShell2::GetVSSysColorEx`，如本主題稍後所述。  
  
##### <a name="from-managed-code"></a>從 managed 程式碼  
透過原生程式碼存取 VSColor 服務就相當簡單。 如果您正在執行 managed 程式碼，不過，決定如何使用服務可能很困難。 這一點之後，以下是 C# 程式碼片段示範此程序：  
  
```  
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)  
{  
    //getIVSUIShell2  
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;  
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");  
  
    if (uiShell2 != null)  
    {  
        //get the COLORREF structure  
        uint win32Color;  
        uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);  
  
        //translate it to a managed Color structure  
        Color myColor = ColorTranslator.FromWin32((int)win32Color);  
        //use it  
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);  
    }  
}  
```  
  
如果您使用 Visual Basic 中，使用：  
  
```  
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)  
```  
  
##### <a name="from-wpf-ui"></a>從 WPF UI  
您可以繫結至 Visual Studio 色彩值匯出到應用程式透過`ResourceDictionary`。 以下是使用色彩表中的資源，以及繫結至 XAML 中的環境字型資料的範例。  
  
```  
<Style TargetType="{x:Type Button}">  
    <Setter Property="TextBlock.FontFamily"  
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
    <Setter Property="TextBlock.FontSize"  
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
    <Setter Property="Background"  
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />  
</Style>  
```  
  
#### <a name="helper-classes-and-methods-for-managed-code"></a>Managed 程式碼的協助程式類別和方法  
Managed 程式碼，在 shell Managed Package Framework 程式庫 (`Microsoft.VisualStudio.Shell.12.0.dll`) 包含幾個協助程式類別有助於使用佈景主題色彩。  
  
中的協助程式方法`Microsoft.VisualStudio.Shell.VsColors`中 MPF 類別包含`GetThemedGDIColor()`和`GetThemedWPFColor()`。 這些 helper 方法會傳回做為佈景主題項目的色彩值`System.Drawing.Color`或`System.Windows.Media.Color`WinForms 或 WPF UI 中使用。  
  
```  
IVsUIShell5 shell5;  
Button button = new Button();  
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);  
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);  
  
/// <summary>  
/// Gets a System.Drawing.Color value from the current theme for the given color key.  
/// </summary>  
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>  
/// <param name="themeResourceKey">The key to find the color for.</param>  
/// <returns>The current theme's value of the named color.</returns>  
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Validate.IsNotNull(vsUIShell, "vsUIShell");  
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");  
  
   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);  
  
   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR  
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);  
}  
  
private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Guid category = themeResourceKey.Category;  
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground  
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)  
   {  
      colorType = __THEMEDCOLORTYPE.TCT_Background;  
   }  
  
   // This call will throw an exception if the color is not found  
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);  
   return BitConverter.GetBytes(rgbaColor);  
}  
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Validate.IsNotNull(vsUIShell, "vsUIShell");  
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");  
  
   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);  
  
    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);  
}    
```  
  
類別也可用來取得 VSCOLOR 識別項，指定 WPF 色彩資源索引鍵，反之亦然。  
  
```  
public static string GetColorBaseKey(int vsSysColor);  
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);  
```  
  
方法的`VsColors`類別查詢傳回的色彩值即會叫用每個時間 VSColor 服務。 若要取得色彩值，為`System.Drawing.Color`，效能更佳的替代方式是改用的方法`Microsoft.VisualStudio.PlatformUI.VSThemeColor`類別，會快取取得 VSColor 服務的色彩值。 此類別 shell 廣播的訊息事件，會在內部訂閱與佈景主題變更的事件發生時，就會捨棄快取的值。 此外，這個類別會提供。NET 易記佈景主題變更訂閱的事件。 使用`ThemeChanged`事件加入新的處理常式，並使用`GetThemedColor()`方法，以取得色彩值`ThemeResourceKeys`感興趣。 範例程式碼看起來可能像這樣：  
  
```  
public MyWindowPanel()  
{  
    InitializeComponent();  
  
    // Subscribe to theme changes events so we can refresh the colors  
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;  
  
    RefreshColors();  
}  
  
private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)  
{  
    RefreshColors();  
  
    // Also post a message to all the children so they can apply the current theme appropriately  
    foreach (System.Windows.Forms.Control child in this.Controls)  
    {  
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);  
    }  
}  
  
private void RefreshColors()  
{  
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);  
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);  
}  
  
protected override void Dispose(bool disposing)  
{  
    if (disposing)  
    {  
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;  
        base.Dispose(disposing);}  
}  
```  
  
##  <a name="BKMK_ChoosingHighContrastColors"></a>選擇高對比色彩  
  
### <a name="overview"></a>總覽  
Windows 會使用數種高對比系統層級主題增加文字、 背景和影像的色彩對比，讓項目會出現在螢幕上比較明顯。 為了協助工具，很重要，Visual Studio 介面項目時做出回應正確使用者切換至 高對比佈景主題。  
  
少數幾個系統色彩可以用於高對比佈景主題。 在選擇您的系統色彩名稱時，請記住下列秘訣：  
  
1.  **選擇具有相同的語意意義的系統色彩**色彩的項目。 比方說，如果您選擇高對比的色彩 視窗中的文字，使用 WindowText 和不 ControlText。  
  
2.  **選擇 前景/背景配對**一起或您將無法確定色彩選擇會在所有高對比佈景主題。  
  
3.  **判斷您的 UI 中哪些部分是最重要，並確認 [內容] 區域會突顯出來。**您將會遺失許多詳細資料，通常會區別色彩色調的些微差異，所以使用強式的框線色彩是通用定義內容區域，因為沒有任何不同的內容區域的色彩變化。  
  
### <a name="system-color-set"></a>系統色彩設定  
在資料表[WPF 團隊部落格： SystemColors 參考](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx)表示完整的系統色彩的名稱，與對應的色調顯示在每個主題。  
  
套用此限制的一組色彩至您的 UI 時*預期的是您將會遺失 「 標準 」 主題中的細節*。 以下是範例 UI 具有難以察覺的灰色色彩，可用來區別中工具視窗的區域。 當搭配相同的視窗顯示在 高對比模式中，您可以看到所有的背景是相同的色調，和那些區域的框線會以單獨的框線：  
  
![如何細微的詳細資料的範例在高對比遺失](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 a_PropertiesWindow")<br />高對比中不會遺失如何細微的詳細資料範例
  
#### <a name="choosing-text-colors-in-an-editor"></a>在編輯器中選取文字色彩  
彩色的文字會編輯器或設計介面上表示的意義，例如允許為了易於識別類似的項目群組。 高對比佈景主題，不過，您沒有區分三個以上的文字色彩的能力。 WindowText、 Graytext'> 和 HotTrackText 是 WindowBackground 表面上提供的唯一色彩。 因為您無法使用三個以上的色彩，請小心選擇您想要顯示在高對比模式中最重要的差異。  
  
色調每個允許編輯器介面，因為它們會出現在每個高對比佈景主題的語彙基元名稱：  
  
![高對比編輯器比較](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 b_HCEditorComparison")<br />高對比編輯器比較
  
藍色佈景主題的編輯器介面的範例：  
  
![藍色佈景主題的編輯器](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 c_EditorBlue")<br />藍色佈景主題的編輯器
  
![高對比 #1 佈景主題的編輯器](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 d_EditorHC1")<br />高對比 #1 佈景主題的編輯器
  
### <a name="usage-patterns"></a>使用模式
許多常見的 UI 項目已定義的高對比色彩。 您可以參考這些使用模式選擇自己的系統色彩名稱時，讓您的 UI 項目都符合類似的元件。  
  
| 系統色彩 | 使用量 |
| --- | --- |
| ActiveCaption | -使用中的 IDE 和 rafted 的視窗按鈕上暫留，然後按下字符<br />IDE 和 rafted 的視窗標題列背景<br />預設狀態列背景 |
| ActiveCaptionText | -使用中的 IDE 與 rafted 的視窗標題列前景 （文字和字符）<br />-背景和框線的動態顯示和按上的作用中視窗按鈕 |
| 控制項 | 下拉式方塊、 下拉式清單中，搜尋控制預設及停用背景，包括下拉式按鈕<br />停駐於目標按鈕的背景<br />命令列背景<br />工具視窗背景 |
| ControlDark | -IDE 背景<br />功能表和命令列的分隔符號<br />命令列框線<br />功能表陰影<br />-工具視窗索引標籤的預設和暫留框線和分隔符號<br />-文件也溢位按鈕的背景<br />停駐於目標字符邊界 |
| ControlDarkDark |-未取得焦點，選取文件 索引標籤視窗 |
| ControlLight |-自動隱藏 索引標籤框線<br />下拉式方塊和下拉式清單的框線<br />-停駐目標背景和框線 |
| ControlLightLight | -已選取，已取得焦點的暫時框線 |
| ControlText | 下拉式方塊和下拉式清單中的字符<br />工具視窗取消選取索引標籤文字 |
| Graytext'> |的框線、 下拉式清單圖像 （glyph）、 文字和功能表項目文字下拉式方塊和下拉式清單中已停用<br />-已停用功能表文字<br />搜尋控制項 '搜尋選項' 標頭文字<br />搜尋控制項區段分隔符號 |
| 反白顯示 | -所有暫留和已按下的背景和框線，除了下拉式方塊下拉式按鈕背景和文件以及溢位按鈕框線<br />-選取的項目背景 |
| HighlightText | -所有和已按下的 foregrounds （文字和字符）<br />-具有焦點的工具視窗與文件 索引標籤視窗控制項的前景<br />-具有焦點的工具視窗標題列框線<br />-已取得焦點，選取暫時性索引標籤前景<br />暫留，然後按上的文件以及溢位按鈕框線<br />-選取的圖示框線|
| HotTrack | -捲軸拇指背景和按上的框線<br />-捲軸箭號圖像上按下 |
| InactiveCaption | 為非作用中的 IDE 和 rafted 的視窗按鈕字符暫留時顯示<br />IDE 和 rafted 的視窗標題列背景<br />-已停用的搜尋控制項的背景 |
| InactiveCaptionText | 為非作用中的 IDE 和 rafted 的視窗標題列前景 （文字和字符）<br />為非作用中視窗按鈕的背景和暫留時顯示的框線<br />-未取得焦點的工具視窗 按鈕的背景和框線<br />-已停用的搜尋控制項的前景 |
| 功能表 | -下拉功能表背景<br />-已核對及已停用核取記號背景 |
| MenuText | -下拉功能表框線<br />-核取記號<br />功能表字符<br />-下拉功能表文字<br />-選取的圖示框線 |  
| 捲軸 | -捲動列和捲軸箭號背景，所有的狀態 |
| 視窗 | -自動隱藏 索引標籤的背景<br />功能表列和命令櫃背景<br />-未取得焦點或未選取的文件視窗索引標籤的背景，並開啟和暫時性索引標籤的文件框線<br />-未取得焦點的工具視窗標題列背景<br />工具視窗索引標籤背景，選取和取消選取 |
| WindowFrame | -IDE 框線 |
| WindowText | -自動隱藏 索引標籤前景<br />-選取的工具視窗索引標籤前景<br />-未取得焦點的文件視窗索引標籤和暫時性索引標籤未取得焦點或未選取前景<br />-樹狀檢視預設前景和暫留在未選取圖像 （glyph）<br />工具視窗選取的索引標籤框線<br />-捲軸拇指背景、 框線與圖像 （glyph） |
  
##  <a name="BKMK_ExposingColorsForEndUsers"></a>適用於一般使用者公開色彩  
  
### <a name="overview"></a>總覽  
有時您會想要允許使用者自訂 UI，例如當您在建立程式碼編輯器或設計介面時。 若要這樣做的最常見方式是使用**工具&gt;選項**對話方塊。 除非您有高特製化需要特殊控制項的 UI，來提供自訂的最簡單方式是透過**字型和色彩**頁面內**環境** 對話方塊的區段。 對於您公開自訂每個項目，使用者可以選擇變更的前景色彩、 背景色彩，或兩者。

### <a name="building-a-vspackage-for-your-customizable-colors"></a>建立 VSPackage，您可自訂的色彩  
VSPackage 可以控制的字型和色彩透過自訂類別，和字型和色彩 屬性頁上顯示的項目。 當使用這項機制，Vspackage 必須實作[IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx)介面和其相關聯的介面。  
  
基本上，此機制可用來修改所有現有的顯示項目和包含它們的類別。 不過，它不應修改的文字編輯器的類別目錄或其顯示的項目。 如需有關文字編輯器分類的詳細資訊，請參閱[字型和色彩概觀](../font-and-color-overview.md)。  
  
若要實作的自訂類別，或顯示項目，VSPackage 必須：  
  
-   **建立或識別登錄中的類別。** IDE 的實作**字型和色彩**屬性頁會使用此資訊正確查詢支援某個的類別的服務。  
  
-   **建立或識別 （選擇性） 在登錄中的群組。** 它可能會很有用定義一個群組，表示兩個或多個類別目錄的聯集。 如果定義群組，則 IDE 自動合併子類別目錄，並將發佈群組內的顯示項目。  
  
-   **實作 IDE 支援。**  
  
-   **處理字型和色彩的變更。**  
  
#### <a name="to-create-or-identify-categories"></a>若要建立或識別類別目錄  
建構類別下的登錄項目一種特殊型別的`[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]`其中`<Category>`為非當地語系化的類別目錄名稱。
  
填入具有兩個值的登錄：  

| 名稱 | 類型 | 資料 | 描述 |
| --- | --- | --- | --- |
| 分類 | REG_SZ | GUID | 若要識別類別目錄建立 GUID |
| Package | REG_SZ | GUID | 支援類別目錄之 VSPackage 服務 GUID |
  
 在登錄中指定的服務必須提供實作[IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)對應分類。  
  
#### <a name="to-create-or-identify-groups"></a>若要建立或識別群組  
建構類別下的登錄項目一種特殊型別的`[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]`其中`<group>`為非當地語系化的群組名稱。  
  
填入具有兩個值的登錄：

| 名稱 | 類型 | 資料 | 描述 |
|--- | --- | --- | --- |
| 分類 | REG_SZ | GUID | 若要識別類別目錄建立 GUID |
| Package | REG_SZ | GUID | 支援類別目錄之 VSPackage 服務 GUID |
  
在登錄中指定的服務必須提供實作`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`對應的群組。

![實作以得知是 IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304 a_FontAndColorGroup")<br />實作`IVsFontAndColorGroup`
  
### <a name="to-implement-ide-support"></a>若要實作 IDE 支援  
實作[GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx)，這會傳回[IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)介面或`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`介面，以便每個類別目錄 IDE 或群組提供的 GUID。  
  
它支援每個類別目錄，如需 VSPackage 實作的個別執行個體[IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)介面。  
  
方法實作透過[IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)必須提供此 IDE:  
  
-   顯示類別目錄中的項目清單  
  
-   可當地語系化的顯示項目名稱  
  
-   顯示每個成員的類別目錄資訊  
  
 > **注意：**每個類別目錄必須包含至少一個顯示項目。
  
IDE 使用`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`介面來定義數種類別的聯集。

它的實作會提供此 IDE:

-   指定群組所組成的分類清單  
  
-   存取的執行個體[IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)支援群組內的每個類別目錄  
  
-   可當地語系化的群組名稱  
  
#### <a name="updating-the-ide"></a>更新 IDE  
IDE 會快取的字型和色彩設定的相關資訊。 因此，IDE 字型和色彩設定的任何修改，確保最新的快取之後的最佳作法。  
  
更新快取透過[IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx)介面，並可以執行全域方式或只在選取的項目。  
  
### <a name="handling-font-and-color-changes"></a>處理字型和色彩的變更  
若要正確支援 VSPackage 顯示文字的顏色標示，支援 VSPackage 的顏色標示服務必須回應使用者起始所做的變更透過 [字型和色彩] 屬性頁面。  
  
若要這樣做，VSPackage 必須：  
  
-   **處理 IDE 所產生的事件**藉由實作[IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx)介面。 IDE 呼叫適當的方法遵循使用者修改的字型和色彩頁面。 例如，它會呼叫[OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx)方法，如果已選取新的字型。  
  
 **OR**  
  
-   **輪詢變更 IDE**。 這可以透過系統實作[IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx)介面。 雖然主要是針對支援的持續性， [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx)方法可以取得字型和色彩資訊顯示項目。 如需有關字型和色彩設定的詳細資訊，請參閱 MSDN 文章：[存取儲存的字型和色彩設定](../accessing-stored-font-and-color-settings.md)。  
  
> **注意：**若要確保輪詢結果正確無誤，請使用[IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx)介面，以判斷是否需要快取排清及更新之前呼叫的方法擷取[IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx)介面。
  
#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>註冊自訂的字型和色彩類別目錄，而不需要實作介面  
下列程式碼範例示範如何註冊自訂的字型和色彩類別目錄，而不需要實作介面：  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]  
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"  
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"  
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"  
  
    "NameID"=dword:00000064  
```  

這個程式碼範例：   
-   `"NameID"`= 在封裝中的當地語系化類別目錄名稱的資源識別碼
-   `"ToolWindowPackage"`= 封裝 GUID
-   `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"`只是範例和實際的值可以是實作器所提供的新 GUID。  
  
### <a name="set-the-font-and-color-property-category-guid"></a>設定字型和色彩屬性類別目錄 GUID  
下列程式碼範例將示範如何設定分類的 Guid。  
  
```  
// m_pView is your IVsTextView  
IVsTextEditorPropertyCategoryContainer spPropCatContainer =  
(IVsTextEditorPropertyCategoryContainer)m_pView;  
if (spPropCatContainer != null)  
{  
IVsTextEditorPropertyContainer spPropContainer;  
Guid GUID_EditPropCategory_View_MasterSettings =  
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");  
hr = spPropCatContainer.GetPropertyCategory(  
ref GUID_EditPropCategory_View_MasterSettings,  
out spPropContainer);  
if(hr == 0)  
{  
hr =  
spPropContainer.SetProperty(  
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,  
catGUID);  
hr =  
spPropContainer.SetProperty(  
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,  
catGUID);  
}  
}  
```  
