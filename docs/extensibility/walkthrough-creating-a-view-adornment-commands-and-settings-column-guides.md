---
title: 建立視圖裝飾、命令和設定 |Microsoft Docs
description: 瞭解如何使用本逐步解說，以資料行輔助線擴充 Visual Studio 程式碼編輯器。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2108abe89a47fa276da53a14439a52451d936eea
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863075"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>逐步解說：建立視圖裝飾、命令和設定 (資料行指南) 
您可以使用命令和視圖效果來延伸 Visual Studio 的 text/code 編輯器。 本文說明如何開始使用熱門擴充功能和資料行指南。 資料行輔助線是以視覺方式繪製在文字編輯器的視圖上，可協助您將程式碼管理為特定的資料行寬度。 具體而言，格式化程式碼對於您包含在檔、blog 文章或錯誤報表中的範例而言很重要。

在本逐步解說中，您將：
- 建立 VSIX 專案
- 加入編輯器視圖裝飾
- 新增儲存和取得設定的支援 (在哪裡繪製資料行輔助線及其色彩) 
- 新增命令 (新增/移除資料行指南、變更其色彩) 
- 將命令放在 [編輯] 功能表和 [文字檔] 內容功能表上
- 新增從 Visual Studio 命令視窗叫用命令的支援

  您可以使用此 Visual Studio 資源庫[延伸](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)模組來試用資料行指南功能的版本。

  > [!NOTE]
  > 在這個逐步解說中，您會將大量的程式碼貼入 Visual Studio 擴充功能範本所產生的幾個檔案中。 但本逐步解說很快將會參考 GitHub 上已完成的解決方案與其他擴充功能範例。 完成的程式碼稍微不同，因為它具有真實的命令圖示，而不是使用 generictemplate 圖示。

## <a name="get-started"></a>開始使用
從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="set-up-the-solution"></a>設定解決方案
首先，您要建立一個 VSIX 專案、加入編輯器視圖裝飾，然後加入一個命令 (，這會新增 VSPackage 以擁有命令) 。 基本架構如下所示：
- 您有一個可為每個視圖建立物件的文字視圖建立接聽程式 `ColumnGuideAdornment` 。 這個物件會在必要時，接聽變更或變更變更、更新或重繪資料行指南的相關事件。
- 有一個 `GuidesSettingsManager` 會處理 Visual Studio 設定儲存體的讀取和寫入。 設定管理員也有作業可更新支援使用者命令 (新增資料行、移除資料行、變更色彩) 的設定。
- 如果您有使用者命令，就有必要的 VSIP 封裝，但它只是可初始化命令執行物件的重複使用程式碼。
- 有一個 `ColumnGuideCommands` 物件會執行使用者命令，並連結 *.vsct* 檔案中所宣告命令的命令處理常式。

  **VSIX**。 使用 [檔案] **&#124; [新增 ...** ] 命令以建立專案。 在左側導覽窗格中選擇 [ **c #** ] 底下的 [擴充性 **] 節點，** 然後在右窗格中選擇 [ **VSIX 專案**]。 輸入名稱 **ColumnGuides** ，然後選擇 **[確定]** 以建立專案。

  **視圖裝飾**。 在方案總管的專案節點上按下滑鼠右鍵。 選擇 [ **加入 &#124; 新增專案** ] 命令，以加入新的 view 裝飾專案。 選擇左側導覽窗格中的 [擴充性 **&#124; 編輯器** ]，然後在右窗格中選擇 [ **編輯器區裝飾** ]。 輸入名稱 **ColumnGuideAdornment** 作為專案名稱，然後選擇 [ **加入** ] 以加入它。

  您可以看到這個專案範本將兩個檔案新增至專案 (以及參考，依此類推) ： **ColumnGuideAdornment.cs** 和 **ColumnGuideAdornmentTextViewCreationListener.cs**。 這些範本會在視圖上繪製一個紫色的矩形。 在下一節中，您會在 view 建立接聽程式中變更幾行程式碼，並取代 **ColumnGuideAdornment.cs** 的內容。

  **命令**。 在 **方案總管** 中，按下專案節點上的右指標按鈕。 選擇 [ **加入 &#124; 新增專案** ] 命令，以加入新的 view 裝飾專案。 選擇左側導覽窗格中的 [擴充性] **&#124; VSPackage** ，然後在右窗格中選擇 [ **自訂] 命令** 。 輸入名稱 **ColumnGuideCommands** 作為專案名稱，然後選擇 [ **加入**]。 除了多個參考之外，新增命令和封裝也會新增 **ColumnGuideCommands.cs**、 **ColumnGuideCommandsPackage.cs** 和 **ColumnGuideCommandsPackage. .vsct**。 在下一節中，您將取代第一個和最後一個檔案的內容，以定義和執行這些命令。

## <a name="set-up-the-text-view-creation-listener"></a>設定文字視圖建立接聽程式
在編輯器中開啟 *ColumnGuideAdornmentTextViewCreationListener.cs* 。 這段程式碼會在 Visual Studio 建立文字視圖時，執行處理常式。 有一些屬性可控制處理常式的呼叫時機，視視圖的特性而定。

程式碼也必須宣告裝飾層。 當編輯器更新視圖時，它會取得視圖的裝飾層，以及從中取得裝飾元素的裝飾層。 您可以使用屬性來宣告圖層的順序（相對於其他人）。 將以下程式碼：

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

這兩行：

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

您所取代的行是在宣告裝飾層的屬性群組中。 您變更的第一行只會變更資料行輔助線的出現位置。 在視圖中的文字「之前」繪製線條表示它們出現在文字後方或下方。 第二行會宣告資料行引導裝飾適用于符合您檔概念的文字實體，但您可以宣告裝飾，例如，只對可編輯的文字運作。 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)中有更多詳細資訊

## <a name="implement-the-settings-manager"></a>執行設定管理員
以下列程式碼取代 *GuidesSettingsManager.cs* 的內容 (說明) ：

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

大部分的程式碼都會建立並剖析設定格式： "RGB (\<int> ， \<int> ， \<int>) \<int> ，， \<int> ..."。  結尾的整數是您想要資料行參考資料的一種資料行。 資料行輔助線擴充功能會在單一設定值字串中捕捉其所有設定。

程式碼有一些值得強調的部分。 下列程式程式碼會取得設定儲存體的 Visual Studio 受控包裝函式。 在大部分的情況下，這會在 Windows 登錄上抽象化，但此 API 與儲存機制無關。

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Visual Studio 設定儲存體會使用類別識別碼和設定識別碼來唯一識別所有設定：

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

您不需要使用做 `"Text Editor"` 為類別目錄名稱。 您可以挑選任何您喜歡的。

前幾個函數是變更設定的進入點。 他們會檢查高階條件約束，例如允許的最大指南數目。  然後，它們會呼叫 `WriteSettings` ，以撰寫設定字串並設定屬性 `GuideLinesConfiguration` 。 設定此屬性會將設定值儲存至 Visual Studio 設定存放區，並引發 `SettingsChanged` 事件以更新所有 `ColumnGuideAdornment` 物件，每個物件都與文字視圖相關聯。

有幾個進入點函式，例如 `CanAddGuideline` ，用來執行變更設定的命令。 當 Visual Studio 顯示功能表時，它會查詢命令執行，以查看命令目前是否已啟用、其名稱為何等等。  在下方，您會瞭解如何連結這些進入點以進行命令執行。 如需命令的詳細資訊，請參閱 [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)。

## <a name="implement-the-columnguideadornment-class"></a>執行 ColumnGuideAdornment 類別
`ColumnGuideAdornment`類別會針對每個可以有裝飾的文字視圖具現化。 此類別會接聽變更變更或變更設定的相關事件，以及視需要更新或重繪資料行指南。

以下列程式碼取代 *ColumnGuideAdornment.cs* 的內容 (說明) ：

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

這個類別的實例會保存到相關聯的 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> ，以及在 `Line` 該視圖上繪製之物件的清單。

Visual Studio 建立新的視圖時，會呼叫 (的函式 `ColumnGuideAdornmentTextViewCreationListener`) 建立資料行指南 `Line` 物件。  此函式也會加入 `SettingsChanged`) 中定義之事件 (的處理常式 `GuidesSettingsManager` ，以及視圖事件 `LayoutChanged` 和 `Closed` 。

此 `LayoutChanged` 事件引發的原因是因為視圖中有數種變更，包括 Visual Studio 建立視圖時。 `OnViewLayoutChanged`要執行的處理常式呼叫 `AddGuidelinesToAdornmentLayer` 。 中的程式碼 `OnViewLayoutChanged` 決定是否需要根據變更（例如，字型大小變更、觀賞裝訂邊、水準滾動等等）更新行位置。 中的 `UpdatePositions` 程式碼會讓輔助線在字元之間，或在文字行中指定字元位移的文字資料行之後繪製。

每當設定變更時，函式 `SettingsChanged` 只 `Line` 會使用新的設定來重新建立所有物件。 設定行位置之後，程式碼會從裝飾層移除所有先前的 `Line` 物件 `ColumnGuideAdornment` ，並加入新的物件。

## <a name="define-the-commands-menus-and-menu-placements"></a>定義命令、功能表和功能表放置
宣告命令和功能表、將命令或功能表群組放置在不同的其他功能表上，以及連結命令處理常式，可能會有很多。 本逐步解說會強調命令在此延伸模組中的運作方式，但如需更深入的資訊，請參閱 [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)。

### <a name="introduction-to-the-code"></a>程式碼簡介
[資料行指南] 延伸模組會顯示宣告一組隸屬的命令， (新增資料行]、[移除資料行]、[變更線條色彩]) ，然後將該群組放在編輯器內容功能表的子功能表上。  資料行指南延伸模組也會將命令新增至主要的 [ **編輯** ] 功能表，但會將它們保持不可見，並在下方討論為一般模式。

命令的執行有三個部分： ColumnGuideCommandsPackage.cs、ColumnGuideCommandsPackage .vsct 和 ColumnGuideCommands.cs。 範本所產生的程式碼會在 [ **工具** ] 功能表上放置一個命令，以在執行時將對話方塊彈出。 您可以看看如何在 *.vsct* 和 *ColumnGuideCommands.cs* 檔案中執行，因為它很簡單。 您可以取代下列檔案中的程式碼。

封裝程式碼包含 Visual Studio 所需的重複宣告，以找出擴充功能提供命令及尋找命令的放置位置。 當封裝初始化時，它會具現化命令實類別。 如需與命令相關之封裝的詳細資訊，請參閱 [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)。

### <a name="a-common-commands-pattern"></a>常見的命令模式
資料行指南延伸模組中的命令是 Visual Studio 中非常常見的模式範例。 您將相關的命令放在群組中，然後將該群組放置在主功能表上，通常會將該群組 `<CommandFlag>CommandWellOnly</CommandFlag>` 設定為不隱藏命令。  將命令放在主功能表上 (例如 **編輯**) 會為他們提供很好的名稱 (例如 **AddColumnGuide**) ，在 [ **工具] 選項** 中重新指派金鑰系結時，這非常有用。 從 **命令視窗** 叫用命令時，它也很有用。

然後，您可以將命令群組新增至您希望使用者使用命令的內容功能表或子功能表。 Visual Studio `CommandWellOnly` 只會將視為主要功能表的隱藏旗標。 當您在操作功能表或子功能表上放置同一組命令時，會顯示命令。

在一般模式中，資料行輔助線會建立另一個包含單一子功能表的群組。 子功能表接著會包含具有四欄輔助命令的第一個群組。 保留子功能表的第二個群組是您放在各種內容功能表上的可重複使用資產，其會在這些內容功能表上放置子功能表。

### <a name="the-vsct-file"></a>.Vsct 檔案
*.Vsct* 檔案會宣告命令及其位置，以及圖示等等。 以下列程式碼取代 *.vsct* 檔案的內容 (說明) ：

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

**Guid**。 若要讓 Visual Studio 尋找您的命令處理常式並加以叫用，您必須確保在 *ColumnGuideCommandsPackage.cs* 檔中宣告的封裝 guid (從專案專案範本產生) 符合 *.vsct* 檔中所宣告的封裝 guid (從上述) 複製。 如果您重複使用此範例程式碼，您應該確定您有不同的 GUID，如此您才不會與可能已複製此程式碼的其他人衝突。

在 *ColumnGuideCommandsPackage.cs* 中尋找這一行，並從引號之間複製 GUID：

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

然後，將 GUID 貼入 *.vsct* 檔案中，讓您在宣告中有下行 `Symbols` ：

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

針對您的延伸模組，命令集和點陣圖影像檔案的 Guid 也應該是唯一的：

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

但是，您不需要在此逐步解說中變更命令集和點陣圖影像 Guid，就能讓程式碼正常運作。 命令集 GUID 必須符合 *ColumnGuideCommands.cs* 檔中的宣告，但您也要取代該檔案的內容。因此，Guid 會相符。

*.Vsct* 檔案中的其他 guid 會識別已新增資料行指南命令的預先存在功能表，因此永遠不會變更。

檔案 **區段**。 *.Vsct* 有三個外部區段：命令、放置和符號。 命令區段會定義命令群組、功能表、按鈕或功能表項目，以及圖示的點陣圖。 位置區段會宣告群組在功能表上的進入位置，或在現有的功能表上進行其他放置。 符號區段會宣告 *.vsct* 檔案中其他位置所使用的識別碼，使 *.vsct* 程式碼更容易閱讀，而不是任何地方都有 guid 和十六進位數位。

**命令區段，群組定義**。 命令區段會先定義命令群組。 命令的群組是您在功能表中看到的命令，並以稍微灰色的線條分隔群組。 群組也可以填滿整個子功能表，如本範例所示，在此案例中，您不會看到以灰色分隔的行。 *.Vsct* 檔案會宣告兩個群組， `GuidesMenuItemsGroup` 也就是主要 [編輯] 功能表 (的父代 `IDM_VS_MENU_EDIT`) 和 `GuidesContextMenuGroup` `IDM_VS_CTXT_CODEWIN` (程式碼編輯器內容功能表) 的父代。

第二個群組宣告的 `0x0600` 優先順序如下：

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

其構想是將資料行指南子功能表放在您要加入子功能表群組的任何內容功能表的結尾。 但是，您不應該假設您知道最好，然後使用的優先權來強制子功能表一律是最後一個 `0xFFFF` 。 您必須試驗數位，以查看子功能表在您放置它的內容功能表上的位置。 在這種情況下， `0x0600` 夠高，可以將它放在功能表的結尾，如您所見，但如果需要的話，還可以讓其他人將擴充功能設計成低於資料行指南延伸模組。

**命令區段，功能表定義**。 接下來，命令區段會定義子功能表 `GuidesSubMenu` ，其父代為 `GuidesContextMenuGroup` 。 `GuidesContextMenuGroup`是您新增至所有相關內容功能表的群組。 在 [位置] 區段中，此程式碼會將群組放置在這個子功能表上的四個數據行指南命令。

**命令區段、按鈕定義**。 接著，[命令] 區段會定義功能表項目或具有四個數據行的輔助命令的按鈕。 `CommandWellOnly`以上討論過，這表示放置在主功能表上時，不會看到命令。 其中兩個功能表項目按鈕宣告 (新增指南和移除指南) 也有 `AllowParams` 旗標：

```xml
<CommandFlag>AllowParams</CommandFlag>
```

這個旗標可讓您在 Visual Studio 叫用命令處理常式時，透過主功能表位置來接收引數的命令。  如果使用者從命令視窗執行命令，則會將引數傳遞至事件引數中的命令處理常式。

**命令區段、點陣圖定義**。 最後，命令區段會宣告用於命令的點陣圖或圖示。 此區段是識別專案資源的簡單宣告，並且會列出已使用圖示的一個索引。 *.Vsct* 檔案的 [符號] 區段會宣告用來作為索引的識別碼值。 本逐步解說會使用已加入至專案的自訂命令專案範本所提供的點陣圖帶。

**放置區段**。 在 [命令] 區段是 [放置] 區段之後。 第一個是程式碼將上面討論的第一個群組，其中包含四個數據行的指南命令，指向出現命令的子功能表：

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

其他所有位置都會將 `GuidesContextMenuGroup` 包含) 的 (新增 `GuidesSubMenu` 至其他編輯器內容功能表。 當程式碼宣告時 `GuidesContextMenuGroup` ，它是程式碼編輯器內容功能表的父代。 這就是為什麼您看不到程式碼編輯器內容功能表的位置。

**符號區段**。 如上所述，符號區段會宣告 *.vsct* 檔案中其他位置所使用的識別碼，使 *.vsct* 程式碼更容易閱讀，而不是任何地方都有 guid 和十六進位數位。 本節中的重點是套件 GUID 必須同意 package 類別中的宣告。 而且，命令集 GUID 必須同意命令實類別中的宣告。

## <a name="implement-the-commands"></a>執行命令
*ColumnGuideCommands.cs* 檔案會執行命令並連結處理常式。 當 Visual Studio 載入封裝並將它初始化時，封裝接著會在 `Initialize` 命令執行類別上呼叫。 命令初始化只會具現化類別，而此函式會連結所有的命令處理常式。

以下列程式碼取代 *ColumnGuideCommands.cs* 檔案的內容 (說明) ：

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

**修正參考**。 此時您已遺失參考。 在方案總管的 [參考] 節點上按下滑鼠右鍵。 選擇 [ **新增 ...** ] 命令。 [ **加入參考** ] 對話方塊的右上角有搜尋方塊。 輸入「編輯器」 (不) 雙引號。 選擇 [ **VisualStudio 編輯器** ] 專案 (您必須核取專案左邊的方塊，而不只是選取) 的專案，然後選擇 **[確定]** 以加入參考。

**初始化**。  當封裝類別初始化時，它會 `Initialize` 在命令執行類別上呼叫。 初始化會具現 `ColumnGuideCommands` 化類別，並將類別實例和封裝參考儲存在類別成員中。

讓我們看看來自類別的函式的其中一個命令處理常式攔截：

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

您會建立 `OleMenuCommand` 。 Visual Studio 使用 Microsoft Office 命令系統。 當具現化時，主要引數是會執行命令的函式 `OleMenuCommand` (`AddColumnGuideExecuted`) 、Visual Studio 顯示具有命令 () 的功能表時所要呼叫的函式 `AddColumnGuideBeforeQueryStatus` ，以及命令識別碼。 Visual studio 會在顯示功能表上的命令之前呼叫查詢狀態函式，讓命令可以針對功能表的特定顯示隱藏或呈現灰色 (例如，如果沒有選取) 範圍，則停用 **複製** 、變更其圖示或甚至變更其名稱 (例如，從 [新增專案] 以移除) 等。 命令識別碼必須符合 *.vsct* 檔案中所宣告的命令識別碼。 在 *.vsct* 檔案和 *ColumnGuideCommands.cs* 之間，命令集和資料行指南 add 命令的字串必須相符。

下列程式程式碼提供使用者透過命令視窗叫用命令時的協助， (如下所述) ：

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **查詢狀態**。 查詢狀態的函式 `AddColumnGuideBeforeQueryStatus` 和 `RemoveColumnGuideBeforeQueryStatus` 檢查部分設定 (例如最大的輔助線數目或最大資料行) 或有要移除的資料行指南。 如果條件正確，則會啟用命令。  查詢狀態功能必須有效率，因為它們會在每次 Visual Studio 顯示功能表和功能表上的每個命令時執行。

 **AddColumnGuideExecuted** 函式。 新增指南的有趣部分是找出目前的編輯器視圖和插入號位置。  首先，此函式 `GetApplicableColumn` 會呼叫，以檢查命令處理常式的事件引數中是否有使用者提供的引數，如果沒有，則函式會檢查編輯器的觀點：

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

`GetCurrentEditorColumn` 必須深入瞭解，才能取得程式 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> 代碼的觀點。  如果您透過 `GetActiveTextView` 、 `GetActiveView` 和來追蹤， `GetTextViewFromVsTextView` 您可以瞭解如何執行該動作。 下列程式碼是相關的程式碼抽象化，從目前的選取範圍開始，然後取得選取範圍的框架，然後取得畫面格的 DocView，然後從 IVsTextView 取得，然後 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> 取得視圖主控制項，最後是 IWpfTextView：

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

一旦有了 IWpfTextView，您就可以取得插入號所在的資料行：

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

在使用者按一下的目前資料行中，程式碼只會在設定管理員上呼叫，以新增或移除資料行。 [設定管理員] 會引發所有物件都會 `ColumnGuideAdornment` 接聽的事件。 當事件引發時，這些物件會以新的資料行指南設定更新其相關聯的文字。

## <a name="invoke-command-from-the-command-window"></a>從命令視窗叫用命令
資料行指南範例可讓使用者從命令視窗以擴充性形式叫用兩個命令。 如果您使用 **View &#124; 其他 Windows &#124; 命令視窗** 命令，您可以看到命令視窗。 您可以藉由輸入 "edit" 來與命令視窗互動，並使用命令名稱完成並提供引數120，您會得到下列結果：

```csharp
> Edit.AddColumnGuide 120
>
```

啟用此行為的範例部分是在 *.vsct* 檔宣告中、在連結 `ColumnGuideCommands` 命令處理常式時使用類別的函式，以及檢查事件引數的命令處理常式。

您看到了 .vsct 檔案中的 ""，以及在 [編輯] `<CommandFlag>CommandWellOnly</CommandFlag>` 主功能表中的位置，即使命令未顯示在 [**編輯**] 功能表 UI 中也是一樣。   將這些專案放在主要的 [ **編輯** ] 功能表上，就會提供其名稱，如 **AddColumnGuide**。 包含四個命令的命令群組宣告會將群組直接放在 [ **編輯** ] 功能表上：

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

[按鈕] 區段稍後宣告了命令， `CommandWellOnly` 讓它們不會出現在主功能表上，並使用宣告 `AllowParams` ：

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

您看到命令處理常式連結類別的函式中的程式碼時 `ColumnGuideCommands` ，提供了允許參數的描述：

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

您看到 `GetApplicableColumn` 函數會檢查 `OleMenuCmdEventArgs` 值，然後再檢查編輯器的 view 是否有目前的資料行：

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

## <a name="try-your-extension"></a>試用您的延伸模組
您現在可以按 **F5** 來執行資料行指南延伸模組。 開啟文字檔，並使用編輯器的內容功能表來新增輔助線、將其移除，以及變更其色彩。 按一下文字 (非空白字元傳遞的行尾) 來加入資料行指南，否則編輯器會將它新增至該行的最後一個資料行。 如果您使用命令視窗並使用引數叫用命令，您可以在任何位置加入資料行指南。

如果您想要嘗試不同的命令位置、變更名稱、變更圖示等，而且有任何 Visual Studio 顯示功能表中的最新程式碼，您可以重設正在進行偵錯工具的實驗 hive。 顯示 Windows [ **開始] 功能表** 並輸入「重設」。 尋找並執行命令， **重設下一個 Visual Studio 實驗實例**。 此命令會清除所有延伸模組元件的實驗登錄 hive。 它不會清除元件的設定，所以當您在下次啟動時，當您的程式碼讀取設定存放區時，仍會有任何您在關閉 Visual Studio 實驗 hive 時所發生的指南。

## <a name="finished-code-project"></a>完成的程式碼專案
Visual Studio 擴充性範例的 GitHub 專案即將推出，而已完成的專案將會出現在該處。 本文將會更新，以在發生這種情況時將其指向。 完成的範例專案可能會有不同的 guid，而且會有不同的命令圖示點陣圖區。

您可以使用此 Visual Studio 資源庫[延伸](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)模組來試用資料行指南功能的版本。

## <a name="see-also"></a>請參閱
- [在編輯器內](../extensibility/inside-the-editor.md)
- [擴充編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)
- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
- [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)
- [將子功能表新增至功能表](../extensibility/adding-a-submenu-to-a-menu.md)
- [使用編輯器專案範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)
