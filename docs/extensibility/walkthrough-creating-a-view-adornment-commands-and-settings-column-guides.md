---
title: 建立檢視修飾、命令和設定 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4aab9e0ede95eebe6f8f54cc3f01e7e7d5f98d1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697651"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>演練:建立檢視裝飾、指令和設定(列參考線)
您可以使用命令和檢視效果擴展 Visual Studio 文字/代碼編輯器。 本文介紹如何開始使用流行的擴展功能,列指南。 列參考線是在文字編輯器的檢視上繪製的視覺光線,可説明您將代碼管理到特定的列寬度。 具體來說,格式化的代碼對於包含在文檔、博客文章或 Bug 報告中的範例非常重要。

在本逐步解說中，您將：
- 建立 VSIX 專案
- 新增編輯器檢視修飾
- 新增對儲存及取得設定的支援 (在何處繪製列參考線及其顏色)
- 新增指令(新增/刪除列參考線,更改其顏色)
- 將指令放在「編輯」選單和文字文件上下文選單上
- 新增從視覺化工作室指令視窗呼叫指令

  您可以使用此可視化工作室庫[擴展名](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)試用列指南功能的版本。

  > [!NOTE]
  > 在本演練中,您將大量程式碼貼上到 Visual Studio 擴充樣本生成的幾個檔中。 但是,很快本演練將參考 GitHub 上已完成的解決方案以及其他擴展示例。 已完成的代碼略有不同,因為它具有真正的命令圖示,而不是使用泛型範本。

## <a name="get-started"></a>開始使用
從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="set-up-the-solution"></a>設定解決方案
首先,創建 VSIX 專案,添加編輯器檢視修飾,然後添加一個命令(該命令添加 VSPackage 來擁有該命令)。 基本體系結構如下所示:
- 您有一個文字檢視建立偵聽器`ColumnGuideAdornment`,用於創建每個檢視的物件。 此物件根據需要偵聽有關檢視更改或設置更改、更新或重繪列參考線的事件。
- 有一個`GuidesSettingsManager`處理從 Visual Studio 設置儲存讀取和寫入。 設置管理員還有用於更新支援使用者命令的設置的操作(添加列、刪除列、更改顏色)。
- 如果您有使用者命令,則需要使用 VSIP 包,但只是初始化命令實現對象的樣板代碼。
- 有一個`ColumnGuideCommands`物件運行使用者命令,並掛接*在 .vsct*檔中聲明的命令的命令處理程式。

  **VSIX**. 使用**檔案&#124; New ...** 指令建立專案。 在左邊導覽窗格中選擇**C#** 下的 **'擴充性節點' 的選項**, 並在右邊窗格中選擇**VSIX 專案**。 輸入名稱 **「列指南**」並選擇 **「確定」** 以建立專案。

  **檢視修飾**。 按解決方案資源管理器中專案節點上的右指標按鈕。 選擇「**新增&#124;新項目 ...** 在左側導航窗格中選擇 **「可擴充性&#124;編輯器**」,並在右側窗格中選擇 **「編輯器視口裝飾**」。 輸入名稱 **「列指南」** 作為專案名稱,然後選擇 **「添加**」以添加它。

  您可以看到此選項的樣本向專案新增了兩個檔案(以及引用,等等 **):ColumnGuideAdornment.cs**和**ColumnGuideAdornmentTextViewCreationListener.cs**。 範本在視圖上繪製紫色矩形。 在以下部分中,您將更改檢視創建偵聽器中的幾行,並替換**ColumnGuideAdornment.cs**的內容。

  **命令**. 在**解決方案資源管理員中**,按專案節點上的右指標按鈕。 選擇「**新增&#124;新項目 ...** 在左側導航窗格**中選擇"擴充性&#124; VSPackage",** 並在右側窗格中選擇 **「自定義命令**」。 輸入名稱**列指南命令**作為專案名稱,然後選擇 **「添加**」。 除了幾個引用,添加命令和包還新增了**ColumnGuideCommands.cs、ColumnGuideCommandsPackage.cs**和**ColumnGuideCommandsPackage.cs** **ColumnGuideCommandsPackage.vsct**。 在以下部分中,替換第一個和最後一個文件的內容,以定義和實現命令。

## <a name="set-up-the-text-view-creation-listener"></a>設定文字檢視建立偵聽器
在編輯器中打開*ColumnGuideAdornmentTextViewCreationListener.cs。* 每當 Visual Studio 創建文字檢視時,此代碼都會實現處理程式。 根據視圖的特徵,有一些屬性可以控制調用處理程式。

代碼還必須聲明修飾層。 當編輯器更新檢視時,它會獲取視圖的修飾圖層,並從中獲取修飾元素。 您可以使用屬性聲明圖層相對於其他圖層的順序。 更換以下行:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

用這兩行:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

替換的行位於聲明修飾圖層的一組屬性中。 您更改的第一列僅更改列參考線顯示的位置。 在檢視中繪製「之前」的文本意味著它們顯示在文本後面或下方。 第二行聲明,列指南修飾適用於符合文檔概念的文本實體,但您可以聲明修飾(例如,僅適用於可編輯文本)。 [語言服務和編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)中提供更多資訊

## <a name="implement-the-settings-manager"></a>設定管理員
將*GuidesSettingsManager.cs*的內容取代為以下代碼(如下所述):

```csharp
using Microsoft.VisualStudio.Settings;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Settings;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows.Media;

namespace ColumnGuides
{
    internal static class GuidesSettingsManager
    {
        // Because my code is always called from the UI thred, this succeeds.
        internal static SettingsManager VsManagedSettingsManager =
            new ShellSettingsManager(ServiceProvider.GlobalProvider);

        private const int _maxGuides = 5;
        private const string _collectionSettingsName = "Text Editor";
        private const string _settingName = "Guides";
        // 1000 seems reasonable since primary scenario is long lines of code
        private const int _maxColumn = 1000;

        static internal bool AddGuideline(int column)
        {
            if (! IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column",
                    "The paramenter must be between 1 and " + _maxGuides.ToString());
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            if (offsets.Count() >= _maxGuides)
                return false;
            // Check for duplicates
            if (offsets.Contains(column))
                return false;
            offsets.Add(column);
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);
            return true;
        }

        static internal bool RemoveGuideline(int column)
        {
            if (!IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column", "The paramenter must be between 1 and 10,000");
            var columns = GuidesSettingsManager.GetColumnOffsets();
            if (! columns.Remove(column))
            {
                // Not present.  Allow user to remove the last column
                // even if they're not on the right column.
                if (columns.Count != 1)
                    return false;

                columns.Clear();
            }
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);
            return true;
        }

        static internal bool CanAddGuideline(int column)
        {
            if (!IsValidColumn(column))
                return false;
            var offsets = GetColumnOffsets();
            if (offsets.Count >= _maxGuides)
                return false;
            return ! offsets.Contains(column);
        }

        static internal bool CanRemoveGuideline(int column)
        {
            if (! IsValidColumn(column))
                return false;
            // Allow user to remove the last guideline regardless of the column.
            // Okay to call count, we limit the number of guides.
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            return offsets.Contains(column) || offsets.Count() == 1;
        }

        static internal void RemoveAllGuidelines()
        {
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);
        }

        private static bool IsValidColumn(int column)
        {
            // zero is allowed (per user request)
            return 0 <= column && column <= _maxColumn;
        }

        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".
        // There can be any number of ints following the RGB part,
        // and each int is a column (char offset into line) where to draw.
        static private string _guidelinesConfiguration;
        static private string GuidelinesConfiguration
        {
            get
            {
                if (_guidelinesConfiguration == null)
                {
                    _guidelinesConfiguration =
                        GetUserSettingsString(
                            GuidesSettingsManager._collectionSettingsName,
                            GuidesSettingsManager._settingName)
                        .Trim();
                }
                return _guidelinesConfiguration;
            }

            set
            {
                if (value != _guidelinesConfiguration)
                {
                    _guidelinesConfiguration = value;
                    WriteUserSettingsString(
                        GuidesSettingsManager._collectionSettingsName,
                        GuidesSettingsManager._settingName, value);
                    // Notify ColumnGuideAdornments to update adornments in views.
                    var handler = GuidesSettingsManager.SettingsChanged;
                    if (handler != null)
                        handler();
                }
            }
        }

        internal static string GetUserSettingsString(string collection, string setting)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);
            return store.GetString(collection, setting, "RGB(255,0,0) 80");
        }

        internal static void WriteUserSettingsString(string key, string propertyName,
                                                     string value)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetWritableSettingsStore(SettingsScope.UserSettings);
            store.CreateCollection(key);
            store.SetString(key, propertyName, value);
        }

        // Persists settings and sets property with side effect of signaling
        // ColumnGuideAdornments to update.
        static private void WriteSettings(Color color, IEnumerable<int> columns)
        {
            string value = ComposeSettingsString(color, columns);
            GuidelinesConfiguration = value;
        }

        private static string ComposeSettingsString(Color color,
                                                    IEnumerable<int> columns)
        {
            StringBuilder sb = new StringBuilder();
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();
            if (columnsEnumerator.MoveNext())
            {
                sb.AppendFormat(" {0}", columnsEnumerator.Current);
                while (columnsEnumerator.MoveNext())
                {
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);
                }
            }
            return sb.ToString();
        }

        // Parse a color out of a string that begins like "RGB(255,0,0)"
        static internal Color GuidelinesColor
        {
            get
            {
                string config = GuidelinesConfiguration;
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))
                {
                    int lastParen = config.IndexOf(')');
                    if (lastParen > 4)
                    {
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');

                        if (rgbs.Length >= 3)
                        {
                            byte r, g, b;
                            if (byte.TryParse(rgbs[0], out r) &&
                                byte.TryParse(rgbs[1], out g) &&
                                byte.TryParse(rgbs[2], out b))
                            {
                                return Color.FromRgb(r, g, b);
                            }
                        }
                    }
                }
                return Colors.DarkRed;
            }

            set
            {
                WriteSettings(value, GetColumnOffsets());
            }
        }

        // Parse a list of integer values out of a string that looks like
        // "RGB(255,0,0) 1, 5, 10, 80"
        static internal List<int> GetColumnOffsets()
        {
            var result = new List<int>();
            string settings = GuidesSettingsManager.GuidelinesConfiguration;
            if (String.IsNullOrEmpty(settings))
                return new List<int>();

            if (!settings.StartsWith("RGB("))
                return new List<int>();

            int lastParen = settings.IndexOf(')');
            if (lastParen <= 4)
                return new List<int>();

            string[] columns = settings.Substring(lastParen + 1).Split(',');

            int columnCount = 0;
            foreach (string columnText in columns)
            {
                int column = -1;
                // VS 2008 gallery extension didn't allow zero, so per user request ...
                if (int.TryParse(columnText, out column) && column >= 0)
                {
                    columnCount++;
                    result.Add(column);
                    if (columnCount >= _maxGuides)
                        break;
                }
            }
            return result;
        }

        // Delegate and Event to fire when settings change so that ColumnGuideAdornments
        // can update.  We need nothing special in this event since the settings manager
        // is statically available.
        //
        internal delegate void SettingsChangedHandler();
        static internal event SettingsChangedHandler SettingsChanged;

    }
}

```

大多數此代碼創建並分析設置格式:「RGB(>、int\<\<>、int\<>)int \<>、int \<>......"。  末尾的整數是需要列參考線的一個基於列的列。 列參考線擴展在單個設置值字串中捕獲其所有設置。

代碼的某些部分值得突出顯示。 以下代碼行獲取用於設置存儲的 Visual Studio 託管包裝器。 在大多數情況下,此摘要通過 Windows 註冊表,但此 API 獨立於儲存機制。

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Visual Studio 設定儲存使用類別識別碼和設定識別子來唯一識別所有設定:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

您不必用作`"Text Editor"`類別名稱。 你可以選擇任何你喜歡的東西。

前幾個函數是更改設置的入口點。 它們檢查高級約束,如允許的最大參考線數。  然後,他們呼叫`WriteSettings`,它組成一個設定字串並設定屬性`GuideLinesConfiguration`。 設置此屬性會將設置值保存到 Visual Studio 設置`SettingsChanged`存儲,並觸發事件`ColumnGuideAdornment`以更新所有 物件,每個物件都與文本視圖相關聯。

有幾個入口點函數,如`CanAddGuideline`,用於實現更改設置的命令。 當 Visual Studio 顯示選單時,它會查詢命令實現以查看該命令當前是否啟用、名稱是什麼,等等。  下面您將看到如何連接這些入口點以執行命令實現。 關於命令的詳細資訊,請參閱[延伸選單和指令](../extensibility/extending-menus-and-commands.md)。

## <a name="implement-the-columnguideadornment-class"></a>實現列指南修飾類
對於`ColumnGuideAdornment`每個可以具有修飾的文本視圖,將實例化該類。 此類偵聽有關檢視更改或設置更改的事件,以及根據需要更新或重繪列參考線的事件。

將*ColumnGuideAdornment.cs*的內容取代為以下代碼(如下所述):

```csharp
using System;
using System.Windows.Media;
using Microsoft.VisualStudio.Text.Editor;
using System.Collections.Generic;
using System.Windows.Shapes;
using Microsoft.VisualStudio.Text.Formatting;
using System.Windows;

namespace ColumnGuides
{
    /// <summary>
    /// Adornment class, one instance per text view that draws a guides on the viewport
    /// </summary>
    internal sealed class ColumnGuideAdornment
    {
        private const double _lineThickness = 1.0;
        private IList<Line> _guidelines;
        private IWpfTextView _view;
        private double _baseIndentation;
        private double _columnWidth;

        /// <summary>
        /// Creates editor column guidelines
        /// </summary>
        /// <param name="view">The <see cref="IWpfTextView"/> upon
        /// which the adornment will be drawn</param>
        public ColumnGuideAdornment(IWpfTextView view)
        {
            _view = view;
            _guidelines = CreateGuidelines();
            GuidesSettingsManager.SettingsChanged +=
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);
            view.LayoutChanged +=
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);
            _view.Closed += new EventHandler(OnViewClosed);
        }

        void SettingsChanged()
        {
            _guidelines = CreateGuidelines();
            UpdatePositions();
            AddGuidelinesToAdornmentLayer();
        }

        void OnViewClosed(object sender, EventArgs e)
        {
            _view.LayoutChanged -= OnViewLayoutChanged;
            _view.Closed -= OnViewClosed;
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;
        }

        private bool _firstLayoutDone;

        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
        {
            bool fUpdatePositions = false;

            IFormattedLineSource lineSource = _view.FormattedLineSource;
            if (lineSource == null)
            {
                return;
            }
            if (_columnWidth != lineSource.ColumnWidth)
            {
                _columnWidth = lineSource.ColumnWidth;
                fUpdatePositions = true;
            }
            if (_baseIndentation != lineSource.BaseIndentation)
            {
                _baseIndentation = lineSource.BaseIndentation;
                fUpdatePositions = true;
            }
            if (fUpdatePositions ||
                e.VerticalTranslation ||
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)
            {
                UpdatePositions();
            }
            if (!_firstLayoutDone)
            {
                AddGuidelinesToAdornmentLayer();
                _firstLayoutDone = true;
            }
        }

        private static IList<Line> CreateGuidelines()
        {
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });
            IList<Line> result = new List<Line>();
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())
            {
                Line line = new Line()
                {
                    // Use the DataContext slot as a cookie to hold the column
                    DataContext = column,
                    Stroke = lineBrush,
                    StrokeThickness = _lineThickness,
                    StrokeDashArray = dashArray
                };
                result.Add(line);
            }
            return result;
        }

        void UpdatePositions()
        {
            foreach (Line line in _guidelines)
            {
                int column = (int)line.DataContext;
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;
                line.X1 = line.X2;
                line.Y1 = _view.ViewportTop;
                line.Y2 = _view.ViewportBottom;
            }
        }

        void AddGuidelinesToAdornmentLayer()
        {
            // Grab a reference to the adornment layer that this adornment
            // should be added to
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener
            IAdornmentLayer adornmentLayer =
                _view.GetAdornmentLayer("ColumnGuideAdornment");
            if (adornmentLayer == null)
                return;
            adornmentLayer.RemoveAllAdornments();
            // Add the guidelines to the adornment layer and make them relative
            // to the viewport
            foreach (UIElement element in _guidelines)
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,
                                            null, null, element, null);
        }
    }

}
```

此類的實例保留到關聯的<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>`Line`物件和在視圖上繪製的物件清單。

建構函數(在`ColumnGuideAdornmentTextViewCreationListener`Visual Studio創建新檢視時調用)創建列指南`Line`物件。  建構函數`SettingsChanged`還添加事件(在`GuidesSettingsManager`中定義)和檢視事件`LayoutChanged`和`Closed`的處理程式。

由於`LayoutChanged`檢視中的多種更改(包括 Visual Studio 創建檢視時),事件將觸發。 處理程式`OnViewLayoutChanged`調`AddGuidelinesToAdornmentLayer`用 以執行。 中`OnViewLayoutChanged`的代碼確定是否需要根據更改(如字體大小更改、視圖排水溝、水平滾動等)更新行位置。 中的`UpdatePositions`代碼會導致引導行在字元之間或文本列之後繪製,該列位於文本行中指定的字元偏移量中。

每當設定更改時`SettingsChanged`,函數只需使用任何新`Line`設置重新創建所有物件。 設置列位置後,代碼將從`Line``ColumnGuideAdornment`修飾圖層中刪除所有以前的物件並添加新物件。

## <a name="define-the-commands-menus-and-menu-placements"></a>定義命令、選單和選單位置
聲明命令和功能表、在各種其他功能表上放置命令或功能表組以及掛接命令處理程式可能有很多。 這個演練重點介紹命令在此擴展中的工作方式,但有關更深入的資訊,請參閱[延伸選單和命令](../extensibility/extending-menus-and-commands.md)。

### <a name="introduction-to-the-code"></a>程式碼簡介
"列參考線"副檔名顯示聲明屬於一組命令(添加列、刪除列、更改行顏色),然後將該組放在編輯器上下文菜單的子菜單上。  "列參考線"副檔名還會將指令添加到**主編輯**功能表中,但使其不可見,下面是一個常見模式。

命令實現有三個部分:ColumnGuideCommandsPackage.cs、列指南命令包.vsct 和ColumnGuideCommands.cs。 範本生成的代碼在 **「工具」** 選單上放置一個命令,該命令彈出一個對話框作為實現。 您可以查看如何在 *.vsct*和*ColumnGuideCommands.cs*檔中實現,因為它非常簡單。 替換下面這些檔案中的代碼。

包代碼包含 Visual Studio 發現擴展提供命令並找到將命令放置位置所需的樣板聲明。 當包初始化時,它會實例化命令實現類。 有關與指令相關的套件的詳細資訊,請參閱[延伸選單和指令](../extensibility/extending-menus-and-commands.md)。

### <a name="a-common-commands-pattern"></a>通用命令模式
列參考線擴展中的命令是可視化工作室中非常常見的模式的示例。 將相關命令放在組中,並將該組放在主菜單上,通常設置""`<CommandFlag>CommandWellOnly</CommandFlag>`使命令不可見。  在主選單(如**Edit)** 上放置命令會為它們提供漂亮的名稱(如**Edit.AddColumnGuide),** 這對於在**工具選項**中重新分配鍵綁定時查找命令非常有用。 當從**命令視窗**調用命令時,它對於完成也很有用。

然後,將命令組添加到上下文菜單或子功能表中,您希望使用者使用這些命令。 Visual Studio`CommandWellOnly`僅視為主功能表的不可見標誌。 將同一組命令放在上下文菜單或子功能表上時,這些命令是可見的。

作為常見模式的一部分,"列參考線"擴展將創建第二個組,該組包含單個子功能表。 子功能表依次包含具有四列引導命令的第一組。 保存子功能表的第二個組是放置在各種上下文菜單上的可重用資產,該資產在這些上下文菜單上放置了一個子功能表。

### <a name="the-vsct-file"></a>.vsct 檔案
*.vsct*檔聲明命令及其去向以及圖示等。 將 *.vsct*檔案的內容取代為以下代碼(以下的語記):

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <!--  This is the file that defines the actual layout and type of the commands.
        It is divided in different sections (e.g. command definition, command
        placement, ...), with each defining a specific set of properties.
        See the comment before each section for more details about how to
        use it. -->

  <!--  The VSCT compiler (the tool that translates this file into the binary
        format that VisualStudio will consume) has the ability to run a preprocessor
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so
        it is possible to define includes and macros with the same syntax used
        in C++ files. Using this ability of the compiler here, we include some files
        defining some of the constants that we will use inside the file. -->

  <!--This is the file that defines the IDs for all the commands exposed by
      VisualStudio. -->
  <Extern href="stdidcmd.h"/>

  <!--This header contains the command ids for the menus provided by the shell. -->
  <Extern href="vsshlids.h"/>

  <!--The Commands section is where commands, menus, and menu groups are defined.
      This section uses a Guid to identify the package that provides the command
      defined inside it. -->
  <Commands package="guidColumnGuideCommandsPkg">
    <!-- Inside this section we have different sub-sections: one for the menus, another
    for the menu groups, one for the buttons (the actual commands), one for the combos
    and the last one for the bitmaps used. Each element is identified by a command id
    that is a unique pair of guid and numeric identifier; the guid part of the identifier
    is usually called "command set" and is used to group different command inside a
    logically related group; your package should define its own command set in order to
    avoid collisions with command ids defined by other packages. -->

    <!-- In this section you can define new menu groups. A menu group is a container for
         other menus or buttons (commands); from a visual point of view you can see the
         group as the part of a menu contained between two lines. The parent of a group
         must be a menu. -->
    <Groups>

      <!-- The main group is parented to the edit menu. All the buttons within the group
           have the "CommandWellOnly" flag, so they're actually invisible, but it means
           they get canonical names that begin with "Edit". Using placements, the group
           is also placed in the GuidesSubMenu group. -->
      <!-- The priority 0xB801 is chosen so it goes just after
           IDG_VS_EDIT_COMMANDWELL -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that
           drops the sub menu). The group is parented to
           the context menu for code windows. That takes care of most editors, but it's
           also placed in a couple of other windows using Placements -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />
      </Group>

    </Groups>

    <Menus>
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"
            type="Menu">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />
        <Strings>
          <ButtonText>&Column Guides</ButtonText>
        </Strings>
      </Menu>
    </Menus>

    <!--Buttons section. -->
    <!--This section defines the elements the user can interact with, like a menu command or a button
        or combo box in a toolbar. -->
    <Buttons>
      <!--To define a menu group you have to specify its ID, the parent menu and its
          display priority.
          The command is visible and enabled by default. If you need to change the
          visibility, status, etc, you can use the CommandFlag node.
          You can add more than one CommandFlag node e.g.:
              <CommandFlag>DefaultInvisible</CommandFlag>
              <CommandFlag>DynamicVisibility</CommandFlag>
          If you do not want an image next to your command, remove the Icon node or
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->

      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
              priority="0x0100" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicAddGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Add Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"
              priority="0x0101" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Remove Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"
              priority="0x0103" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicChooseColor" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Column Guide &Color...</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"
              priority="0x0102" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Remove A&ll Columns</ButtonText>
        </Strings>
      </Button>
    </Buttons>

    <!--The bitmaps section is used to define the bitmaps that are used for the
        commands.-->
    <Bitmaps>
      <!--  The bitmap id is defined in a way that is a little bit different from the
            others:
            the declaration starts with a guid for the bitmap strip, then there is the
            resource id of the bitmap strip containing the bitmaps and then there are
            the numeric ids of the elements used inside a button definition. An important
            aspect of this declaration is that the element id
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />
    </Bitmaps>

  </Commands>

  <CommandPlacements>

    <!-- Define secondary placements for our groups -->

    <!-- Place the group containing the three commands in the sub-menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                      priority="0x0100">
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
    </CommandPlacement>

    <!-- The HTML editor context menu, for some reason, redefines its own groups
         so we need to place a copy of our context menu there too. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />
    </CommandPlacement>

    <!-- The HTML context menu in Dev12 changed. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />
    </CommandPlacement>

    <!-- Similarly for Script -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />
    </CommandPlacement>

    <!-- Similarly for ASPX  -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />
    </CommandPlacement>

    <!-- Similarly for the XAML editor context menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x0600">
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />
    </CommandPlacement>

  </CommandPlacements>

  <!-- This defines the identifiers and their values used above to index resources
       and specify commands. -->
  <Symbols>
    <!-- This is the package guid. -->
    <GuidSymbol name="guidColumnGuideCommandsPkg"
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />

    <!-- This is the guid used to group the menu commands together -->
    <GuidSymbol name="guidColumnGuidesCommandSet"
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />
      <IDSymbol name="GuidesSubMenu" value="0x1022" />
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />
    </GuidSymbol>

    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
      <IDSymbol name="bmpPicAddGuide" value="1" />
      <IDSymbol name="bmpPicRemoveGuide" value="2" />
      <IDSymbol name="bmpPicChooseColor" value="3" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />
    </GuidSymbol>

    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />
    </GuidSymbol>
  </Symbols>

</CommandTable>

```

**GUIDS**. 對於 Visual Studio 尋找指令處理程式並調用它們,您需要確保*在 ColumnGuideCommands Package.cs*檔中聲明的包 GUID(從專案樣本產生)與 *.vsct*檔中聲明的包 GUID(從上面複製)匹配。 如果重複使用此示例代碼,則應確保具有不同的 GUID,以便不與可能複製此代碼的任何其他人發生衝突。

在*ColumnGuideCommandsPackage.cs*中尋找此行,並在引號之間複製 GUID:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

然後,將 GUID 貼上到 *.vsct*檔`Symbols`中,以便在聲明中具有以下行:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

命令集的 GUID 和位圖影像檔對於擴展也是唯一的:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

但是,在本演練中,您不需要更改命令集和位圖圖像 GUID 即可使代碼正常工作。 命令集 GUID 需要匹配*ColumnGuideCommands.cs*檔中的聲明,但您也替換該文件的內容;因此,GUID 將匹配。

*.vsct*檔中的其他 GUID 標識將列指南命令添加到的預先存在的功能表,因此它們永遠不會更改。

**檔案部份**。 *.vsct*有三個外部部分:命令、位置和符號。 命令部分定義圖示的命令組、功能表、按鈕或功能表項以及位圖。 放置部分聲明組在功能表上或將其他放置位置轉到預先存在的菜單的位置。 符號部分聲明*在 .vsct*檔的其他位置使用的標識碼,這使得 *.vsct*代碼比隨處都有 GUID 和十六進位數位更具可讀性。

**指令部份,群組定義**。 命令部分首先定義命令組。 命令組是您在功能表中看到的命令,這些命令帶有分隔組的輕微灰色線條。 組還可以填充整個子功能表,如本示例所示,在這種情況下,您看不到灰色分隔線。 *.vsct*檔聲明兩個組`GuidesMenuItemsGroup`, 一個組是`IDM_VS_MENU_EDIT`父級 的(主 編輯`GuidesContextMenuGroup`功能表`IDM_VS_CTXT_CODEWIN`)和 父級組 (代碼編輯器的上下文選單)。**Edit**

第二組宣告具有`0x0600`優先權:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

其想法是將列參考線子功能表放在向其添加子功能表組的任何上下文菜單的末尾。 但是,您不應假定您最了解,並且使用`0xFFFF`的優先順序強制子菜單始終為最後。 您必須嘗試該數位,以查看子菜單位於放置該功能表的上下文菜單上的位置。 在這種情況下,`0x0600`足夠高,可以盡可能將其放在菜單的末尾,但它為其他人留出空間來設計其擴展,使其低於列參考線擴展名(如果需要)。

**命令部份,選單定義**。 接下來,命令部分定義子選單,該子`GuidesSubMenu`選單為 父`GuidesContextMenuGroup`選單 。 是`GuidesContextMenuGroup`添加到所有相關上下文菜單的組。 在放置部分中,代碼將組在此子功能表上放置帶有四列指南命令的組。

**命令部份,按鈕定義**。 然後,命令部分定義功能表項或作為四列參考線命令的按鈕。 `CommandWellOnly`,上面討論,意味著命令是不可見的,當放置在主菜單上。 選單項目按鈕聲明的兩個(新增指南和刪除指南)也有一個`AllowParams`標誌:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

此標誌啟用在 Visual Studio 呼叫命令處理程式時接收參數的命令,以及具有主選單位置的命令。  如果使用者從命令視窗運行該命令,則參數將傳遞給事件參數中的命令處理程式。

**命令部份,點陣圖定義**。 最後,命令部分聲明用於命令的點陣圖或圖示。 本節是一個簡單的聲明,用於標識專案資源並列出已使用的圖示的一個基於一個索引。 *.vsct*檔的符號部分聲明用作索引的標識符的值。 本演練使用添加到專案的自定義命令項範本提供的位圖條。

**放置部份**. 命令節後是放置部分。 第一個代碼將上面討論的第一組新增到出現指令的子選單中,該組將四列引導命令保留到:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

所有其他位置將`GuidesContextMenuGroup`(`GuidesSubMenu`包含 ) 添加到其他編輯器上下文功能表。 當代碼聲明`GuidesContextMenuGroup`時 ,它被父級聲明到代碼編輯器的上下文菜單。 這就是為什麼您看不到代碼編輯器上下文菜單的位置。

**符號部份**. 如上所述,符號部分聲明*在 .vsct*檔的其他位置使用的標識符,這使得 *.vsct*代碼比隨處都有 GUID 和十六進位數位更具可讀性。 本節的要點是包 GUID 必須同意包類中的聲明。 而且,命令集 GUID 必須同意命令實現類中的聲明。

## <a name="implement-the-commands"></a>執行指令
*ColumnGuideCommands.cs*文件實現命令並掛接處理程式。 當 Visual Studio 載入包並初始化包時,包`Initialize`反過來會調用命令實現類。 命令初始化只需實例化類,建構函數將連接所有命令處理程式。

將*ColumnGuideCommands.cs*檔案的內容取代為以下代碼(以下的語記):

```csharp
using System;
using System.ComponentModel.Design;
using System.Globalization;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;
using Microsoft.VisualStudio.TextManager.Interop;
using Microsoft.VisualStudio.Text.Editor;
using Microsoft.VisualStudio;

namespace ColumnGuides
{
    /// <summary>
    /// Command handler
    /// </summary>
    internal sealed class ColumnGuideCommands
    {

        const int cmdidAddColumnGuide = 0x0100;
        const int cmdidRemoveColumnGuide = 0x0101;
        const int cmdidChooseGuideColor = 0x0102;
        const int cmdidRemoveAllColumnGuides = 0x0103;

        /// <summary>
        /// Command menu group (command set GUID).
        /// </summary>
        static readonly Guid CommandSet =
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");

        /// <summary>
        /// VS Package that provides this command, not null.
        /// </summary>
        private readonly Package package;

        OleMenuCommand _addGuidelineCommand;
        OleMenuCommand _removeGuidelineCommand;

        /// <summary>
        /// Initializes the singleton instance of the command.
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        public static void Initialize(Package package)
        {
            Instance = new ColumnGuideCommands(package);
        }

        /// <summary>
        /// Gets the instance of the command.
        /// </summary>
        public static ColumnGuideCommands Instance
        {
            get;
            private set;
        }

        /// <summary>
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.
        /// Adds our command handlers for menu (commands must exist in the command
        /// table file)
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        private ColumnGuideCommands(Package package)
        {
            if (package == null)
            {
                throw new ArgumentNullException("package");
            }

            this.package = package;

            // Add our command handlers for menu (commands must exist in the .vsct file)

            OleMenuCommandService commandService =
                this.ServiceProvider.GetService(typeof(IMenuCommandService))
                    as OleMenuCommandService;
            if (commandService != null)
            {
                // Add guide
                _addGuidelineCommand =
                    new OleMenuCommand(AddColumnGuideExecuted, null,
                                       AddColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidAddColumnGuide));
                _addGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_addGuidelineCommand);
                // Remove guide
                _removeGuidelineCommand =
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,
                                       RemoveColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidRemoveColumnGuide));
                _removeGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_removeGuidelineCommand);
                // Choose color
                commandService.AddCommand(
                    new MenuCommand(ChooseGuideColorExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidChooseGuideColor)));
                // Remove all
                commandService.AddCommand(
                    new MenuCommand(RemoveAllGuidelinesExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidRemoveAllColumnGuides)));
            }
        }

        /// <summary>
        /// Gets the service provider from the owner package.
        /// </summary>
        private IServiceProvider ServiceProvider
        {
            get
            {
                return this.package;
            }
        }

        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _addGuidelineCommand.Enabled =
                GuidesSettingsManager.CanAddGuideline(currentColumn);
        }

        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _removeGuidelineCommand.Enabled =
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);
        }

        private int GetCurrentEditorColumn()
        {
            IVsTextView view = GetActiveTextView();
            if (view == null)
            {
                return -1;
            }

            try
            {
                IWpfTextView textView = GetTextViewFromVsTextView(view);
                int column = GetCaretColumn(textView);

                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based
                // positions.
                // However, do not subtract one here since the caret is positioned to the
                // left of
                // the given column and the guidelines are positioned to the right. We
                // want the
                // guideline to line up with the current caret position. e.g. When the
                // caret is
                // at position 1 (zero-based), the status bar says column 2. We want to
                // add a
                // guideline for column 1 since that will place the guideline where the
                // caret is.
                return column;
            }
            catch (InvalidOperationException)
            {
                return -1;
            }
        }

        /// <summary>
        /// Find the active text view (if any) in the active document.
        /// </summary>
        /// <returns>The IVsTextView of the active view, or null if there is no active
        /// document or the
        /// active view in the active document is not a text view.</returns>
        private IVsTextView GetActiveTextView()
        {
            IVsMonitorSelection selection =
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
                                                    as IVsMonitorSelection;
            object frameObj = null;
            ErrorHandler.ThrowOnFailure(
                selection.GetCurrentElementValue(
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));

            IVsWindowFrame frame = frameObj as IVsWindowFrame;
            if (frame == null)
            {
                return null;
            }

            return GetActiveView(frame);
        }

        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)
        {
            if (windowFrame == null)
            {
                throw new ArgumentException("windowFrame");
            }

            object pvar;
            ErrorHandler.ThrowOnFailure(
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));

            IVsTextView textView = pvar as IVsTextView;
            if (textView == null)
            {
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;
                if (codeWin != null)
                {
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
                }
            }
            return textView;
        }

        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)
        {

            if (view == null)
            {
                throw new ArgumentNullException("view");
            }

            IVsUserData userData = view as IVsUserData;
            if (userData == null)
            {
                throw new InvalidOperationException();
            }

            object objTextViewHost;
            if (VSConstants.S_OK
                   != userData.GetData(Microsoft.VisualStudio
                                                .Editor
                                                .DefGuidList.guidIWpfTextViewHost,
                                       out objTextViewHost))
            {
                throw new InvalidOperationException();
            }

            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
            if (textViewHost == null)
            {
                throw new InvalidOperationException();
            }

            return textViewHost.TextView;
        }

        /// <summary>
        /// Given an IWpfTextView, find the position of the caret and report its column
        /// number. The column number is 0-based
        /// </summary>
        /// <param name="textView">The text view containing the caret</param>
        /// <returns>The column number of the caret's position. When the caret is at the
        /// leftmost column, the return value is zero.</returns>
        private static int GetCaretColumn(IWpfTextView textView)
        {
            // This is the code the editor uses to populate the status bar.
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
                textView.Caret.ContainingTextViewLine;
            double columnWidth = textView.FormattedLineSource.ColumnWidth;
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                       / columnWidth));
        }

        /// <summary>
        /// Determine the applicable column number for an add or remove command.
        /// The column is parsed from command arguments, if present. Otherwise
        /// the current position of the caret is used to determine the column.
        /// </summary>
        /// <param name="e">Event args passed to the command handler.</param>
        /// <returns>The column number. May be negative to indicate the column number is
        /// unavailable.</returns>
        /// <exception cref="ArgumentException">The column number parsed from event args
        /// was not a valid integer.</exception>
        private int GetApplicableColumn(EventArgs e)
        {
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
            if (!string.IsNullOrEmpty(inValue))
            {
                int column;
                if (!int.TryParse(inValue, out column) || column < 0)
                    throw new ArgumentException("Invalid column");
                return column;
            }

            return GetCurrentEditorColumn();
        }

        /// <summary>
        /// This function is the callback used to execute a command when the a menu item
        /// is clicked. See the Initialize method to see how the menu item is associated
        /// to this function using the OleMenuCommandService service and the MenuCommand
        /// class.
        /// </summary>
        private void AddColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.AddGuideline(column);
            }
        }

        private void RemoveColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.RemoveGuideline(column);
            }
        }

        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)
        {
            GuidesSettingsManager.RemoveAllGuidelines();
        }

        private void ChooseGuideColorExecuted(object sender, EventArgs e)
        {
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;

            using (System.Windows.Forms.ColorDialog picker =
                new System.Windows.Forms.ColorDialog())
            {
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,
                                                             color.B);
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)
                {
                    GuidesSettingsManager.GuidelinesColor =
                        System.Windows.Media.Color.FromRgb(picker.Color.R,
                                                           picker.Color.G,
                                                           picker.Color.B);
                }
            }
        }

    }
}

```

**修復參考**。 此時缺少引用。 按解決方案資源管理員中的「參考」節點上的右指標按鈕。 選擇"**添加..."** 命令。 "**新增參考對話**框的右上角有一個搜尋框。 輸入"編輯器"(沒有雙引號)。 選擇**Microsoft.VisualStudio.編輯器**項(您必須選中項目左側的複選框,而不僅僅是選擇該專案),然後選擇 **「確定」** 以添加引用。

**初始化**。  當包類初始化時,它將調用`Initialize`命令實現類。 初始`ColumnGuideCommands`化實例化類,並將類實例和包引用保存在類成員中。

讓我們看一下來自類建構函數的命令處理程式掛接:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

建立一`OleMenuCommand`個 。 可視化工作室使用微軟 Office 命令系統。 實例化時的關鍵參數`OleMenuCommand`是實現命令`AddColumnGuideExecuted`( ) 的函數,當 Visual Studio 顯示具有命令 (`AddColumnGuideBeforeQueryStatus`) 和命令 ID 的選單時要調用的函數。 Visual Studio 在選單上顯示命令之前調用查詢狀態函數,以便該命令可以使自身不可見或灰顯,用於功能表的特定顯示(例如,如果沒有選擇,則禁用**Copy)、** 更改其圖示,甚至更改其名稱(例如,從"添加內容到刪除內容")等。 命令 ID 必須與 *.vsct*檔中聲明的命令 ID 匹配。 命令集和列參考線添加命令的字串必須在 *.vsct*檔和*ColumnGuideCommands.cs*之間匹配。

以下行為使用者透過命令視窗呼叫命令時提供説明(如下所述):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **查詢狀態**。 查詢狀態功能`AddColumnGuideBeforeQueryStatus``RemoveColumnGuideBeforeQueryStatus`並 檢查某些設置(如參考線的最大數量或最大列),或者如果有要刪除的列參考線。 如果條件合適,它們將啟用命令。  查詢狀態函數需要高效,因為它們在每次 Visual Studio 顯示功能表和功能表上的每個命令時都會運行。

 **新增欄線指南執行函數**。 添加指南的有趣部分是找出當前編輯器視圖和精心的位置。  首先,此函數調用`GetApplicableColumn`,它檢查命令處理程式的事件參數中是否有使用者提供的參數,如果沒有,則函數檢查編輯器的視圖:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

    return GetCurrentEditorColumn();
}

```

`GetCurrentEditorColumn`必須挖掘一點才能查看<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>代碼。  如果遍通`GetActiveTextView``GetActiveView`了`GetTextViewFromVsTextView`, 可以看到如何執行此操作。 以下代碼是抽象的相關代碼,從目前選擇開始,然後取得所選內容的幀,然後將幀的 DocView<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>作為, 然後從<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>IVTextView 獲取, 然後取得檢視主機,最後是 IWpfTextView:

```csharp
   IVsMonitorSelection selection =
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
           as IVsMonitorSelection;
   object frameObj = null;

ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,
                                out frameObj));

   IVsWindowFrame frame = frameObj as IVsWindowFrame;
   if (frame == null)
       <<do nothing>>;

...
   object pvar;
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,
                                                  out pvar));

   IVsTextView textView = pvar as IVsTextView;
   if (textView == null)
   {
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;
       if (codeWin != null)
       {
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
       }
   }

...
   if (textView == null)
       <<do nothing>>

   IVsUserData userData = textView as IVsUserData;
   if (userData == null)
       <<do nothing>>

   object objTextViewHost;
   if (VSConstants.S_OK
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList
                                                            .guidIWpfTextViewHost,
                                out objTextViewHost))
   {
       <<do nothing>>
   }

   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
   if (textViewHost == null)
       <<do nothing>>

   IWpfTextView textView = textViewHost.TextView;

```

取得 IWpfTextView 後,即可取得該選護符所在的列:

```csharp
private static int GetCaretColumn(IWpfTextView textView)
{
    // This is the code the editor uses to populate the status bar.
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
        textView.Caret.ContainingTextViewLine;
    double columnWidth = textView.FormattedLineSource.ColumnWidth;
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                / columnWidth));
}

```

當用戶按下的當前列時,程式碼只需調用設置管理員來添加或刪除列。 設置管理器觸發所有`ColumnGuideAdornment`物件偵聽的事件。 觸發事件時,這些物件使用新的列指南設置更新其關聯的文本視圖。

## <a name="invoke-command-from-the-command-window"></a>從命令視窗呼叫指令
該列參考線示例使用戶能夠從命令視窗調用兩個命令作為擴展形式。 如果使用 **「查看 &#124;其他窗口&#124;命令視窗」命令**,則可以看到命令視窗。 您可以透過輸入編輯「編輯」與命令視窗進行互動,並且在命令名稱完成並提供參數 120 時,您有以下結果:

```csharp
> Edit.AddColumnGuide 120
>
```

啟用此行為的範例部分位於 *.vsct*檔`ColumnGuideCommands`聲明、 連接命令處理程式時的類構造函數以及檢查事件參數的命令處理程式實現中。

您在`<CommandFlag>CommandWellOnly</CommandFlag>`*.vsct*檔中看到""""""""""""""""""""**編輯**主菜單中的位置",即使這些命令未顯示在 **"編輯"** 功能表 UI 中。 將它們放在主**編輯**功能表上,可以給他們起像**Edit.AddColumnGuide**這樣的名稱。 儲存四個指令的指令群組聲明將群組直接放置在 **「編輯」** 選單上:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

按鈕部份稍後宣告指令`CommandWellOnly`,使其在主選單上不可見,並聲明它們`AllowParams`與 :

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

您看到命令處理程式在類別建構函式`ColumnGuideCommands`中 掛接碼提供允許參數的說明:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

在檢查目前`GetApplicableColumn`欄`OleMenuCmdEventArgs`的 編輯器檢視之前,您看到函數檢查值:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

```

## <a name="try-your-extension"></a>嘗試延伸
現在,您可以按**F5**執行列參考線擴展。 開啟文字檔案並使用編輯器的上下文選單添加引導行、刪除它們並更改其顏色。 按下文字(不是通過行末尾的空白)以添加列指南,或者編輯器將其添加到行的最後一列。 如果使用命令視窗並使用參數調用命令,則可以在任何地方添加列參考線。

如果要嘗試不同的命令放置、更改名稱、更改圖示等,並且 Visual Studio 在功能表中顯示最新代碼時遇到任何問題,則可以重置正在調試的實驗配置單元。 啟動**Windows 開始功能表**並鍵入「重置」。 尋找並執行此指令,**重設下一個視覺化工作室實驗實體**。 此命令清理所有擴展元件的實驗註冊表配置單元。 它不會清除元件中的設定,因此當您關閉 Visual Studio 的實驗單元時,任何參考線都仍然存在,當您的代碼在下次啟動時讀取設置儲存時。

## <a name="finished-code-project"></a>已完成的代碼項目
很快將有一個GitHub專案的視覺工作室擴展性示例,完成的專案將在那裡。 本文將更新,以便發生此情況時指向該點。 已完成的範例專案可能具有不同的 guid,並且對於命令圖示將有不同的位圖條帶。

您可以使用此可視化工作室庫[擴展名](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)試用列指南功能的版本。

## <a name="see-also"></a>另請參閱
- [編輯器內部](../extensibility/inside-the-editor.md)
- [延伸編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)
- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
- [延伸選單與指令](../extensibility/extending-menus-and-commands.md)
- [加入選單加入子選單](../extensibility/adding-a-submenu-to-a-menu.md)
- [使用編輯器項目建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)
