---
title: 逐步解說： 建立檢視裝飾、 命令和設定 （分欄輔助線） |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ba345940e956975ea6ac4bf7a29ca59bd5deca76
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795774"
---
# <a name="walkthrough-creating-a-view-adornment-commands-and-settings-column-guides"></a>逐步解說︰建立檢視裝飾、命令和設定 (分欄輔助線)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以擴充 Visual Studio 文字/程式碼編輯器與命令和檢視效果。  本主題說明如何開始使用熱門的擴充功能，分欄輔助線。  分欄輔助線是以視覺化方式淺色可協助您管理您的程式碼，以特定的資料行寬度的文字編輯器的檢視上所繪製的線條。  特別的格式化程式碼可以是很重要的範例包含在文件，部落格文章，或錯誤報告。  
  
 在此逐步解說中，您將：  
  
- 建立 VSIX 專案  
  
- 新增編輯器檢視透過裝飾  
  
- 新增對儲存和取得設定 （其中繪製分欄輔助線和色彩） 的支援  
  
- 新增命令 （新增/移除資料行的輔助線，變更其色彩）  
  
- 將命令放在 [編輯] 功能表和文字文件內容功能表  
  
- 新增支援叫用的命令，從 Visual Studio 命令視窗  
  
  您可以試試看這個 Visual Studio 組件庫的資料行指南功能的版本[延伸模組](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home)。  
  
  **請注意**： 在此逐步解說中您必須將大量程式碼貼入 visual studio 延伸模組範本，所產生的一些檔案，但很快就本逐步解說會參考和其他擴充功能範例的 github 上已完成的方案。  已完成的程式碼會稍微不同，在於它有實際的命令圖示，而不是使用 generictemplate 圖示。  
  
## <a name="getting-started"></a>快速入門  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="setting-up-the-solution"></a>設定解決方案  
 第一次您將建立 VSIX 專案、 新增編輯器檢視透過裝飾，然後再加入命令 （這會加入 VSPackage 也可以擁有命令）。  基本架構如下所示：  
  
- 您有建立文字檢視建立接聽程式`ColumnGuideAdornment`每個檢視的物件。  這個物件接聽檢視變更的相關事件或變更的設定，視引導更新或重新繪製的資料行。  
  
- 沒有`GuidesSettingsManager`可處理從 Visual Studio 設定儲存體讀取和寫入。  Settings manager 也有更新的設定，以支援使用者命令的作業 （加入資料行、 移除資料行、 變更色彩）。  
  
- VSIP 封裝所需，如果您有使用者命令，但它是只將命令實作物件初始化未定案程式碼。  
  
- 沒有`ColumnGuideCommands`.vsct 檔案中宣告的物件，實作使用者命令和命令的命令處理常式攔截程序。  
  
  **VSIX**。  使用**檔案&#124;新的...** 若要建立專案的命令。  在左側的導覽窗格中選擇 C# 下的 擴充性 節點，然後選擇**VSIX 專案**右窗格中。  輸入 ColumnGuides 的名稱，然後選擇**確定**建立專案。  
  
  **檢視裝飾**。  在 [方案總管] 中的專案節點上，請按右指標按鈕。  選擇**新增&#124;新項目...** 要加入新的檢視裝飾項目的命令。  選擇**擴充性&#124;編輯器**左側的導覽窗格中，然後選擇 **編輯器檢視區 Adornment**右窗格中。  輸入名稱 ColumnGuideAdornment 做為項目名稱，然後選擇**新增**將它加入。  
  
  您可以看到這個項目範本加入至專案 （以及參考等等） 的兩個檔案： ColumnGuideAdornment.cs 和 ColumnGuideAdornmentTextViewCreationListener.cs。  範本只會在檢視上繪製一個紫色的矩形。  以下您將變更幾行中的檢視建立接聽程式，並取代 ColumnGuideAdornment.cs 的內容。  
  
  **命令**。  在 [方案總管] 中的專案節點上，請按右指標按鈕。  選擇**新增&#124;新項目...** 要加入新的檢視裝飾項目的命令。  選擇**擴充性&#124;VSPackage**左側的導覽窗格中，然後選擇 **自訂命令**右窗格中。  輸入名稱 ColumnGuideCommands 做為項目名稱，然後選擇**新增**將它加入。  除了數個參考，加入命令和封裝新增 ColumnGuideCommands.cs、 ColumnGuideCommandsPackage.cs 和 ColumnGuideCommandsPackage.vsct。  以下您將會取代定義並實作命令的第一個和最後一個檔案的內容。  
  
## <a name="setting-up-the-text-view-creation-listener"></a>設定文字檢視建立接聽程式  
 在編輯器中開啟 ColumnGuideAdornmentTextViewCreationListener.cs。  Visual Studio 會建立文字檢視時，此程式碼會實作處理常式。  有可控制根據檢視的特性，當呼叫此處理常式的屬性。  
  
 程式碼也必須宣告 adornment 層。  時，編輯器會更新檢視，它會取得 adornment 層檢視，並從中取得裝飾項目。  您可以宣告屬性相對於其他您層的順序。  將下面這一行：  
  
```csharp  
[Order(After = PredefinedAdornmentLayers.Caret)]  
```  
  
 使用這兩行：  
  
```csharp  
[Order(Before = PredefinedAdornmentLayers.Text)]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
```  
  
 您更換的一行是群組中的宣告 adornment 圖層的屬性。   第一行已變更的資料行指導方針的出現位置的唯一變更。  「 之前 」 檢視中的文字表示後置或的文字下方，則會出現，請繪製線條。  第二行宣告資料行指南裝飾都適用於文字實體符合您的文件的概念，但您無法宣告 adornment，比方說，只適用於可編輯的文字。  中的詳細資訊[語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)  
  
## <a name="implementing-the-settings-manager"></a>實作 Settings Manager  
 GuidesSettingsManager.cs 內容取代為下列程式碼 （如下所述）：  
  
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
  
 大部分的這段程式碼只會建立，並剖析設定格式:"RGB (\<int >，\<int >，\<int >) \<int >， \<int >...」。  結束的整數是以一為基的資料行要分欄輔助線。  資料行的輔助線延伸模組會擷取它在單一設定值，字串中的所有設定。  
  
 有個值得反白顯示的程式碼某些部分。  下列程式碼會取得 Visual Studio 的 managed 包裝函式的設定儲存體。  大部分的情況下，此摘要透過 Windows 登錄中，但此 API 是獨立的儲存機制。  
  
```csharp  
internal static SettingsManager VsManagedSettingsManager =  
    new ShellSettingsManager(ServiceProvider.GlobalProvider);  
```  
  
 Visual Studio 設定儲存體使用類別識別碼和設定識別碼來唯一識別所有設定：  
  
```csharp  
private const string _collectionSettingsName = "Text Editor";  
private const string _settingName = "Guides";  
```  
  
 您沒有使用`“Text Editor”`做為類別目錄名稱，以及您可以挑選任何您喜歡的項目。  
  
 前幾個函式會變更設定的進入點。  他們檢查高層級的條件約束，例如允許的輔助線的最大數目。  然後在呼叫`WriteSettings`其會撰寫設定字串，並設定屬性`GuideLinesConfiguration`。  設定這個屬性將設定值儲存至 Visual Studio 設定存放區並引發`SettingsChanged`事件，以更新所有`ColumnGuideAdornment`物件，每個相關聯的文字檢視。  
  
 有幾個進入點函式的這類`CanAddGuideline`，用來實作變更設定的命令。  Visual Studio 會顯示功能表，它會查詢命令實作，請參閱是否命令目前已啟用，其名稱為何，依此類推。以下您將了解如何將連結命令實作這些進入點。  請參閱[擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)如需有關命令。  
  
## <a name="implementing-the-columnguideadornment-class"></a>實作 ColumnGuideAdornment 類別  
 `ColumnGuideAdornment`可以裝飾每一個文字檢視具現化類別。  這個類別會接聽檢視變更的相關事件或變更的設定，視引導更新或重新繪製的資料行。  
  
 ColumnGuideAdornment.cs 內容取代為下列程式碼 （如下所述）：  
  
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
  
 此類別的執行個體保存到相關聯<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>以及一份`Line`檢視上所繪製的物件。  
  
 建構函式 (從呼叫`ColumnGuideAdornmentTextViewCreationListener`當 Visual Studio 會建立新的檢視) 會建立資料行指南`Line`物件。  建構函式也會加入處理常式`SettingsChanged`事件 (定義於`GuidesSettingsManager`) 並檢視事件`LayoutChanged`和`Closed`。  
  
 `LayoutChanged`因為數種檢視，包括當 Visual Studio 會建立檢視表中的變更而引發的事件。  `OnViewLayoutChanged`處理常式會呼叫`AddGuidelinesToAdornmentLayer`來執行。  中的程式碼`OnViewLayoutChanged`決定是否需要更新根據變更例如字型大小的變更，檢視間距、 水平捲動，以及等等的行位置。  中的程式碼`UpdatePositions`導致繪製字元之間，或只在文字中的一行文字中指定的字元位移的資料行之後的輔助線。  
  
 設定變更，每當`SettingsChanged`函式只會重新建立所有`Line`具有任何新設定的物件。  設定行位置之後, 的程式碼會移除所有先前`Line`物件從`ColumnGuideAdornment`adornment 層，並將新的。  
  
## <a name="defining-the-commands-menus-and-menu-placements"></a>定義命令、 功能表和功能表的位置  
 可以有許多宣告命令和功能表、 各種其他的功能表中，在放置群組的命令或功能表和命令處理常式連結。  本逐步解說會反白顯示此延伸模組，但在深入資訊，命令的運作方式，請參閱 <<c0> [ 擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)。  
  
### <a name="introduction-to-the-code"></a>程式碼的簡介  
 分欄輔助線延伸模組會顯示宣告一組彼此互屬的命令 （加入資料行、 移除資料行、 變更線條色彩），然後將該群組放在子功能表中的編輯器操作功能表上。  分欄輔助線延伸模組也會將命令新增至主**編輯**功能表但使其保持看不見，討論以下列常見的模式。  
  
 有三個部分命令的實作： ColumnGuideCommandsPackage.cs、 ColumnGuideCommandsPackage.vsct 和 ColumnGuideCommands.cs。  範本所產生的程式碼會將命令放**工具**功能表快顯對話方塊中，做為實作。  您可以看看如何實作在.vsct 和 ColumnGuideCommands.cs 檔案因為它是非常簡單。  您將會取代下列這些檔案中的程式碼。  
  
 封裝程式碼會是未定案宣告所需的 Visual Studio 探索擴充功能提供命令和命令的位置。  當封裝初始化時，它具現化命令實作類別。  請參閱連結上方，如需詳細資訊，關於封裝與命令相關的命令。  
  
### <a name="a-common-commands-pattern"></a>常見的命令模式  
 分欄輔助線延伸模組中的命令是模式的很常見，在 Visual Studio 中的範例。  您在群組中，把相關的命令，然後您將該群組放在主功能表中，通常與 「`<CommandFlag>CommandWellOnly</CommandFlag>`"設為隱藏的命令。  將命令放在主功能表上 (例如**編輯**) 這種方式可讓這些好用的名稱 (例如**Edit.AddColumnGuide**) 這是用於重新指派中的索引鍵繫結時，找出命令**工具選項**並叫用命令時，取得完成**命令視窗**。  
  
 然後，您會加入操作功能表中的命令群組或子的功能表在您想要使用命令的使用者。  Visual Studio 會將視為`CommandWellOnly`為只有主功能表的隱藏旗標。  當您將相同的命令群組放在操作功能表或子功能表時，命令會顯示。  
  
 在常見的模式，分欄輔助線延伸會建立包含單一子功能表中的第二個群組。  子功能表中依序包含四個資料行快速入門命令的第一個群組。  包含子功能表中的第二個群組是可重複使用資產，您將各種不同的操作功能表中，會將這些內容功能表上的子功能表。  
  
### <a name="the-vsct-file"></a>.Vsct 檔  
 .Vsct 檔宣告的命令，以及它們在哪裡，以及圖示等。  .Vsct 檔案的內容取代為下列程式碼 （如下所述）：  
  
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
  
 **GUID**。  針對 Visual Studio 中尋找您的命令處理常式，並叫用它們，您必須確定的封裝 ColumnGuideCommandsPackage.cs 檔案 （產生與專案項目範本） 中宣告的 GUID 符合的封裝 （複製上述的.vsct 檔案中宣告的 GUID).  如果您重複使用此範例程式碼，您應該確定您有不同的 GUID，讓您與其他人可能已複製此程式碼沒有衝突。  
  
 ColumnGuideCommandsPackage.cs 中尋找此行，並複製 GUID，頭尾包括在內的引號：  
  
```csharp  
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";  
```  
  
 然後貼上 GUID.vsct 檔案中，讓您在下面這行程式`Symbols`宣告：  
  
```xml  
<GuidSymbol name="guidColumnGuideCommandsPkg"   
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />  
```  
  
 設定命令的 Guid 和點陣圖影像檔太應該是唯一的延伸模組：  
  
```xml  
<GuidSymbol name="guidColumnGuidesCommandSet"   
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
```  
  
 不過，您不需要變更的命令集，並點陣圖本逐步解說中的映像 Guid，以取得程式碼才能運作。  命令集的 GUID 必須符合在 ColumnGuideCommands.cs 檔案中，宣告，但您將會取代該檔案的內容太;因此，會比對的 Guid。  
  
 其他.vsct 檔中的 Guid 會識別預先存在的功能表新增到其中的資料行的快速入門命令，讓它們永遠不會變更。  
  
 **檔案區段**。  .vsct 有三個外部的區段： 命令、 位置和符號。  [命令] 區段會定義命令群組、 功能表、 按鈕或功能表項目和圖示的點陣圖。  [位置] 區段可宣告群組功能表上既有的功能表上的其他位置在哪裡。  Symbols 區段宣告在.vsct 檔案中，可讓.vsct 程式碼更容易閱讀，到處都有 Guid 和十六進位數字比其他地方使用的識別項。  
  
 **命令區段、 群組定義**。  [命令] 區段會先定義命令群組。  群組的命令是您會看到功能表中使用分隔的群組的灰色線條些微的命令。  群組也可能會填滿整個子功能表中，如同此範例中，且您未看到灰色區隔線時，在此情況下。  .Vsct 檔案會宣告兩個群組，`GuidesMenuItemsGroup`的父代`IDM_VS_MENU_EDIT`(主要**編輯**功能表) 和`GuidesContextMenuGroup`的父代`IDM_VS_CTXT_CODEWIN`（程式碼編輯器的內容功能表）。  
  
 第二個群組宣告具有`0x0600`優先順序：  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
```  
  
 其概念是將資料行引導我們將新增的任何內容功能表中的子功能表群組結尾的子功能表。  不過，您不應該假設您最了解，並強制子功能表中，永遠是上次使用的優先順序`0xFFFF`。  您不必在玩這個數字，請參閱子功能表位於您放置它的操作功能表上的位置。  在此情況下`0x0600`夠高，無法將它放在功能表的結束，就我們所見，但留下空間給其他人來設計其延伸模組，並視需要為低於資料行的輔助線延伸模組。  
  
 **命令區段中，功能表定義**。  [命令] 區段定義子功能表中的下一步`GuidesSubMenu`，以父代`GuidesContextMenuGroup`。  `GuidesContextMenuGroup`是我們將新增至所有相關的內容功能表的群組。  在 [位置] 區段中，程式碼會置於這個子功能表中使用四個資料行指南命令群組。  
  
 **命令區段，按鈕定義**。  [命令] 區段，然後定義的功能表項目，或者是四個資料行的按鈕會引導命令。  `CommandWellOnly`上面所討論，表示是放在主功能表上看不見的命令。  兩個功能表項目的按鈕宣告 （新增輔助線和移除指南） 也有`AllowParams`旗標：  
  
```xml  
<CommandFlag>AllowParams</CommandFlag>  
```  
  
 這個旗標允許，以及具有主功能表的位置，以接收時 Visual Studio 叫用命令處理常式的引數的命令。  如果使用者叫用的命令，從命令視窗，引數傳遞至命令處理常式在事件引數。  
  
 **命令的區段中，點陣圖定義**。  最後的命令 」 一節所宣告的點陣圖或命令所使用的圖示。  這是簡單的宣告，以識別專案資源，並列出使用的圖示的其中一個為基礎的索引。  .Vsct 檔的 symbols 區段宣告做為索引的識別碼值。  本逐步解說會使用自訂命令項目範本加入專案中隨附的點陣圖區。  
  
 **配置區段**。  命令之後區段會是 [位置] 區段。  第一個是程式碼新增上面所討論的第一個群組包含四個資料行指南子功能表中的命令命令出現的位置：  
  
```xml  
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                  priority="0x0100">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
</CommandPlacement>  
```  
  
 所有其他位置新增`GuidesContextMenuGroup`(其中包含`GuidesSubMenu`) 以其他編輯器操作功能表。  當程式碼宣告`GuidesContextMenuGroup`，它父代的程式碼編輯器的操作功能表。  這就是為什麼您沒有看到程式碼編輯器的內容功能表的位置。  
  
 **符號區段**。  如上所述的 symbols 區段宣告在.vsct 檔案中，可讓.vsct 程式碼更容易閱讀，到處都有 Guid 和十六進位數字比其他地方使用的識別項。  在本節中的重點是封裝 GUID 必須與 GUID 必須同意命令實作類別中宣告的宣告套件類別中，和命令集一致。  
  
## <a name="implementing-the-commands"></a>實作命令  
 ColumnGuideCommands.cs 檔案會實作的命令，並連結處理常式。  當 Visual Studio 會載入此封裝，並將它初始化時，封裝會反過來呼叫`Initialize`命令實作類別上。  命令初始化直接具現化類別，並將所有的命令處理常式連結的建構函式。  
  
 ColumnGuideCommands.cs 檔案的內容取代為下列程式碼 （如下所述）：  
  
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
  
 **修正參考**。  您在此時遺漏的參考。  在 [方案總管] 中的 [參考] 節點，請按右指標按鈕。  選擇**加入...** 方塊。  **加入參考**對話方塊已在右上角的 [搜尋] 方塊。  輸入 「 編輯器 」 （不含雙引號）。  選擇**Microsoft.VisualStudio.Editor** （您必須核取方塊左邊的項目，只要選取的項目） 的項目，然後選擇**確定**加入參考。  
  
 **初始化**。  在封裝類別初始化時，它會呼叫`Initialize`命令實作類別上。  `ColumnGuideCommands`初始化具現化類別，並將類別執行個體，且封裝參考儲存在類別成員。  
  
 讓我們看看其中一個命令處理常式攔截 ups 從類別建構函式：  
  
```csharp  
_addGuidelineCommand =   
    new OleMenuCommand(AddColumnGuideExecuted, null,  
                       AddColumnGuideBeforeQueryStatus,  
                       new CommandID(ColumnGuideCommands.CommandSet,  
                                     cmdidAddColumnGuide));  
  
```  
  
 您建立`OleMenuCommand`。  Visual Studio 會使用 Microsoft Office 命令系統。  當具現化 OleMenuCommand 是實作命令的函式的索引鍵引數 (`AddColumnGuideExecuted`)，Visual Studio 會顯示含有命令的功能表時要呼叫的函式 (`AddColumnGuideBeforeQueryStatus`)，及命令 id。  Visual studio 會顯示命令功能表上，使命令可以讓本身可見或灰色功能表以特定顯示之前呼叫查詢狀態函式 (例如，停用**複製**如果沒有選取範圍)，變更它的圖示，或甚至變更其名稱 （例如，來自加入某樣東西要移除的項目），並依此類推。  命令 ID 必須符合.vsct 檔案中宣告的命令識別碼。  設定命令字串和分欄輔助線可讓您新增命令必須符合.vsct 檔與 ColumnGuideCommands.cs 之間。  
  
 當使用者叫用的命令，透過 [命令] 視窗 （如下所述） 下, 面這一行會提供協助：  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
```  
  
 **查詢狀態**。  查詢狀態函式`AddColumnGuideBeforeQueryStatus`和`RemoveColumnGuideBeforeQueryStatus`檢查一些設定 （例如最大數目指南或最大的資料行的詳細資訊） 或是否有要移除的資料行指南。  如果條件為正確，它們就會啟用命令。  查詢狀態函式必須是非常有效率，因為它們執行每次 Visual Studio 會顯示在功能表上的每個命令中的功能表。  
  
 **AddColumnGuideExecuted 函式**。  新增輔助線的有趣的部分找出目前的編輯器檢視與插入號位置。  此函式會先呼叫`GetApplicableColumn`哪些檢查是否命令處理常式的事件引數中，沒有使用者提供的引數，而且如果沒有，此函式檢查編輯器的檢視：  
  
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
  
 `GetCurrentEditorColumn` 必須有提供能夠找到<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>程式碼檢視。  如果是透過追蹤`GetActiveTextView`， `GetActiveView`，和`GetTextViewFromVsTextView`，您可以了解如何這麼做。  以下是相關的程式碼抽象化，從目前的選取範圍，然後取得選取範圍的框架內，取得做為框架 DocView <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>，然後取得<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>IVsTextView，然後取得檢視的主應用程式，並最後 IWpfTextView:  
  
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
  
 IWpfTextView 之後，您可以取得插入號所在的資料行：  
  
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
  
 與目前的資料行手中，使用者已按下，程式碼只會呼叫 「 設定管理員 」 新增或移除資料行上。  Settings manager 就會引發所有事件`ColumnGuideAdornment`物件接聽。  當事件引發時，這些物件會以新的資料行指南設定更新其相關聯的文字檢視。  
  
## <a name="invoking-command-from-the-command-window"></a>叫用的命令，從命令視窗  
 資料行指南範例可讓使用者叫用做為一種擴充性的兩個命令從命令視窗。  如果您使用**檢視&#124;其他的 Windows&#124;命令視窗**命令時，您可以看到 [命令] 視窗。  您可以互動 [命令] 視窗中輸入 「 編輯 」，和命令名稱完成和提供的引數為 120，您具備下列項目：  
  
```  
> Edit.AddColumnGuide 120  
>  
```  
  
 此範例的項目可讓在.vsct 檔案宣告中，是`ColumnGuideCommands`時它會連結命令處理常式，並檢查事件引數的命令處理常式實作的類別建構函式。  
  
 您看到 「`<CommandFlag>CommandWellOnly</CommandFlag>`"在.vsct 檔，以及編輯主功能表中的配置即使我們不要顯示中的命令**編輯**功能表 UI。  主要的 [編輯] 功能表上有提供名稱，例如**Edit.AddColumnGuide**。  命令群組包含四個命令放在群組 [編輯] 功能表直接宣告：  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
```  
  
 [按鈕] 區段後面宣告命令`CommandWellOnly`讓它們保持不可見的主功能表上，且宣告以`AllowParams`:  
  
```xml  
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
        priority="0x0100" type="Button">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
  <Icon guid="guidImages" id="bmpPicAddGuide" />  
  <CommandFlag>CommandWellOnly</CommandFlag>  
  <CommandFlag>AllowParams</CommandFlag>  
  
```  
  
 您所見連結中的程式碼的命令處理常式`ColumnGuideCommands`類別建構函式所提供的允許的參數描述：  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
  
```  
  
 您所見`GetApplicableColumn`函式會檢查`OleMenuCmdEventArgs`值之前檢查目前的資料行的編輯器的檢視：  
  
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
  
## <a name="trying-your-extension"></a>嘗試您的延伸模組  
 您現在可以按下**F5**執行您的資料行指南延伸模組。  開啟文字檔案並使用編輯器操作功能表來加入輔助線，將它們移除，並變更其色彩。  您需要按一下 以文字 （沒有空格會傳遞行結尾） 新增資料行指南或編輯器將其新增至該行最後一個資料行。  如果您使用 [命令] 視窗，並叫用命令的引數，您可以新增任何地方分欄輔助線。  
  
 如果您想要嘗試不同的命令位置中，變更名稱、 變更圖示，並依此類推，而且您有任何問題，與顯示在功能表中的最新的程式碼的 Visual Studio，您可以重設實驗登錄區中您要偵錯。  啟動**Windows [開始] 功能表**並輸入 [重設]。  尋找並叫用命令**重設下一個 Visual Studio 實驗執行個體**。  這會清除所有的延伸模組元件的實驗登錄區。  它並不會清除出從元件的設定，因此當您關閉 Visual Studio 的實驗登錄區，您有任何指南仍會有您的程式碼讀取設定存放區，在下一步 啟動時。  
  
## <a name="finished-code-project"></a>完成的程式碼專案  
 即將發生的 Visual Studio 擴充性範例 github 專案，而且已完成的專案會有。  我們將更新本主題，當發生這種情況發生點。  已完成的範例專案可能會有不同的 guid，並會有不同的點陣圖寬帶命令圖示。  
  
 您可以試試看這個 Visual Studio 組件庫的資料行指南功能的版本[延伸模組](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home)。  
  
## <a name="see-also"></a>另請參閱  
 [在編輯器內](../extensibility/inside-the-editor.md)   
 [擴充編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)   
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)   
 [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)   
 [加入功能表中的子功能表](../extensibility/adding-a-submenu-to-a-menu.md)   
 [使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)

