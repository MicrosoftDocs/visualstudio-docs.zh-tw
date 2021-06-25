---
title: Visual Studio 的色彩和樣式 |Microsoft Docs
description: 瞭解 Visual Studio 使用者體驗如何使用色彩作為通訊工具，而不是純粹美觀的原因。
ms.custom: SEO-VS-2020
ms.date: 07/31/2017
ms.topic: reference
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 307a4013c06258524c60619c6eff40e4d64740b6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904483"
---
# <a name="colors-and-styling-for-visual-studio"></a>適用於 Visual Studio 的色彩和樣式設定

## <a name="use-color-in-visual-studio"></a>在 Visual Studio 中使用色彩

在 Visual Studio 中，色彩主要是用來做為通訊工具，而不是作為裝飾。 使用色彩最少，並在您想要執行下列動作的情況下保留它：

- 傳達意義或關係 (例如平臺或語言修飾詞) 

- 吸引人注意 (例如，表示狀態變更) 

- 提高可讀性並提供流覽 UI 的地標

- 增加 desirability

有幾個選項可用來指派色彩給 Visual Studio 中的 UI 元素。 有時候，可能很難找出您應該使用哪一個選項，或如何正確使用它。 本主題將協助您：

- 瞭解用來在 Visual Studio 中定義色彩的不同服務和系統。

- 針對指定的元素，選取正確的選項。

- 正確地使用您選擇的選項。

> [!NOTE]
> 絕對不要將十六進位、RGB 或系統色彩硬式編碼到您的 UI 元素。 使用這些服務可彈性地調整色調。 此外，如果沒有此服務，您將無法利用 [VSColor 服務](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)的主題切換功能。

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>指派色彩給 Visual Studio 介面元素的方法

選擇最適合您 UI 元素的方法。

| 您的 UI | 方法 | 是哪兩種？ |
| --- | --- | --- |
| 您有內嵌或獨立的對話方塊。 | **系統色彩** | 系統名稱，可讓作業系統定義 UI 元素的色彩和外觀，例如通用對話方塊控制項。 |
| 您有想要與整體 VS 環境一致的自訂 UI，且您有符合共用權杖類別和語義意義的 UI 元素。 | **常見的共用色彩** | 特定 UI 元素的現有預先定義色彩標記名稱 |
| 您有個別的功能或一組功能，但類似的元素沒有共用的色彩。 | **自訂色彩** | 區域專屬的色彩標記名稱，而不想要與其他 UI 共用 |
| 您想要允許使用者自訂 UI 或內容 (例如，適用于文字編輯器或特製化設計工具視窗) 。 | **終端使用者自訂**<br /><br />**(工具 &gt; 選項] 對話方塊)** | 在 [ **工具 &gt; 選項** ] 對話方塊的 [字型和色彩] 頁面中定義的設定，或在一個 UI 功能專屬的特殊頁面上定義的設定。 |

### <a name="visual-studio-themes"></a>Visual Studio 主題

Visual Studio 有三種不同的色彩主題：淺色、深色和藍色。 它也會偵測高對比模式，這是專為輔助功能設計的全系統色彩主題。

系統會在使用者第一次使用 Visual Studio 時提示使用者選取主題，並且可以在稍後切換至 [ **工具 &gt; 選項 &gt; 環境 &gt; 一般** ]，然後從 [色彩主題] 下拉式功能表中選擇新的主題來切換主題。

使用者也可以使用主控台將其整個系統切換至數個高對比主題的其中一個。 如果使用者選取高對比主題，則 Visual Studio 色彩主題選取器將不再影響 Visual Studio 中的色彩，不過當使用者離開高對比模式時，會儲存任何主題變更。 如需高對比模式的詳細資訊，請參閱 [選擇高對比色彩](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)。

### <a name="the-vscolor-service"></a>VSColor 服務

Visual Studio 提供稱為 VSColor 服務的環境色彩服務，可讓您將 UI 元素的色彩值系結至包含每個 Visual Studio 主題色彩值的命名專案。 這可確保您的色彩會自動變更，以反映目前使用者選取的主題或系統高對比模式。 使用服務表示會在同一處處理所有主題相關色彩變更的執行，如果您使用來自服務的一般共用色彩，您的 UI 將會在未來的 Visual Studio 版本中自動反映新的主題。

### <a name="implementation"></a>實作

Visual Studio 的原始程式碼包含數個套件定義檔案，其中包含每個主題的標記名稱和個別色彩值的清單。 Color 服務會讀取這些封裝定義檔中定義的 VSColors。 這些色彩會在 XAML 標記或程式碼中參考，然後透過 `IVsUIShell5.GetThemedColor` 方法或 DynamicResource 對應來載入。

### <a name="system-colors"></a>系統色彩

通用控制項預設會參考系統色彩。 如果您想要讓 UI 使用系統色彩，例如建立內嵌或獨立對話方塊時，您不需要執行任何動作。

### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor 服務中的常見共用色彩

您的介面元素應該會反映整體的 Visual Studio 環境。 藉由重複使用適用于您所設計之 UI 元件的常見共用色彩，您可以確定您的介面與其他 Visual Studio 介面一致，而且在新增或更新主題時，會自動更新您的色彩。

使用常見的共用色彩之前，請確定您已瞭解如何正確使用它們。 常見共用色彩的使用不正確可能會導致使用者不一致、令人困惑或令人困惑的體驗。

### <a name="user-customizable-colors"></a>使用者可自訂的色彩

請參閱： [公開終端使用者的色彩](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

有時候，您會想要讓使用者自訂您的 UI，例如在建立程式碼編輯器或設計介面時。 可自訂的 UI 元件可在 [**工具 &gt; 選項**] 對話方塊的 [字型 **和色彩**] 區段中找到，使用者可以選擇變更前景色彩、背景色彩或兩者。

![工具 &gt; 選項對話方塊](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />工具 &gt; 選項對話方塊

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a> VSColor 服務

Visual Studio 提供環境色彩服務，也稱為 VSColor 服務或 shell color 服務。 這項服務可讓您將 UI 元素的色彩值系結至包含每個主題色彩的名稱/值色彩集。 VSColor 服務必須用於所有 UI 元素，以便讓色彩自動變更以反映目前使用者選取的主題，因此系結至環境色彩服務的 UI 將會與未來版本的 Visual Studio 中的新主題整合。

### <a name="how-the-service-works"></a>服務 的運作方式

環境色彩服務會讀取 .pkgdef 中針對 UI 元件定義的 VSColors。 然後，會在 XAML 標記或程式碼中參考這些 VSColors，並透過或對應來載入這些 `IVsUIShell5.GetThemedColor` `DynamicResource` 。

![環境色彩服務架構](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />環境色彩服務架構

### <a name="accessing-the-service"></a>存取服務

有幾種不同的方式可存取 VSColor 服務，視您使用的是哪種色彩標記以及您擁有的程式碼類型而定。

#### <a name="predefined-environment-colors"></a>預先定義的環境色彩

##### <a name="from-native-code"></a>從機器碼

Shell 提供的服務可提供色彩的存取權 `COLORREF` 。 服務/介面為：

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

在 VSShell80 檔案中，列舉 `__VSSYSCOLOREX` 具有 shell 色彩常數。 若要使用它，請以索引值形式傳入 MSDN 中記載的其中一個值， `enum __VSSYSCOLOREX` 或 Windows 系統 API 所接受的一般索引編號 `GetSysColor` 。 這樣做會取得應該在第二個參數中使用之色彩的 RGB 值。

如果使用新的色彩來儲存畫筆或筆刷，您必須 `AdviseBroadcastMessages` (off Visual Studio shell) 並接聽 `WM_SYSCOLORCHANGE` 和 `WM_THEMECHANGED` 訊息。

若要以機器碼存取 color 服務，您會進行類似下面的呼叫：

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> 所 `COLORREF` 傳回的值 `GetVSSysColorEx()` 只會包含 R、G、B 主題色彩的元件。 如果主題專案使用透明度，則會在傳回之前捨棄 Alpha 通道值。 因此，如果有興趣的環境色彩需要在透明通道很重要的地方使用，您應該改用 `IVsUIShell5.GetThemedColor` 而非 `IVsUIShell2::GetVSSysColorEx` ，如本主題稍後所述。

##### <a name="from-managed-code"></a>從 managed 程式碼

透過原生程式碼存取 VSColor 服務相當簡單。 但是，如果您正在處理 managed 程式碼，則判斷如何使用服務可能會很棘手。 記住這點之後，以下是示範此程式的 c # 程式碼片段：

```csharp
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell2.GetVSSysColorEx((int)__VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

如果您在 Visual Basic 中工作，請使用：

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>從 WPF UI

您可以透過匯出至應用程式的值來系結至 Visual Studio 色彩 `ResourceDictionary` 。 以下範例說明如何使用色彩資料表中的資源，以及如何在 XAML 中系結至環境字型資料。

```xml
<Style TargetType="{x:Type Button}">
    <Setter Property="TextBlock.FontFamily"
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
    <Setter Property="TextBlock.FontSize"
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />
    <Setter Property="Background"
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />
</Style>
```

#### <a name="helper-classes-and-methods-for-managed-code"></a>適用于 managed 程式碼的 Helper 類別和方法

針對 managed 程式碼，shell 的 Managed Package Framework 程式庫 (`Microsoft.VisualStudio.Shell.12.0.dll`) 包含一些協助程式類別，以促進主題色彩的使用。

`Microsoft.VisualStudio.Shell.VsColors`MPF 中類別的 helper 方法包括 `GetThemedGDIColor()` 和 `GetThemedWPFColor()` 。 這些 helper 方法會以或形式傳回主題專案的色彩 `System.Drawing.Color` 值 `System.Windows.Media.Color` ，以在 WINFORMS 或 WPF UI 中使用。

```csharp
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

類別也可以用來取得指定之 WPF 色彩資源索引鍵的 VSCOLOR 識別碼，反之亦然。

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

類別的方法 `VsColors` 會查詢 VSColor 服務，以在每次叫用時傳回色彩值。 為了取得的色彩值 `System.Drawing.Color` ，具有較佳效能的替代方法是改為使用類別的方法，以快取 `Microsoft.VisualStudio.PlatformUI.VSThemeColor` 從 VSColor 服務取得的色彩值。 類別會在內部訂閱 shell 廣播訊息事件，並在發生主題變更事件時捨棄快取的值。 此外，此類別也會提供。訂閱主題變更的網路易記事件。 使用 `ThemeChanged` 事件來加入新的處理常式，並使用 `GetThemedColor()` 方法來取得 `ThemeResourceKeys` 感興趣之的色彩值。 範例程式碼看起來會像這樣：

```csharp
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

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a> 選擇高對比色彩

### <a name="overview"></a>概觀

Windows 會使用數個高對比的系統層級主題，以增加文字、背景和影像的色彩對比，讓元素在螢幕上顯示得更相異。 基於協助工具的考慮，當使用者切換至高對比主題時，Visual Studio 介面元素必須正確回應，是很重要的。

只有少數系統色彩可以用於高對比主題。 選擇您的系統色彩名稱時，請記住下列秘訣：

- 選擇與您要著色的元素 **具有相同語義意義的系統色彩**。 比方說，如果您選擇的是視窗內文字的高對比色彩，請使用 WindowText 而不是 ControlText。

- **選擇 [前景]/[背景** 組]，就不會確信您的色彩選擇在所有高對比主題中都能正常運作。

- **判斷您的 UI 哪些部分是最重要的部分，並確保內容區域將會醒目提示。** 您將會遺失許多色彩色調差異通常會區分的詳細資料，因此使用強式框線色彩通常是用來定義內容區域，因為不同內容區域都沒有色彩變化。

### <a name="system-color-set"></a>系統色彩組

[ [WPF Team Blog： SystemColors 參考](/archive/blogs/wpf/systemcolors-reference) ] 中的資料表指出一組完整的系統色彩名稱，以及每個主題中顯示的對應色相。

將這組有限的色彩套用至您的 UI 時， *您應該會遺失出現在「一般」主題中的微妙詳細資料*。 以下是具有微妙灰色色彩的 UI 範例，可用來區別工具視窗內的區域。 當搭配高對比模式中顯示的相同視窗時，您可以看到所有背景都是相同的色調，而這些區域的框線會單獨以框線表示：

![如何在高對比中遺失微妙細節的範例](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />如何在高對比中遺失微妙細節的範例

#### <a name="choosing-text-colors-in-an-editor"></a>選擇編輯器中的文字色彩

以色彩標示文字是在編輯器或設計介面上用來表示意義，例如允許輕鬆識別類似專案的群組。 不過，在高對比主題中，您無法區分三種以上的文字色彩。 WindowText、GrayText 和 HotTrackText 是 WindowBackground 表面上唯一可用的色彩。 由於您無法使用三種以上的色彩，因此請小心選擇在高對比模式下要顯示的最重要差異。

編輯器介面上所允許的每個標記名稱的色調，因為它們出現在每個高對比主題中：

![高對比編輯器比較](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />高對比編輯器比較

藍色主題中的編輯器介面範例：

![藍色佈景主題的編輯器](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />藍色佈景主題的編輯器

![高對比 #1 主題中的編輯器](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />高對比 #1 主題中的編輯器

### <a name="usage-patterns"></a>使用模式

許多常見的 UI 元素已定義高對比的色彩。 您可以在選擇自己的系統色彩名稱時參考這些使用模式，讓您的 UI 元素與類似的元件一致。

| 系統色彩 | 使用方式 |
| --- | --- |
| ActiveCaption | -暫留和按下時使用中的 IDE 和 rafted 視窗按鈕圖像<br />-IDE 和 rafted 視窗的標題列背景<br />-預設狀態列背景 |
| ActiveCaptionText | -適用于標題列前景 (文字和字元的作用中 IDE 和 rafted 視窗) <br />-停留並按下使用中視窗按鈕的背景和框線 |
| 控制 | -下拉式方塊、下拉式清單，以及搜尋控制項預設和停用的背景，包括下拉式按鈕<br />-停駐目標按鈕背景<br />-命令列背景<br />-工具視窗背景 |
| ControlDark | -IDE 背景<br />-功能表和命令列分隔符號<br />-命令列框線<br />-功能表陰影<br />-工具視窗索引標籤預設和暫留框線和分隔符號<br />-檔溢位按鈕背景<br />-停駐目標字型框線 |
| ControlDarkDark |-未取得焦點，選取的檔索引標籤視窗 |
| ControlLight |-自動隱藏定位鍵框線<br />-下拉式方塊和下拉式清單方塊線<br />-停駐目標背景和框線 |
| ControlLightLight | -已選取，焦點的臨時框線 |
| ControlText | -下拉式方塊和下拉式清單字元<br />-未選取的工具視窗索引標籤文字 |
| GrayText |-下拉式方塊和下拉式清單停用的框線、下拉式圖像、文字和功能表項目文字<br />-已停用的功能表文字<br />-搜尋控制項的搜尋選項標頭文字<br />-搜尋控制項區段分隔符號 |
| 反白顯示 | -所有停留和按下的背景和框線，但下拉式方塊下拉式按鈕背景和檔溢位按鈕框線除外<br />-選取的專案背景 |
| HighlightText | -所有停留和按下的 foregrounds (文字和圖像) <br />焦點的工具視窗和檔索引標籤視窗控制項前景<br />焦點的工具視窗標題列框線<br />-焦點、選取的臨時索引標籤前景<br />-暫留和按下時，檔溢位按鈕框線<br />-選取的圖示框線|
| HotTrack | -按下捲軸捲軸的背景和框線<br />-按下捲軸箭號字元 |
| InactiveCaption | -暫止時，非使用中的 IDE 和 rafted 視窗按鈕字型<br />-IDE 和 rafted 視窗的標題列背景<br />-已停用搜尋控制項背景 |
| InactiveCaptionText | -非作用中的 IDE 和 rafted windows 標題列前景 (文字和圖像) <br />-暫止的非作用中視窗按鈕背景和框線<br />-未取得焦點工具視窗按鈕的背景和框線<br />-已停用搜尋控制項前景 |
| 功能表 | -下拉式功能表背景<br />-已核取和停用核取記號背景 |
| MenuText | -下拉式功能表框線<br />-核取記號<br />-功能表符號<br />-下拉式功能表文字<br />-選取的圖示框線 |
| 捲軸 | -捲軸和捲軸箭號背景、所有狀態 |
| 時間範圍 | -自動隱藏索引標籤背景<br />-功能表列和命令貨位背景<br />-針對開啟和暫時索引標籤的 [未取得焦點] 或 [未選取的文件視窗] 索引標籤背景和檔框線<br />-未取得焦點工具視窗標題列背景<br />-工具視窗索引標籤背景，已選取和未選取 |
| WindowFrame | -IDE 框線 |
| WindowText | -自動隱藏索引標籤前景<br />-選取的工具視窗索引標籤前景<br />-未取得焦點文件視窗索引標籤及未取得焦點或未選取的臨時索引標籤前景<br />-樹狀檢視預設前景，並將滑鼠停留在未選取的圖像上<br />-工具視窗選取的索引標籤框線<br />-捲軸捲軸的背景、框線和字元 |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a> 公開終端使用者的色彩

### <a name="overview"></a>概觀

有時候您會想要讓使用者自訂您的 UI，就像是在建立程式碼編輯器或設計介面時一樣。 最常見的方法是使用 [ **工具 &gt; 選項** ] 對話方塊。 除非您有需要特殊控制項的高度特製化 UI，否則呈現自訂最簡單的方式是透過對話方塊的 [**環境**] 區段內的 [字型]**和 [色彩**] 頁面。 針對您為了自訂而公開的每個專案，使用者可以選擇變更前景色彩、背景色彩或兩者。

### <a name="building-a-vspackage-for-your-customizable-colors"></a>建立可自訂色彩的 VSPackage

VSPackage 可以透過自訂類別來控制字型和色彩，並在 [字型和色彩] 屬性頁上顯示專案。 使用這種機制時，Vspackage 必須執行 [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) 介面及其相關聯的介面。

基本上，這個機制可以用來修改所有現有的顯示專案和包含它們的類別。 不過，它不應該用來修改文字編輯器類別或其顯示專案。 如需文字編輯器分類的詳細資訊，請參閱 [字型和色彩總覽](/previous-versions/visualstudio/visual-studio-2015/extensibility/font-and-color-overview?preserve-view=true&view=vs-2015)。

若要執行自訂類別或顯示專案，VSPackage 必須：

- **建立或識別登錄中的類別。** IDE 的 [字型 **和色彩** ] 屬性頁的執行會使用這項資訊，正確地查詢支援指定分類的服務。

- **在登錄中建立或識別群組 (選擇性) 。** 定義群組（代表兩個或多個類別的聯集）可能會很有用。 如果已定義群組，IDE 會自動合併子類別，並將顯示專案散發到群組中。

- **執行 IDE 支援。**

- **處理字型和色彩變更。**

#### <a name="to-create-or-identify-categories"></a>若要建立或識別類別

在底下建立類別目錄登錄專案的特殊類型， `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` 其中 `<Category>` 是分類的非當地語系化名稱。

以兩個值填入登錄：

| 名稱 | 類型 | 資料 | 描述 |
| --- | --- | --- | --- |
| 類別 | REG_SZ | GUID | 為了識別類別而建立的 GUID |
| 套件 | REG_SZ | GUID | 支援類別目錄的 VSPackage 服務 GUID |

 登錄中指定的服務必須為對應的分類提供 [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) 的執行。

#### <a name="to-create-or-identify-groups"></a>若要建立或識別群組

在下，建立類別目錄登錄專案的特殊類型， `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` 其中 `<group>` 是群組的非當地語系化名稱。

以兩個值填入登錄：

| 名稱 | 類型 | 資料 | 描述 |
|--- | --- | --- | --- |
| 類別 | REG_SZ | GUID | 為了識別類別而建立的 GUID |
| 套件 | REG_SZ | GUID | 支援類別目錄的 VSPackage 服務 GUID |

登錄中指定的服務必須提供對應群組的實作為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> 。

![得知是 ivsfontandcolorgroup 的執行](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />`IVsFontAndColorGroup` 的實作

### <a name="to-implement-ide-support"></a>若要執行 IDE 支援

針對所提供的每個類別或群組 GUID，執行 [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject)，以將 [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) 介面或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> 介面傳回至 IDE。

針對它支援的每個類別，VSPackage 會執行個別的 [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) 介面實例。

透過 [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) 所執行的方法必須提供 IDE：

- 類別目錄中顯示專案的清單

- 顯示專案的可當地語系化名稱

- 顯示每個類別成員的資訊

> [!NOTE]
> 每個類別都必須包含至少一個顯示專案。

IDE 會使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> 介面來定義數個類別的聯集。

它的實作為 IDE 提供：

- 組成指定群組的類別清單

- 存取支援群組內每個類別的 [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) 實例

- 可當地語系化的組名

#### <a name="updating-the-ide"></a>更新 IDE

IDE 會快取字型和色彩設定的相關資訊。 因此，在任何修改 IDE 字型和色彩設定之後，最好的做法是確保快取是最新的。

更新快取是透過 [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) 介面完成，而且可以在全域或只在選取的專案上執行。

### <a name="handling-font-and-color-changes"></a>處理字型和色彩變更

若要適當地支援 VSPackage 所顯示之文字的顏色標示，支援 VSPackage 的顏色標示服務必須透過 [字型] 和 [色彩] 屬性頁來回應使用者所起始的變更。

若要這樣做，VSPackage 必須：

- 藉由執行 [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents)介面來 **處理 IDE 產生的事件**。 IDE 會在使用者修改 [字型和色彩] 頁面之後，呼叫適當的方法。 例如，如果選取新的字型，則會呼叫 [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) 方法。

  **OR**

- **輪詢 IDE 的變更**。 這可以透過系統實行的 [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) 介面來完成。 雖然主要是為了支援持續性，但 [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) 方法可以取得顯示專案的字型和色彩資訊。 如需字型和色彩設定的詳細資訊，請參閱 MSDN 文章 [存取儲存的字型和色彩設定](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-stored-font-and-color-settings?preserve-view=true&view=vs-2015)。

> [!NOTE]
> 若要確保輪詢結果正確無誤，請在呼叫[IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage)介面的抓取方法之前，使用[IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager)介面判斷是否需要快取排清和更新。

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>註冊自訂字型和色彩類別而不執行介面

下列程式碼範例示範如何註冊自訂字型和色彩類別，而不需要執行介面：

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

針對此程式碼範例：

- `"NameID"` = 封裝中當地語系化分類名稱的資源識別碼
- `"ToolWindowPackage"` = 封裝 GUID
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` 只是一個範例，而實際值可以是實作者提供的新 GUID。

### <a name="set-the-font-and-color-property-category-guid"></a>設定字型和色彩屬性類別目錄 GUID

下列程式碼範例將示範設定分類 Guid。

```csharp
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
