---
redirect_url: /azure/app-service-mobile/app-service-mobile-windows-store-dotnet-get-started
title: "逐步解說：建立連接至 Azure 行動服務的 WPF 桌面應用程式 | Microsoft Docs"
ms.custom: 
ms.date: 10/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d42620f-553b-4b04-a38b-f6b306d73a50
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- csharp
- vb
ms.workload: azure
ms.openlocfilehash: f3fd548234dbd7f02be4abfab77a22d3efd9b34a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service"></a>逐步解說：建立連接至 Azure 行動服務的 WPF 桌面應用程式
您可以使用 Windows Presentation Foundation (WPF) 快速建立現代桌面應用程式，以使用 Azure 行動服務來儲存與提供資料。  
  
## <a name="prerequisites"></a>必要條件  
您需要下列項目才能完成本逐步解說：  
  
-   Visual Studio 2017 或支援 WPF 開發的任何版本。  
  
-   使用中的 Microsoft Azure 帳戶。  
  
    -   您可以在 [這裡](http://azure.microsoft.com/en-us/pricing/free-trial/)註冊免費試用帳戶。  
  
    -   您可以啟動 [MSDN 訂閱者權益](https://azure.microsoft.com/en-us/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F)。 MSDN 訂閱可每月提供信用額度，讓您使用付費型 Azure 服務。  
  
## <a name="create-a-project-and-add-references"></a>建立專案並加入參考  
 第一個步驟是建立 WPF 專案，並加入可讓您連接到 Azure 行動服務的 NuGet 封裝。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
1.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
2.  在 [新增專案] 對話方塊中，展開 [Visual C#] 或 [Visual Basic] 節點，然後選擇 [Windows 傳統桌面] 節點。  
  
3.  在範本清單中，選擇 [WPF 應用程式] (.NET Framework) 範本。  
  
4.  在 [新增專案]  文字方塊中，輸入 `WPFQuickStart`，然後選擇 [確定]  按鈕。  
  
     隨即建立專案，並將專案檔新增至方案總管。 名為 **MainWindow.xaml** 之預設應用程式視窗的設計工具隨即顯示。  
  
#### <a name="to-add-a-reference-to-the-windows-azure-mobile-services-sdk"></a>若要加入 Windows Azure Mobile Services SDK 的參考  
  
1.  在方案總管中，開啟 [參考] 節點的捷徑功能表，然後選擇 [管理 NuGet 套件]。  
  
2.  在 [NuGet 套件管理員] 中，選擇接近頂端的 [瀏覽]，然後在搜尋方塊中輸入 `mobileservices`。  
  
3.  在左窗格中選擇 **WindowsAzure.MobileServices**，然後在右窗格中選擇 [安裝]  按鈕。  
  
    > [!NOTE]
    >  如果出現 [預覽]  對話方塊，請檢閱建議的變更，然後選擇 [確定]  按鈕。  
  
4.  在 [接受授權]  對話方塊中，檢閱授權條款並選擇 [我接受]  按鈕以接受條款。  
  
     必要的參考即會加入 **方案總管**。  
  
    > [!NOTE]
    >  如果您不同意授權條款，請選擇 [我拒絕] 按鈕。 這樣一來，您將無法完成此逐步解說的其餘部分。  
  
## <a name="create-the-user-interface"></a>建立使用者介面  
下一步是建立應用程式的使用者介面。 首先您要建立可重複使用的使用者控制項，其會顯示兩個窗格並排的標準版面配置。 您要將使用者控制項新增至主應用程式視窗，並新增控制項以輸入和顯示資料，然後撰寫程式碼來定義與行動服務後端的互動。  
  
#### <a name="to-add-a-user-control"></a>若要加入使用者控制項  
  
1.  在 **方案總管**中，開啟 [WPFQuickStart]  節點的捷徑功能表，然後依序選擇 [加入] 和 [新增資料夾] 。  
  
2.  將資料夾命名為 `Common`註冊免費試用帳戶。  
  
3.  開啟 [Common]  資料夾的捷徑功能表，然後依序選擇 [加入] 和 [使用者控制項] 。  
  
4.  在 [新增專案]  對話方塊中，選擇 [名稱] 欄位並輸入 `QuickStartTask`，然後選擇 [確定]  按鈕。  
  
     隨即將使用者控制項加入專案，並會在設計工具中開啟 **QuickStartTask.xaml** 檔案。  
  
5.  在設計工具下方窗格中選取 `<Grid>` 和 `</Grid>` 標記，並將它們取代成下列 XAML 程式碼：  
  
    ```xaml  
    <Grid VerticalAlignment="Top">
        <StackPanel Orientation="Horizontal">
            <Border BorderThickness="0,0,1,0" BorderBrush="DarkGray" Margin="0,10" MinWidth="70">
                <TextBlock Text="{Binding Number}" FontSize="45" Foreground="DarkGray" Margin="20,0"/>
            </Border>
            <StackPanel>
                <TextBlock Text="{Binding Title}" Margin="10,10,0,0" FontSize="16" FontWeight="Bold" />
                <TextBlock Text="{Binding Description}" Margin="10,0,0,0" TextWrapping="Wrap" MaxWidth="500" />
            </StackPanel>
        </StackPanel>
    </Grid>  
    ```  
  
     這個 XAML 程式碼會建立可重複使用的版面配置，其中含有數字、標題和描述欄位的預留位置。 在執行階段時，可將預留位置取代為文字，如下圖所示。  
  
     ![QuickStartTask 使用者控制項](../designers/media/wpfquickstart1.PNG "WPFQuickStart1")  
  
6.  在 **方案總管**中，展開 [QuickStartTask.xaml]  節點並開啟 **QuickStartTask.xaml.cs** 或 **QuickStartTask.xaml.vb** 檔案。  
  
7.  在程式碼編輯器中，將 `namespace WPFQuickStart.Common` (C#) 命名空間或 `Public Class QuickStartTask` (VB) 方法取代為下面程式碼：  
  
    ```csharp  
    namespace WPFQuickStart.Common  
    {  
        /// <summary>  
        /// Interaction logic for QuickStartTask.xaml  
        /// </summary>  
        public partial class QuickStartTask : UserControl  
        {  
            public QuickStartTask()  
            {  
                this.InitializeComponent();  
                this.DataContext = this;  
            }  
  
            public int Number  
            {  
                get { return (int)GetValue(NumberProperty); }  
                set { SetValue(NumberProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty NumberProperty =  
                DependencyProperty.Register("Number", typeof(int), typeof(QuickStartTask), new PropertyMetadata(0));  
  
            public string Title  
            {  
                get { return (string)GetValue(TitleProperty); }  
                set { SetValue(TitleProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty TitleProperty =  
                DependencyProperty.Register("Title", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));  
  
            public string Description  
            {  
                get { return (string)GetValue(DescriptionProperty); }  
                set { SetValue(DescriptionProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty DescriptionProperty =  
                DependencyProperty.Register("Description", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));  
        }  
    }  
    ```  
  
    ```vb  
    Partial Public Class QuickStartTask  
            Inherits UserControl  
  
            Public Sub New()  
                Me.InitializeComponent()  
                Me.DataContext = Me  
            End Sub  
  
            Public Property Number() As Integer  
                Get  
                    Return CInt(Fix(GetValue(NumberProperty)))  
                End Get  
                Set(ByVal value As Integer)  
                    SetValue(NumberProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly NumberProperty As DependencyProperty = DependencyProperty.Register("Number", GetType(Integer), GetType(QuickStartTask), New PropertyMetadata(0))  
  
            Public Property Title() As String  
                Get  
                    Return CStr(GetValue(TitleProperty))  
                End Get  
                Set(ByVal value As String)  
                    SetValue(TitleProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly TitleProperty As DependencyProperty = DependencyProperty.Register("Title", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))  
  
            Public Property Description() As String  
                Get  
                    Return CStr(GetValue(DescriptionProperty))  
                End Get  
                Set(ByVal value As String)  
                    SetValue(DescriptionProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly DescriptionProperty As DependencyProperty = DependencyProperty.Register("Description", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))  
        End Class  
    ```  
  
     此程式碼會使用相依性屬性，在執行階段時設定數字、標題和描述欄位的值。  
  
8.  在功能表列上，依序選擇 [建置] 、[建置 WPFQuickStart]  以建置使用者控制項。  
  
#### <a name="to-create-and-modify-the-main-window"></a>若要建立及修改主視窗  
  
1.  在 **方案總管**中，開啟 **MainWindow.xaml** 檔。  
  
2.  **重要事項**： 這個步驟只適用於 C#。 如果您使用 Visual Basic，請跳至下一個步驟。 在設計工具下方窗格中，找到 `xmlns:local="clr-namespace:WPFQuickStart"` 行，並將它取代成下列 XAML 程式碼：  
  
    ```xaml  
    xmlns:local="clr-namespace:WPFQuickStart.Common"  
    ```  
  
3.  在 [新增專案]  視窗中，展開 [通用] **Common** 分類節點並選擇 [標題]  屬性，然後輸入 `WPF Todo List` 按下 **Enter** 鍵。  
  
     請注意，XAML 視窗中的 [標題]  元素會變更以符合新的值。 您可以在 XAML 視窗或 [屬性]  視窗中修改 XAML 屬性，變更會同步處理。  
  
4.  在 XAML 視窗中，將 [高度] 項目的值設為 `768`，將 [寬度] 屬性的值設為 `1280`。  
  
     對應到 [高度]  和 [寬度]  屬性的這些元素，可在 [屬性]  視窗的 [版面配置]  分類中找到。  
  
5.  選取 `<Grid>` 和 `</Grid>` 標記，並將它們取代成下列 XAML 程式碼：  
  
    ```xaml  
    <Grid>
        <Grid Margin="50,50,10,10">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="*" />
                <ColumnDefinition Width="*" />
            </Grid.ColumnDefinitions>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto" />
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Grid Grid.Row="0" Grid.ColumnSpan="2" Margin="0,0,0,20">
                <StackPanel>
                    <TextBlock Foreground="#0094ff" FontFamily="Segoe UI Light" Margin="0,0,0,6">MICROSOFT AZURE MOBILE SERVICES</TextBlock>
                    <TextBlock Foreground="Gray" FontFamily="Segoe UI Light" FontSize="45" ><Run Text="My Todo List"/></TextBlock>
                </StackPanel>
            </Grid>
            <Grid Grid.Row="1">
                <StackPanel>
                    <local:QuickStartTask Number="1" Title="Insert a TodoItem" Description="Enter some text below and click Save to insert a new todo item into the list." />
                    <StackPanel Orientation="Horizontal" Margin="72,0,0,0">
                        <TextBox x:Name="TodoInput" Margin="5" MinWidth="300"/>
                        <Button x:Name="ButtonSave" Click="ButtonSave_Click" Content="Save"/>
                    </StackPanel>
                </StackPanel>
            </Grid>
            <Grid Grid.Row="1" Grid.Column="1">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition />
                </Grid.RowDefinitions>
                <StackPanel>
                    <local:QuickStartTask Number="2" Title="Query and Update Data" Description="Click the Refresh button to load the unfinished TodoItems from the Azure Mobile Service. Select the checkbox to mark a ToDo item as complete and update the list." />
                    <Button Margin="72,0,0,0" Name="ButtonRefresh" Click="ButtonRefresh_Click">Refresh</Button>
                </StackPanel>
                <ListView Name="ListItems" Margin="62,10,0,0" Grid.Row="1">
                    <ListView.ItemTemplate>
                        <DataTemplate>
                            <StackPanel Orientation="Horizontal">
                                <CheckBox Name="CheckBoxComplete" IsChecked="{Binding Complete, Mode=TwoWay}" Checked="CheckBoxComplete_Checked" Content="{Binding Text}" Margin="10,5" VerticalAlignment="Center"/>
                            </StackPanel>
                        </DataTemplate>
                    </ListView.ItemTemplate>
                </ListView>
            </Grid>
        </Grid>
    </Grid>  
    ```  
  
     請注意，所做的變更會反映在 [設計] 視窗中。 同樣地，您也可以從 [工具箱]  視窗加入控制項，並在 [屬性]  視窗中設定屬性，以定義使用者介面。 任何可在設計工具中完成的項目，皆可在 XAML 程式碼中完成，反之亦然。  
  
     此時，您的設計看起來應該像下圖：  
  
     ![設計工具中的 MainWindow](../designers/media/wpfquickstart2.PNG "WPFQuickStart2")  
  
    > [!NOTE]
    >  遵循接下來的幾個程序時，您可能會在開啟的 [錯誤清單]  中看到一些錯誤。 別擔心，一旦完成其餘的程序後，這些錯誤就會消失。  
  
6.  在 **方案總管**中，展開 [MainWindow.xaml]  節點並開啟 **MainWindow.xaml.cs** 檔或 **MainWindow.xaml.vb** 檔。  
  
7.  在程式碼編輯器中，將 `using` 或 `Imports` 指示詞加入檔案的頂端：  
  
    ```csharp  
    using Microsoft.WindowsAzure.MobileServices;  
    using Newtonsoft.Json;   
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    Imports Newtonsoft.Json  
    ```  
  
8.  將 **WPFQuickStart** 命名空間 (C#) 或 **Class MainWindow** 類別 (VB) 中的全部程式碼取代為下列程式碼：  
  
    ```csharp  
    namespace WPFQuickStart  
    {  
        /// <summary>  
        /// Interaction logic for MainWindow.xaml  
        /// </summary>  
        public class TodoItem  
        {  
            public string Id { get; set; }  
  
            [JsonProperty(PropertyName = "text")]  
            public string Text { get; set; }  
  
            [JsonProperty(PropertyName = "complete")]  
            public bool Complete { get; set; }  
        }  
  
        public partial class MainWindow : Window  
        {  
            private MobileServiceCollection<TodoItem, TodoItem> items;  
            private IMobileServiceTable<TodoItem> todoTable = App.MobileService.GetTable<TodoItem>();  
  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            private async void InsertTodoItem(TodoItem todoItem)  
            {  
                // This code inserts a new TodoItem into the database. When the operation completes  
                // and Mobile Services has assigned an Id, the item is added to the CollectionView  
                await todoTable.InsertAsync(todoItem);  
                items.Add(todoItem);  
            }  
  
            private async void RefreshTodoItems()  
            {  
                try  
                {  
                    // This code refreshes the entries in the list view by querying the TodoItem table.  
                    // The query excludes completed TodoItems  
                    items = await todoTable  
                        .Where(todoItem => todoItem.Complete == false)  
                        .ToCollectionAsync();  
                    ListItems.ItemsSource = items;  
                }  
                catch (MobileServiceInvalidOperationException e)  
                {  
                    MessageBox.Show(e.Message, "Error loading items");  
                }  
            }  
  
            private async void UpdateCheckedTodoItem(TodoItem item)  
            {  
                // This code takes a freshly completed TodoItem and updates the database. When the MobileService   
                // responds, the item is removed from the list   
                await todoTable.UpdateAsync(item);  
                items.Remove(item);  
            }  
  
            private void ButtonRefresh_Click(object sender, RoutedEventArgs e)  
            {  
                RefreshTodoItems();  
            }  
  
            private void ButtonSave_Click(object sender, RoutedEventArgs e)  
            {  
                var todoItem = new TodoItem { Text = TodoInput.Text };  
                InsertTodoItem(todoItem);  
                TodoInput.Text = "";  
            }  
  
            private void CheckBoxComplete_Checked(object sender, RoutedEventArgs e)  
            {  
                CheckBox cb = (CheckBox)sender;  
                TodoItem item = cb.DataContext as TodoItem;  
                UpdateCheckedTodoItem(item);  
            }  
  
            protected override void OnActivated(EventArgs e)  
            {  
                RefreshTodoItems();  
            }  
        }  
  
    }  
    ```  
  
    ```vb  
    Public Class TodoItem  
        Public Property Id() As String  
  
        <JsonProperty(PropertyName:="text")>  
        Public Property Text() As String  
  
        <JsonProperty(PropertyName:="complete")>  
        Public Property Complete() As Boolean  
    End Class  
  
    Partial Public Class MainWindow  
        Inherits Window  
  
        Private items As MobileServiceCollection(Of TodoItem, TodoItem)  
        Private todoTable As IMobileServiceTable(Of TodoItem) = Application.MobileService.GetTable(Of TodoItem)()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        Private Async Sub InsertTodoItem(ByVal todoItem As TodoItem)  
            ' This code inserts a new TodoItem into the database. When the operation completes  
            ' and Mobile Services has assigned an Id, the item is added to the CollectionView  
            Await todoTable.InsertAsync(todoItem)  
            items.Add(todoItem)  
        End Sub  
  
        Private Async Sub RefreshTodoItems()  
            Dim exception As MobileServiceInvalidOperationException = Nothing  
            Try  
                ' This code refreshes the entries in the list view by querying the TodoItem table.  
                ' The query excludes completed TodoItems  
                items = Await todoTable.Where(Function(todoItem) todoItem.Complete = False).ToCollectionAsync()  
            Catch e As MobileServiceInvalidOperationException  
                exception = e  
            End Try  
  
            If exception IsNot Nothing Then  
                MessageBox.Show(exception.Message, "Error loading items")  
            Else  
                ListItems.ItemsSource = items  
            End If  
        End Sub  
  
        Private Async Sub UpdateCheckedTodoItem(ByVal item As TodoItem)  
            ' This code takes a freshly completed TodoItem and updates the database. When the MobileService   
            ' responds, the item is removed from the list   
            Await todoTable.UpdateAsync(item)  
            items.Remove(item)  
        End Sub  
  
        Private Sub ButtonRefresh_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            RefreshTodoItems()  
        End Sub  
  
        Private Sub ButtonSave_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            Dim todoItem = New TodoItem With {.Text = TodoInput.Text}  
            InsertTodoItem(todoItem)  
            TodoInput.Text = ""  
        End Sub  
  
        Private Sub CheckBoxComplete_Checked(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            Dim cb As CheckBox = DirectCast(sender, CheckBox)  
            Dim item As TodoItem = TryCast(cb.DataContext, TodoItem)  
            UpdateCheckedTodoItem(item)  
        End Sub  
  
        Protected Overrides Sub OnActivated(ByVal e As EventArgs)  
            RefreshTodoItems()  
        End Sub  
    End Class  
    ```  
  
     此程式碼會定義在使用非同步方法時，行動服務中使用者介面與資料庫之間的互動。  
  
## <a name="create-the-azure-mobile-service"></a>建立 Azure 行動服務  
 最後一個步驟是建立 Microsoft Azure 行動服務，並加入資料表以儲存資料，然後透過您的應用程式來參考服務執行個體。  
  
#### <a name="to-create-a-mobile-service"></a>若要建立行動服務  
  
1.  開啟網頁瀏覽器，並登入 Microsoft Azure 入口網站，然後選擇 [行動服務]  索引標籤。  
  
2.  選擇 [新增] 按鈕，然後在快顯對話方塊中依序選擇 [計算]、[行動服務]、[建立]。  
  
3.  在 [新的行動服務] 對話方塊中，選擇 [URL] 文字方塊並輸入 `wpfquickstart01`。  
  
    > [!NOTE]
    >  您可能需要變更 URL 的數字部分。 Microsoft Azure 要求每個行動服務皆具備唯一的 URL。  
  
    這會將服務的 URL 設為 *https://wpfquickstart01.azure-mobile.net/*。  
  
4.  在 [資料庫]  清單中，選擇資料庫選項。 由於這個應用程式應該不常使用，所以您可以選擇 [建立免費的 20MB SQL 資料庫] 選項，或選擇已與訂閱建立關聯的免費資料庫。  
  
5.  在 [區域]  清單中，選擇您要部署行動服務的資料中心，然後選擇 [下一步]  (向右箭號) 按鈕。  
  
    > [!NOTE]
    >  針對這項服務，您要使用預設 [後端]  設定與 [JavaScript] 。  
  
6.  如果您要建立新的資料庫，請在 [指定資料庫設定]  頁面上的 [伺服器]  清單中選擇 [新的 SQL 資料庫伺服器] ，輸入您的 **SQL 登入名稱** 和 **密碼**，然後選擇 [完成]  (勾選記號) 按鈕。  
  
7.  如果您選擇現有的資料庫，請在 [資料庫設定]  頁面上，輸入您的 **登入密碼** ，然後選擇 [完成]  (勾選記號) 按鈕。  
  
     建立行動服務的程序隨即開始。 程序完成時，狀態會變更為 [就緒]  ，您即可移至下一個步驟。  
  
8.  在入口網站中，選取新建立的行動服務，然後選擇 [管理金鑰]  按鈕。  
  
9. 在 [管理存取金鑰]  對話方塊中，複製 **應用程式金鑰**，  
  
     以便在下一個程序中使用。  
  
#### <a name="to-create-a-table"></a>若要建立資料表  
  
1.  在 Microsoft Azure 入口網站中，選擇行動服務名稱旁的向右箭號，並在功能表列上選擇 [資料] ，然後選擇 [加入資料表]  連結。  
  
2.  在 [新增專案]  對話方塊的 [資料表名稱]  文字方塊中，輸入 `TodoItem`，然後選擇 [確定] \(勾選記號) 按鈕。  
  
     等候資料表建立，即可移至最後的程序。  
  
#### <a name="to-add-a-declaration-for-the-mobile-service"></a>若要加入行動服務的宣告  
  
1.  返回 Visual Studio。 在 **方案總管**中，展開 [App.xaml]  (C#) 或 [Application.xaml]  (Visual Basic) 節點並開啟 **App.xaml.cs** 檔或 **App.xaml.vb** 檔。  
  
2.  在程式碼編輯器中，將 `using` 或 **Imports** 指示詞加入檔案的頂端：  
  
    ```csharp  
    using Microsoft.WindowsAzure.MobileServices;  
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    ```  
  
3.  在類別中加入下列宣告，再將 *YOUR-SERVICE_HERE* 取代為您服務的 URL 名稱，並將 *YOUR-KEY-HERE* 取代為您在上一個程序中複製的應用程式金鑰：  
  
    ```csharp  
    public static MobileServiceClient MobileService = new MobileServiceClient(  
                 "https://YOUR-SERVICE-HERE.azure-mobile.net/",  
                 "YOUR-KEY-HERE"  
             );  
    ```  
  
    ```vb  
    Public Shared MobileService As New MobileServiceClient("https://YOUR-SERVICE-HERE.azure-mobile.net/", "YOUR-KEY-HERE")  
    ```  
  
     此程式碼可讓應用程式存取 Microsoft Azure 上執行的行動服務。  
  
## <a name="test-the-application"></a>測試應用程式  
 這樣就行了 - 您已建立可存取 Azure 行動服務的 WPF 桌面應用程式。 現在只需執行應用程式並查看它的運作情況。  
  
#### <a name="to-run-the-application"></a>若要執行應用程式  
  
1.  在功能表列上，依序選擇 [偵錯] 和 [開始偵錯] (或按 **F5**)。  
  
2.  在 [新增專案]  文字方塊中輸入 `Do something`，然後選擇 [確定]  按鈕。  
  
3.  Enter `Do something else`，然後選擇 [確定]  按鈕。  
  
     請注意，[查詢及更新資料]  清單會加入兩個項目，如下圖所示。  
  
     ![待辦項目會加入清單。](../designers/media/wpfquickstart3.PNG "WPFQuickStart3")  
  
4.  選取清單中 **Do something else** 的項目核取方塊。  
  
     這會呼叫 **UpdateCheckedTodoItem** 方法並從清單和資料庫中移除項目。  
  
## <a name="next-steps"></a>後續步驟  
 您已經完成一個含 Azure 後端的 WPF 桌面應用程式範例，且相當簡單。 當然，實際應用程式很可能更複雜，但仍適用相同的基本概念。 請參閱 [.NET Framework 中的 WPF](https://msdn.microsoft.com/en-us/library/ms754130)。  
  
 您可以加入色彩、圖案、圖形甚至動畫，讓使用者介面更吸引人。 請參閱[在 Visual Studio 中使用 XAML 設計工具建立 UI](creating-a-ui-by-using-xaml-designer-in-visual-studio.md) 和[使用 Blend for Visual Studio 建立 UI](creating-a-ui-by-using-blend-for-visual-studio.md)。 如需工具之間的比較，請參閱[在 Visual Studio 和 Blend for Visual Studio 中設計 XAML](../designers/designing-xaml-in-visual-studio.md)。  

 您可以連接到現有的 SQL 資料庫或其他使用 Azure 行動服務的資料來源。 請參閱 [行動服務文件](http://azure.microsoft.com/en-us/services/app-service/mobile/)。  
  
## <a name="see-also"></a>請參閱  
 [逐步解說：我的第一個 WPF 桌面應用程式](../designers/walkthrough-my-first-wpf-desktop-application2.md)   
 [使用 Windows Presentation Foundation 建立新式桌面應用程式](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)