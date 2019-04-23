---
title: WPF 簡介 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8d20b8938f4d841bb42299b7aa9abaf633f72e7d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074605"
---
# <a name="introduction-to-wpf"></a>WPF 簡介
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Presentation Foundation (WPF) 可讓您建立具有豐富視覺效果之使用者介面的 Windows 桌面用戶端應用程式。  
  
 ![Contoso Healthcare UI 範例](../designers/media/wpfintrofigure24.png "WPFIntroFigure24")  
  
 WPF 的核心是與解析度無關並以向量為基礎的轉譯引擎，其建置目的是為了利用現代化圖形硬體。 WPF 利用一組完整的應用程式開發功能來擴充核心，包括 XAML (Extensible Application Markup Language)、控制項、資料繫結、版面配置、2D 和 3D 圖形、動畫、樣式、範本、文件、媒體、文字，以及印刷樣式。 WPF 隨附於 .NET Framework，因此您可以建置納入 .NET Framework 類別庫之其他項目的應用程式。  
  
 本概觀適用於初學者，內容涵蓋 WPF 的主要功能和概念。  
  
## <a name="Programming_with_WPF"></a> 使用 WPF 進行程式設計  
 WPF 是以 .NET Framework 類型的子集來表示，大部分位於 <xref:System.Windows> 命名空間中。 如果您之前使用過 ASP.NET 和 Windows Form 等 Managed 技術建置 .NET Framework 應用程式，應該很熟悉基本 WPF 程式設計功能：您可以具現化類別、設定屬性、呼叫方法及處理事件，全部透過您最愛的 .NET 程式設計語言來完成，例如 C# 或 Visual Basic。  
  
 WPF 包含可增強屬性和事件的額外程式設計建構： [相依性屬性](https://msdn.microsoft.com/library/ms752914\(v=vs.100\).aspx) 和 [路由事件](https://msdn.microsoft.com/library/ms742806\(v=vs.100\).aspx)。  
  
## <a name="Markup_And_Codebehind"></a> 標記和程式碼後置  
 WPF 可讓您使用 *標記* 和 *程式碼後置*來開發應用程式，這是 ASP.NET 開發人員應該很熟悉的功能。 您通常會使用 XAML 標記來實作應用程式的外觀，同時使用 Managed 程式設計語言 (程式碼後置) 來實作其行為。 將外觀與行為區隔開來的優點如下：  
  
- 由於外觀特定標記未與行為特定程式碼緊密結合，因此可降低開發和維護成本。  
  
- 由於實作應用程式外觀的設計人員可以與實作應用程式行為的設計人員同時進行，因此開發作業會更有效率。  
  
- WPF 應用程式的[全球化和當地語系化](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx) 已經過簡化。  
  
  以下是 WPF 標記和程式碼後置的簡介。  
  
### <a name="markup"></a>標記  
 XAML 是以宣告方式來實作應用程式外觀所用的 XML 標記語言。 它通常可用來建立視窗、對話方塊、頁面和使用者控制項，並填入控制項、圖案和圖形。  
  
 下列範例使用 XAML 來實作包含單一按鈕的視窗外觀。  
  
```xaml  
<Window  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    Title="Window with Button"  
    Width="250" Height="100">  
  
  <!-- Add button to window -->  
  <Button Name="button">Click Me!</Button>  
  
</Window>  
```  
  
 具體而言，這個 XAML 會分別使用 `Window` 和 `Button` 項目來定義一個視窗和一個按鈕。 每個項目都會透過屬性進行設定，例如 `Window` 項目的 `Title` 屬性可指定視窗的標題列文字。 在執行階段，WPF 會將標記中定義的項目和屬性轉換成 WPF 類別的執行個體。 例如， `Window` 項目會轉換成 <xref:System.Windows.Window> 類別的執行個體，其 <xref:System.Windows.Window.Title%2A> 屬性即為 `Title` 屬性的值。  
  
 下圖顯示上述範例中 XAML 所定義的使用者介面 (UI)。  
  
 ![包含按鈕的視窗](../designers/media/wpfintrofigure10.png "WPFIntroFigure10")  
  
 由於 XAML 是以 XML 為基礎，您以此撰寫的 UI 會組合成巢狀項目階層架構，稱為 [項目樹狀結構](https://msdn.microsoft.com/library/ms753391\(v=vs.100\).aspx)。 項目樹狀結構提供一個邏輯和直覺方式來建立及管理 UI。  
  
### <a name="code-behind"></a>程式碼後置  
 應用程式的主要行為是實作回應使用者互動的功能，包括處理事件 (例如按一下功能表、工具列或按鈕)，以及呼叫商務邏輯和資料存取邏輯進行回應。 在 WPF 中，這項行為通常會在與標記相關聯的程式碼中實作。 這種類型的程式碼稱為程式碼後置。 下列範例顯示從上一個範例更新的標記和程式碼後置。  
  
```xaml  
<Window  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Class="SDKSample.AWindow"  
    Title="Window with Button"  
    Width="250" Height="100">  
  
  <!-- Add button to window -->  
  <Button Name="button" Click="button_Click">Click Me!</Button>  
  
</Window>  
```  
  
```csharp  
using System.Windows; // Window, RoutedEventArgs, MessageBox   
  
namespace SDKSample  
{  
    public partial class AWindow : Window  
    {  
        public AWindow()  
        {  
            // InitializeComponent call is required to merge the UI   
            // that is defined in markup with this class, including    
            // setting properties and registering event handlers  
            InitializeComponent();  
        }  
  
        void button_Click(object sender, RoutedEventArgs e)  
        {  
            // Show message box when button is clicked  
            MessageBox.Show("Hello, Windows Presentation Foundation!");  
        }  
    }  
}  
```  
  
```vb  
Namespace SDKSample  
  
    Partial Public Class AWindow  
        Inherits System.Windows.Window  
  
        Public Sub New()  
  
            ' InitializeComponent call is required to merge the UI   
            ' that is defined in markup with this class, including    
            ' setting properties and registering event handlers  
            InitializeComponent()  
  
        End Sub   
  
        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
  
            ' Show message box when button is clicked  
            MessageBox.Show("Hello, Windows Presentation Foundation!")  
  
        End Sub   
  
    End Class   
  
End Namespace  
  
```  
  
 在這個範例中，程式碼後置會實作一個衍生自 <xref:System.Windows.Window> 類別的類別。 它使用 `x:Class` 屬性來建立標記與程式碼後置類別的關聯， 並從程式碼後置類別的建構函式呼叫 `InitializeComponent`，以合併標記中定義的 UI 與程式碼後置類別 (當系統建置您的應用程式時，會為您產生 `InitializeComponent`，因此您不需要手動實作)。`x:Class` 和 `InitializeComponent` 的組合可確保您的實作在每次建立時，都能正確地初始化。 程式碼後置類別也會針對按鈕的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件實作事件處理常式。 當您按一下按鈕時，事件處理常式會呼叫 <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> 方法來顯示訊息方塊。  
  
 下圖顯示按下按鈕的結果。  
  
 ![訊息方塊](../designers/media/wpfintrofigure25.png "WPFIntroFigure25")  
  
## <a name="Controls"></a> 控制項  
 應用程式模型所傳遞的使用者體驗是已建構的控制項。 在 WPF 中，「控制項」是一個籠統的名詞，泛指裝載於視窗或頁面上之具有使用者介面並實作一些行為的某種 WPF 類別。  
  
 如需詳細資訊，請參閱 [控制項](http://msdn.microsoft.com/library/3f255a8a-35a8-4712-9065-472ff7d75599)。  
  
### <a name="wpf-controls-by-function"></a>依功能列出 WPF 控制項  
 以下列出內建 WPF 控制項。  
  
- **按鈕**： <xref:System.Windows.Controls.Button> 和 <xref:System.Windows.Controls.Primitives.RepeatButton>。  
  
- **資料顯示**： <xref:System.Windows.Controls.DataGrid>、 <xref:System.Windows.Controls.ListView>和 <xref:System.Windows.Controls.TreeView>。  
  
- **日期顯示和選取**： <xref:System.Windows.Controls.Calendar> 和 <xref:System.Windows.Controls.DatePicker>。  
  
- **對話方塊**： <xref:Microsoft.Win32.OpenFileDialog>、 <xref:System.Windows.Controls.PrintDialog>和 <xref:Microsoft.Win32.SaveFileDialog>。  
  
- **數位筆跡**： <xref:System.Windows.Controls.InkCanvas> 和 <xref:System.Windows.Controls.InkPresenter>。  
  
- **文件**： <xref:System.Windows.Controls.DocumentViewer>、 <xref:System.Windows.Controls.FlowDocumentPageViewer>、 <xref:System.Windows.Controls.FlowDocumentReader>、 <xref:System.Windows.Controls.FlowDocumentScrollViewer>和 <xref:System.Windows.Controls.StickyNoteControl>。  
  
- **輸入**： <xref:System.Windows.Controls.TextBox>、 <xref:System.Windows.Controls.RichTextBox>和 <xref:System.Windows.Controls.PasswordBox>。  
  
- **版面配置**： <xref:System.Windows.Controls.Border>、 <xref:System.Windows.Controls.Primitives.BulletDecorator>、 <xref:System.Windows.Controls.Canvas>、 <xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.Expander>、 <xref:System.Windows.Controls.Grid>、 <xref:System.Windows.Controls.GridView>、 <xref:System.Windows.Controls.GridSplitter>、 <xref:System.Windows.Controls.GroupBox>、 <xref:System.Windows.Controls.Panel>、 <xref:System.Windows.Controls.Primitives.ResizeGrip>、 <xref:System.Windows.Controls.Separator>、 <xref:System.Windows.Controls.Primitives.ScrollBar>、 <xref:System.Windows.Controls.ScrollViewer>、 <xref:System.Windows.Controls.StackPanel>、 <xref:System.Windows.Controls.Primitives.Thumb>、 <xref:System.Windows.Controls.Viewbox>、 <xref:System.Windows.Controls.VirtualizingStackPanel>、 <xref:System.Windows.Window>和 <xref:System.Windows.Controls.WrapPanel>。  
  
- **媒體**： <xref:System.Windows.Controls.Image>、 <xref:System.Windows.Controls.MediaElement>和 <xref:System.Windows.Controls.SoundPlayerAction>。  
  
- **功能表**： <xref:System.Windows.Controls.ContextMenu>、 <xref:System.Windows.Controls.Menu>和 <xref:System.Windows.Controls.ToolBar>。  
  
- **巡覽**： <xref:System.Windows.Controls.Frame>、 <xref:System.Windows.Documents.Hyperlink>、 <xref:System.Windows.Controls.Page>、 <xref:System.Windows.Navigation.NavigationWindow>和 <xref:System.Windows.Controls.TabControl>。  
  
- **選取**： <xref:System.Windows.Controls.CheckBox>、 <xref:System.Windows.Controls.ComboBox>、 <xref:System.Windows.Controls.ListBox>、 <xref:System.Windows.Controls.RadioButton>和 <xref:System.Windows.Controls.Slider>。  
  
- **使用者資訊**： <xref:System.Windows.Controls.AccessText>、 <xref:System.Windows.Controls.Label>、 <xref:System.Windows.Controls.Primitives.Popup>、 <xref:System.Windows.Controls.ProgressBar>、 <xref:System.Windows.Controls.Primitives.StatusBar>、 <xref:System.Windows.Controls.TextBlock>和 <xref:System.Windows.Controls.ToolTip>。  
  
## <a name="Input_And_Commanding"></a> 輸入和命令  
 控制項最常用來偵測及回應使用者輸入。 [WPF 輸入系統](https://msdn.microsoft.com/library/ms754010\(v=vs.100\).aspx) 使用直接和路由事件來支援文字輸入、焦點管理和滑鼠定位。  
  
 應用程式通常具有複雜的輸入需求。 WPF 提供一個 [命令系統](https://msdn.microsoft.com/library/ms752308\(v=vs.100\).aspx) ，將使用者輸入動作與回應這些動作的程式碼區隔開來。  
  
## <a name="Layout"></a> 版面配置  
 當您建立使用者介面時，您可依位置和大小排列控制項，以形成一個版面配置。 所有版面配置的一個關鍵需求是隨視窗大小和顯示設定的變更進行調整。 WPF 為您提供一流且可擴充的版面配置系統，而不是強迫您在這些情況下撰寫程式碼來調整版面配置。  
  
 這個版面配置系統是以相對定位為基礎，藉此提升依視窗和顯示狀況變更來做調整的能力。 此外，這個版面配置系統可管理控制項之間的交涉，以決定版面配置。 此交涉是兩個步驟的程序：控制項會先指示其父代所需的位置和大小，然後再由父代指示控制項其可擁有的空間。  
  
 版面配置系統會透過基底 WPF 類別公開給子控制項。 WPF 針對格線、堆疊和停駐等常見版面配置，提供了數個版面配置控制項：  
  
- <xref:System.Windows.Controls.Canvas>：子控制項會提供自己的版面配置。  
  
- <xref:System.Windows.Controls.DockPanel>：子控制項會沿著面板邊緣對齊。  
  
- <xref:System.Windows.Controls.Grid>：子控制項會依資料列和資料行定位。  
  
- <xref:System.Windows.Controls.StackPanel>：子控制項會垂直或水平堆疊。  
  
- <xref:System.Windows.Controls.VirtualizingStackPanel>：子控制項會依水平或垂直方向，以單行顯示及排列。  
  
- <xref:System.Windows.Controls.WrapPanel>：子控制項會從左至右排序定位，並在目前這一行的控制項超出空間所允許的數目時，換至下一行。  
  
  下列範例使用 <xref:System.Windows.Controls.DockPanel> 來配置多個 <xref:System.Windows.Controls.TextBox> 控制項：  
  
  [!code-xml[IntroToWPFSnippets#LayoutMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/LayoutWindow.xaml#layoutmarkup)]  
  
  <xref:System.Windows.Controls.DockPanel> 可讓子 <xref:System.Windows.Controls.TextBox> 控制項指示排列方式。 為了執行這項操作， <xref:System.Windows.Controls.DockPanel> 會實作公開給子控制項的 <xref:System.Windows.Controls.DockPanel.Dock%2A> 屬性，讓每個控制項都能指定停駐樣式。  
  
> [!NOTE]
>  WPF 建構是由父控制項實作並可供子控制項使用的屬性，又稱為 [附加屬性](https://msdn.microsoft.com/library/ms749011\(v=vs.100\).aspx)。  
  
 下圖顯示上述範例中之 XAML 標記的結果。  
  
 ![DockPanel 頁面](../designers/media/wpfintrofigure11.png "WPFIntroFigure11")  
  
## <a name="Data_Binding"></a> 資料繫結  
 大多數已建立的應用程式會為使用者提供檢視及編輯資料的方法。 至於 WPF 應用程式，儲存和存取資料的工作已由 SQL Server 和 ADO.NET 等技術提供。 存取資料並將資料載入應用程式的 Managed 物件之後，才會開始 WPF 應用程式的困難工作。 基本上，這涉及兩個動作：  
  
1. 將資料從 Managed 物件複製到控制項，以在其中顯示及編輯資料。  
  
2. 確保使用控制項對資料所做的變更，會複製回 Managed 物件。  
  
   為了簡化應用程式開發工作，WPF 提供資料繫結引擎以自動執行這些步驟。 資料繫結引擎的核心單位是 <xref:System.Windows.Data.Binding> 類別，其工作是將控制項 (繫結目標) 繫結至資料物件 (繫結來源)。 下圖說明這個關聯性。  
  
   ![基本資料繫結圖](../designers/media/databindingmostbasic.png "DataBindingMostBasic")  
  
   下列範例示範如何將 <xref:System.Windows.Controls.TextBox> 繫結至自訂 `Person` 物件的執行個體。 `Person` 實作則如下列程式碼所示。  
  
   [!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/Person.cs#personclasscode)]
   [!code-vb[SimpleDataBindingSnippets#PersonClassCODE](../snippets/visualbasic/VS_Snippets_Wpf/SimpleDataBindingSnippets/VisualBasic/Person.vb#personclasscode)]  
  
   下列標記會將 <xref:System.Windows.Controls.TextBox> 繫結至自訂 `Person` 物件的執行個體。  
  
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP1](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup1)]  
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP2](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup2)]  
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP3](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup3)]  
  
   [!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml.cs#databindingcodebehind)]
   [!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/SimpleDataBindingSnippets/VisualBasic/DataBindingWindow.xaml.vb#databindingcodebehind)]  
  
   在這個範例中， `Person` 類別會在程式碼後置中具現化，並已設定為 `DataBindingWindow`的資料內容。 在標記中， <xref:System.Windows.Controls.TextBox.Text%2A> 的 <xref:System.Windows.Controls.TextBox> 屬性已繫結至 `Person.Name` 屬性 (使用"`{Binding ... }`" XAML 語法)。 這個 XAML 會指示 WPF 將 <xref:System.Windows.Controls.TextBox> 控制項繫結至儲存在視窗之 `Person` 屬性中的 <xref:System.Windows.FrameworkElement.DataContext%2A> 物件。  
  
   WPF 資料繫結引擎還提供其他支援，包括驗證、排序、篩選和群組。 此外，資料繫結可在標準 WPF 控制項所顯示的使用者介面不適用時，使用資料範本來建立繫結資料的自訂使用者介面。  
  
   如需詳細資訊，請參閱 [資料繫結概觀](https://msdn.microsoft.com/library/ms752347\(v=vs.100\).aspx)。  
  
## <a name="Graphics"></a> 圖形  
 WPF 引進了一組詳盡、可擴充且彈性的圖形功能，其優點如下：  
  
- **解析度獨立與裝置獨立圖形**。 WPF 圖形系統的基本測量單位是裝置獨立畫素，不論實際螢幕解析度為何，都是 1 英吋的 1/96，並會為解析度獨立與裝置獨立轉譯提供基礎。 每個裝置獨立畫素會依轉譯所在系統的 DPI (每英吋的點數) 設定來自動調整。  
  
- **改進精確度**。 WPF 座標系統是使用雙精確度浮點數進行測量，而不是單精確度。 轉換和透明度值也會以雙精確度來表示。 WPF 也支援廣色域 (scRGB)，並提供整合式支援，以管理來自不同色彩空間的輸入。  
  
- **進階圖形和動畫支援**： WPF 藉由為您管理動畫場景來簡化圖形程式設計；您不需要擔心場景處理、轉譯迴圈和雙線性插補。 此外，WPF 還提供叫用測試支援和完整的 alpha 複合支援。  
  
- **硬體加速**： WPF 圖形系統利用圖形硬體將 CPU 使用量降到最低。  
  
### <a name="2-d-shapes"></a>2D 圖案  
 WPF 提供以通用向量繪製之 2D 圖案的圖庫，例如下圖所示的矩形和橢圓形。  
  
 ![橢圓形和矩形](../designers/media/wpfintrofigure4.PNG "WPFIntroFigure4")  
  
 圖案有趣的一點是它不僅用於顯示，還可實作許多您預期控制項會有的功能，包括鍵盤和滑鼠輸入。 下列範例示範所要處理之 <xref:System.Windows.UIElement.MouseUp> 的 <xref:System.Windows.Shapes.Ellipse> 事件。  
  
 [!code-xml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/EllipseEventHandlingWindow.xaml#handleellipsemouseupeventmarkup)]  
  
 [!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/EllipseEventHandlingWindow.xaml.cs#handleellipsemouseupeventcodebehind)]
 [!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/EllipseEventHandlingWindow.xaml.vb#handleellipsemouseupeventcodebehind)]  
  
 下圖顯示上述程式碼所產生的結果。  
  
 ![包含 "you clicked the ellipse&#33;" 文字的視窗](../designers/media/wpfintrofigure12.png "WPFIntroFigure12")  
  
 如需詳細資訊，請參閱 [WPF 中圖案和基本繪圖概觀](https://msdn.microsoft.com/library/ms747393\(v=vs.100\).aspx)。  
  
### <a name="2-d-geometries"></a>2D 幾何  
 WPF 提供的 2D 圖案涵蓋一組標準的基本圖案。 不過，您可能需要建立自訂圖案，來實現自訂使用者介面的設計。 為了達成這個目的，WPF 提供了幾何。 下圖示範如何使用幾何來建立自訂圖案，您可以直接繪製、當做筆刷來使用，或是用來裁剪其他圖案和控制項。  
  
 <xref:System.Windows.Shapes.Path> 物件可用來繪製封閉或開放的圖案、多個圖案，甚至是彎曲的圖案。  
  
 <xref:System.Windows.Media.Geometry> 物件可用來裁剪、叫用測試及轉譯 2D 圖形資料。  
  
 ![Path 的各種用法](../designers/media/wpfintrofigure5.PNG "WPFIntroFigure5")  
  
 如需詳細資訊，請參閱 [幾何概觀](https://msdn.microsoft.com/library/ms751808\(v=vs.100\).aspx)。  
  
### <a name="2-d-effects"></a>2D 效果  
 WPF 2D 功能子集包含漸層、點陣圖、繪圖、利用視訊繪製、旋轉、縮放和傾斜等視覺效果。 這些全部可用筆刷來完成；下圖顯示一些範例。  
  
 ![不同筆刷的圖例](../designers/media/wpfintrofigure6.PNG "WPFIntroFigure6")  
  
 如需詳細資訊，請參閱 [WPF 筆刷概觀](https://msdn.microsoft.com/library/aa970904\(v=vs.100\).aspx)。  
  
### <a name="3-d-rendering"></a>3D 轉譯  
 WPF 也包含可與 2D 圖形互動的 3D 轉譯功能，以便建立更生動有趣的使用者介面。 例如，下圖顯示轉譯成 3D 圖案的 2D 影像。  
  
 ![Visual3D 範例螢幕擷取畫面](../designers/media/wpfintrofigure13.png "WPFIntroFigure13")  
  
 如需詳細資訊，請參閱 [3D 圖形診斷](https://msdn.microsoft.com/library/ms747437\(v=vs.100\).aspx)。  
  
## <a name="Animation"></a> 動畫  
 WPF 動畫支援可讓您將控制項設為放大、搖晃、旋轉和淡出，以建立有趣的網頁切換及執行其他工作。 您可以建立大多數 WPF 類別的動畫，甚至是自訂類別。 下圖顯示執行中的簡單動畫。  
  
 ![動畫效果立方體的影像](../designers/media/wpfintrofigure7.png "WPFIntroFigure7")  
  
 如需詳細資訊，請參閱 [動畫概觀](https://msdn.microsoft.com/library/ms752312\(v=vs.100\).aspx)。  
  
## <a name="Media"></a> 媒體  
 傳達豐富內容的一個方式是透過視聽媒體。 WPF 提供對影像、視訊和音訊的特殊支援。  
  
### <a name="images"></a>影像  
 影像是大多數應用程式的共通功能，WPF 提供數種方式來使用影像。 下圖顯示具有包含縮圖影像之清單方塊的使用者介面。 選取縮圖時，會顯示完整大小的影像。  
  
 ![縮圖影像與完整大小影像](../designers/media/wpfintrofigure8.PNG "WPFIntroFigure8")  
  
 如需詳細資訊，請參閱 [影像處理概觀](https://msdn.microsoft.com/library/ms748873\(v=vs.100\).aspx)。  
  
### <a name="video-and-audio"></a>視訊和音訊  
 <xref:System.Windows.Controls.MediaElement> 控制項可播放視訊和音訊，而且有足夠的彈性可做為自訂媒體播放程式的基礎。 下列 XAML 標記實作一個媒體播放程式。  
  
 [!code-xml[IntroToWPFSnippets#MediaElementMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/MediaElementWindow.xaml#mediaelementmarkup)]  
  
 下圖中的視窗顯示執行中的 <xref:System.Windows.Controls.MediaElement> 控制項。  
  
 ![具有音訊與視訊的 MediaElement 控制項](../designers/media/wpfintrofigure1.png "WPFIntroFigure1")  
  
 如需詳細資訊，請參閱 [WPF 圖形、動畫和媒體概觀](https://msdn.microsoft.com/library/ms742562\(v=vs.100\).aspx)。  
  
## <a name="Text_and_Typography"></a> 文字和印刷樣式  
 為了達成高品質文字轉譯，WPF 提供下列功能：  
  
- OpenType 字型支援。  
  
- ClearType 增強功能。  
  
- 利用硬體加速的高效能。  
  
- 將文字與媒體、圖形和動畫進行整合。  
  
- 國際字型支援和後援機制。  
  
  為了示範文字與圖形的整合，下圖顯示文字裝飾的應用。  
  
  ![帶有各種文字裝飾的文字](../designers/media/wpfintrofigure23.png "WPFIntroFigure23")  
  
  如需詳細資訊，請參閱 [Windows Presentation Foundation 中的印刷樣式](https://msdn.microsoft.com/library/ms742190\(v=vs.100\).aspx)。  
  
## <a name="WPF_Customization"></a> 自訂 WPF 應用程式  
 到目前為止，您已經認識用於開發應用程式的核心 WPF 建置組塊。 您可以使用應用程式模型，來裝載及傳遞主要由控制項所組成的應用程式內容。 為了簡化使用者介面中的控制項排列方式，並確保不論視窗大小和顯示設定如何變更，都能維持此排列方式，您可以使用 WPF 版面配置系統。 由於大多數應用程式可讓使用者與資料互動，因此您可以使用資料繫結來減少使用者介面與資料整合的工作。 若要改進應用程式的視覺外觀，您可以使用的 WPF 所提供的各種圖形、動畫和媒體支援。  
  
 不過，這些基本功能通常並不足以建立及管理與眾不同且具有豐富視覺效果的使用者介面。 標準 WPF 控制項可能未與應用程式所需的外觀進行整合。 資料可能不會以最有效的方式來顯示。 Windows 佈景主題的預設外觀和風格可能不適合您應用程式的整體使用者介面。 在許多方面，呈現技術除了擴充其他任何類型的功能之外，也需要擴充視覺化功能。  
  
 因此，WPF 會提供各種不同的機制來建立唯一的使用者介面，包括控制項、觸發程序、控制項和資料範本、樣式、使用者介面資源，以及佈景主題和面板的豐富內容模型。  
  
### <a name="content-model"></a>內容模型  
 大多數 WPF 控制項的主要用途在於顯示內容。 在 WPF 中，可構成控制項內容的項目類型和數目，稱為控制項的 *「內容模型」*(Content Model)。 有些控制項可能包含單一內容類型的單一項目；例如， <xref:System.Windows.Controls.TextBox> 的內容是指派給 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性的字串值。 下列範例會設定 <xref:System.Windows.Controls.TextBox>的內容。  
  
 [!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup1)]  
[!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup2)]  
[!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup3)]  
  
 其結果如下圖所示。  
  
 ![包含文字的 TextBox 控制項](../designers/media/wpfintrofigure21.png "WPFIntroFigure21")  
  
 不過，其他控制項可能包含不同內容類型的多個項目； <xref:System.Windows.Controls.Button>屬性所指定的 <xref:System.Windows.Controls.ContentControl.Content%2A> 內容可包含各種項目，包括版面配置控制項、文字、影像和圖案。 下列範例示範具有內含 <xref:System.Windows.Controls.Button> 、 <xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.Label>和 <xref:System.Windows.Controls.Border>之內容的 <xref:System.Windows.Controls.MediaElement>。  
  
 [!code-xml[IntroToWPFSnippets#ButtonContentMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup1)]  
[!code-xml[IntroToWPFSnippets#ButtonContentMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup2)]  
[!code-xml[IntroToWPFSnippets#ButtonContentMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup3)]  
  
 下圖顯示這個按鈕的內容。  
  
 ![包含多種類型內容的按鈕](../designers/media/wpfintrofigure22.png "WPFIntroFigure22")  
  
 如需各種控制項所支援之內容類型的詳細資訊，請參閱 [WPF 內容模型](https://msdn.microsoft.com/library/bb613548\(v=vs.100\).aspx)。  
  
### <a name="triggers"></a>觸發程序  
 雖然 XAML 標記的主要目的是要實作應用程式的外觀，您也可以使用 XAML 來實作某些方面的應用程式行為。 其中一個範例是使用觸發程序，根據使用者互動來變更應用程式的外觀。 如需詳細資訊，請參閱 [設定樣式和範本](https://msdn.microsoft.com/library/ms745683\(v=vs.100\).aspx)。  
  
### <a name="control-templates"></a>控制項範本  
 WPF 控制項的預設使用者介面通常是從其他控制項和圖案建構而來。 例如， <xref:System.Windows.Controls.Button> 是由 <xref:Microsoft.Windows.Themes.ButtonChrome> 和 <xref:System.Windows.Controls.ContentPresenter> 控制項所組成。 <xref:Microsoft.Windows.Themes.ButtonChrome> 提供標準按鈕外觀，而 <xref:System.Windows.Controls.ContentPresenter> 則顯示 <xref:System.Windows.Controls.ContentControl.Content%2A> 屬性所指定的按鈕內容。  
  
 有時候，控制項的預設外觀可能與應用程式的整體外觀不搭。 在這種情況下，您可以使用 <xref:System.Windows.Controls.ControlTemplate> 變更控制項使用者介面的外觀，而不需要變更其內容和行為。  
  
 例如，下列範例示範如何使用 <xref:System.Windows.Controls.Button> 來變更 <xref:System.Windows.Controls.ControlTemplate>的外觀。  
  
 [!code-xml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ControlTemplateButtonWindow.xaml#buttoncontroltemplatewindowmarkup)]  
  
 [!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ControlTemplateButtonWindow.xaml.cs#buttoncontroltemplatewindowcodebehind)]
 [!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/ControlTemplateButtonWindow.xaml.vb#buttoncontroltemplatewindowcodebehind)]  
  
 在這個範例中，預設按鈕的使用者介面已取代成具有深藍色框線的 <xref:System.Windows.Shapes.Ellipse> ，並使用 <xref:System.Windows.Media.RadialGradientBrush>填滿。 <xref:System.Windows.Controls.ContentPresenter> 控制項會顯示 <xref:System.Windows.Controls.Button>的內容："Click Me!" 按下 <xref:System.Windows.Controls.Button> 之後，仍會引發 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件做為 <xref:System.Windows.Controls.Button> 控制項預設行為的一部分。 其結果如下圖所示。  
  
 ![橢圓形按鈕和第二個視窗](../designers/media/wpfintrofigure2.png "WPFIntroFigure2")  
  
### <a name="data-templates"></a>資料範本  
 控制項範本可讓您指定控制項的外觀，而資料範本則可讓您指定控制項內容的外觀。 資料範本通常可用來增強繫結資料的顯示方式。 下圖顯示繫結至 <xref:System.Windows.Controls.ListBox> 物件集合之 `Task` 的預設外觀，其中每項工作都有名稱、描述和優先權。  
  
 ![具有預設外觀的清單方塊](../designers/media/wpfintrofigure18.png "WPFIntroFigure18")  
  
 預設外觀是您可預期的 <xref:System.Windows.Controls.ListBox>外觀。 不過，每項工作的預設外觀只包含工作名稱。 若要顯示工作名稱、描述和優先權，則必須使用 <xref:System.Windows.Controls.ListBox> 變更 <xref:System.Windows.DataTemplate>控制項之繫結清單項目的預設外觀。 下列 XAML 會定義此 <xref:System.Windows.DataTemplate>，您可以使用 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 屬性將其套用至每項工作。  
  
 [!code-xml[IntroToWPFSnippets#DataTemplateMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup1)]  
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup2)]  
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup3)]  
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP4](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup4)]  
  
 下圖顯示這段程式碼的效果。  
  
 ![使用資料範本的清單方塊](../designers/media/wpfintrofigure19.png "WPFIntroFigure19")  
  
 請注意， <xref:System.Windows.Controls.ListBox> 已保留其行為和整體外觀，只會變更清單方塊所要顯示的內容外觀。  
  
 如需詳細資訊，請參閱 [資料範本化概觀](https://msdn.microsoft.com/library/ms742521\(v=vs.100\).aspx)。  
  
### <a name="styles"></a>樣式  
 樣式可讓開發人員和設計人員標準化其產品的特定外觀。 WPF 提供強式樣式模型，其中的基礎就是 <xref:System.Windows.Style> 項目。 下列範例會建立一個樣式，以將視窗上每一個 <xref:System.Windows.Controls.Button> 的背景色彩設定為 `Orange`。  
  
 [!code-xml[IntroToWPFSnippets#StyleMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup1)]  
[!code-xml[IntroToWPFSnippets#StyleMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup2)]  
[!code-xml[IntroToWPFSnippets#StyleMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup3)]  
[!code-xml[IntroToWPFSnippets#StyleMARKUP4](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup4)]  
  
 由於這種樣式是以所有 <xref:System.Windows.Controls.Button> 控制項為目標，系統會將該樣式自動套用至視窗中的所有按鈕，如下圖所示。  
  
 ![兩個橙色按鈕](../designers/media/wpfintrofigure20.png "WPFIntroFigure20")  
  
 如需詳細資訊，請參閱 [設定樣式和範本](https://msdn.microsoft.com/library/ms745683\(v=vs.100\).aspx)。  
  
### <a name="resources"></a>資源  
 應用程式中的控制項應該共用相同的外觀，可包含從字型和背景色彩，到控制項範本、資料範本和樣式的任何項目。 您可以使用 WPF 對使用者介面資源的支援，將這些資源封裝到單一位置以重複使用。  
  
 下列範例會定義 <xref:System.Windows.Controls.Button> 和 <xref:System.Windows.Controls.Label>共用的一般背景色彩。  
  
 [!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup1)]  
[!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup2)]  
[!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup3)]  
  
 這個範例使用 `Window.Resources` 屬性項目來實作背景色彩資源。 這項資源可供 <xref:System.Windows.Window>的所有子系使用。 以下依其解析順序列出各種資源範圍，包括：  
  
1. 個別控制項 (使用繼承的 <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> 屬性)。  
  
2. <xref:System.Windows.Window> 或 <xref:System.Windows.Controls.Page> (也使用繼承的 <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> 屬性)。  
  
3. <xref:System.Windows.Application> (使用 <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> 屬性)。  
  
   上述各種範圍可讓您彈性地定義及共用資源。  
  
   除了直接建立資源與特定範圍的關聯之外，您還可以使用個別 <xref:System.Windows.ResourceDictionary> 封裝一或多項資源，以做為應用程式的其他組件來參考。 例如，下列範例會定義資源字典中的預設背景色彩。  
  
   [!code-xml[IntroToWPFSnippets#ResourceDictionaryMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/BackgroundColorResources.xaml#resourcedictionarymarkup1)]  
   [!code-xml[IntroToWPFSnippets#ResourceDictionaryMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/BackgroundColorResources.xaml#resourcedictionarymarkup2)]  
  
   下列範例會參考上述範例中定義的資源字典，以便在應用程式內部共用。  
  
   [!code-xml[IntroToWPFSnippets#ApplicationScopedResourceDictionaryMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/App.xaml#applicationscopedresourcedictionarymarkup1)]  
   [!code-xml[IntroToWPFSnippets#ApplicationScopedResourceDictionaryMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/App.xaml#applicationscopedresourcedictionarymarkup2)]  
  
   資源與資源字典是 WPF 支援佈景主題和面板的基礎。  
  
   如需詳細資訊，請參閱 [資源概觀](https://msdn.microsoft.com/library/ms750613\(v=vs.100\).aspx)。  
  
### <a name="custom-controls"></a>自訂控制項  
 雖然 WPF 提供許多自訂支援，但是您可能還是會遇到現有 WPF 控制項不符合應用程式或其使用者需求的情況。 這種情況的發生原因包括：  
  
- 您無法藉由自訂現有 WPF 實作的外觀和風格，來建立所需的使用者介面。  
  
- 現有 WPF 實作不支援 (或無法輕易支援) 您需要的行為。  
  
  不過在這種情況下，您可以利用三種 WPF 模型之一來建立新的控制項。 每個模型各有適用的特定情況，並要求您的自訂控制項衍生自特定 WPF 基底類別。 以下列出這三種模型：  
  
- **使用者控制項模型**： 自訂控制項衍生自 <xref:System.Windows.Controls.UserControl> ，並由一或多個其他控制項所組成。  
  
- **控制項模型**： 自訂控制項衍生自 <xref:System.Windows.Controls.Control> ，並使用範本來建置實作以區隔其行為和外觀，與大多數 WPF 控制項非常類似。 衍生自 <xref:System.Windows.Controls.Control> 比使用者控制項更能夠讓您自由地建立自訂使用者介面，但可能需要投入更多時間。  
  
- **架構項目模型**： 如果其外觀是由自訂轉譯邏輯 (而不是範本) 所定義，自訂控制項衍生自 <xref:System.Windows.FrameworkElement> 。  
  
  下列範例示範衍生自 <xref:System.Windows.Controls.UserControl>的自訂數值上下按鈕控制項。  
  
  [!code-xml[IntroToWPFSnippets#UserControlMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml#usercontrolmarkup)]  
  
  [!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml.cs#usercontrolcodebehind1)]
  [!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/NumericUpDown.xaml.vb#usercontrolcodebehind1)]  
  [!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml.cs#usercontrolcodebehind2)]
  [!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND2](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/NumericUpDown.xaml.vb#usercontrolcodebehind2)]  

 下一個範例說明將使用者控制項併入 <xref:System.Windows.Window>所需的 XAML。  
  
 [!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup1)]  
[!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup2)]  
[!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup3)]  
  
 下圖顯示 `NumericUpDown` 中所裝載的 <xref:System.Windows.Window>控制項。  
  
 ![自訂使用者控制項](../designers/media/wpfintrofigure3.png "WPFIntroFigure3")  
  
 如需自訂控制項的詳細資訊，請參閱 [控制項撰寫概觀](https://msdn.microsoft.com/library/ms745025\(v=vs.100\).aspx)。  
  
## <a name="WPF_Best_Practices"></a> WPF 最佳作法  
 如同任何開發平台，您可以透過各種方式來使用 WPF，以取得想要的結果。 為了確保您的 WPF 應用程式提供所需的使用者體驗，並符合一般大眾的需求，已針對協助工具、全球化和當地語系化，以及效能提供了建議的最佳作法。 如需詳細資訊，請參閱下列主題：  
  
- [協助工具最佳作法](https://msdn.microsoft.com/library/aa350483\(v=vs.100\).aspx)協助工具最佳作法  
  
- [WPF 全球化和當地語系化概觀](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx)  
  
- [最佳化 WPF 應用程式效能](https://msdn.microsoft.com/library/aa970683\(v=vs.100\).aspx)  
  
- [Windows Presentation Foundation 安全性](https://msdn.microsoft.com/library/aa970906\(v=vs.100\).aspx)  
  
## <a name="Summary"></a> 總結  
 WPF 是功能齊全的呈現技術，可建置具有豐富視覺效果的各種用戶端應用程式。 本簡介提供 WPF 的主要功能一覽。  
  
 下一個步驟是建置 WPF 應用程式！  
  
 當您建置應用程式時，您可以回顧本簡介，以複習主要功能，並找到針對本簡介所涵蓋之功能更詳細解說的資源。  
  
## <a name="see-also"></a>另請參閱  
 [WPF 使用者入門](../designers/getting-started-with-wpf.md)   
 [使用 Windows Presentation Foundation 建立新式桌面應用程式](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)   
 [Windows Presentation Foundation](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx)
