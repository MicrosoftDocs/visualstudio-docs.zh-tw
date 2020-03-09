---
title: Visual Studio 的色彩和樣式 |Microsoft Docs
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ceea00a3fa77a9c1106f24f28ac1d5890437b41
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409006"
---
# <a name="colors-and-styling-for-visual-studio"></a>Visual Studio 的色彩和樣式

## <a name="use-color-in-visual-studio"></a>在 Visual Studio 中使用色彩

在 Visual Studio 中，色彩主要是做為通訊工具使用，而不是作為裝飾。 使用 [最低色彩]，並在您想要執行的情況下保留它：

- 溝通意義或關係（例如，平臺或語言修飾詞）

- 吸引人注意（例如，表示狀態變更）

- 改善可讀性並提供流覽 UI 的地標

- 增加 desirability

有數個選項可用來將色彩指派給 Visual Studio 中的 UI 元素。 有時候，可能很難以找出您應該使用的選項，或如何正確地使用它。 本主題將協助您：

- 瞭解用來在 Visual Studio 中定義色彩的不同服務和系統。

- 針對指定的元素選取正確的選項。

- 正確地使用您所選擇的選項。

> [!NOTE]
> 絕對不要將十六進位、RGB 或系統色彩硬式編碼到您的 UI 元素。 使用這些服務可彈性地調整色調。 此外，如果沒有此服務，您將無法利用[VSColor 服務](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)的主題切換功能。

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>將色彩指派給 Visual Studio 介面元素的方法

選擇最適合您的 UI 元素的方法。

| 您的 UI | 方法 | 這是什麼？ |
| --- | --- | --- |
| 您有內嵌或獨立的對話方塊。 | **系統色彩** | 系統名稱，可讓作業系統定義 UI 元素的色彩和外觀，例如一般對話方塊控制項。 |
| 您有想要與整體 VS 環境一致的自訂 UI，而且您有符合共用標記之類別和語義意義的 UI 元素。 | **一般共用色彩** | 特定 UI 元素的現有預先定義色彩標記名稱 |
| 您有個別的功能或一組功能，但沒有類似元素的共用色彩。 | **自訂色彩** | 區域特有的色彩標記名稱，而非與其他 UI 共用 |
| 您想要允許使用者自訂 UI 或內容（例如，針對文字編輯器或特殊設計工具視窗）。 | **使用者自訂**<br /><br />**（工具 &gt; 選項 對話方塊）** | [**工具] &gt; [選項**] 對話方塊的 [字型和色彩] 頁面中所定義的設定，或是一個 UI 功能特定的特殊頁面。 |

### <a name="visual-studio-themes"></a>Visual Studio 主題

Visual Studio 有三種不同的色彩主題：淺色、深色和藍色。 它也會偵測高對比模式，這是專為輔助功能而設計的全系統色彩主題。

使用者在第一次使用 Visual Studio 時，系統會提示他們選取主題，而且稍後可以前往 [工具] [ **&gt; 選項] &gt; [環境] &gt; [一般**]，然後從 [色彩主題] 下拉式功能表中選擇新的主題，以切換主題。

使用者也可以使用 [控制台]，將其整個系統切換成數個高對比主題的其中一個。 如果使用者選取高對比主題，則 Visual Studio 色彩主題選取器不會再影響 Visual Studio 中的色彩，不過當使用者結束高對比模式時，會儲存任何主題變更。 如需高對比模式的詳細資訊，請參閱[選擇高對比色彩](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)。

### <a name="the-vscolor-service"></a>VSColor 服務

Visual Studio 提供稱為「VSColor 服務」的環境顏色服務，可讓您將 UI 元素的色彩值系結到包含每個 Visual Studio 主題之色彩值的名稱專案。 這可確保您的色彩會自動變更，以反映目前使用者選取的主題或系統高對比模式。 使用此服務表示所有主題相關色彩變更的執行都會在一個位置處理，而且如果您使用服務的一般共用色彩，您的 UI 就會自動反映 Visual Studio 未來版本中的新主題。

### <a name="implementation"></a>實作

Visual Studio 的原始程式碼包含數個套件定義檔案，其中包含每個主題的標記名稱和個別色彩值的清單。 色彩服務會讀取這些套件定義檔中定義的 VSColors。 這些色彩會在 XAML 標記或程式碼中參考，然後透過 `IVsUIShell5.GetThemedColor` 方法或 DynamicResource 對應來載入。

### <a name="system-colors"></a>系統色彩

通用控制項預設會參考系統色彩。 如果您想要讓 UI 使用系統色彩，例如當您建立內嵌或獨立對話時，就不需要執行任何動作。

### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor 服務中的一般共用色彩

您的介面元素應該反映整體的 Visual Studio 環境。 藉由重複使用適用于您所設計之 UI 元件的一般共用色彩，您可以確保您的介面與其他 Visual Studio 介面一致，而且當加入或更新主題時，您的色彩會自動更新。

使用一般共用色彩之前，請確定您瞭解如何正確使用它們。 不正確地使用常見的共用色彩可能會導致您的使用者不一致、令人困惑或混淆。

### <a name="user-customizable-colors"></a>使用者可自訂的色彩

請參閱：[公開使用者的色彩](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

有時候，您會想要允許使用者自訂您的 UI，例如當您建立程式碼編輯器或設計介面時。 可自訂的 UI 元件位於 **工具 &gt; 選項** 對話方塊的 字型**和色彩** 區段中，使用者可以在其中選擇變更前景色彩、背景色彩或兩者。

![工具 &gt; 選項對話方塊](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />工具 &gt; 選項對話方塊

## <a name="BKMK_TheVSColorService"></a>VSColor 服務

Visual Studio 提供環境色彩服務，也稱為 VSColor 服務或 shell color 服務。 這項服務可讓您將 UI 元素的色彩值系結至名稱-值色彩集，其中包含每個主題的色彩。 VSColor 服務必須用於所有 UI 元素，如此一來，色彩就會自動變更以反映目前使用者選取的主題，因此系結至環境色彩服務的 UI 將會與未來 Visual Studio 版本中的新主題進行整合。

### <a name="how-the-service-works"></a>服務 的運作方式

環境色彩服務會讀取 UI 元件的 .pkgdef 中所定義的 VSColors。 然後，這些 VSColors 會在 XAML 標記或程式碼中參考，並透過 `IVsUIShell5.GetThemedColor` 或 `DynamicResource` 對應來載入。

![環境色彩服務架構](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />環境色彩服務架構

### <a name="accessing-the-service"></a>存取服務

有幾種不同的方式可存取 VSColor 服務，視您使用的色彩標記種類，以及您擁有的程式碼種類而定。

#### <a name="predefined-environment-colors"></a>預先定義的環境色彩

##### <a name="from-native-code"></a>從機器碼

Shell 會提供一項服務，可讓您存取色彩的 `COLORREF`。 服務/介面為：

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

在 VSShell80 檔案中，列舉 `__VSSYSCOLOREX` 具有 shell 色彩常數。 若要使用它，請傳入做為索引值，其中一個值來自 MSDN 中記載的 `enum __VSSYSCOLOREX`，或是 Windows 系統 API `GetSysColor`所接受的一般索引編號。 這麼做會傳回第二個參數中應該使用之色彩的 RGB 值。

如果使用新的色彩來儲存畫筆或筆刷，您必須 `AdviseBroadcastMessages` （從 Visual Studio shell），並接聽 `WM_SYSCOLORCHANGE` 和 `WM_THEMECHANGED` 訊息。

若要存取機器碼中的 color 服務，您會進行類似下列的呼叫：

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> `GetVSSysColorEx()` 傳回的 `COLORREF` 值只包含主題色彩的 R、G、B 元件。 如果主題專案使用透明度，則會先捨棄 Alpha 通道值，然後再傳回。 因此，如果需要在透明度通道很重要的地方使用感興趣的環境色彩，您應該使用 `IVsUIShell5.GetThemedColor` 而不是 `IVsUIShell2::GetVSSysColorEx`，如本主題稍後所述。

##### <a name="from-managed-code"></a>從 managed 程式碼

透過機器碼存取 VSColor 服務相當簡單。 不過，如果您是透過 managed 程式碼來工作，則判斷如何使用服務可能會有點棘手。 記住這一點之後，以下是示範C#此流程的程式碼片段：

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

如果您使用 Visual Basic，請使用：

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>從 WPF UI

您可以透過匯出至應用程式 `ResourceDictionary`中的值，系結至 Visual Studio 色彩。 以下是使用 color 資料表中的資源，以及在 XAML 中系結至環境字型資料的範例。

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

對於 managed 程式碼，shell 的 Managed 封裝架構程式庫（`Microsoft.VisualStudio.Shell.12.0.dll`）包含幾個協助程式類別，以方便使用主題色彩。

MPF 的 `Microsoft.VisualStudio.Shell.VsColors` 類別中的 helper 方法包括 `GetThemedGDIColor()` 和 `GetThemedWPFColor()`。 這些 helper 方法會將主題專案的色彩值傳回為 `System.Drawing.Color` 或 `System.Windows.Media.Color`，以用於 WinForms 或 WPF UI。

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

類別也可以用來取得給定 WPF 色彩資源索引鍵的 VSCOLOR 識別碼，反之亦然。

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

`VsColors` 類別的方法會查詢 VSColor 服務，以在每次叫用時傳回色彩值。 若要取得色彩值做為 `System.Drawing.Color`，有較佳效能的替代方案是改用 `Microsoft.VisualStudio.PlatformUI.VSThemeColor` 類別的方法，這會快取從 VSColor 服務取得的色彩值。 類別會在內部訂閱以 shell 廣播訊息事件，並在發生主題變更事件時捨棄快取的值。 此外，類別會提供。訂閱主題變更的網路易記事件。 使用 `ThemeChanged` 事件加入新的處理常式，並使用 `GetThemedColor()` 方法來取得感利率 `ThemeResourceKeys` 的色彩值。 範例程式碼看起來可能像這樣：

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

## <a name="BKMK_ChoosingHighContrastColors"></a>選擇高對比色彩

### <a name="overview"></a>概觀

Windows 使用數種高對比的系統層級主題，可增加文字、背景和影像的色彩對比，讓元素在螢幕上出現更相異的外觀。 基於協助工具的原因，當使用者切換至高對比主題時，Visual Studio 介面元素必須正確回應。

只有少數系統色彩可以用於高對比主題。 選擇您的系統色彩名稱時，請記住下列秘訣：

- 選擇與您要著色之專案**具有相同語義意義的系統色彩**。 例如，如果您要為視窗中的文字選擇高對比的色彩，請使用 WindowText 而非 ControlText。

- 同時**選擇前景/背景配對**，或您不會確信色彩選擇適用于所有的高對比主題。

- **判斷 UI 的哪些部分是最重要的，並確保內容區域將會醒目提示。** 您將會遺失許多色彩色調的細微差異通常會區分，因此，使用強式框線色彩是定義內容區域的常見方式，因為不同的內容區域不會有色彩變化。

### <a name="system-color-set"></a>系統色彩集

[ [WPF 小組 Blog： SystemColors 參考](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/)] 資料表指出一組完整的系統色彩名稱，以及每個主題中顯示的對應色調。

將這組有限的色彩套用至您的 UI 時，*預期會遺失出現在「一般」主題中的細微詳細資料*。 以下是具有微妙灰色色彩的 UI 範例，可用來區分工具視窗中的區域。 當與高對比模式中顯示的相同視窗配對時，您可以看到所有背景都是相同的色調，而這些區域的框線會單獨以框線表示：

![如何在高對比中遺失細微詳細資料的範例](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />如何在高對比中遺失細微詳細資料的範例

#### <a name="choosing-text-colors-in-an-editor"></a>在編輯器中選擇文字色彩

以色彩標示文字用於編輯器或設計介面上，以指出意義，例如允許輕鬆識別類似專案的群組。 不過，在高對比的主題中，您無法區分三種以上的文字色彩。 WindowText、GrayText 和 HotTrackText 是 WindowBackground 表面上唯一可用的色彩。 因為您無法使用三種以上的色彩，請小心選擇在高對比模式中，您想要顯示的最重要差異。

編輯器介面上允許的每個標記名稱的色調，因為它們出現在每個高對比主題中：

![高對比編輯器比較](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />高對比編輯器比較

藍色主題中的編輯器介面範例：

![藍色主題的編輯器](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />藍色佈景主題的編輯器

![高對比 #1 主題中的編輯器](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />高對比 #1 主題中的編輯器

### <a name="usage-patterns"></a>使用模式

許多常用的 UI 元素已經定義高對比色彩。 當您選擇自己的系統色彩名稱時，可以參考這些使用模式，讓您的 UI 元素與類似的元件一致。

| 系統色彩 | 使用方式 |
| --- | --- |
| ActiveCaption | -使用中 IDE 和 rafted 視窗按鈕在滑鼠停留時顯示圖示<br />-IDE 和 rafted 視窗的標題列背景<br />-預設狀態列背景 |
| ActiveCaptionText | -作用中 IDE 和標題列前景的 rafted 視窗（文字和圖像）<br />-停留並按下使用中視窗按鈕的背景和框線 |
| 控制項 | -下拉式方塊、下拉式清單，以及搜尋控制項的預設和停用背景，包括下拉按鈕<br />-停駐目標按鈕背景<br />-命令列背景<br />-工具視窗背景 |
| ControlDark | -IDE 背景<br />-功能表和命令列分隔符號<br />-命令列框線<br />-功能表陰影<br />-工具視窗索引標籤預設和暫留框線和分隔符號<br />-檔的溢位按鈕背景<br />-停駐靶心圖表像框線 |
| ControlDarkDark |-未取得焦點，選取的檔索引標籤視窗 |
| ControlLight |-自動隱藏索引標籤框線<br />-下拉式方塊和下拉式清單方塊<br />-停駐目標背景和框線 |
| ControlLightLight | -已選取，專注的臨時框線 |
| ControlText | -下拉式方塊和下拉式清單圖像<br />-工具視窗未選取的索引標籤文字 |
| GrayText |-下拉式方塊和下拉式清單已停用框線、下拉圖像、文字和功能表項目文字<br />-已停用的功能表文字<br />-搜尋控制項的 [搜尋選項] 標頭文字<br />-搜尋控制項區段分隔符號 |
| 反白顯示 | -所有暫留和按下的背景和框線，除了下拉式方塊下拉按鈕背景和檔的溢位按鈕外框外<br />-選取的專案背景 |
| HighlightText | -所有暫留和按下的 foregrounds （文字和圖像）<br />-焦點工具視窗和 [檔] 索引標籤視窗控制項前景<br />-焦點工具視窗標題列框線<br />-焦點，選取的臨時索引標籤前景<br />-暫留和按下的檔溢位按鈕框線<br />-選取的圖示框線|
| HotTrack | -按下捲軸的背景和框線<br />-按下的捲軸箭號圖示 |
| InactiveCaption | -暫留時的非作用中 IDE 和 rafted 視窗按鈕字型<br />-IDE 和 rafted 視窗的標題列背景<br />-已停用搜尋控制項背景 |
| InactiveCaptionText | -非使用中 IDE 和 rafted windows 標題列前景（文字和圖像）<br />-停留時顯示非作用中的視窗按鈕背景和框線<br />-未取得焦點工具視窗按鈕的背景和框線<br />-停用的搜尋控制項前景 |
| 功能表 | -下拉式功能表背景<br />-已核取並停用核取記號背景 |
| MenuText | -下拉式功能表框線<br />-核取記號<br />-功能表字型<br />-下拉式功能表文字<br />-選取的圖示框線 |
| 捲軸 | -捲軸和捲軸箭號背景，所有狀態 |
| 視窗 | -自動隱藏索引標籤背景<br />-功能表列和命令貨位背景<br />-未取得焦點或取消選取的文件視窗索引標籤背景和檔框線，適用于開啟和臨時索引標籤<br />-未取得焦點工具視窗標題列背景<br />-工具視窗索引標籤背景，同時選取和取消選取 |
| Documentsite | -IDE 框線 |
| WindowText | -自動隱藏索引標籤前景<br />-選取的工具視窗索引標籤前景<br />-未取得焦點文件視窗索引標籤和未取得焦點或取消選取的臨時索引標籤前景<br />-樹狀檢視預設前景並停留在未選取的圖像上<br />-工具視窗選取的索引標籤框線<br />-捲軸捲動方塊的背景、框線和圖像 |

## <a name="BKMK_ExposingColorsForEndUsers"></a>公開終端使用者的色彩

### <a name="overview"></a>概觀

有時候，您會想要允許使用者自訂您的 UI，例如當您建立程式碼編輯器或設計介面時。 最常見的做法是使用 [工具] &gt; [**選項**] 對話方塊。 除非您有需要特殊控制項的高度特製化 UI，否則呈現自訂最簡單的方式是透過對話方塊的 [**環境**] 區段中的 [字型**和色彩**] 頁面。 針對您針對自訂所公開的每個元素，使用者可以選擇變更前景色彩、背景色彩或兩者。

### <a name="building-a-vspackage-for-your-customizable-colors"></a>建立可自訂色彩的 VSPackage

VSPackage 可以透過自訂類別控制字型和色彩，以及在 [字型和色彩] 屬性頁上顯示專案。 使用這種機制時，Vspackage 必須執行[IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider)介面和其相關聯的介面。

就原則而言，這項機制可以用來修改所有現有的顯示專案和包含它們的類別。 不過，它不應該用來修改文字編輯器分類或其顯示專案。 如需文字編輯器分類的詳細資訊，請參閱[字型和色彩總覽](/visualstudio/extensibility/font-and-color-overview?view=vs-2015)。

若要執行自訂類別或顯示專案，VSPackage 必須：

- **在登錄中建立或識別類別目錄。** IDE 的 [字型**和色彩**] 屬性頁的 [執行] 會使用這項資訊來正確查詢支援給定分類的服務。

- **在登錄中建立或識別群組（選擇性）。** 定義群組（代表兩個或多個類別的聯集）可能會很有用。 如果定義了群組，IDE 會自動合併子類別，並在群組內散發顯示專案。

- **執行 IDE 支援。**

- **處理字型和色彩變更。**

#### <a name="to-create-or-identify-categories"></a>若要建立或識別類別目錄

在 `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` 下建立特殊類型的 category 登錄專案，其中 `<Category>` 是分類的非當地語系化名稱。

在登錄中填入兩個值：

| 名稱 | 類型 | Data | 描述 |
| --- | --- | --- | --- |
| 類別 | REG_SZ | GUID | 建立用來識別類別目錄的 GUID |
| 套件 | REG_SZ | GUID | 支援類別目錄之 VSPackage 服務的 GUID |

 登錄中指定的服務必須為對應的分類提供[IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)的執行。

#### <a name="to-create-or-identify-groups"></a>建立或識別群組

在 `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` 下建立特殊類型的 category 登錄專案，其中 `<group>` 是群組的非當地語系化名稱。

在登錄中填入兩個值：

| 名稱 | 類型 | Data | 描述 |
|--- | --- | --- | --- |
| 類別 | REG_SZ | GUID | 建立用來識別類別目錄的 GUID |
| 套件 | REG_SZ | GUID | 支援類別目錄之 VSPackage 服務的 GUID |

登錄中指定的服務必須為對應的群組提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> 的執行。

![IVsFontAndColorGroup 的執行](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />`IVsFontAndColorGroup` 的實作

### <a name="to-implement-ide-support"></a>若要執行 IDE 支援

執行[GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject)，它會針對每個提供的類別或群組 GUID，將[IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)介面或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> 介面傳回至 IDE。

針對它支援的每個類別，VSPackage 會實[IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)介面的個別實例。

透過[IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)所執行的方法必須提供 IDE：

- 類別目錄中顯示專案的清單

- 顯示專案的可當地語系化名稱

- 顯示類別中每個成員的資訊

> [!NOTE]
> 每個類別都必須包含至少一個顯示專案。

IDE 會使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> 介面來定義數個類別的聯集。

它的實作為提供 IDE：

- 組成指定群組的分類清單

- 存取支援群組內每個類別的[IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)實例

- 可當地語系化的組名

#### <a name="updating-the-ide"></a>更新 IDE

IDE 會快取字型和色彩設定的相關資訊。 因此，在任何修改 IDE 字型和色彩設定之後，確保快取是最新的最佳作法。

更新快取是透過[IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager)介面來完成，而且可以在全域或只在選取的專案上執行。

### <a name="handling-font-and-color-changes"></a>處理字型和色彩變更

若要適當地支援 VSPackage 顯示的文字顏色標示，支援 VSPackage 的顏色標示服務必須回應使用者起始的變更（透過 [字型] 和 [色彩] 屬性頁面）。

若要這樣做，VSPackage 必須：

- 藉由執行[IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents)介面來**處理 IDE 產生的事件**。 在使用者修改 [字型和色彩] 頁面之後，IDE 會呼叫適當的方法。 例如，如果選取了新字型，它會呼叫[OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged)方法。

  **OR**

- **輪詢 IDE 以取得變更**。 這可以透過系統實[IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage)介面來完成。 雖然主要是為了支援持續性，但[GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem)方法可以取得顯示專案的字型和色彩資訊。 如需字型和色彩設定的詳細資訊，請參閱 MSDN 文章[存取預存字型和色彩設定](/visualstudio/extensibility/accessing-stored-font-and-color-settings?view=vs-2015)。

> [!NOTE]
> 為確保輪詢結果正確，請使用[IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager)介面來判斷在呼叫[IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage)介面的抓取方法之前是否需要快取排清和更新。

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>註冊自訂字型和色彩類別，但不執行介面

下列程式碼範例示範如何註冊自訂字型和色彩類別，而不需執行介面：

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

針對此程式碼範例：

- `"NameID"` = 封裝中當地語系化分類名稱的資源識別碼
- `"ToolWindowPackage"` = 套件 GUID
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` 只是一個範例，而實際的值可以是實施者所提供的新 GUID。

### <a name="set-the-font-and-color-property-category-guid"></a>設定字型和色彩屬性類別目錄 GUID

下列程式碼範例示範如何設定分類 Guid。

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
