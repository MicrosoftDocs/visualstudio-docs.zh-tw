---
title: 視覺工作室的顏色和造型 |微軟文件
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c7d8a02de9331f268cd06ad35e19faab6494fe0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699857"
---
# <a name="colors-and-styling-for-visual-studio"></a>適用於 Visual Studio 的色彩和樣式設定

## <a name="use-color-in-visual-studio"></a>在視覺工作室中使用顏色

在視覺工作室中,顏色主要用作通信工具,而不僅僅是裝飾。 最小使用顏色,並保留它的情況,你想:

- 傳達含義或隸屬關係(例如,平臺或語言修改器)

- 吸引注意力(例如,指示狀態更改)

- 提高可讀性並提供用於導航 UI 的地標

- 提高可取性

在 Visual Studio 中,存在將顏色分配給 UI 元素的幾個選項。 有時,很難確定您應該使用哪個選項,或者如何正確使用它。 本主題會說明您:

- 瞭解用於在 Visual Studio 中定義顏色的不同服務和系統。

- 為給定元素選擇正確的選項。

- 正確使用您選擇的選項。

> [!NOTE]
> 切勿對 UI 元素硬編碼十六進制、RGB 或系統顏色。 使用服務可以靈活地調整色調。 此外,如果沒有該服務,您將無法利用[VSColor 服務](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)的主題切換功能。

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>為視覺化工作室介面元素配置顏色的方法

選擇最適合 UI 元素的方法。

| 您的 UI | 方法 | 它們是什麼? |
| --- | --- | --- |
| 您有嵌入的或獨立的對話方塊。 | **系統顏色** | 允許作業系統定義 UI 元素的顏色和外觀的系統名稱,如通用對話方塊控制元件。 |
| 您有要與整個 VS 環境一致的自定義 UI,並且具有與共用權杖的類別和語義含義相匹配的 UI 元素。 | **常見分享顏色** | 特定 UI 元素的現有預先定義顏色權杖名稱 |
| 您具有單個要素或一組要素,並且沒有類似元素的共享顏色。 | **自訂色彩** | 特定於區域且不打算與其他 UI 分享的顏色權杖名稱 |
| 您希望允許最終使用者自定義 UI 或內容(例如,對於文字編輯器或專用設計器視窗)。 | **最終使用者自訂**<br /><br />**(工具&gt;選項對話框)** | **在「工具&gt;選項**」對話方塊的「字型和顏色」頁或特定於一個 UI 功能的專用頁面中定義的設定。 |

### <a name="visual-studio-themes"></a>視覺工作室主題

Visual Studio 具有三種不同的顏色主題:淺色、深色和藍色。 它還檢測高對比度模式,這是專為輔助功能而設計的全系統顏色主題。

在首次使用 Visual Studio 時,系統會提示使用者選擇主題,並稍後透過轉到 **「工具選項&gt;環境&gt;常規&gt;」** 並從「顏色主題」 下拉選單選擇新主題來切換主題。

使用者還可以使用控制面板將其整個系統切換到幾個高對比度主題之一。 如果用戶選擇高對比度主題,則 Visual Studio 顏色主題選擇器不再影響 Visual Studio 中的顏色,儘管當使用者退出高對比度模式時,將保存任何主題更改。 有關高對比度模式的詳細資訊,請參閱[選擇高對比度顏色](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)。

### <a name="the-vscolor-service"></a>VSColor 服務

Visual Studio 提供一種稱為 VSColor 服務的環境顏色服務,該服務允許您將 UI 元素的顏色值綁定到包含每個 Visual Studio 主題顏色值的命名條目。 這可確保顏色將自動更改以反映當前用戶選擇的主題或系統高對比度模式。 使用該服務意味著所有主題相關顏色更改的實現都在一個位置處理,如果您使用服務中的常見共用顏色,則 UI 將自動反映 Visual Studio 的未來版本中的新主題。

### <a name="implementation"></a>實作

Visual Studio 原始碼包括多個包定義檔,其中包含權杖名稱清單和每個主題的相應顏色值。 顏色服務讀取這些包定義檔中定義的 VSColors。 這些顏色在 XAML 標記或代碼中引用,`IVsUIShell5.GetThemedColor`然後透過方法或動態資源映射載入。

### <a name="system-colors"></a>系統顏色

預設情況下,公共控件引用系統顏色。 如果希望 UI 使用系統顏色(如建立嵌入或獨立對話方塊時),則無需執行任何操作。

### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor 服務中的常見分享顏色

您的介面元素應反映整個可視化工作室環境。 通過重用適用於所設計的 UI 元件的常見共享顏色,可確保介面與其他 Visual Studio 介面一致,並確保在添加或更新主題時顏色將自動更新。

在使用公共共享顏色之前,請確保您瞭解如何正確使用它們。 對常見共用顏色的不正確使用可能會導致用戶體驗不一致、令人沮喪或混亂。

### <a name="user-customizable-colors"></a>使用者可自訂的顏色

請參考:[為最終使用者公開顏色](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

有時,您需要允許最終使用者自定義 UI,例如創建代碼編輯器或設計圖面時。 可自訂的 UI 元件位於 **「&gt;工具選項」** 對話方塊的「**字型與顏色**」 部分,使用者可以選擇更改前景顏色、背景顏色或兩者。

![工具&gt;選項對話框](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />工具&gt;選項對話框

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a>VSColor 服務

Visual Studio 提供環境顏色服務,也稱為 VSColor 服務或外殼顏色服務。 此服務允許您將 UI 元素的顏色值綁定到包含每個主題顏色的名稱值顏色集。 VSColor 服務必須用於所有 UI 元素,以便顏色自動更改以反映當前使用者選擇的主題,以便綁定到環境顏色服務的 UI 將與 Visual Studio 的未來版本中的新主題集成。

### <a name="how-the-service-works"></a>服務 的運作方式

環境顏色服務讀取在 .pkgdef 中定義的 UI 元件中的 VSColors。 然後,這些 VSColors 在 XAML 標記或代碼中`IVsUIShell5.GetThemedColor`引用`DynamicResource`,並通過 或映射載入。

![環境色彩服務架構](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />環境色彩服務架構

### <a name="accessing-the-service"></a>存取服務

有幾種不同的方法來造訪 VSColor 服務,具體取決於您正在使用的顏色令牌類型以及您擁有的代碼類型。

#### <a name="predefined-environment-colors"></a>預先定義環境顏色

##### <a name="from-native-code"></a>從本機代碼

shell 提供一種服務,該服務允許`COLORREF`訪問 顏色。 服務/介面是:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

在檔 VSShell80.idl 中,`__VSSYSCOLOREX`枚舉 具有外殼顏色常量。 要使用它,請傳入為索引值,從 MSDN`enum __VSSYSCOLOREX`中記錄的值之一或 Windows`GetSysColor`系統 API 接受的常規索引號。 執行此操作將返回應在第二個參數中使用的顏色的 RGB 值。

如果存儲具有新顏色的筆或畫筆,則必須`AdviseBroadcastMessages`(關閉 Visual Studio 外殼`WM_SYSCOLORCHANGE`)`WM_THEMECHANGED`並偵聽 和消息。

要存取本機代碼中的顏色服務,您將進行類似於以下的呼叫:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> 傳`COLORREF``GetVSSysColorEx()`回的值僅包含主題顏色的 R、G、B 元件。 如果主題條目使用透明度,則在返回之前將丟棄 Alpha 通道值。 因此,如果需要在透明度通道很重要的地方使用感興趣的環境顏色,則應使用`IVsUIShell5.GetThemedColor``IVsUIShell2::GetVSSysColorEx`而不是 ,如本主題後面所述。

##### <a name="from-managed-code"></a>從託管代碼

通過本機代碼訪問 VSColor 服務相當簡單。 但是,如果您正在處理託管代碼,則確定如何使用服務可能比較棘手。 考慮到這一點,下面是一個 C# 代碼段,演示了此過程:

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

如果您在視覺化基礎中工作,請使用:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>從 WPF UI

您可以透過匯出到應用程式的值繫結到 Visual Studio 顏色`ResourceDictionary`。 下面是使用顏色表中的資源以及綁定到 XAML 中的環境字體數據的範例。

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>託管代碼的說明器類別和方法

對於託管代碼,shell 的託管包框架庫(`Microsoft.VisualStudio.Shell.12.0.dll`) 包含幾個幫助器類,便於使用主題顏色。

MPF 類別`Microsoft.VisualStudio.Shell.VsColors`的說明器方法`GetThemedGDIColor()`包括`GetThemedWPFColor()`與 。 這些幫助器方法返回主題條目的顏色值,作為`System.Drawing.Color`或`System.Windows.Media.Color`,用於 WinForms 或 WPF UI。

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

該類還可用於獲取給定 WPF 顏色資源鍵的 VSCOLOR 識別符,反之亦然。

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

`VsColors`類查詢 VSColor 服務的方法,以在每次調用顏色值時返回顏色值。 要取得顏色值,`System.Drawing.Color`性能更好的替代方法是`Microsoft.VisualStudio.PlatformUI.VSThemeColor`使用 類的方法,該方法緩存從 VSColor 服務獲取的顏色值。 類在內部訂閱 shell 廣播消息事件,並在發生主題更改事件時丟棄緩存的值。 此外,類提供 。NET 友好活動,用於訂閱主題更改。 使用`ThemeChanged`事件添加新處理程式,並`GetThemedColor()`使用 方法獲取感興趣的顏色`ThemeResourceKeys`值。 範例代碼可能如下所示:

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

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a>選擇高對比度顏色

### <a name="overview"></a>概觀

Windows 使用多個高對比度的系統級主題,這些主題可增加文本、背景和圖像的顏色對比度,從而使元素在螢幕上顯得更加清晰。 出於輔助功能的原因,當使用者切換到高對比度主題時,Visual Studio 介面元素正確回應非常重要。

只有少量系統顏色可用於高對比度主題。 選擇系統顏色名稱時,請記住以下提示:

- 選擇與色的元素**具有相同語意含義的系統顏色**。 例如,如果要為視窗中的文本選擇高對比度顏色,請使用 WindowText 而不是 ControlText。

- **一起選擇前景/背景對**,否則您不會確信您的顏色選擇在所有高對比度主題中都起作用。

- **確定 UI 的哪些部分最重要,並確保內容區域脫穎而出。** 您將失去顏色色調的細微差異通常會區分的很多細節,因此使用強邊框顏色是定義內容區域的常見內容,因為不同內容區域沒有顏色變體。

### <a name="system-color-set"></a>系統顏色集

[WPF 團隊部落格中的表:系統顏色參考](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/)指示完整的系統顏色名稱集,以及每個主題中顯示的相應色調。

當將這種有限的顏色集應用於 UI 時 *,預計您將遺失「正常」主題中存在的細微細節*。 下面是一個帶有微妙灰色 UI 的範例,用於區分工具視窗中的區域。 與在高對比度模式下顯示的同一視窗配對時,您可以看到所有背景都具有相同的色調,並且這些區域的邊界僅由邊框表示:

![高對比度中如何遺失細微細節的範例](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />高對比度中如何遺失細微細節的範例

#### <a name="choosing-text-colors-in-an-editor"></a>在編輯器中選擇文字顏色

著色文字用於編輯器或設計表面以指示含義,例如允許輕鬆識別類似項組。 但是,在高對比度主題中,您無法區分三種以上文本顏色。 視窗文字、灰色文本和熱軌道文本是視窗背景曲面上唯一可用的顏色。 由於不能使用三種顏色以上,請仔細選擇在高對比度模式下要顯示的最重要差異。

編輯器曲面上允許的每個權杖名稱的色調,因為它們出現在每個高對比度主題中:

![高對比編輯器比較](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />高對比編輯器比較

藍色主題中編輯器表面的範例:

![藍色佈景主題的編輯器](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />藍色佈景主題的編輯器

![高對比度#1主題的編輯](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />高對比度#1主題的編輯

### <a name="usage-patterns"></a>使用模式

許多常見的 UI 元素已定義了高對比度顏色。 在選擇自己的系統顏色名稱時,可以引用這些使用模式,以便UI元素與類似的元件一致。

| 系統顏色 | 使用量 |
| --- | --- |
| ActiveCaption | - 活動 IDE 和漂流視窗按鈕字形懸停並按下<br />- IDE 與漂流視窗的標題列背景<br />- 預設狀態列背景 |
| ActiveCaptionText | - 標題列前景的活動 IDE 和漂流視窗(文字和字形)<br />- 移動移動視窗按鈕的背景與邊框, 然後按下 |
| 控制 | - 組合框、下拉清單以及搜尋控制項預設和關閉的背景,包括下拉按鈕<br />- 停用目標按鍵背景<br />- 命令列背景<br />- 工具視窗背景 |
| ControlDark | - IDE 背景<br />- 選單和指令列分隔符號<br />- 命令列邊框<br />- 選單陰影<br />- 工具視窗選項卡預設值和懸停邊框和分隔符<br />- 記錄位值背景<br />- 停靠目標字形邊框 |
| ControlDarkDark |- 未聚焦、選擇的文件選項卡視窗 |
| ControlLight |- 自動隱藏選項卡邊框<br />- 組合框與下拉列表邊框<br />- 停用目標背景與邊框 |
| 控制燈 | - 選定、重點突出的臨時邊界 |
| 控制項文字 | - 組合框與下拉清單字形<br />- 工具視窗沒有選取的選項卡文字 |
| 灰色文字 |- 組合框與下拉清單關閉邊框、下拉字、文字和選單項目<br />- 關閉選單文字<br />- 搜尋控制檔「搜尋選項」標題文字<br />- 搜尋控制截面分隔符 |
| 反白顯示 | - 所有移動和按下的背景與邊框,但組合框下拉按鈕背景和文件溢出按鈕邊框<br />- 選擇的項目背景 |
| 突顯文字 | - 所有一個的前景(文字與字形)<br />- 焦點工具視窗與文件選項卡視窗控制前景<br />- 焦點工具視窗標題列邊框<br />- 焦點的暫時選項<br />- 在懸停上記錄溢流按鈕邊框,然後按<br />- 選擇的圖示框框|
| 熱軌道 | - 按壓上捲軸條拇指背景與邊框<br />- 按壓時捲動條箭頭字形 |
| 非作用標題 | - 移動視窗鍵字形<br />- IDE 與漂流視窗的標題列背景<br />- 停用的搜尋控制背景 |
| 非作用字幕文字 | - 非活動 IDE 和漂流視窗標題列前景(文字和字形)<br />- 非作用視窗按鍵背景與移動邊框<br />- 無焦點工具視窗按鈕背景與邊框<br />- 停用的搜尋控制前景 |
| 功能表 | - 下拉選單背景<br />- 已選取的選擇並關閉複選標記背景 |
| 選單文字 | - 下拉選單邊框<br />- 檢查標籤<br />- 選單字形<br />- 下拉選單文字<br />- 選擇的圖示框框 |
| 捲軸 | - 捲動條和捲動條箭頭背景,所有狀態 |
| 時間範圍 | - 自動隱藏選項卡背景<br />- 選單列與指令擱板背景<br />- 未聚焦或未選擇的文件視窗選項卡背景和文件邊框,適用於開啟和暫時選項卡<br />- 無焦點工具視窗標題列背景<br />- 工具視窗選項卡背景,已選擇與未選取 |
| 視窗框架 | - IDE 邊框 |
| 視窗文字 | - 自動隱藏選項卡前景<br />- 選擇的工具視窗選項卡前景<br />- 未聚焦的文件視窗選項卡與未聚焦或未選取的暫時選項卡前景<br />- 樹狀圖預設前景,並將滑鼠懸停在未選擇的字形上<br />- 工具視窗選擇選項卡邊框<br />- 捲動條拇指背景、邊框和字形 |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a>為最終使用者公開顏色

### <a name="overview"></a>概觀

有時,您希望允許最終使用者自定義 UI,例如創建代碼編輯器或設計圖面時。 最常見的方法是使用 **「&gt;工具 選項」** 對話框。 除非您具有需要特殊控制式的高度專業化 UI,否則顯示自訂的最簡單方法是透過對話框 **「環境**」部分中的 **「字型和顏色**」頁。 對於要自定義公開的每個元素,用戶可以選擇更改前景顏色、背景顏色或兩者。

### <a name="building-a-vspackage-for-your-customizable-colors"></a>為可自訂的顏色建構 VS 套件

VSPackage 可以通過自定義類別控制字體和顏色,並在"字體和顏色"屬性頁上顯示專案。 使用此機制時,VSPackages 必須實現[IVsFontAndColorDefaults 提供程式介面](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider)及其關聯的介面。

原則上,此機制可用於修改所有現有的顯示項及其包含它們的類別。 但是,它不應用於修改文本編輯器類別或其顯示項。 關於文字編輯器類別的詳細資訊,請參考[字型與顏色概述](/visualstudio/extensibility/font-and-color-overview?view=vs-2015)。

要實現自訂類別或顯示專案,VS 的項目必須:

- **創建或標識註冊表中的類別。** IDE 的 **「字型和顏色**」屬性頁的實現使用此資訊正確查詢支援給定類別的服務。

- **在註冊表中創建或標識組(可選)。** 定義表示兩個或多個類別的聯合的組可能很有用。 如果定義了組,IDE 將自動合併子類別並在組中分發顯示項。

- **實施 IDE 支援。**

- **處理字型和顏色更改。**

#### <a name="to-create-or-identify-categories"></a>建立或識別類別

建構特殊類型的類別註冊表項,其`[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]``<Category>`下是類別的非本地化名稱。

使用兩個值填充註冊表:

| 名稱 | 類型 | 資料 | 描述 |
| --- | --- | --- | --- |
| 類別 | REG_SZ | GUID | 為識別類別與建立的 GUID |
| Package | REG_SZ | GUID | 支援類別的 VSPackage 服務的 GUID |

 註冊表中指定的服務必須為相應的類別提供[IVsFontAndColorDefaults 的](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)實現。

#### <a name="to-create-or-identify-groups"></a>建立或識別群組

建構特殊類型的類別註冊表項,其`[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]``<group>`下是組的非本地化名稱。

使用兩個值填充註冊表:

| 名稱 | 類型 | 資料 | 描述 |
|--- | --- | --- | --- |
| 類別 | REG_SZ | GUID | 為識別類別與建立的 GUID |
| Package | REG_SZ | GUID | 支援類別的 VSPackage 服務的 GUID |

註冊表中指定的服務必須為相應的組提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>的 實現。

![實施IVsfontandColor集團](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />`IVsFontAndColorGroup` 的實作

### <a name="to-implement-ide-support"></a>實作 IDE 支援

實現[GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject),它傳回[IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)介面<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>或每個類別或 GUID 提供的 IDE 介面。

對於它支援的每個類別,VS包實現[IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)介面的單獨實例。

透過[IVsfontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)可提供 IDE 提供:

- 類別顯示項目清單

- 顯示項目的可本地化名稱

- 顯示類別每個成員的資訊

> [!NOTE]
> 每個類別必須至少包含一個顯示項。

IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>使用介面定義多個類別的聯合。

其實現為 IDE 提供:

- 組成給定群組的類別清單

- 存取支援群組的[IVsFontAndColorDefaults 實體](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)

- 可本地化群組名稱

#### <a name="updating-the-ide"></a>更新 IDE

IDE 快取有關字型和顏色設定的資訊。 因此,在修改 IDE 字體和顏色配置後,最佳做法是確保緩存是最新的。

更新緩存透過[IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager)介面完成,可以全域執行,也可以僅對選定專案執行。

### <a name="handling-font-and-color-changes"></a>處理字型與顏色變更

為了正確支援 VSPackage 顯示的文本著色,支援 VSPackage 的著色服務必須回應使用者透過"字體和顏色"屬性頁所做的更改。

為此,VS 包必須:

- 透過[IVsfontAndColor 事件](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents)介面**來處理 IDE 產生的事件**。 在使用者修改"字體和顏色"頁後,IDE 調用適當的方法。 例如,如果選擇了新字體,它將調用[OnFont"更改](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged)"方法。

  **OR**

- **輪詢 IDE 以變更**。 這可以通過系統實現的[IVsfontAndColor 儲存](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage)介面來完成。 儘管主要為了支援持久性,但[GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem)方法可以獲取顯示專案的字體和顏色資訊。 關於字型與顏色設定的詳細資訊,請參考 MSDN 文章[存取記憶體的字型與顏色設定](/visualstudio/extensibility/accessing-stored-font-and-color-settings?view=vs-2015)。

> [!NOTE]
> 為確保輪詢結果正確,請使用[IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager)介面來確定是否需要緩存刷新和更新,然後調用[IVsFontAndColor 儲存](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage)介面的檢索方法。

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>註冊自訂字型和顏色類別,無需實現介面

以下代碼範例展示如何在不實作介面的註冊自訂字型和顏色類別:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

對於此代碼範例:

- `"NameID"`• 套件內化類別名稱的資源識別碼
- `"ToolWindowPackage"`• 包 GUID
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"`只是一個示例,實際值可以是實現器提供的新 GUID。

### <a name="set-the-font-and-color-property-category-guid"></a>設定字型與顏色屬性類別 GUID

下面的代碼示例演示了設置類別 GUID。

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
