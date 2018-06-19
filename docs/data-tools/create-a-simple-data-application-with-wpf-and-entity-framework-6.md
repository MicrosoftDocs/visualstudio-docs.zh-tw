---
title: 使用 WPF 和 Entity Framework 6 中建立簡單資料應用程式
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b6bb3cf022aadc00f8cc1b148dee239cf925ef30
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31927594"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>使用 WPF 和 Entity Framework 6 中建立簡單資料應用程式

本逐步解說示範如何在 Visual Studio 中建立基本 「 資料表單 」 應用程式。 應用程式會使用 SQL Server LocalDB，Northwind 資料庫中，Entity Framework 6 和 Windows Presentation Foundation。 它會顯示如何執行基本的資料繫結的主版詳細資料檢視，而且也有自訂 「 繫結導覽 」 與 「 移動下一步] 按鈕，「 移到上一個""將移至 [開始時，「"Move 若要結束，"「 更新 」 和 「 刪除 」。

本文著重於在 Visual Studio 中使用資料的工具，並不會嘗試說明中任意深度的基礎技術。 它會假設您有基本的認識 XAML、 Entity Framework 和 SQL。 此範例中也不會示範 WPF 應用程式的標準的模型檢視 View Model (MVVM) 架構。 不過，您可以將此程式碼複製到您自己的 MVVM 應用程式具有一些修改。

## <a name="install-and-connect-to-northwind"></a>安裝並連接到 Northwind

這個範例會使用 SQL Server Express LocalDB 與 Northwind 範例資料庫。 如果該產品的 ADO.NET 資料提供者支援 Entity Framework，它應該與其他 SQL 資料庫產品只會運作。

1.  如果您沒有 SQL Server Express LocalDB，將其安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)，或透過**Visual Studio 安裝程式**。 在 Visual Studio 安裝程式，可以安裝 SQL Server Express LocalDB 的一部份 **.NET 桌面開發**工作負載，或做為個別的元件。

2.  安裝 Northwind 範例資料庫執行下列步驟：

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (SQL Server 物件總管 中安裝的一部份**資料儲存和處理**在 Visual Studio 安裝程式工作負載。)展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢...**.

       查詢編輯器視窗隨即開啟。

    2. 複製[Northwind TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。

    3. T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。

       在一段時間之後, 查詢完成執行，並建立 Northwind 資料庫。

3.  [加入新連接](../data-tools/add-new-connections.md)northwind。

## <a name="configure-the-project"></a>設定專案

1.  在 Visual Studio 中，選擇 **檔案**，**新增**，**專案...** ，然後建立新 C# WPF 應用程式。

2.  接下來我們針對 Entity Framework 6 新增 NuGet 封裝。 在 [方案總管] 中選取專案節點。 在主功能表中，選擇 **專案**，**管理 NuGet 封裝...**

     ![管理 NuGet 封裝的功能表項目](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3.  在 [NuGet 封裝管理員] 中，按一下**瀏覽**連結。 Entity Framework 可能是最上層的套件清單中。 按一下**安裝**右窗格中，並遵循提示。 [輸出] 視窗會告訴您完成安裝。

     ![Entity Framework NuGet 封裝](../data-tools/media/raddata_vs2015_nuget_ef.png)

4.  現在我們可以使用 Visual Studio 來建立模型，根據 Northwind 資料庫。

## <a name="create-the-model"></a>建立模型

1.  以滑鼠右鍵按一下方案總管] 中的專案節點，然後選擇 [**新增**，**新項目...**.在左窗格中，C#] 節點下，選擇 [**資料**，然後在中間窗格選擇**ADO.NET 實體資料模型**。

     ![Entity Framework 模型新專案項目](../data-tools/media/raddata-ef-new-project-item.png)

  2.  呼叫模型`Northwind_model`，然後選擇 [確定]。 **實體資料模型精靈**隨即開啟。 選擇**資料庫的 EF Designer** ，然後按一下 **下一步**。

     ![從資料庫的 EF 模型](../data-tools/media/raddata-ef-model-from-database.png)

3.  在下一個畫面中，選擇您的 LocalDB Northwind 連線按一下**下一步**。

4.  在精靈的下一個頁面中，我們選擇哪些資料表、 預存程序和 Entity Framework 模型中包含其他資料庫物件。 展開樹狀結構檢視中的 dbo 節點，然後選擇 客戶、 訂單及訂單詳細資料。 保留預設值檢查，再按**完成**。

     ![選擇模型的資料庫物件](../data-tools/media/raddata-choose-ef-objects.png)

5.  精靈將產生的 C# 類別代表 Entity Framework 模型。 類別是純舊 C# 類別，而它們就是資料繫結至 WPF 使用者介面。 .Edmx 檔案描述的關聯性，將類別與資料庫中的物件相關聯的其他中繼資料。 .Tt 檔案 T4 範本產生的模型運作的程式碼，並將變更儲存至資料庫。 您可以看到所有這些檔案在 方案總管 Northwind_model 節點下：

       ![方案總管 EF 模型檔案](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

     .Edmx 檔案的設計工具介面可讓您修改某些屬性和模型中的關聯性。 我們不在本逐步解說使用設計工具。

6.  .Tt 檔案是一般用途，我們需要調整才能使用 WPF 資料繫結，需要 ObservableCollections 其中一個。 在方案總管 中，展開 Northwind_model 節點，直到您找到 Northwind_model.tt。 (請確定您是*不*中 *。內容.tt 檔案，這是正下方的.edmx 檔案。）

    -   取代的兩個<xref:System.Collections.ICollection>與<xref:System.Collections.ObjectModel.ObservableCollection%601>。

    -   取代第一個出現項目的<xref:System.Collections.Generic.HashSet%601>與<xref:System.Collections.ObjectModel.ObservableCollection%601>大約第 51。 請勿取代 HashSet 的第二個項目

    -   取代的唯一相符項目<xref:System.Collections.Generic>（繞行 431） 與<xref:System.Collections.ObjectModel>。

7.  按**Ctrl + Shift + B**建置專案。 組建完成時，會出現資料來源精靈模型類別。

現在我們已經準備好連結至 XAML 頁面此模型，讓我們可以檢視、 瀏覽，並修改的資料。

## <a name="databind-the-model-to-the-xaml-page"></a>資料繫結至 XAML 頁面模型

它為撰寫您自己的資料繫結程式碼，但更輕鬆地讓您的 Visual Studio。

1.  從主要功能表選擇**專案 > 加入新的資料來源**啟動**資料來源組態精靈**。 選擇**物件**因為我們要繫結的模型類別，不是針對資料庫：

     ![與物件來源的資料來源組態精靈](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2.  選取客戶。 （訂單的來源會自動產生從客戶的訂單瀏覽屬性。）

     ![將實體類別加入做為資料來源](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3.  按一下**完成**

4.  瀏覽至程式碼檢視中的 MainWindow.xaml。 我們會針對此範例的目的簡化 XAML。 將 MainWindow 的標題變更為更具描述性，和它的高度和寬度，增加現在為 600 x 800。 您可以一律稍後加以變更。 現在請將下列三個資料列定義加入至主要方格中，瀏覽按鈕，另一個用於客戶的詳細資訊，其中一個方格，其中顯示訂單的一個資料列：

    ```xaml
    <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5.  現在開啟 MainWindow.xaml，讓您在設計工具中檢視它。 這會導致資料來源 視窗，顯示為 Visual Studio 視窗旁邊的邊界 工具箱 選項。 若要開啟視窗，否則按 [] 索引標籤上按一下**Shift**+**Alt**+**D**或選擇**檢視** > **其他 Windows** > **資料來源**。 我們將在客戶類別在它自己的個別文字 方塊中顯示每個屬性。 第一次按一下客戶下拉式方塊中的箭號，然後選擇**詳細資料**。 使設計工具可讓您知道您想要在中間的資料列，然後拖曳到設計介面的中間部分節點。 如果您找不到它時，您可以稍後以手動方式在 XAML 中指定的資料列。 根據預設，控制項將垂直放置方格項目中，但此時您可以加以排列您要在表單上。 例如，可能會更有意義名稱 文字方塊中放置在最上層，上述的位址。 這個發行項的範例應用程式重新排列欄位，然後重新加以排列成兩個資料行。

     ![為個別控制項的客戶資料來源繫結](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     在程式碼檢視中，您現在可以看到新`Grid`第 1 列 （中間的資料列） 父元素之方格。 方格具有父代`DataContext`屬性，它是指已加入到 CollectionViewSource`Windows.Resources`項目。 指定該資料內容，當第一個文字方塊中會繫結至 「 位址 」，該名稱會對應至`Address`屬性在目前`Customer`CollectionViewSource 中的物件。

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6.  顯示在視窗的上半部客戶時，我們想要半查看他們在底部的訂單。 我們在單一方格檢視控制項中顯示訂單。 主版詳細資料資料繫結至如預期般運作，很重要，我們繫結至客戶類別，不以個別的 [訂單] 節點中的 Orders 屬性。 將訂單的客戶類別屬性拖曳到表單的下半部，讓設計工具將它放在資料列 2:

     ![以方格拖曳訂單類別](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7.  Visual Studio 產生的所有連接至模型中的事件的 UI 控制項繫結程式碼。 我們需要如何做，才能看到某些資料，則要撰寫程式碼來擴展模型。 第一個讓我們來瀏覽至 MainWindow.xaml.cs，並將資料成員加入至 MainWindow 類別的資料內容。 此物件，讓我們產生之後，作用類似的控制項，會追蹤變更與模型中的事件。 我們也可以加入的建構函式初始化邏輯。 我們類別頂端看起來應該像這樣：

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     新增`using`System.Data.Entity，將負載擴充方法帶入範圍指示詞：

     ```csharp
     using System.Data.Entity;
     ```

     現在，向下捲動並尋找 Window_Loaded 事件處理常式。 請注意，Visual Studio 已為我們新增 CollectionViewSource 物件。 這表示我們在建立模型時，我們選取 NorthwindEntities 物件。 讓我們加入程式碼 Window_Loaded 使整個方法看起來像這樣：

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8.  請按 **F5**。 第一個客戶所擷取至 CollectionViewSource 應該會看到詳細資料。 您也應該會看到他們在資料格中的訂單。 格式不太好，因此讓我們先修正。 我們也將建立檢視的其他記錄，並執行基本 CRUD 作業的方式。

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>調整頁面設計並新增新的客戶和訂單的方格

Visual Studio 所產生的預設排列方式不適合我們的應用程式，因此我們會在 XAML 中，以手動方式進行一些變更。 我們也會需要某些 「 表單 」 （也就是實際方格） 可讓使用者加入新的客戶或訂單。 為了加入新的客戶和訂單，我們需要一組個別的文字方塊不是資料繫結至`CollectionViewSource`。 我們會控制哪些設定 Visible 屬性處理常式方法中，使用者會看到任何給定時間的方格。 最後，我們將刪除 按鈕加入至訂單方格可讓使用者刪除個別的訂單中每個資料列。

首先，加入下列樣式給 MainWindow.xaml Windows.Resources 元素：

```xaml
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Left"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="23"/>
</Style>
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Right"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="26"/>
    <Setter Property="Width" Value="120"/>
</Style>
```

接下來，取代這個標記整個外部的方格：

```xaml
<Grid>
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="New Order Form" FontWeight="Bold"/>
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">
         <DataGrid.Columns>
             <DataGridTemplateColumn>
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <Button Content="Delete" Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>
         </DataGrid.Columns>
     </DataGrid>
 </Grid>
```

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>加入按鈕，瀏覽、 新增、 更新和刪除

在 Windows Forms 應用程式，則會以按鈕 BindingNavigator 物件瀏覽資料庫中的資料列和執行基本 CRUD 作業。 WPF 不提供 BindingNavigator，但它很容易建立一個。 這是以水平 StackPanel，內部的按鈕，我們會關聯至背後的程式碼中的方法繫結的命令按鈕。

有慵命令邏輯部分: （1） 的命令、 （2） 的繫結、 （3) 按鈕，以及 （4） 命令中的處理常式程式碼後置。

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>在 XAML 中新增命令、 繫結和按鈕

1.  首先，我們將命令加入我們 Windows.Resources 元素內的 MainWindow.xaml 檔案中：

    ```xaml
    <RoutedUICommand x:Key="FirstCommand" Text="First"/>
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>
    ```

2.  CommandBinding 會將 RoutedUICommand 事件對應到中後面的程式碼的方法。 新增此 CommandBindings 元素 Windows.Resources 結尾標記之後：

    ```xaml
    <Window.CommandBindings>
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>
    </Window.CommandBindings>
    ```

3.  現在讓我們加入導覽 StackPanel、 新增、 刪除和更新按鈕。 首先，將這個樣式加入至 Windows.Resources:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     只在外部的 Grid 項目，向 XAML 頁面頂端的 RowDefinitions 之後，第二，貼上這段程式碼：

    ```xaml
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

### <a name="add-command-handlers-to-the-mainwindow-class"></a>將命令處理常式加入至 MainWindow 類別

程式碼後置很低的加入和刪除方法除外。 瀏覽執行的 CollectionViewSource 檢視屬性上呼叫方法。 DeleteOrderCommandHandler 示範如何對訂單的串聯刪除。 我們必須先刪除與它相關聯的訂單明細。 UpdateCommandHandler 將新的客戶或訂單加入至集合中，或是只使用使用者在文字方塊中所做的變更來更新現有客戶或順序。

這些處理常式方法加入 MainWindow.xaml.cs 中的 MainWindow 類別。 如果您 CollectionViewSource 針對 Customers 資料表具有不同的名稱，您需要調整中每一種方法的名稱：

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>執行應用程式

若要開始偵錯，請按 **F5**。 您應該會看到客戶和訂單資料，填入在方格中，並瀏覽按鈕應該可正常運作。 按一下 「 認可 」 會將新客戶或訂單加入至模型，在您輸入的資料之後。 按一下 「 取消 」 返回用完新客戶或新的訂單表單而不儲存資料。 您可以對現有的客戶和訂單直接在文字方塊中編輯，而且這些變更會自動寫入至模型。

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Entity Framework 文件](/ef/)