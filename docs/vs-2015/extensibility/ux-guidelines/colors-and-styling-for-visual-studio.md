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
ms.openlocfilehash: 0330ef80fc1127893590ef8d326cb5b8e0cf0160
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302438"
---
# <a name="colors-and-styling-for-visual-studio"></a>適用於 Visual Studio 的色彩和樣式設定
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="using-color-in-visual-studio"></a>在視覺工作室中使用顏色
 在視覺工作室中，顏色主要用作通信工具，而不僅僅是裝飾。 最小使用顏色，並保留它的情況，你想：

- 傳達含義或隸屬關係（例如，平臺或語言修改器）

- 吸引注意力（例如，指示狀態更改）

- 提高可讀性並提供用於導航 UI 的地標

- 提高可取性

  在 Visual Studio 中，存在將顏色分配給 UI 元素的幾個選項。 有時，很難確定您應該使用哪個選項，或者如何正確使用它。 本主題將説明您：

1. 瞭解用於在 Visual Studio 中定義顏色的不同服務和系統。

2. 為給定元素選擇正確的選項。

3. 正確使用您選擇的選項。

   **重要提示：** 切勿對 UI 元素硬編碼十六進位、RGB 或系統色彩。 使用服務可以靈活地調整色調。 此外，如果沒有該服務，您將無法利用[VSColor 服務](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)的主題切換功能。

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>為視覺化工作室介面元素分配顏色的方法
 選擇最適合 UI 元素的方法。

|您的 UI|方法|它們是什麼？|
|-------------|------------|--------------------|
|您有嵌入的或獨立的對話方塊。|**系統色彩**|允許作業系統定義 UI 元素的顏色和外觀的系統名稱，例如用於常見對話方塊控制項。|
|您有要與整個 VS 環境一致的自訂 UI，並且具有與共享權杖的類別和語義含義相匹配的 UI 元素。|**常見共用顏色**|特定 UI 元素的現有預定義顏色權杖名稱|
|您具有單個要素或一組要素，並且沒有類似元素的共用顏色。|**自訂色彩**|特定于區域且不打算與其他 UI 共用的顏色權杖名稱|
|您希望允許最終使用者自訂 UI 或內容（例如，對於文字編輯器或專用設計器視窗）。|**最終使用者自訂**<br /><br /> **（工具>選項對話方塊）**|**在"工具>選項**"對話方塊的"字體和顏色"頁面或特定于一個 UI 功能的專用頁面中定義的設置。|

### <a name="visual-studio-themes"></a>視覺工作室主題
 Visual Studio 具有三種不同的顏色主題：淺色、深色和藍色。 它還檢測高對比模式，這是專為輔助功能而設計的全系統色彩主題。

 在首次使用 Visual Studio 時，系統會提示使用者選擇主題，並稍後通過轉到 **"工具>選項>環境>一般**"以及從"顏色主題"下拉式功能表中選擇新主題來切換主題。

 使用者還可以使用控制台將其整個系統切換到幾個高對比主題之一。 如果使用者選擇高對比主題，則 Visual Studio 顏色主題選擇器不再影響 Visual Studio 中的顏色，儘管當使用者退出高對比模式時，將保存任何主題更改。 有關高對比模式的詳細資訊，請參閱[選擇高對比顏色](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)。

### <a name="the-vscolor-service"></a>VSColor 服務
 Visual Studio 提供一種稱為 VSColor 服務的環境顏色服務，該服務允許您將 UI 元素的顏色值綁定到包含每個 Visual Studio 主題顏色值的命名條目。 這可確保顏色將自動更改以反映當前使用者選擇的主題或系統高對比模式。 使用該服務意味著所有主題相關顏色更改的實現都在一個位置處理，如果您使用服務中的常見共用顏色，則 UI 將自動反映 Visual Studio 的未來版本中的新主題。

### <a name="implementation"></a>實作
 Visual Studio 原始程式碼包括多個包定義檔，其中包含權杖名稱清單和每個主題的相應顏色值。 顏色服務讀取這些包定義檔中定義的 VSColors。 這些顏色在 XAML 標記或代碼中引用，然後通過**IVsUIShell5.Get 主題顏色**方法或動態資源映射載入。

### <a name="system-colors"></a>系統色彩
 預設情況下，公共控制項引用系統色彩。 如果希望 UI 使用系統色彩（例如，在創建嵌入或獨立對話方塊時），則無需執行任何操作。

### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor 服務中的常見共用顏色
 您的介面元素應反映整個視覺化工作室環境。 通過重用適用于所設計的 UI 元件的常見共用顏色，可確保介面與其他 Visual Studio 介面一致，並確保在添加或更新主題時顏色將自動更新。

 在使用公共共用顏色之前，請確保您瞭解如何正確使用它們。 對常見共用顏色的不正確使用可能會導致使用者體驗不一致、令人沮喪或混亂。

### <a name="user-customizable-colors"></a>使用者可自訂的顏色
 請參閱：[為最終使用者公開顏色](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

 有時，您需要允許最終使用者自訂 UI，例如創建代碼編輯器或設計介面時。 可自訂的 UI 元件位於 **"工具>選項"** 對話方塊的"**字體和顏色**"部分，使用者可以選擇更改前景顏色、背景顏色或兩者。

 ![視覺化工作室中的工具&#62;選項對話方塊](../../extensibility/ux-guidelines/media/0301-a-toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")

 **工具>選項對話方塊**

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a>VSColor 服務
 Visual Studio 提供環境顏色服務，也稱為 VSColor 服務或外殼顏色服務。 此服務允許您將 UI 元素的顏色值綁定到包含每個主題顏色的名稱值顏色集。 VSColor 服務必須用於所有 UI 元素，以便顏色自動更改以反映當前使用者選擇的主題，以便綁定到環境顏色服務的 UI 將與 Visual Studio 的未來版本中的新主題集成。

### <a name="how-the-service-works"></a>服務 的運作方式
 環境顏色服務讀取在 .pkgdef 中定義的 UI 元件中的 VSColors。 然後，這些 VSColors 在 XAML 標記或代碼中引用，並通過**IVsUIShell5.Get 主題顏色**或動態資源映射載入。

 ![環境色彩服務架構](../../extensibility/ux-guidelines/media/0302-a-environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")

 **環境色彩服務架構**

### <a name="accessing-the-service"></a>訪問服務
 有幾種不同的方法來訪問 VSColor 服務，具體取決於您正在使用的顏色權杖類型以及您擁有的代碼類型。

#### <a name="predefined-environment-colors"></a>預定義環境顏色

##### <a name="from-native-code"></a>從本機代碼
 shell 提供一種服務，該服務允許訪問顏色的 COLORREF。 服務/介面是：

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

 在檔 VSShell80.idl 中，枚舉 **__VSSYSCOLOREX**具有外殼顏色常量。 要使用它，傳入為索引值，要麼從 MSDN 中記錄的枚舉__VSSYSCOLOREX的值之一，要麼將 Windows 系統 API **GetSysColor**接受的常規索引號。 執行此操作將返回應在第二個參數中使用的顏色的 RGB 值。

 如果存儲具有新顏色的筆或畫筆，則必須建議廣播訊息（從 Visual Studio 外殼中）並偵聽WM_SYSCOLORCHANGE和WM_THEMECHANGED消息。

```
// To access the color service in native code, you'll make a call that resembles this:
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);

```

 **注：****GetVSSysColorEx（）** 返回的 COLORRE光圈值僅包含主題顏色的 R、G、B 元件。 如果主題條目使用透明度，則在返回之前將丟棄 Alpha 色板值。 因此，如果需要在透明度通道很重要的地方使用感興趣的環境顏色，則應使用 IVUIShell5.Get 主題色而不是 IVsUIShell2：：getVSSysColorEx，如本主題後面所述。

##### <a name="from-managed-code"></a>從託管代碼
 通過本機代碼訪問 VSColor 服務相當簡單。 但是，如果您正在處理託管代碼，則確定如何使用服務可能比較棘手。 考慮到這一點，下面是一個 C# 程式碼片段，演示了此過程：

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

 如果您在視覺化基礎中工作，請使用：

```
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>從 WPF UI
 您可以通過匯出到應用程式的資源字典的值綁定到 Visual Studio 顏色。 下面是使用顏色表中的資源以及綁定到 XAML 中的環境字體資料的示例。

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>託管代碼的説明器類和方法
 對於託管代碼，shell 的託管包框架庫（Microsoft.VisualStudio.shell.12.0.dll）包含幾個説明器類，便於使用主題顏色。

 微軟中的説明器方法 **.VisualStudio.shell.VsColors**類中 MPF 中包括**獲取主題 GDIColor（）** 和**獲取主題WPFColor（）**。 這些説明器方法將主題條目的顏色值返回為"系統.繪圖.顏色或系統.Windows.Media.Color"，用於 WinForms 或 WPF UI。

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

 該類還可用於獲取給定 WPF 顏色資源鍵的 VSCOLOR 識別碼，反之亦然。

```
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

 **VsColors**類的方法查詢 VSColor 服務，以便每次調用它們時返回顏色值。 要獲得顏色值為 **"系統.繪圖.顏色**"，另一種性能更好的方法是使用**Microsoft.VisualStudio.PlatformUI.VSTheMeColor**類的方法，該方法緩存從 VSColor 服務獲取的顏色值。 類在內部訂閱 shell 廣播訊息事件，並在發生主題變更事件時丟棄緩存的值。 此外，類提供 。NET 友好活動，用於訂閱主題更改。 使用**Methe"更改"** 事件添加新處理常式，並使用 Get**主題顏色（）** 方法獲取感興趣的**主題資源鍵**的顏色值。 示例代碼可能如下所示：

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

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a>選擇高對比顏色

### <a name="overview"></a>概觀
 Windows 使用多個高對比的系統級主題，這些主題可增加文本、背景和圖像的顏色對比度，從而使元素在螢幕上顯得更加清晰。 出於協助工具的原因，當使用者切換到高對比主題時，Visual Studio 介面元素正確回應非常重要。

 只有少量系統色彩可用於高對比主題。 選擇系統色彩名稱時，請記住以下提示：

1. 選擇與著色的元素**具有相同語義含義的系統色彩**。 例如，如果要為視窗中的文本選擇高對比顏色，請使用 WindowText 而不是 ControlText。

2. **一起選擇前景/背景對**，否則您不會確信您的顏色選擇在所有高對比主題中都起作用。

3. **確定 UI 的哪些部分最重要，並確保內容區域脫穎而出。** 您將失去顏色色調的細微差異通常會區分的很多細節，因此使用強邊框顏色是定義內容區域的常見內容，因為不同內容區域沒有顏色變體。

### <a name="system-color-set"></a>系統色彩集
 [WPF 團隊博客中的表：系統色彩參考](https://devblogs.microsoft.com/wpf/systemcolors-reference/)指示完整的系統色彩名稱集，以及每個主題中顯示的相應色調。

 當將這種有限的顏色集應用於 UI 時 *，預計您將丟失"正常"主題中存在的細微細節*。 下面是一個帶有微妙灰色 UI 的示例，用於區分工具視窗中的區域。 與在高對比模式下顯示的同一視窗配對時，您可以看到所有背景都具有相同的色調，並且這些區域的邊界僅由邊框表示：

 ![屬性視窗](../../extensibility/ux-guidelines/media/030303-a-propertieswindow.png "030303-a_PropertiesWindow")

 **高對比時如何丟失細微細節的示例**

#### <a name="choosing-text-colors-in-an-editor"></a>在編輯器中選擇文本顏色
 著色文本用於編輯器或設計表面，以指示含義，例如允許輕鬆識別類似項組。 但是，在高對比主題中，您無法區分三種以上文本顏色。 視窗文本、灰色文本和熱軌道文本是視窗背景曲面上唯一可用的顏色。 由於不能使用三種顏色以上，請仔細選擇在高對比模式下要顯示的最重要差異。

 編輯器曲面上允許的每個權杖名稱的色調，因為它們出現在每個高對比主題中：

 ![高對比編輯器比較](../../extensibility/ux-guidelines/media/030303-b-hceditorcomparison.png "030303-b_HCEditorComparison")

 **高對比編輯器比較**

 藍色主題中編輯器表面的示例：

 ![藍色佈景主題的編輯器](../../extensibility/ux-guidelines/media/030303-c-editorblue.png "030303-c_EditorBlue")

 **藍色佈景主題的編輯器**

 ![高對比佈景主題的編輯器](../../extensibility/ux-guidelines/media/030303-d-editorhc1.png "030303-d_EditorHC1")

 **高對比#1主題的編輯**

### <a name="usage-patterns"></a>使用模式
 許多常見的 UI 元素已定義高對比顏色。 在選擇自己的系統色彩名稱時，可以引用這些使用模式，以便 UI 元素與類似的元件一致。

|系統色彩|使用量|
|------------------|-----------|
|ActiveCaption|- 活動 IDE 和漂流視窗按鈕字形懸停並按下<br />- IDE 和漂流視窗的標題列背景<br />- 預設狀態列背景|
|ActiveCaptionText|- 標題列前景的活動 IDE 和漂流視窗（文本和字形）<br />- 懸停上使用中視窗按鈕的背景和邊框，然後按|
|控制|- 下拉式列示方塊、下拉清單和搜索控制項預設和禁用背景，包括下拉按鈕<br />- 停靠目標按鈕背景<br />- 命令列背景<br />- 工具視窗背景|
|ControlDark|- IDE 背景<br />- 功能表和命令列分隔符號<br />- 命令列邊框<br />- 功能表陰影<br />- 工具視窗選項卡預設值和懸停邊框和分隔符號<br />- 記錄溢出按鈕背景<br />- 停靠目標字形邊框|
|ControlDarkDark|- 未聚焦、選定的文檔選項卡視窗|
|ControlLight|- 自動隱藏選項卡邊框<br />- 下拉式列示方塊和下拉清單邊框<br />- 停靠目標背景和邊框|
|控制燈|- 選定、重點突出的臨時邊界|
|控制項文本|- 下拉式列示方塊和下拉清單字形<br />- 工具視窗未選中選項卡文本|
|灰色文本|- 下拉式列示方塊和下拉清單禁用邊框、下拉字、文本和功能表項目文本<br />- 禁用功能表文本<br />- 搜索控制項"搜索選項"標題文本<br />- 搜索控制截面分隔符號|
|反白顯示|- 所有懸停和按下的背景和邊框，但下拉式列示方塊下拉按鈕背景和文檔溢出按鈕邊框<br />- 選定的專案背景|
|突出顯示文本|- 所有懸停和按下的前景（文本和字形）<br />- 聚焦工具視窗和文檔選項卡視窗控制前景<br />- 聚焦工具視窗標題列邊框<br />- 聚焦、選定的臨時選項卡前景<br />- 在懸停上記錄溢流按鈕邊框，然後按<br />- 選定的圖示邊框|
|熱軌道|- 按下的捲軸拇指背景和邊框<br />- 按下時捲軸箭頭字形|
|非活動標題|- 懸停時非活動 IDE 和漂流視窗按鈕字形<br />- IDE 和漂流視窗的標題列背景<br />- 禁用的搜索控制背景|
|非活動字幕文本|- 非活動 IDE 和漂流視窗標題列前景（文本和字形）<br />- 非使用中視窗按鈕背景和懸停邊框<br />- 無焦點工具視窗按鈕背景和邊框<br />- 禁用的搜索控制前景|
|功能表|- 下拉式功能表背景<br />- 已選中和禁用核取記號背景|
|功能表文本|- 下拉式功能表邊框<br />- 核取記號檢查<br />- 功能表字形<br />- 下拉式功能表文本<br />- 選定的圖示邊框|
|捲軸|- 捲軸和捲軸箭頭背景，所有狀態|
|時間範圍|- 自動隱藏選項卡背景<br />- 功能表列和命令擱板背景<br />- 未聚焦或未選擇的文件視窗選項卡背景和文檔邊框，適用于打開和臨時選項卡<br />- 無焦點工具視窗標題列背景<br />- 工具視窗選項卡背景，已選擇和未選中|
|視窗框架|- IDE 邊框|
|視窗文本|- 自動隱藏選項卡前景<br />- 選定的工具視窗選項卡前景<br />- 未專注的文件視窗選項卡和未聚焦或未選中的臨時選項卡前景<br />- 樹狀檢視預設前景，並將滑鼠懸停在未選擇的字形上<br />- 工具視窗選擇選項卡邊框<br />- 捲軸拇指背景、邊框和字形|

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a>為最終使用者公開顏色

### <a name="overview"></a>概觀
 有時，您需要允許最終使用者自訂 UI，例如創建代碼編輯器或設計介面時。 最常見的方法是使用 **"工具>選項"** 對話方塊。 除非您具有需要特殊控制項的高度專業化 UI，否則顯示自訂的最簡單方法是通過對話方塊 **"環境**"部分中的 **"字體和顏色**"頁。 對於要自訂公開的每個元素，使用者可以選擇更改前景顏色、背景顏色或兩者。

### <a name="building-a-vspackage-for-your-customizable-colors"></a>為可自訂的顏色構建 VS 包
 VSPackage 可以通過自訂類別控制字體和顏色，並在"字體和顏色"屬性頁上顯示專案。 使用此機制時，VSPackages 必須實現[IVsFontAndColorDefaults 提供程式介面](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx)及其關聯的介面。

 原則上，此機制可用於修改所有現有的顯示項及其包含它們的類別。 但是，它不應用於修改文字編輯器類別或其顯示項。 有關文字編輯器類別的詳細資訊，請參閱[字體和顏色概述](https://msdn.microsoft.com/library/bb165065.aspx)。

 要實現自訂類別或顯示專案，VS 包必須：

- **創建或標識註冊表中的類別。** IDE 的 **"字體和顏色**"屬性頁的實現使用此資訊正確查詢支援給定類別的服務。

- **在註冊表中創建或標識組（可選）。** 定義表示兩個或多個類別的聯合的組可能很有用。 如果定義了組，IDE 將自動合併子類別並在組中分發顯示項。

- **實施 IDE 支援。**

- **處理字體和顏色更改。**

#### <a name="to-create-or-identify-categories"></a>創建或標識類別
 在 [HKLM_SOFTWARE]微軟 [視覺工作室<視覺\\工作室版本\>[FontAndColors\\<類別 ]\>下構造特殊類型的類別登錄機碼。 \<類別>是類別的非當地語系化名稱。

 使用兩個值填充註冊表：

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|類別|REG_SZ|GUID|為識別類別而創建的 GUID|
|Package|REG_SZ|GUID|支援類別的 VSPackage 服務的 GUID|

 註冊表中指定的服務必須為相應的類別提供[IVsFontAndColorDefaults 的](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)實現。

#### <a name="to-create-or-identify-groups"></a>創建或標識組
 在 [HKLM_SOFTWARE]微軟 [視覺\\工作室<視覺工作室版本\>[FontAndColors\\<組\>]下構造特殊類型的類別登錄機碼。 \<組>是組的非當地語系化名稱。

 使用兩個值填充註冊表：

|名稱|類型|資料|描述|
|----------|----------|----------|-----------------|
|類別|REG_SZ|GUID|為識別類別而創建的 GUID|
|Package|REG_SZ|GUID|支援類別的 VSPackage 服務的 GUID|

 註冊表中指定的服務必須為相應的組提供**T：Microsoft.VisualStudio.shell.Interop.IVsfontAndColorGroup**的實現。

 ![IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a-fontandcolorgroup.png "0304-a_FontAndColorGroup")

### <a name="to-implement-ide-support"></a>實現 IDE 支援
 實現[GetObject](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx)，它返回[IVsfontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)介面或**T：Microsoft.VisualStudio.shell.Interop.IVsfontAndColorGroup**介面到 IDE 為每個類別或組 GUID 提供。

 對於它支援的每個類別，VS包實現[IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)介面的單獨實例。

 通過[IVsfontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)實現的方法必須為 IDE 提供：

- 類別中顯示項的清單

- 顯示項的可當地語系化名稱

- 顯示類別每個成員的資訊

  **注：** 每個類別必須至少包含一個顯示項。

  IDE 使用**T：Microsoft.VisualStudio.shell.Interop.IVsfontAndColorGroup**介面來定義多個類別的聯盟。

  其實現為 IDE 提供了：

- 組成給定組的類別清單

- 訪問支援組內每個類別的[IVsFontAndColorDefaults 實例](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)

- 可當地語系化組名稱

#### <a name="updating-the-ide"></a>更新 IDE
 IDE 緩存有關字體和顏色設置的資訊。 因此，在修改 IDE 字體和顏色配置後，最佳做法是確保緩存是最新的。

 更新緩存通過[IvsFontAndColorCacheManager](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx)介面完成，可以全域執行，也可以僅對選定專案執行。

### <a name="handling-font-and-color-changes"></a>處理字體和顏色更改
 為了正確支援 VSPackage 顯示的文本著色，支援 VSPackage 的著色服務必須回應使用者通過"字體和顏色"屬性頁所做的更改。

 為此，VS 包必須：

- 通過實現[IVsfontAndColor 事件](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx)介面**來處理 IDE 生成的事件**。 在使用者修改"字體和顏色"頁後，IDE 調用適當的方法。 例如，如果選擇了新字體，它將調用[OnFont"更改](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx)"方法。

  **或**

- **輪詢 IDE 以進行更改**。 這可以通過系統實現的[IVsfontAndColor 存儲](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx)介面來完成。 儘管主要為了支援持久性，但[GetItem](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx)方法可以獲取顯示專案的字體和顏色資訊。 有關字體和顏色設置的詳細資訊，請參閱 MSDN 文章[訪問存儲的字體和顏色設置](https://msdn.microsoft.com/library/bb166382.aspx)。

  **注：** 為確保輪詢結果正確，請使用[IVsFontAndColorCacheManager](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx)介面來確定是否需要緩存刷新和更新，然後調用[IVsFontAndColor 存儲](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx)介面的檢索方法。

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>註冊自訂字體和色彩類別，無需實現介面
 以下代碼示例演示如何在不實現介面的情況下註冊自訂字體和色彩類別：

```xml
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

 **注意：**

- "NameID" = 包中當地語系化類別名稱的資源識別碼

- "工具視窗包" = 包 GUID

- "類別"[][9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE]只是一個例子，實際值可以是實現者提供的新GUID。

### <a name="set-the-font-and-color-property-category-guid"></a>設置字體和顏色屬性類別 GUID
 下面的代碼示例演示了設置類別 GUID。

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
