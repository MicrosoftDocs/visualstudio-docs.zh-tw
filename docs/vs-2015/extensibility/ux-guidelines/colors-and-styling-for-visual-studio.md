---
title: 色彩與樣式
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 257c5944ee1939849c4163fef518abf513183998
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60095811"
---
# <a name="colors-and-styling-for-visual-studio"></a>色彩和樣式設定適用於 Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="using-color-in-visual-studio"></a>使用 Visual Studio 中的色彩
 在 Visual Studio 中，會使用主要是當做通訊工具，而不只是裝飾的色彩。 最少使用的色彩，並保留您想要的情況下：

- 傳達意義或關係 （例如，平台或語言修飾詞）

- 吸引注意 （例如，表示狀態變更）

- 改善可讀性，並提供用於巡覽 UI 的地標

- 增加的符合度

  有數個選項將色彩指派給在 Visual Studio 中的 UI 項目。 有時候很難圖出哪一個選項您應該使用，或如何正確使用它。 本主題將協助您：

1. 了解不同的服務和系統用來在 Visual Studio 中定義的色彩。

2. 選取正確的選項，針對指定的項目。

3. 正確地使用您選擇的選項。

   **重要：** 永遠不會硬式編碼十六進位、 RGB 或系統來將 UI 元素的色彩。 使用服務用來微調 hue 的彈性。 此外，但服務不會，您將無法利用的佈景主題切換功能[The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>將色彩指派給 Visual Studio 介面項目方法
 選擇最適合您的 UI 元素的方法。

|您的 UI|方法|什麼是它們？|
|-------------|------------|--------------------|
|具有內嵌或獨立的對話方塊。|**系統色彩**|系統允許作業系統定義的色彩及外觀的 UI 項目，例如的通用對話方塊控制項的名稱。|
|您有想要與整體的 VS 環境保持一致的自訂 UI，您有符合的類別目錄和共用的語彙基元的語意意義的 UI 項目。|**常見共用的色彩**|現有的預先定義的色彩語彙基元名稱的特定 UI 項目|
|您有個別的功能的群組，並針對類似的項目沒有共用的色彩。|**自訂色彩**|特定的區域並不是用來與其他 UI 共用的色彩語彙基元名稱|
|您想要允許使用者在自訂 UI 或內容 （例如，針對在文字編輯器或特製化的設計工具視窗）。|**使用者自訂**<br /><br /> **(工具 > [選項] 對話方塊)**|「 字型和色彩 」 頁面中定義的設定**工具 > 選項**對話方塊或特製化的一個 UI 功能的特定頁面。|

### <a name="visual-studio-themes"></a>Visual Studio 佈景主題
 Visual Studio 功能的三個不同的色彩佈景主題： 亮色、 暗色，及藍色。 它也會偵測高對比模式中，也就是針對協助工具設計全系統色彩佈景主題。

 使用者在他們的 Visual Studio 的第一次使用期間選取的佈景主題系統提示時，可以稍後前往中切換佈景主題**工具 > 選項 > 環境 > 一般**從"色彩佈景主題 」 下拉式功能表中選擇新的佈景主題。

 使用者也可以使用控制台，切換到數個高對比佈景主題的其中一個的整個系統。 如果使用者選取高對比佈景主題，然後 Visual Studio 色彩佈景主題選取器不會再影響色彩，在 Visual Studio 中，雖然使用者結束高對比模式時，將會儲存供的佈景主題中的任何變更。 如需有關高對比模式的詳細資訊，請參閱[選擇高對比色彩](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)。

### <a name="the-vscolor-service"></a>VSColor service
 Visual Studio 提供稱為 VSColor service，可讓您繫結至具名的項目，其中包含每個 Visual Studio 佈景主題色彩值的色彩值，您的 UI 項目的環境色彩服務。 這可確保您的色彩會自動將變更以反映目前使用者選取的佈景主題或系統高對比模式。 使用服務表示的色彩佈景主題相關的所有變更的實作會處理在一個地方，而且如果您使用從服務的常見共用的色彩，您的 UI 會自動反映新的佈景主題的 Visual Studio 的未來版本中。

### <a name="implementation"></a>實作
 Visual Studio 原始程式碼包含數個封裝定義檔包含的語彙基元名稱和每個佈景主題的個別色彩值清單。 色彩服務會讀取這些封裝定義檔中定義 VSColors。 這些色彩是參考 XAML 標記或程式碼，然後再載入透過**IVsUIShell5.GetThemedColor**方法或 DynamicResource 對應。

### <a name="system-colors"></a>系統色彩
 通用控制項參考預設系統色彩。 如果您想要將使用者介面和使用系統色彩，例如當您建立內嵌或獨立 對話方塊中，您不需要採取任何動作。

### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor service 中的常見共用的色彩
 您的介面項目應反映出整體的 Visual Studio 環境。 藉由重複使用常見共用的色彩適用於您正在設計的 UI 元件，您可以確保您的介面與其他 Visual Studio 介面中，一致，並新增或更新佈景主題時您的色彩將會自動更新。

 之前使用常見共用的色彩，請確定您了解如何正確使用它們。 常見共用色彩的用法不正確可能會導致不一致，令人沮喪，或令人困惑的體驗，為您的使用者。

### <a name="user-customizable-colors"></a>使用者可自訂的色彩
 請參閱：[公開使用者的色彩](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

 有時候，您要允許使用者在自訂 UI，例如建立程式碼編輯器或設計介面。 可自訂的 UI 元件位於**字型和色彩**一節**工具 > 選項**對話方塊中，使用者可以選擇變更的前景色彩、 背景色彩，或兩者。

 ![工具&#62;在 Visual Studio 中的 [選項] 對話方塊](../../extensibility/ux-guidelines/media/0301-a-toolsoptionsdialog.png "0301 a_ToolsOptionsDialog")

 **工具 > [選項] 對話方塊**

## <a name="BKMK_TheVSColorService"></a> VSColor Service
 Visual Studio 提供的環境色彩服務，也稱為 VSColor service 或殼層色彩服務。 這項服務可讓您將 UI 元素的色彩值繫結為集，其中包含每個佈景主題色彩的名稱 / 值色彩。 VSColor service 必須用於所有的 UI 項目，以便色彩會自動變更以反映目前的使用者選取主題，並使 UI 繫結至環境色彩服務將與整合新的佈景主題在未來版本的 Visual Studio。

### <a name="how-the-service-works"></a>服務的運作方式
 環境色彩服務讀取 VSColors UI 元件.pkgdef 中所定義。 這些 VSColors 接著會參考 XAML 標記或程式碼，並會透過載入**IVsUIShell5.GetThemedColor**或 DynamicResource 對應。

 ![環境色彩服務架構](../../extensibility/ux-guidelines/media/0302-a-environmentcolorservicearchitecture.png "0302 a_EnvironmentColorServiceArchitecture")

 **環境色彩服務架構**

### <a name="accessing-the-service"></a>存取服務
 有幾種不同方式 VSColor service，取決於何種色彩語彙基元您正在使用的存取，而且您有何種程式碼。

#### <a name="predefined-environment-colors"></a>預先定義的環境色彩

##### <a name="from-native-code"></a>從原生程式碼
 Shell 提供可存取的色彩 COLORREF 服務。 服務/介面是：

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

 在檔案 VSShell80.idl，列舉 **__VSSYSCOLOREX**具有 shell 色彩常數。 若要使用它，索引值，其中一項的值記載於 MSDN 列舉 __VSSYSCOLOREX 或一般的索引編號，Windows 系統 API，傳入**GetSysColor**，接受。 如此一來取得回應該在第二個參數中使用的色彩的 RGB 值。

 如果儲存的畫筆或新的色彩的筆刷，您必須 AdviseBroadcastMessages （離開 Visual Studio shell)，並接聽 WM_SYSCOLORCHANGE 和 WM_THEMECHANGED 訊息。

```
// To access the color service in native code, you'll make a call that resembles this:
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);

```

 **注意：** 所傳回的值 COLORREF **GetVSSysColorEx()** 包含只是 R、 G、 B 元件的佈景主題色彩。 如果佈景主題項目使用透明度的 alpha 色頻值會被捨棄之前傳回。 因此，如果感興趣的環境色彩需要使用在其中透明通道是重要的地方，您應該使用 IVsUIShell5.GetThemedColor 代替 IVsUIShell2::GetVSSysColorEx，本主題稍後所述。

##### <a name="from-managed-code"></a>從 managed 程式碼
 透過原生程式碼存取 VSColor service 就相當簡單。 如果您正在透過 managed 程式碼，不過，決定如何使用服務可能很難。 這一點之後，以下是 C# 程式碼片段示範此程序：

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
 您可以繫結至 Visual Studio 色彩透過匯出到應用程式的資源字典的值。 以下是使用色彩表的資源，以及繫結至 XAML 中的環境字型資料的範例。

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
 Managed 程式碼，命令介面的 Managed Package Framework 程式庫 (Microsoft.VisualStudio.Shell.12.0.dll) 會包含幾個協助程式類別，可促進使用佈景主題色彩。

 中的協助程式方法**Microsoft.VisualStudio.Shell.VsColors** MPF 類別包含**GetThemedGDIColor()** 並**GetThemedWPFColor()**。 這些協助程式方法會傳回為 System.Drawing.Color 或 System.Windows.Media.Color，用於 WinForms 或 WPF UI 佈景主題項目的色彩值。

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

 類別也可用來取得 VSCOLOR 識別項，指定 WPF 色彩資源金鑰，反之亦然。

```
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

 方法**VsColors**類別查詢傳回的色彩值每次叫用這些 VSColor service。 若要取得色彩值做為**System.Drawing.Color**，效能更佳的替代方案是改用的方法**Microsoft.VisualStudio.PlatformUI.VSThemeColor**類別，哪一個快取從 VSColor service 取得色彩值。 此類別會訂閱 shell 廣播的訊息的事件，在內部，而且佈景主題變更的事件發生時，就會捨棄快取的值。 此外，這個類別會提供。NET 友善佈景主題變更訂閱的事件。 使用  **ThemeChanged**事件新增處理常式，並使用**GetThemedColor()** 方法，以取得色彩值**ThemeResourceKeys**感興趣。 範例程式碼看起來像這樣：

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

## <a name="BKMK_ChoosingHighContrastColors"></a> 選擇高對比色彩

### <a name="overview"></a>總覽
 Windows 會使用數個高對比系統層級佈景主題，增加文字、 背景和影像的色彩對比，讓出現在螢幕上多不同的項目。 基於協助工具，請務必 Visual Studio 介面項目正確回應時使用者切換至 高對比佈景主題。

 只有少數幾種系統色彩可以用於高對比佈景主題。 選擇您的系統色彩的名稱，請記住下列秘訣：

1. **選擇具有相同的語意意義的系統色彩**著色的項目。 比方說，如果您選擇高對比的色彩 視窗中的文字，便需要使用 WindowText 和不 ControlText。

2. **選擇 前景/背景配對**一起或您將不會確定您的色彩選擇可在所有的高對比佈景主題。

3. **判斷您的 UI 中哪些部分最重要的並確定 [內容] 區域會突顯出來。** 因為沒有任何不同的內容區域的色彩變化，因此使用強式的框線色彩來定義內容區域，常見，就會遺失許多通常會區分色彩色調的細微差異的詳細資料。

### <a name="system-color-set"></a>系統色彩設定
 在資料表[WPF 團隊部落格：SystemColors 參考](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx)表示一組完整的系統色彩的名稱，以及對應的色調顯示在每個佈景主題。

 當套用這個有限的一組在 ui 中，色彩*預計將會遺失微妙的細節，原本在 「 標準 」 佈景主題中*。 以下是範例 UI 具有難以察覺的灰色色彩，用於區別的工具視窗內的區域。 與同一個視窗顯示高對比模式中搭配時，您可以看到所有的背景是相同的色調，這些區域的框線會以單獨的框線：

 ![屬性視窗](../../extensibility/ux-guidelines/media/030303-a-propertieswindow.png "030303 a_PropertiesWindow")

 **在 高對比如何微妙的細節的範例都會遺失**

#### <a name="choosing-text-colors-in-an-editor"></a>選擇在編輯器中的文字色彩
 彩色的文字來在編輯器或設計介面上表示意義，例如允許易於識別相似項目的群組。 高對比佈景主題，不過，您沒有能夠區別三個以上的文字色彩。 WindowText、 GrayText HotTrackText 等 WindowBackground 介面上提供的唯一色彩。 因為您無法使用三個以上的色彩，請小心選擇您想要在高對比模式中顯示最重要的差異。

 針對每個允許編輯器介面，因為它們會出現在每個高對比佈景主題的語彙基元名稱的色調：

 ![高對比編輯器比較](../../extensibility/ux-guidelines/media/030303-b-hceditorcomparison.png "030303 b_HCEditorComparison")

 **高對比編輯器比較**

 藍色佈景主題編輯器介面的範例：

 ![藍色佈景主題編輯器](../../extensibility/ux-guidelines/media/030303-c-editorblue.png "030303 c_EditorBlue")

 **藍色佈景主題編輯器**

 ![高對比佈景主題編輯器](../../extensibility/ux-guidelines/media/030303-d-editorhc1.png "030303 d_EditorHC1")

 **高對比 #1 佈景主題的編輯器**

### <a name="usage-patterns"></a>使用模式
 許多常見的 UI 項目已定義的高對比色彩。 您可以參考這些使用模式選擇您自己的系統色彩名稱時，讓您的 UI 項目都必須配合類似的元件。

|系統色彩|使用量|
|------------------|-----------|
|ActiveCaption|-使用中的 IDE 和 rafted 的視窗按鈕上暫留和按下的圖像 （glyph）<br />IDE 和 rafted 的視窗的標題列背景<br />預設狀態列背景|
|ActiveCaptionText|-使用中的 IDE 與 rafted 的視窗標題列前景 （文字和圖像 （glyph））<br />-背景和框線上暫留和按下的使用中視窗按鈕|
|控制項|-下拉式方塊、 下拉式清單中，並搜尋控制預設和已停用的背景，包括下拉式按鈕<br />-停駐目標按鈕背景<br />命令列背景<br />工具視窗背景|
|ControlDark|-IDE 背景<br />功能表和命令列的分隔符號<br />命令列框線<br />功能表遮蔽<br />-工具視窗索引標籤的預設和暫留時框線和分隔符號<br />-文件也溢位按鈕的背景<br />-停駐目標圖像 （glyph） 的框線|
|ControlDarkDark|-未取得焦點，選取文件 索引標籤視窗|
|ControlLight|-自動隱藏索引標籤的框線<br />下拉式方塊和下拉式清單中的框線<br />-停駐目標背景和框線|
|ControlLightLight|-已選取，已取得焦點的暫時框線|
|ControlText|下拉式方塊和下拉式清單中的字符<br />工具視窗中未選取索引標籤文字|
|GrayText|下拉式方塊和下拉式清單停用框線、 下拉式清單中的圖像 （glyph）、 文字和功能表項目文字<br />-已停用的功能表文字<br />搜尋控制項 '搜尋選項' 標頭文字<br />搜尋控制項區段分隔符號|
|反白顯示|-All 暫留和背景和框線，除了下拉式方塊下拉式清單中，按下按鈕的背景和文件也會溢位按鈕框線<br />-選取的項目背景|
|HighlightText|-所有暫留和已按下的 foregrounds （文字和圖像 （glyph））<br />-具有焦點的工具視窗和文件 索引標籤視窗控制項的前景<br />-具有焦點的工具視窗標題列框線<br />-具有焦點，選取佈建 索引標籤前景<br />上暫留和按下的文件以及溢位按鈕框線<br />-選取的圖示框線|
|HotTrack|-捲軸捲動方塊的背景，並按下的框線<br />-按下的捲軸箭號圖像|
|InactiveCaption|為非作用中的 IDE 和 rafted 的視窗按鈕暫留時顯示的圖像 （glyph）<br />IDE 和 rafted 的視窗的標題列背景<br />-已停用的搜尋控制項背景|
|InactiveCaptionText|為非作用中的 IDE 和 rafted 的視窗的標題列前景 （文字和圖像 （glyph））<br />為非使用中視窗按鈕的背景和暫留時的框線<br />-未取得焦點的工具視窗 按鈕的背景和框線<br />-已停用的搜尋控制項的前景|
|功能表|-下拉式清單功能表背景<br />-已核取並且停用核取記號背景|
|MenuText|-下拉式清單功能表框線<br />-核取記號核取<br />功能表圖像 （glyph)<br />-下拉式清單功能表文字<br />-選取的圖示框線|
|捲軸|-捲軸] 和 [捲軸箭號背景，所有狀態|
|視窗|-自動隱藏 索引標籤背景<br />功能表列，然後命令櫃背景<br />-未取得焦點或未選取的文件視窗索引標籤的背景，並開啟和取得暫時性的索引標籤的文件框線<br />-未取得焦點的工具視窗標題列背景<br />工具視窗索引標籤的背景，兩者都選取，並取消選取|
|WindowFrame|-IDE 框線|
|WindowText|-自動隱藏 索引標籤前景<br />-選取的工具視窗索引標籤前景<br />-未取得焦點的文件視窗索引標籤和未取得焦點或未選取佈建 索引標籤前景<br />-樹狀檢視的預設前景和暫留時透過未選取圖像 （glyph）<br />-選取索引標籤的框線工具視窗。<br />-捲軸捲動方塊的背景、 框線及圖像 （glyph）|

## <a name="BKMK_ExposingColorsForEndUsers"></a> 公開使用者的色彩

### <a name="overview"></a>總覽
 有時候，您要允許使用者在自訂 UI，例如建立程式碼編輯器或設計介面。 若要這樣做的最常見方式是使用**工具 > 選項**對話方塊。 除非您具備高度特殊需要特殊的控制項的 UI，來呈現自訂最簡單的方式是透過**字型和色彩**頁面內**環境**對話方塊區段。 對於您公開自訂每個項目，使用者可以選擇變更的前景色彩、 背景色彩，或兩者。

### <a name="building-a-vspackage-for-your-customizable-colors"></a>建置自訂色彩的 VSPackage
 VSPackage 可以控制的字型和色彩，透過自訂分類，和 [字型和色彩] 屬性頁上顯示的項目。 當使用這項機制，必須實作 Vspackage [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx)介面和其相關聯的介面。

 基本上，這項機制可用來修改所有現有的顯示項目和包含它們的類別。 不過，它應該不會用來修改文字編輯器 類別或其顯示項目。 如需文字編輯器 類別的詳細資訊，請參閱[字型和色彩概觀](https://msdn.microsoft.com/library/bb165065.aspx)。

 若要實作自訂類別，或顯示的項目，VSPackage 必須：

- **建立或識別登錄中的類別。** IDE 的實作**字型和色彩**屬性頁會使用此資訊正確查詢服務，支援指定的類別。

- **建立或識別登錄 （選擇性） 中的群組。** 它可能是適合用來定義群組，這代表兩個或多個類別的聯集。 如果定義群組，則 IDE 會自動合併子類別，並且會顯示群組內的項目。

- **實作 IDE 支援。**

- **處理字型和色彩的變更。**

#### <a name="to-create-or-identify-categories"></a>若要建立或識別分類
 建構一種特殊的類別目錄下的登錄項目 [HKLM\SOFTWARE\Microsoft \Visual Studio\\< 的 Visual Studio 版本\>\FontAndColors\\< 分類\>]。 \<類別目錄 > 類別目錄的非當地語系化名稱。

 填入登錄中的以兩個值：

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|分類|REG_SZ|GUID|若要識別類別目錄建立 GUID|
|套件|REG_SZ|GUID|服務的 GUID VSPackage 支援類別|

 在登錄中指定的服務必須提供實作[IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)對應分類。

#### <a name="to-create-or-identify-groups"></a>若要建立或識別群組
 建構一種特殊的類別目錄下的登錄項目 [HKLM\SOFTWARE\Microsoft \Visual Studio\\< 的 Visual Studio 版本\>\FontAndColors\\< 群組\>]。 \<群組 > 群組的非當地語系化名稱。

 填入登錄中的以兩個值：

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|分類|REG_SZ|GUID|若要識別類別目錄建立 GUID|
|套件|REG_SZ|GUID|服務的 GUID VSPackage 支援類別|

 在登錄中指定的服務必須提供實作**T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup**對應的群組。

 ![IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a-fontandcolorgroup.png "0304-a_FontAndColorGroup")

### <a name="to-implement-ide-support"></a>若要實作 IDE 支援
 實作[GetObject](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx)，這會傳回[IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)介面或有**T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup**針對每個類別或群組 GUID 提供 IDE 介面。

 它支援每個類別目錄，VSPackage 實作的個別執行個體[IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)介面。

 透過實作的方法[IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)必須提供具有的 IDE:

- 顯示分類中的項目清單

- 顯示項目的可當地語系化的名稱

- 針對每個類別成員的顯示資訊

  **注意：** 每個類別目錄必須包含至少一個顯示項目。

  IDE 使用**T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup**介面來定義數個類別的聯集。

  它的實作提供的 IDE:

- 指定群組所組成的分類清單

- 存取的執行個體[IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)支援群組內的每個類別目錄

- 可當地語系化的群組名稱

#### <a name="updating-the-ide"></a>更新 IDE
 IDE 會快取的字型和色彩設定的相關資訊。 因此，在 IDE 字型和色彩設定的任何修改之後, 確保最新的快取是最佳的作法。

 更新快取透過[IvsFontAndColorCacheManager](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx)介面，而且可以是執行全域方式或只在選取的項目。

### <a name="handling-font-and-color-changes"></a>處理變更字型和色彩
 若要正確支援 VSPackage 顯示文字的顏色標示，支援 VSPackage 的顏色標示服務必須回應使用者起始所做的變更透過 [字型和色彩] 屬性頁面。

 若要這樣做，VSPackage 必須：

- **處理 IDE 所產生的事件**藉由實作[IVsFontAndColorEvents](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx)介面。 IDE 呼叫適當的方法，下列字型和色彩頁面的使用者修改。 比方說，它會呼叫[OnFontChanged](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx)方法如果在選取新的字型。

  **或**

- **輪詢變更 IDE**。 這可透過系統實作[IVsFontAndColorStorage](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx)介面。 主要目的是為了支援持續性，雖然[GetItem](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx)方法可以取得顯示項目的字型和色彩資訊。 如需有關字型和色彩設定的詳細資訊，請參閱 MSDN 文章[存取儲存的字型和色彩設定](https://msdn.microsoft.com/library/bb166382.aspx)。

  **注意：** 若要確保輪詢結果正確無誤，請使用[IVsFontAndColorCacheManager](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx)介面，以決定在呼叫的擷取方法之前是否需要快取排清和更新[IVsFontAndColorStorage](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx)介面。

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>註冊自訂的字型和色彩類別目錄，而不需要實作介面
 下列程式碼範例示範如何註冊自訂的字型和色彩而不需要實作介面的類別：

```xml
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

 **注意：**

- 「 NameID 」 = 在套件中的當地語系化類別目錄名稱的資源識別碼

- 「 ToolWindowPackage"= 封裝 GUID

- [類別] ="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"是只是範例，實際的值可以是實作者所提供的新 GUID。

### <a name="set-the-font-and-color-property-category-guid"></a>設定字型和色彩屬性類別 GUID
 下列程式碼範例將示範如何設定分類的 Guid。

```cs
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
  IVsTextEditorPropertyContainer spPropContainer;
  Guid GUID_EditPropCategory_View_MasterSettings =
  new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
  hr = spPropCatContainer.GetPropertyCategory(
  ref GUID_EditPropCategory_View_MasterSettings, out spPropContainer);
  if(hr == 0)
  {
    hr = spPropContainer.SetProperty(VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory, catGUID);
    hr = spPropContainer.SetProperty(VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory, catGUID);
  }
}
```
