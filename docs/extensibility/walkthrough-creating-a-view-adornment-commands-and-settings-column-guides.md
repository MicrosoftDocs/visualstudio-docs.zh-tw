---
title: "建立檢視裝飾、 命令和設定 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: c1836489b1845bca9e57daf83fc97bafeaf9da72
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="walkthrough-creating-a-view-adornment-commands-and-settings-column-guides"></a>逐步解說： 建立檢視裝飾、 命令和設定 （資料行指南）
您可以擴充 Visual Studio 文字/程式碼編輯器與命令和檢視效果。  本主題會示範如何開始使用常見的延伸模組功能，資料行的指南。  資料行的輔助線是以視覺化方式淺色文字編輯器的檢視，可協助您管理您的程式碼的特定資料行寬度上繪製的直線。  特別是格式化程式碼可能很重要的範例包含在文件，部落格文章，或錯誤報告。  
  
 在本逐步解說，您將：  
  
-   建立 VSIX 專案  
  
-   加入編輯器檢視裝飾  
  
-   新增支援儲存和取得設定 （其中繪製資料行的輔助線和其色彩）  
  
-   將命令加入 （新增/移除資料行的指南，變更其色彩）  
  
-   將命令放在 [編輯] 功能表和文字文件內容功能表  
  
-   加入叫用 Visual Studio 命令視窗中命令的支援  
  
 您可以試用版本與這個 Visual Studio 組件庫的資料行指南功能[延伸](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home)。  
  
 **請注意**： 這個逐步解說中您必須將大量程式碼貼入 visual studio 擴充功能的範本，所產生的一些檔案，但很快就本逐步解說會指向具有其他擴充功能範例 github 上已完成的方案。  已實際命令而不是使用 generictemplate 圖示的圖示，已完成的程式碼會有些許不同。  
  
## <a name="getting-started"></a>快速入門  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="setting-up-the-solution"></a>設定解決方案  
 第一次您將建立 VSIX 專案，加入編輯器檢視裝飾，然後再加入命令 （這會將 VSPackage 也可以擁有命令）。  基本架構如下所示：  
  
-   您必須建立文字檢視建立接聽程式`ColumnGuideAdornment`每一檢視的物件。  這個物件接聽事件的相關檢視變更，或視需要輔助線的設定變更，更新或重繪資料行。  
  
-   沒有`GuidesSettingsManager`可處理從 Visual Studio 設定儲存體讀取和寫入。  設定管理員也會有更新的設定，支援使用者命令的作業 （加入資料行、 移除資料行、 變更色彩）。  
  
-   VSIP 封裝所需，如果您有使用者命令，但它是只會初始化命令實作物件未定案程式碼。  
  
-   沒有`ColumnGuideCommands`.vsct 檔中宣告可實作使用者命令和命令的命令處理常式連結的物件。  
  
 **VSIX**。  使用**檔案 &#124;新...**命令，以建立專案。  在左側瀏覽窗格中選擇 C# 下的 擴充性 節點，選擇  **VSIX 專案**右窗格中。  輸入 ColumnGuides 的名稱，然後選擇**確定**建立專案。  
  
 **檢視裝飾**。  在 [方案總管] 中的專案節點上按右指標按鈕。  選擇**新增 &#124;新增項目...**命令，以加入新的檢視裝飾項目。  選擇**擴充性 &#124;編輯器**左側的導覽窗格中，然後選擇 **編輯器檢視區裝飾**右窗格中。  輸入名稱 ColumnGuideAdornment 做為項目名稱，然後選擇**新增**，將它加入。  
  
 您可以看到這個項目範本加入至專案 （以及參考等等） 的兩個檔案： ColumnGuideAdornment.cs 和 ColumnGuideAdornmentTextViewCreationListener.cs。  範本只會在檢視上繪製一個紫色的矩形。  下面將變更幾行中的檢視建立接聽程式，並取代 ColumnGuideAdornment.cs 的內容。  
  
 **命令**。  在 [方案總管] 中的專案節點上按右指標按鈕。  選擇**新增 &#124;新增項目...**命令，以加入新的檢視裝飾項目。  選擇**擴充性 &#124;VSPackage**左側的導覽窗格中，然後選擇 **自訂命令**右窗格中。  輸入名稱 ColumnGuideCommands 做為項目名稱，然後選擇**新增**，將它加入。  數個參考，除了新增的命令和封裝新增 ColumnGuideCommands.cs、 ColumnGuideCommandsPackage.cs 和 ColumnGuideCommandsPackage.vsct。  下面，您將會取代來定義並實作命令的第一個和最後一個檔案的內容。  
  
## <a name="setting-up-the-text-view-creation-listener"></a>設定文字檢視建立接聽程式  
 在編輯器中開啟 ColumnGuideAdornmentTextViewCreationListener.cs。  這段程式碼會實作一個處理常式，每當 Visual Studio 建立文字檢視。  沒有屬性，以控制當呼叫此處理常式是根據檢視的特性。  
  
 程式碼也必須宣告裝飾圖層。  當編輯器 中更新的檢視時，它會取得檢視裝飾圖層的連線，並從該取得裝飾項目。  您可以宣告具有屬性相對於其他程式層級的順序。  取代為下列行：  
  
```csharp  
[Order(After = PredefinedAdornmentLayers.Caret)]  
```  
  
 下列兩行：  
  
```csharp  
[Order(Before = PredefinedAdornmentLayers.Text)]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
```  
  
 您更換的線條是群組中的宣告裝飾圖層的屬性。   第一行您變更資料行的輔助線的出現位置的唯一變更。  「 之前 」 檢視中的文字表示後置或的文字下方，則會出現，請繪製線條。  第二行宣告資料行指南裝飾時，適用於符合您的文件的概念的文字項目，但您無法宣告裝飾，比方說，用於編輯的文字。  中的詳細資訊[語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)  
  
## <a name="implementing-the-settings-manager"></a>實作設定管理員  
 GuidesSettingsManager.cs 的內容取代為下列程式碼 （如下所述）：  
  
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
  
 大部分的這段程式碼只會建立並剖析設定格式:"RGB (\<int >，\<int >，\<int >) \<int >， \<int >，..."。  結束的整數都以一為您想要資料行的指南。  資料行的輔助線擴充功能會擷取它在單一的設定值字串中的所有設定。  
  
 沒有值得反白顯示的程式碼的某些部分。  下列程式碼會取得 Visual Studio managed 包裝函式的設定儲存體。  大部分的情況下，此抽象化透過 Windows 登錄中，但此 API 是獨立的儲存機制。  
  
```csharp  
internal static SettingsManager VsManagedSettingsManager =  
    new ShellSettingsManager(ServiceProvider.GlobalProvider);  
```  
  
 Visual Studio 設定儲存體使用類別識別碼和設定識別碼，來唯一識別所有設定：  
  
```csharp  
private const string _collectionSettingsName = "Text Editor";  
private const string _settingName = "Guides";  
```  
  
 您沒有使用`"Text Editor"`做為類別目錄名稱，以及您可以挑選任何您喜歡的項目。  
  
 在前幾個函式會變更設定的進入點。  他們檢查高層級的條件約束類似指南允許的最大數目。  然後這些呼叫`WriteSettings`的撰寫設定字串，並且設定屬性`GuideLinesConfiguration`。  設定這個屬性將設定值儲存至 Visual Studio 設定存放區和引發`SettingsChanged`事件來更新所有`ColumnGuideAdornment`物件，每個相關聯的文字檢視。  
  
 一些的進入點函式，例如`CanAddGuideline`，可用來實作變更設定的命令。  Visual Studio 會顯示功能表，它會查詢命令實作，請參閱是否命令目前已啟用，其名稱是什麼，依此類推。下面，您會看到如何連結命令實作這些項目點。  請參閱[擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)如需有關命令。  
  
## <a name="implementing-the-columnguideadornment-class"></a>實作 ColumnGuideAdornment 類別  
 `ColumnGuideAdornment`類別具現化提供的每個文字檢視，可以有裝飾。  這個類別會接聽檢視變更的相關事件，或視需要輔助線的設定變更，更新或重繪資料行。  
  
 ColumnGuideAdornment.cs 的內容取代為下列程式碼 （如下所述）：  
  
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
  
 這個類別的執行個體保存到相關聯<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>以及一份`Line`繪製在檢視上的物件。  
  
 建構函式 (從呼叫`ColumnGuideAdornmentTextViewCreationListener`時 Visual Studio 會建立新的檢視表) 會建立資料行指南`Line`物件。  建構函式也加入的處理常式`SettingsChanged`事件 (定義於`GuidesSettingsManager`) 並檢視事件`LayoutChanged`和`Closed`。  
  
 `LayoutChanged`因為數種檢視，包括 Visual Studio 建立的檢視中變更的事件引發。  `OnViewLayoutChanged`處理常式呼叫`AddGuidelinesToAdornmentLayer`來執行。  中的程式碼`OnViewLayoutChanged`決定是否需要更新根據變更，例如字型大小的變更，檢視間距、 水平捲動，以及等等的行位置。  中的程式碼`UpdatePositions`導致繪製字元之間，或只在指定的字元位移中的一行文字中的文字資料行之後的輔助線。  
  
 每當設定變更`SettingsChanged`函式只會重新建立所有`Line`物件與任何新的設定。  設定之後的行位置，程式碼會移除所有先前`Line`物件從`ColumnGuideAdornment`裝飾圖層，並將新的。  
  
## <a name="defining-the-commands-menus-and-menu-placements"></a>定義命令、 功能表和功能表的位置  
 可以有許多在宣告命令和功能表、 置於各種其他的功能表命令或功能表的群組和命令處理常式連結。  本逐步解說會反白顯示命令的運作方式在這個延伸模組，但更深入的資訊，請參閱[擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)。  
  
### <a name="introduction-to-the-code"></a>程式碼的簡介  
 資料行指南延伸模組會顯示宣告一組屬於的命令 （新增資料行、 移除資料行、 變更線條色彩），然後再將該群組放入編輯器的內容功能表中的子功能表上。  資料行指南延伸模組也會將命令加入至 main**編輯**功能表但會保留它們看不見，討論為下列常見的模式。  
  
 有三個命令實作部分： ColumnGuideCommandsPackage.cs、 ColumnGuideCommandsPackage.vsct 和 ColumnGuideCommands.cs。  範本所產生的程式碼會將命令放在**工具**快顯對話方塊中，做為實作的功能表。  您可以查看如何實作在.vsct 和 ColumnGuideCommands.cs 檔案因為它是很直接。  您將會取代下列這些檔案中的程式碼。  
  
 封裝程式碼是未定案宣告所需的 Visual Studio 來探索擴充功能提供命令和指令的放置位置。  當封裝初始化時，它具現化命令的實作類別。  請參閱上述連結如需詳細資訊，關於封裝與命令相關的命令。  
  
### <a name="a-common-commands-pattern"></a>一般的命令模式  
 中的資料行指南延伸模組的命令是模式的很常見，在 Visual Studio 中的範例。  您將相關的命令放在群組中，並將放該群組主功能表中，通常與 「`<CommandFlag>CommandWellOnly</CommandFlag>`」 讓命令看不到設定。  將命令放在主功能表上 (例如**編輯**) 這種方式可讓他們很棒的名稱 (例如**Edit.AddColumnGuide**) 可用來尋找命令，重新指派中的索引鍵繫結時**工具選項**並取得完成時叫用命令從**命令視窗**。  
  
 然後，您會將命令的群組加入至內容功能表或子的功能表在您想要使用命令的使用者。  Visual Studio 會將處理`CommandWellOnly`為只使用主功能表的隱藏旗標。  當您將命令的同一個群組放在內容功能表或子功能表上時，命令會顯示。  
  
 常見的模式的一部分，資料行指南延伸會建立包含單一子功能表的第二個群組。  子功能表依序包含四個資料行指南命令的第一個群組。  保留子功能表的第二個群組是可重複使用的資產您放置在不同的操作功能表上放置這些內容功能表上的子功能表。  
  
### <a name="the-vsct-file"></a>.Vsct 檔  
 .Vsct 檔宣告的命令，而且它們在哪裡，以及圖示，依此類推。  .Vsct 檔案的內容取代為下列程式碼 （如下所述）：  
  
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
  
 **GUID**。  尋找您的命令處理常式，並叫用的 Visual studio，您必須確定的封裝 ColumnGuideCommandsPackage.cs 檔 （從專案項目範本產生） 中宣告的 GUID 符合的封裝 （複製上述.vsct 檔中宣告的 GUID).  如果您重複使用此範例程式碼，您應該確定您有不同的 GUID，讓您與其他人可能已複製這段程式碼沒有衝突。  
  
 ColumnGuideCommandsPackage.cs 中找到這一行，然後將複製的 GUID，頭尾包括在內的引號：  
  
```csharp  
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";  
```  
  
 然後貼上 GUID.vsct 檔中，所以您需要下列行您`Symbols`宣告：  
  
```xml  
<GuidSymbol name="guidColumnGuideCommandsPkg"   
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />  
```  
  
 設定命令的 Guid 和點陣圖影像檔太應該是唯一的您的擴充功能：  
  
```xml  
<GuidSymbol name="guidColumnGuidesCommandSet"   
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
```  
  
 不過，您不需要變更命令集及點陣圖取得程式碼以在此逐步解說中的映像 Guid。  命令集的 GUID 必須符合的宣告在 ColumnGuideCommands.cs 檔案中，但您將會取代該檔案的內容太;因此，Guid 會比對。  
  
 其他.vsct 檔中的 Guid 識別預先存在的功能表新增到其中的資料行指南命令，因此永遠不會變更。  
  
 **檔案區段**。  .vsct 有三個外部區段： 命令、 放置和符號。  Commands 區段會定義命令群組、 功能表、 按鈕或功能表項目和圖示的點陣圖。  放置區段可宣告上的功能表或其他位置，拖曳至預先存在的功能表群組在哪裡。  符號區段宣告在.vsct 檔案中，讓.vsct 的程式碼更容易閱讀，比起 everywhere Guid 和十六進位數字的其他位置使用的識別項。  
  
 **命令 > 一節，群組定義**。  Commands 區段先定義命令的群組。  群組的命令會有些微的灰色線條分隔群組功能表中看見的命令。  群組也可能會填滿整個子功能表上，就如同此範例中，並不會看到以灰色顯示，在此情況下分隔線。  .Vsct 檔會宣告兩個群組`GuidesMenuItemsGroup`的父代`IDM_VS_MENU_EDIT`(主要**編輯**功能表) 與`GuidesContextMenuGroup`的父代`IDM_VS_CTXT_CODEWIN`（程式碼編輯器內容功能表）。  
  
 第二個群組宣告具有`0x0600`優先順序：  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
```  
  
 這個概念是將資料行引導我們將新增的任何內容功能表中的子功能表群組結尾的子功能表。  不過，您不應該假設您知道最佳，而且強制為一律在最後一個使用的優先順序 子功能表`0xFFFF`。  您必須利用這個數字，請參閱子功能表會位於您放置它的內容功能表。  在此情況下`0x0600`夠高，無法將其放置在功能表的結束，就可以看到，但留下空間給其他人來設計其擴充功能，並視需要為低於資料行的輔助線延伸模組。  
  
 **命令 區段中，功能表定義**。  接下來命令區段定義 子功能表`GuidesSubMenu`，以父代`GuidesContextMenuGroup`。  `GuidesContextMenuGroup`是我們將新增至所有相關的內容功能表的群組。  [位置] 區段中，程式碼將放置在具有四個資料行指南命令群組此子功能表。  
  
 **命令 > 一節，按鈕定義**。  Commands 區段，然後定義的功能表項目或是四個資料行的按鈕引導命令。  `CommandWellOnly`上面所討論，表示命令不可見時用來放置主功能表上。  兩個功能表項目按鈕宣告 （新增輔助線和移除指南） 也有`AllowParams`旗標：  
  
```xml  
<CommandFlag>AllowParams</CommandFlag>  
```  
  
 這個旗標可讓，以及使用擁有主功能表位置，以接收時 Visual Studio 會叫用的命令處理常式的引數的命令。  如果在使用者叫用的命令，從命令視窗，引數傳遞至命令處理常式的事件引數。  
  
 **命令的區段中，點陣圖定義**。  最後 commands 區段宣告點陣圖或命令所使用的圖示。  這是簡單的宣告識別專案資源，並列出使用的圖示的其中一個為基礎的索引。  .Vsct 檔的符號區段可宣告為索引所使用的識別碼值。  本逐步解說會使用提供的自訂命令項目範本加入至專案的點陣圖帶。  
  
 **放置區段**。  命令 > 一節之後放置 > 一節。  第一個是程式碼加入上面所討論的第一個群組包含四個資料行指南子功能表的命令命令出現的位置：  
  
```xml  
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                  priority="0x0100">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
</CommandPlacement>  
```  
  
 所有其他位置新增`GuidesContextMenuGroup`(其中包含`GuidesSubMenu`) 以其他編輯器操作功能表。  當程式碼宣告`GuidesContextMenuGroup`，它為程式碼編輯器內容功能表的父代。  這就是為什麼看不到程式碼編輯器的內容功能表上的位置。  
  
 **符號區段**。  如前所述，符號區段可宣告在.vsct 檔案中，讓.vsct 的程式碼更容易閱讀，比起 everywhere Guid 和十六進位數字的其他位置使用的識別項。  這一節的重點是在套件類別中和命令集 GUID 必須同意命令實作類別中宣告的宣告必須同意封裝 GUID。  
  
## <a name="implementing-the-commands"></a>實作命令  
 ColumnGuideCommands.cs 檔案實作命令，並連結處理常式。  當 Visual Studio 會載入封裝，並將它初始化時，封裝會依序呼叫`Initialize`命令實作類別上。  命令初始化直接具現化的類別，並將所有命令處理常式的建構函式都連結。  
  
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
  
 **修正參考**。  您在此時遺漏參考。  在 [方案總管] 中 [參考] 節點上按右指標按鈕。  選擇**新增...**命令。  **加入參考**對話方塊有右上角的 [搜尋] 方塊。  請輸入"editor"（不含雙引號）。  選擇**Microsoft.VisualStudio.Editor** （您必須核取方塊左邊的項目，只要選取的項目） 的項目，然後選擇 **確定**將參考加入。  
  
 **初始化**。  在封裝類別初始化時，它會呼叫`Initialize`命令實作類別上。  `ColumnGuideCommands`初始化具現化類別，並將類別執行個體和封裝參考儲存在類別成員。  
  
 讓我們看看其中一個命令處理常式攔截 ups 從類別建構函式：  
  
```csharp  
_addGuidelineCommand =   
    new OleMenuCommand(AddColumnGuideExecuted, null,  
                       AddColumnGuideBeforeQueryStatus,  
                       new CommandID(ColumnGuideCommands.CommandSet,  
                                     cmdidAddColumnGuide));  
  
```  
  
 您建立`OleMenuCommand`。  Visual Studio 會使用 Microsoft Office 命令系統。  索引鍵的引數時具現化 OleMenuCommand 實作命令的函式 (`AddColumnGuideExecuted`)，Visual Studio 會顯示功能表命令時要呼叫的函式 (`AddColumnGuideBeforeQueryStatus`)，和命令 id。  Visual studio 會顯示命令功能表上，如此不可見或灰色有特定的顯示器功能表的命令也可以進行本身之前呼叫查詢狀態函式 (例如，停用**複製**如果沒有選取範圍)，變更它的圖示，或甚至變更其名稱 （例如，從加入某樣東西要移除的項目），並以此類推。  命令 ID 必須符合.vsct 檔中宣告的命令識別碼。  命令字串設定和資料行的輔助線加入命令必須符合.vsct 檔和 ColumnGuideCommands.cs 之間。  
  
 下面提供的協助，當使用者叫用的命令，透過在命令視窗 （如下所述）：  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
```  
  
 **查詢狀態**。  查詢狀態函數`AddColumnGuideBeforeQueryStatus`和`RemoveColumnGuideBeforeQueryStatus`檢查部份設定 （例如輔助線或最大資料行的最大數目），或如果沒有要移除的資料行指南。  右條件時，它們就會啟用命令。  查詢狀態函式必須是非常有效率，因為它們執行每次 Visual Studio 會顯示在功能表上的每個命令中的功能表。  
  
 **AddColumnGuideExecuted 函式**。  新增輔助線的有趣的部份找出目前的編輯器檢視和插入號位置。  此函式會先呼叫`GetApplicableColumn`的檢查是否有命令處理常式的事件引數中，為使用者提供的引數，以及如果沒有，此函式檢查編輯器的檢視：  
  
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
  
 `GetCurrentEditorColumn`若要取得稍微有<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>檢視程式碼。  如果是透過追蹤`GetActiveTextView`， `GetActiveView`，和`GetTextViewFromVsTextView`，您可以了解如何執行此作業。  以下是相關的程式碼區隔，從目前的選取範圍，再取得選取範圍的範圍內，然後取得做為框架 DocView <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>，然後取得<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>在 IVsTextView 和 快速入門 檢視主機和最後 IWpfTextView:  
  
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
  
 與目前的資料行手其中使用者已按下，程式碼只會呼叫設定管理員来新增或移除資料行上。  設定管理員就會引發事件以所有`ColumnGuideAdornment`物件接聽。  當事件引發時，這些物件會以新的資料行指南設定更新及其相關聯的文字檢視。  
  
## <a name="invoking-command-from-the-command-window"></a>叫用的命令，從命令視窗  
 資料行指南範例可讓使用者叫用做為一種擴充性的兩個命令，從命令視窗。  如果您使用**檢視 &#124;其他視窗 &#124;命令視窗**命令時，您可以看到 [命令] 視窗。  您可以互動命令視窗中輸入 「 編輯 」，並使用命令名稱完成，並提供引數 120，您需要下列：  
  
```  
> Edit.AddColumnGuide 120  
>  
```  
  
 此範例的項目可讓在.vsct 檔案宣告中，是`ColumnGuideCommands`時它就會攔截命令處理常式，以及檢查事件引數的命令處理常式實作的類別建構函式。  
  
 您已看到 「`<CommandFlag>CommandWellOnly</CommandFlag>`".vsct 檔以及位置，在主功能表中編輯即使我們不要顯示中的命令**編輯**功能表 UI。  具有主要的 [編輯] 功能表上提供名稱，例如**Edit.AddColumnGuide**。  命令群組所在的四個命令放在群組 [編輯] 功能表直接宣告：  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
```  
  
 按鈕 > 一節稍後宣告命令`CommandWellOnly`讓它們保持可見主功能表上，且它們與宣告`AllowParams`:  
  
```xml  
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
        priority="0x0100" type="Button">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
  <Icon guid="guidImages" id="bmpPicAddGuide" />  
  <CommandFlag>CommandWellOnly</CommandFlag>  
  <CommandFlag>AllowParams</CommandFlag>  
  
```  
  
 您已看到，連接中的程式碼的命令處理常式`ColumnGuideCommands`類別建構函式提供允許參數的描述：  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
  
```  
  
 您已看到`GetApplicableColumn`函式檢查`OleMenuCmdEventArgs`檢查目前的資料行的編輯器檢視之前的值：  
  
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
  
## <a name="trying-your-extension"></a>嘗試您的擴充功能  
 您現在可以按**F5**執行您的資料行指南擴充功能。  開啟文字檔，並使用編輯器的內容功能表上新增輔助線、 移除它們，並變更其色彩。  您需要按一下 [以文字 （不空白字元傳遞一行的結尾） 加入的資料行指南或編輯器] 中將它加入至該行最後一個資料行。  如果您使用 [命令] 視窗，並叫用命令的引數，您可以加入任何位置的資料行輔助線。  
  
 如果您想要再試一次命令的不同位置、 變更名稱、 變更圖示，並依此類推，顯示功能表中的最新的程式碼的 Visual Studio 中的任何問題，您可以重設在其中您要偵錯在實驗登錄區。  啟動**Windows [開始] 功能表**並輸入 「 重設 」。  尋找並叫用命令**重設下一個 Visual Studio 實驗執行個體**。  這會清除所有擴充功能元件的實驗登錄區。  它並不會清除出從元件的設定，因此當您關閉 Visual Studio 實驗登錄區，您有任何輔助線仍會有您的程式碼會讀取下次啟動 「 設定存放區時。  
  
## <a name="finished-code-project"></a>完成的程式碼專案  
 有即將推出的 Visual Studio 擴充性範例 github 專案和已完成的專案將不會消失。  我們將會更新本主題，當發生這種情況發生點。  已完成的範例專案可能會有不同的 guid，而且必須命令圖示的點陣圖不同區域。  
  
 您可以試用版本與這個 Visual Studio 組件庫的資料行指南功能[延伸](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home)。  
  
## <a name="see-also"></a>另請參閱  
 [在編輯器](../extensibility/inside-the-editor.md)   
 [擴充編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)   
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)   
 [擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)   
 [加入功能表的子功能表](../extensibility/adding-a-submenu-to-a-menu.md)   
 [使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)
