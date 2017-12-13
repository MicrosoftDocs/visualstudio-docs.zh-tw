---
title: "逐步解說：我的第一個 WPF 桌面應用程式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c460fa9-2ea1-413f-ae54-54a1f2a499d1
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- csharp
- vb
ms.openlocfilehash: fb4da07f2ee8d4c30717209ee07221285a8275ee
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2017
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>逐步解說：我的第一個 WPF 桌面應用程式
本逐步解說提供 Windows Presentation Foundation (WPF) 開發的簡介。 您會建立基本的應用程式，包含對大部分 WPF 桌面應用程式都通用的項目：XAML 標記、程式碼後置、應用程式定義、控制項、配置、資料繫結和樣式。  
  
## <a name="creating-the-application-project"></a>建立應用程式專案  
在本節中，您會建立應用程式基礎結構，包括專案及主視窗或表單。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
1.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
2.  在 [新增專案]  對話方塊中，展開 [Visual C#]  或 [Visual Basic]  節點，選擇 [Windows]  節點，然後展開 [Windows]  並選擇 [傳統桌面]  節點。  
  
3.  在範本清單中選擇 [WPF 應用程式]  範本。  
  
4.  在 [新增專案]  文字方塊中，輸入 `ExpenseIt`，然後選擇 [確定]  按鈕。  
  
     隨即建立專案並將專案檔案加入 **方案總管**，並顯示名為 **MainWindow.xaml** 的預設應用程式視窗的設計工具。  
  
#### <a name="to-modify-the-main-window"></a>修改主視窗  
  
1.  在設計工具中，如果 [MainWindow.xaml] 索引標籤還不是使用中的設計工具索引標籤，請選擇它。  
  
2.  如果使用 C#，請找到行 `<Window x:Class="ExpenseIt.MainWindow"`，並用 `<NavigationWindow x:Class="ExpenseIt.MainWindow"` 取代它。  
  
     如果使用 Visual Basic，請找到行 `<Window x:Class=" MainWindow"`，並用 `<NavigationWindow x:Class="MainWindow"` 取代它。  
  
     請注意，當您將 `<Window` 標記變更成 `<NavigationWindow`時，Intellisense 也會自動將結尾標記變更成 `</NavigationWindow>` 。  
  
    > [!NOTE]
    >  變更標記之後，如果 [錯誤清單]  視窗開啟，您可能會注意到數個錯誤。 別擔心，您在後面幾個步驟所做的變更會讓它們消失不見。  
  
3.  選擇並刪除 `<Grid>` 和 `</Grid>` 標記。  
  
     **NavigationWindow** 不能包含其他 UI 項目，例如 [格線]。  
  
4.  在 [新增專案]  視窗中，展開 [通用] **Common** 分類節點並選擇 [標題]  屬性，然後輸入 `ExpenseIt` 按下 **Enter** 鍵。  
  
     請注意，XAML 視窗中的 [標題]  元素會變更以符合新的值。 您可以在 XAML 視窗或 [屬性]  視窗中修改 XAML 屬性，變更會同步處理。  
  
5.  在 XAML 視窗中，將 [高度] 項目的值設為 `375`，將 [寬度] 屬性的值設為 `500`。  
  
     對應到 [高度]  和 [寬度]  屬性的這些項目，可在 [屬性]  視窗的 [配置]  分類中找到。  
  
     **MainWindow.xaml** 檔案現在在 C# 中看起來應該像這樣：  
  
    ```xaml  
    <NavigationWindow x:Class="ExpenseIt.MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500">    
    </NavigationWindow>  
    ```  
  
     或在 Visual Basic 中看起來像這樣：  
  
    ```xaml  
    <NavigationWindow x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500">    
    </NavigationWindow>  
    ```  
  
#### <a name="to-modify-the-code-behind-file-c"></a>修改程式碼後置的檔案 (C#)  
  
1.  在 **方案總管**中，展開 **MainWindow.xaml** 節點並開啟 **MainWindow.xaml.cs** 檔案。  
  
2.  找到行 `public partial class MainWindow : Window` ，並用 `public partial class MainWindow : NavigationWindow`取代它。  
  
     這會使 `MainWindow` 類別變成衍生自 `NavigationWindow`。 在 Visual Basic 中，當您變更 XAML 的視窗時這會自動發生，因此不必變更任何程式碼。  
  
## <a name="adding-files-to-the-application"></a>將檔案加入應用程式  
 在本節中，您要在應用程式中加入兩頁網頁和一個影像。  
  
#### <a name="to-add-a-home-screen"></a>加入主畫面  
  
1.  在 **方案總管**中，開啟 **ExpenseIt** 節點的捷徑功能表，然後依序選擇 [加入] 和 [頁面] 。  
  
2.  在 [新增專案]  對話方塊中，選擇 [名稱]  文字方塊並輸入 `ExpenseItHome`，然後選擇 [確定]  按鈕。  
  
     這個頁面是應用程式啟動時所顯示的第一個視窗。  
  
3.  在設計工具中，如果 [ExpenseItHome.xaml] 索引標籤還不是使用中的設計工具索引標籤，請選擇它。  
  
4.  選擇 `<Title>` 項目，並將標題變更為 **ExpenseIt - 首頁**。  
  
     **ExpenseItHome.xaml** 檔案現在在 C# 中看起來應該像這樣：  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home">    
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
    在 Visual Basic 中，第一行會略為不同：  
  
    ```xaml  
    <Page x:Class="ExpenseItHome"  
    ```  
  
5.  在設計工具中，選擇 [MainWindow.xaml]  索引標籤。  
  
6.  找到行 `Title="ExpenseIt" Height="375" Width="500">` 項目並加入 `Source="ExpenseItHome.xaml"` 屬性。  
  
     這會將 **ExpenseItHome.xaml** 設成應用程式啟動時開啟的第一個頁面。 **MainWindow.xaml** 檔案現在在 C# 中看起來應該像這樣：  
  
    ```xaml  
    <NavigationWindow x:Class="ExpenseIt.MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">    
    </NavigationWindow>  
    ```  
  
    在 Visual Basic 中，第一行會略為不同：  
  
    ```xaml  
    <NavigationWindow x:Class="MainWindow"
    ```  
  
     如同之前設定那些屬性一樣，您也可以在 [屬性] `Source`**視窗的 [其他]****分類中設定** 屬性。  
  
#### <a name="to-add-a-details-window"></a>加入詳細資料視窗  
  
1.  在 **方案總管**中，開啟 **ExpenseIt** 節點的捷徑功能表，然後依序選擇 [加入] 和 [頁面] 。  
  
2.  在 [新增專案]  對話方塊中，選擇 [名稱]  文字方塊並輸入 `ExpenseReportPage`，然後選擇 [確定]  按鈕。  
  
     這個視窗會顯示個別的費用報表。  
  
3.  在設計工具中，如果 [ExpenseReportPage.xaml] 索引標籤還不是使用中的設計工具索引標籤，請選擇它。  
  
4.  選擇 `<Title>` 項目，並將標題變更為 **ExpenseIt - 檢視費用**。  
  
     ExpenseReportPage.xaml 檔案現在在 C# 中看起來應該像這樣：  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseReportPage"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - View Expense">    
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
    在 Visual Basic 中，第一行會略為不同：  
  
    ```xaml  
    <Page x:Class="ExpenseReportPage"  
    ```  
  
5.  在功能表列上，選擇 [偵錯] 、[開始偵錯]\(或按 F5) 執行應用程式。  
  
     下圖顯示具有瀏覽視窗按鈕的應用程式。  
  
     ![ExpenseIt 範例螢幕擷取畫面](../designers/media/gettingstartedfigure1.png "GettingStartedFigure1")  
  
6.  關閉應用程式以返回設計模式。  
  
## <a name="creating-the-user-interface"></a>建立使用者介面  
 配置會按照順序放置項目，也會在重新調整表單大小時管理這些項目的大小和位置。 在本節中，您會建立具有三個資料列的單一資料行。 您要將控制項新增至兩頁頁面、新增一些程式碼，最後為控制項定義可重複使用的樣式。  
  
#### <a name="to-create-the-layout"></a>建立配置  
  
1.  開啟 **ExpenseItHome.xaml** 並選擇 `<Grid>` 項目。  
  
2.  在 [新增專案]  視窗中，展開 [通用]  分類節點，將 [邊界]  值設為 `10`、[新增] `10`、[新增] `0`、[新增] and `10`、[新增] which corresponds to left、[新增] right、[新增] top and bottom margins.  
  
     項目 `Margin="10,0,10,10"` 加入 XAML 的 `<Grid>` 項目。 同樣地，您可以直接在 XAML 程式碼中輸入這些值，不是在 [屬性]  視窗中，也會得到相同的結果。  
  
3.  在 `Grid` 項目中加入下列 XAML 程式碼，以建立資料列和資料行定義：  
  
    ```xaml  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition />  
        <RowDefinition Height="Auto"/>  
    </Grid.RowDefinitions>  
    ```  
  
#### <a name="to-add-controls"></a>加入控制項  
  
1.  開啟 **ExpenseItHome.xaml**。  
  
2.  在 `</Grid>` 標記的正上方新增下列 XAML 程式碼，以建立 `Border`、`ListBox` 和 `Button` 控制項：  
  
    ```xaml  
    <!-- People list -->  
      <Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">  
          <Label VerticalAlignment="Center" Foreground="White">Names</Label>  
      </Border>  
      <ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1">  
          <ListBoxItem>Mike</ListBoxItem>  
          <ListBoxItem>Lisa</ListBoxItem>  
          <ListBoxItem>John</ListBoxItem>  
          <ListBoxItem>Mary</ListBoxItem>  
      </ListBox>  
  
      <!-- View report button -->  
      <Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right">View</Button>    
    ```  
  
     請注意，控制項會出現在 [設計] 視窗中。 您也可以將控制項從 [工具箱]  視窗拖放至 [設計] 視窗，在 [屬性]  視窗中設定其屬性，以這種方式建立控制項。  
  
3.  建置並執行應用程式。 下圖顯示在 XAML 此程序所建立的控制項執行階段外觀。  
  
     ![ExpenseIt 範例螢幕擷取畫面](../designers/media/gettingstartedfigure2.png "GettingStartedFigure2")  
  
4.  關閉應用程式以返回設計模式。  
  
#### <a name="to-add-a-background-image"></a>加入背景影像  
  
1.  選擇下列影像並儲存為 `watermark.png`。  
  
     ![逐步解說的浮水印影像](../designers/media/wpf_watermark.png "WPF_watermark")  
  
    > [!NOTE]
    >  或者，您可以建立自己的影像並儲存為 `watermark.png`。  
  
2.  在 **方案總管**中，開啟 **ExpenseIt** 節點的捷徑功能表，然後依序選擇 [加入] 和 [現有項目] 。  
  
3.  在 [加入現有項目]  對話方塊中，找到剛剛加入的 **watermark.png** 影像，選擇它後再選擇 [加入]  按鈕。  
  
    > [!NOTE]
    >  您可能需要展開 [檔案類型]  清單並選擇 [影像檔] 。  
  
4.  開啟 **ExpenseItHome.xaml** 檔案，並在 `</Grid>` 標記的正上方加入下列 XAML 程式碼，建立背景影像：  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png"/>  
    </Grid.Background>    
    ```  
  
#### <a name="to-add-a-title"></a>加入標題  
  
1.  開啟 **ExpenseItHome.xaml**。  
  
2.  找到行 `<Grid.ColumnDefinitions>` 並在其下加入下列內容：  
  
    ```xaml  
    <ColumnDefinition Width="230" />    
    ```  
  
     這會在固定寬度為 230 個像素的其他資料行左邊建立額外的資料行。  
  
3.  找到行 `<Grid.RowDefinitions>` 並在其下加入下列內容：  
  
    ```xaml  
    <RowDefinition />    
    ```  
  
     這會在方格上方加入一個資料列。  
  
4.  將 `Grid.Column` 值設為 1，將控制項移至第二個資料行。 每個 `Grid.Row` 值加 1，將每個控制項向下移動一個資料列。  
  
    1.  找到行 `<Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">`。 將 `Grid.Column="0"` 變更為 `Grid.Column="1"` ，並將 `Grid.Row="0"` 變更為 `Grid.Row="1"`。  
  
    2.  找到行 `<ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1"`。 將 `Grid.Column="0"` 變更為 `Grid.Column="1"` ，並將 `Grid.Row="1"` 變更為 `Grid.Row="2"`。  
  
    3.  找到行 `<Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"`。 將 `Grid.Column="0"` 變更為 `Grid.Column="1"` ，並將 `Grid.Row="2"` 變更為 `Grid.Row="3"`。  
  
5.  在 `<Border` 項目前加入下列 XAML 程式碼以顯示標題：  
  
    ```xaml  
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
        View Expense Report  
    </Label>    
    ```  
  
     **ExpenseItHome.xaml** 的內容現在在 C# 中看起來應該像這樣：  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home">  
        <Grid Margin="10,0,10,10">  
            <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="230" />  
                <ColumnDefinition />  
            </Grid.ColumnDefinitions>  
            <Grid.RowDefinitions>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
            </Grid.RowDefinitions>  
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">  
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>  
            </Border>  
            <!-- People list -->  
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
                View Expense Report  
            </Label>  
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">  
                <ListBoxItem>Mike</ListBoxItem>  
                <ListBoxItem>Lisa</ListBoxItem>  
                <ListBoxItem>John</ListBoxItem>  
                <ListBoxItem>Mary</ListBoxItem>  
            </ListBox>  
  
            <!-- View report button -->  
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right">View</Button>  
            <Grid.Background>  
                <ImageBrush ImageSource="watermark.png"/>  
            </Grid.Background>  
        </Grid>  
    </Page>  
    ```  
  
    在 Visual Basic 中，第一行會略為不同：  
  
    ```xaml  
    <Page x:Class="ExpenseItHome"  
    ```  
  
6.  如在此時建置並執行應用程式，它看起來應該像下圖：  
  
     ![ExpenseIt 範例螢幕擷取畫面](../designers/media/gettingstartedfigure3.png "GettingStartedFigure3")  
  
#### <a name="to-add-code-to-the-button"></a>將程式碼加入按鈕  
  
1.  開啟 **ExpenseItHome.xaml**。  
  
2.  選擇 `Button` 項目，並在 `HorizontalAlignment="Right"` 項目正後方新增下列 XAML 程式碼：`Click="Button_Click"`。  
  
     這會為按鈕的 `Click` 事件新增事件處理常式。 **Button** 項目程式碼現在看起來應該像這樣：  
  
    ```xaml  
    <!-- View report button -->  
      <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right" Click="Button_Click">View</Button>  
    ```  
  
3.  開啟 **ExpenseItHome.xaml.cs** 或 **ExpenseItHome.xaml.vb** 檔案。  
  
4.  將下列程式碼加入 `ExpenseItHome` 類別：  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        // View Expense Report  
        ExpenseReportPage expenseReportPage = new ExpenseReportPage();  
        this.NavigationService.Navigate(expenseReportPage);    
    }  
    ```  
  
    ```vb  
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
        ' View Expense Report  
        Dim expenseReportPage As New ExpenseReportPage()  
    Me.NavigationService.Navigate(expenseReportPage)  
    End Sub  
    ```  
  
     按一下按鈕，這個事件處理常式就會開啟 [費用報表] 頁面。  
  
#### <a name="to-create-the-ui-for-the-report-page"></a>建立報表頁面的 UI  
  
1.  開啟 **ExpenseReportPage.xaml**。  
  
     這個頁面會顯示首頁上選取的人員費用報表。  
  
2.  在 `<Grid>` 和 `</Grid>` 標記之間加入下列 XAML 程式碼：  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png" />  
    </Grid.Background>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="230" />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto" />  
        <RowDefinition />  
    </Grid.RowDefinitions>  
  
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
    FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
        Expense Report For:  
    </Label>  
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">  
  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="Auto" />  
            <RowDefinition />  
        </Grid.RowDefinitions>  
  
        <!-- Name -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
            <Label Margin="0,0,0,5" FontWeight="Bold">Name:</Label>  
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>  
        </StackPanel>  
  
        <!-- Department -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">  
            <Label Margin="0,0,0,5" FontWeight="Bold">Department:</Label>  
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>  
        </StackPanel>  
  
        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"   
              HorizontalAlignment="Left">  
            <!-- Expense type and Amount table -->  
            <DataGrid  AutoGenerateColumns="False" RowHeaderWidth="0" >  
                <DataGrid.ColumnHeaderStyle>  
                    <Style TargetType="{x:Type DataGridColumnHeader}">  
                        <Setter Property="Height" Value="35" />  
                        <Setter Property="Padding" Value="5" />  
                        <Setter Property="Background" Value="#4E87D4" />  
                        <Setter Property="Foreground" Value="White" />  
                    </Style>  
                </DataGrid.ColumnHeaderStyle>  
                <DataGrid.Columns>  
                    <DataGridTextColumn Header="ExpenseType" />  
                    <DataGridTextColumn Header="Amount"  />  
                </DataGrid.Columns>  
            </DataGrid>  
        </Grid>  
    </Grid>  
    ```  
  
     這個 UI 類似為首頁建立的 UI，但以 **DataGrid** 控制項顯示報表資料。  
  
3.  建置並執行應用程式。  
  
4.  選擇 [檢視]  按鈕。  
  
     報表頁面隨即出現。  
  
     下圖顯示 [費用報表] 頁面。 請注意，已啟用向後巡覽按鈕。  
  
     ![ExpenseIt 範例螢幕擷取畫面](../designers/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
#### <a name="to-style-controls"></a>樣式控制項  
  
1.  開啟 **App.xaml** 檔案 (C#) 或 **Application.xaml** 檔案 (Visual Basic)。  
  
2.  在 `<Application.Resources>` 和 `</Application.Resources>` 標記之間加入下列 XAML：  
  
    ```xaml  
    <!-- Header text style -->  
    <Style x:Key="headerTextStyle">  
        <Setter Property="Label.VerticalAlignment" Value="Center"></Setter>  
        <Setter Property="Label.FontFamily" Value="Trebuchet MS"></Setter>  
        <Setter Property="Label.FontWeight" Value="Bold"></Setter>  
        <Setter Property="Label.FontSize" Value="18"></Setter>  
        <Setter Property="Label.Foreground" Value="#0066cc"></Setter>  
    </Style>  
  
    <!-- Label style -->  
    <Style x:Key="labelStyle" TargetType="{x:Type Label}">  
        <Setter Property="VerticalAlignment" Value="Top" />  
        <Setter Property="HorizontalAlignment" Value="Left" />  
        <Setter Property="FontWeight" Value="Bold" />  
        <Setter Property="Margin" Value="0,0,0,5" />  
    </Style>  
  
    <!-- DataGrid header style -->  
    <Style x:Key="columnHeaderStyle" TargetType="{x:Type DataGridColumnHeader}">  
        <Setter Property="Height" Value="35" />  
        <Setter Property="Padding" Value="5" />  
        <Setter Property="Background" Value="#4E87D4" />  
        <Setter Property="Foreground" Value="White" />  
    </Style>  
  
    <!-- List header style -->  
    <Style x:Key="listHeaderStyle" TargetType="{x:Type Border}">  
        <Setter Property="Height" Value="35" />  
        <Setter Property="Padding" Value="5" />  
        <Setter Property="Background" Value="#4E87D4" />  
    </Style>  
  
    <!-- List header text style -->  
    <Style x:Key="listHeaderTextStyle" TargetType="{x:Type Label}">  
        <Setter Property="Foreground" Value="White" />  
        <Setter Property="VerticalAlignment" Value="Center" />  
        <Setter Property="HorizontalAlignment" Value="Left" />  
    </Style>  
  
    <!-- Button style -->  
    <Style x:Key="buttonStyle" TargetType="{x:Type Button}">  
        <Setter Property="Width" Value="125" />  
        <Setter Property="Height" Value="25" />  
        <Setter Property="Margin" Value="0,10,0,0" />  
        <Setter Property="HorizontalAlignment" Value="Right" />  
    </Style>  
    ```  
  
     這個 XAML 會加入下列樣式：  
  
    -   `headerTextStyle`：格式化頁面標題 `Label`。  
  
    -   `labelStyle`：格式化 `Label` 控制項。  
  
    -   `columnHeaderStyle`：格式化 `DataGridColumnHeader`。  
  
    -   `listHeaderStyle`：格式化清單標頭 `Border` 控制項。  
  
    -   `listHeaderTextStyle`：格式化清單標頭 [標籤] 。  
  
    -   `buttonStyle`：格式化 `Button` ExpenseItHome.xaml **頁面上的** 。  
  
3.  開啟 **ExpenseItHome.xaml**，並以下列 XAML 取代 `<Grid>` 與 `</Grid>` 項目之間的所有內容：  
  
    ```xaml  
    <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="230" />  
                <ColumnDefinition />  
            </Grid.ColumnDefinitions>  
  
            <Grid.RowDefinitions>  
                <RowDefinition/>  
                <RowDefinition Height="Auto"/>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
            </Grid.RowDefinitions>  
            <Label Grid.Column="1" Style="{StaticResource headerTextStyle}" >  
                View Expense Report  
            </Label>  
            <!-- People list -->  
                  <Border Grid.Column="1" Grid.Row="1" Style="{StaticResource listHeaderStyle}">  
                <Label Style="{StaticResource listHeaderTextStyle}">Names</Label>  
            </Border>  
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">  
                <ListBoxItem>Mike</ListBoxItem>  
                <ListBoxItem>Lisa</ListBoxItem>  
                <ListBoxItem>John</ListBoxItem>  
                <ListBoxItem>Mary</ListBoxItem>  
            </ListBox>  
  
            <!-- View report button -->  
            <Button Grid.Column="1" Grid.Row="3" Click="Button_Click" Style="{StaticResource buttonStyle}">View</Button>  
            <Grid.Background>  
                <ImageBrush ImageSource="watermark.png"  />  
            </Grid.Background>  
    ```  
  
     套用樣式會移除並取代諸如 `VerticalAlignment` 和 `FontFamily` 這類會定義每個控制項外觀的屬性。  
  
4.  開啟 **ExpenseReportPage.xaml**，並以下列 XAML 取代 `<Grid>` 與最後一個 `</Grid>` 項目之間的所有內容：  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png" />  
    </Grid.Background>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="230" />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto" />  
        <RowDefinition />  
    </Grid.RowDefinitions>  
    <Label Grid.Column="1" Style="{StaticResource headerTextStyle}">  
        Expense Report For:  
    </Label>  
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="Auto" />  
            <RowDefinition />  
        </Grid.RowDefinitions>  
  
        <!-- Name -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
            <Label Style="{StaticResource labelStyle}">Name:</Label>  
            <Label Style="{StaticResource labelStyle}"></Label>  
        </StackPanel>  
  
        <!-- Department -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1"   
    Orientation="Horizontal">  
            <Label Style="{StaticResource labelStyle}">Department:</Label>  
            <Label Style="{StaticResource labelStyle}"></Label>  
        </StackPanel>  
  
        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"   
              HorizontalAlignment="Left">  
            <!-- Expense type and Amount table -->  
            <DataGrid ColumnHeaderStyle="{StaticResource columnHeaderStyle}"   
                      AutoGenerateColumns="False" RowHeaderWidth="0" >  
                <DataGrid.Columns>  
                    <DataGridTextColumn Header="ExpenseType" />  
                    <DataGridTextColumn Header="Amount"  />  
                </DataGrid.Columns>  
            </DataGrid>  
        </Grid>  
    </Grid>    
    ```  
  
     這樣會將樣式加入 `<Label>` 和 `<Border>` 項目。  
  
## <a name="connecting-to-data"></a>連接到資料  
 在本節中，您會建立資料提供者和資料範本，然後連接至顯示資料的控制項。  
  
#### <a name="to-bind-data-to-a-control"></a>將資料繫結到控制項  
  
1.  開啟 **ExpenseItHome.xaml** 並選擇 `<Grid>` 項目。  
  
2.  加入下列 XAML 程式碼：  
  
    ```xaml    
    <Grid.Resources>  
    <!-- Expense Report Data -->  
    <XmlDataProvider x:Key="ExpenseDataSource" XPath="Expenses">  
        <x:XData>  
            <Expenses xmlns="">  
                <Person Name="Mike" Department="Legal">  
                    <Expense ExpenseType="Lunch" ExpenseAmount="50" />  
                    <Expense ExpenseType="Transportation" ExpenseAmount="50" />  
                </Person>  
                <Person Name="Lisa" Department="Marketing">  
                    <Expense ExpenseType="Document printing"  
          ExpenseAmount="50"/>  
                    <Expense ExpenseType="Gift" ExpenseAmount="125" />  
                </Person>  
                <Person Name="John" Department="Engineering">  
                    <Expense ExpenseType="Magazine subscription"   
         ExpenseAmount="50"/>  
                    <Expense ExpenseType="New machine" ExpenseAmount="600" />  
                    <Expense ExpenseType="Software" ExpenseAmount="500" />  
                </Person>  
                <Person Name="Mary" Department="Finance">  
                    <Expense ExpenseType="Dinner" ExpenseAmount="100" />  
                </Person>  
            </Expenses>  
        </x:XData>  
    </XmlDataProvider>  
    </Grid.Resources>  
    ```  
  
     這個程式碼會建立包含每個人資料的 `XmlDataProvider` 類別。 這通常會載入為檔案，但為求簡化會內嵌資料。  
  
3.  在 `<Grid.Resources>` 項目內加入下列 XAML 程式碼：  
  
    ```xaml  
    <!-- Name item template -->  
    <DataTemplate x:Key="nameItemTemplate">  
        <Label Content="{Binding XPath=@Name}"/>  
    </DataTemplate>  
    ```  
  
     這會加入 `Data Template` ，定義 [清單方塊] 顯示資料的方式。  
  
4.  將現有 `<ListBox>` 項目取代為下列 XAML：  
  
    ```xaml  
    <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2"   
             ItemsSource="{Binding Source={StaticResource ExpenseDataSource}, XPath=Person}"  
             ItemTemplate="{StaticResource nameItemTemplate}">  
    </ListBox>  
    ```  
  
     這個程式碼會將 `ItemsSource` 的 `ListBox` 屬性繫結 到資料來源，並套用資料範本做為 `ItemTemplate`。  
  
#### <a name="to-connect-data-to-controls"></a>將資料連接至控制項  
  
1.  開啟 **ExpenseReportPage.xaml.vb** 或 **ExpenseReportPage.xaml.cs**。  
  
2.  在 C# 中，將下列建構函式加入 **ExpenseReportPage** 類別；或在 Visual Basic 中，將現有的類別更換為下列內容：  
  
    ```csharp  
    // Custom constructor to pass expense report data  
    public ExpenseReportPage(object data):this()  
    {  
        // Bind to expense report data.  
        this.DataContext = data;  
    }  
    ```  
  
    ```vb  
    Partial Public Class ExpenseReportPage  
    Inherits Page  
        Public Sub New()  
        InitializeComponent()  
        End Sub  
  
        ' Custom constructor to pass expense report data  
        Public Sub New(ByVal data As Object)  
            Me.New()  
            ' Bind to expense report data.  
            Me.DataContext = data  
        End Sub    
    End Class  
    ```  
  
     這個建構函式會將資料物件當成參數。 在本例中，資料物件會包含所選人員的名稱。  
  
3.  開啟 **ExpenseItHome.xaml.cs** 或 **ExpenseItHome.xaml.vb**。  
  
4.  以下列內容取代 `Click` 事件處理常式程式碼：  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        // View Expense Report  
        ExpenseReportPage expenseReportPage = new ExpenseReportPage(this.peopleListBox.SelectedItem);  
        this.NavigationService.Navigate(expenseReportPage);    
    }  
    ```  
  
    ```vb  
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
        ' View Expense Report  
        Dim expenseReportPage As New ExpenseReportPage(Me.peopleListBox.SelectedItem)  
        Me.NavigationService.Navigate(expenseReportPage)  
    End Sub  
    ```  
  
     這個程式碼會呼叫新的建構函式。  
  
#### <a name="to-update-the-ui-with-data-templates"></a>使用資料範本更新 UI  
  
1.  開啟 **ExpenseReportPage.xaml**。  
  
2.  以下列內容取代 [名稱]  和 `<StackPanel` 項目的 XAML 程式碼：  
  
    ```xaml  
    <!-- Name -->  
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
        <Label Style="{StaticResource labelStyle}">Name:</Label>  
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Name}"></Label>  
    </StackPanel>  
  
    <!-- Department -->  
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">  
        <Label Style="{StaticResource labelStyle}">Department:</Label>  
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Department}"></Label>  
    </StackPanel>    
    ```  
  
     這會將 [標籤]  控制項繫結至適當的資料來源屬性。  
  
3.  在 `<Grid>` 項目內加入下列 XAML 程式碼：  
  
    ```xaml  
    <!--Templates to display expense report data-->  
    <Grid.Resources>  
        <!-- Reason item template -->  
        <DataTemplate x:Key="typeItemTemplate">  
            <Label Content="{Binding XPath=@ExpenseType}"/>  
        </DataTemplate>  
        <!-- Amount item template -->  
        <DataTemplate x:Key="amountItemTemplate">  
            <Label Content="{Binding XPath=@ExpenseAmount}"/>  
        </DataTemplate>  
    </Grid.Resources>    
    ```  
  
     這會定義 [費用報表] 資料的顯示方式。  
  
4.  以下列內容取代 `<DataGrid>` 項目：  
  
    ```xaml  
    <!-- Expense type and Amount table -->  
    <DataGrid ItemsSource="{Binding XPath=Expense}" ColumnHeaderStyle="{StaticResource columnHeaderStyle}" AutoGenerateColumns="False" RowHeaderWidth="0" >  
  
        <DataGrid.Columns>  
            <DataGridTextColumn Header="ExpenseType" Binding="{Binding XPath=@ExpenseType}"  />  
            <DataGridTextColumn Header="Amount" Binding="{Binding XPath=@ExpenseAmount}" />  
        </DataGrid.Columns>  
  
    </DataGrid>  
    ```  
  
     這會加入 **ItemSource** 和定義費用項目的繫結。  
  
5.  建置並執行應用程式。  
  
6.  選擇人員，然後選擇 [檢視]  按鈕。  
  
     下圖顯示套用了控制項、配置、樣式、資料繫結和資料範本的 ExpenseIt 應用程式的兩頁頁面。  
  
     ![ExpenseIt 範例螢幕擷取畫面](../designers/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
##  <a name="Best_Practices"></a> 最佳做法  
 這個範例示範 WPF 的基本概念，因此不符合應用程式開發的最佳作法。 如需 WPF 和 .NET Framework 應用程式開發最佳作法的完整資訊，請視需要參閱下列主題：  
  
-   協助工具： [協助工具最佳作法](/dotnet/framework/ui-automation/accessibility-best-practices)  
  
-   安全性： [Windows Presentation Foundation 安全性](/dotnet/framework/wpf/security-wpf)  
  
-   當地語系化： [WPF 全球化和當地語系化概觀](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview)  
  
-   效能： [最佳化 WPF 應用程式效能](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)  
  
##  <a name="Whats_Next"></a> 後續步驟  
 您現在有多項技術可使用 WPF 建立桌上型電腦的應用程式。 您現在應該對資料繫結 WPF 應用程式的建置組塊有基本的了解。 本主題並不詳盡，但希望您有一些概念，可以自行發掘本主題所述技術之外的可能性。  
  
 如需 WPF 架構和程式設計模型的詳細資訊，請參閱下列主題：  
  
-   [WPF 架構](/dotnet/framework/wpf/advanced/wpf-architecture)  
  
-   [XAML 概觀](/dotnet/framework/wpf/advanced/xaml-overview-wpf)  
  
-   [相依性屬性概觀](/dotnet/framework/wpf/advanced/dependency-properties-overview)  
  
-   [配置系統](/dotnet/framework/wpf/advanced/layout)  
  
-   [樣式和範本](/dotnet/framework/wpf/controls/styles-and-templates)  
  
 如需建立應用程式的詳細資訊，請參閱下列主題：  
  
-   [應用程式開發概觀](/dotnet/framework/wpf/app-development/index)  
  
-   [控制項概觀](/dotnet/framework/wpf/controls/index)  
  
-   [資料繫結概觀](/dotnet/framework/wpf/data/data-binding-overview)  
  
-   [WPF 圖形、動畫和媒體概觀](https://msdn.microsoft.com/en-us/library/ms742562)  
  
-   [WPF 中的文件](/dotnet/framework/wpf/advanced/documents-in-wpf)  
  
## <a name="see-also"></a>另請參閱  
[使用 Windows Presentation Foundation 建立新式桌面應用程式](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)