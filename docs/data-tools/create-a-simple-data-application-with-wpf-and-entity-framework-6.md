---
title: 使用 WPF 和 Entity Framework 6 建立簡單的資料應用程式
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0febbf31dcf9f0ae1e7a4e47dae2e9cf3d291dbf
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55909163"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>使用 WPF 和 Entity Framework 6 建立簡單的資料應用程式

本逐步解說示範如何在 Visual Studio 中建立基本 「 資料表單 」 應用程式。 SQL Server LocalDB，Northwind 資料庫中，Entity Framework 6，與 Windows Presentation Foundation，則會使用應用程式。 它示範如何執行基本的資料繫結，主版詳細資料檢視，而且也有自訂繫結瀏覽器，並用於按鈕**移到下一個**，**移到上一個**，**移動開始**，**移到結尾**，**更新**並**刪除**。

本文著重於在 Visual Studio 中，使用資料的工具，並不會嘗試說明中任意深度的基礎技術。 這裡假設您有基本的熟悉 XAML、 Entity Framework 和 SQL。 此範例中也不會示範 Model View ViewModel (MVVM) 架構，也就是標準 WPF 應用程式。 不過，您也可以將此程式碼複製到自己的 MVVM 應用程式，需稍微修改一下。

## <a name="install-and-connect-to-northwind"></a>安裝並連接到 Northwind

此範例會使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。 如果該產品的 ADO.NET 資料提供者支援 Entity Framework，它就應該也使用其他的 SQL 資料庫產品。

1.  如果您沒有 SQL Server Express LocalDB，請將它安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)，或透過**Visual Studio 安裝程式**。 在  **Visual Studio 安裝程式**，您可以安裝 SQL Server Express LocalDB 做為一部分 **.NET 桌面開發**工作負載或個別的元件。

2.  安裝 Northwind 範例資料庫執行下列步驟：

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (**SQL Server 物件總管**安裝的一部分**資料儲存和處理**中的工作負載**Visual Studio 安裝程式**。)依序展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢**。

       查詢編輯器視窗隨即開啟。

    2. 複製[Northwind 的 TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。

    3. 將 T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。

       短時間之後，查詢完成執行，並建立 Northwind 資料庫。

3.  [加入新連接](../data-tools/add-new-connections.md)northwind。

## <a name="configure-the-project"></a>設定專案

1.  在 Visual Studio 中，選擇**檔案** > **新增** > **專案**，然後再建立 新C#WPF 應用程式。

2.  接下來，針對 Entity Framework 6 中新增 NuGet 套件。 在 [**方案總管] 中**，選取 [專案] 節點。 在主功能表中，選擇**專案** > **管理 NuGet 套件**。

     ![管理 NuGet 套件 功能表項目](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3.  在  **NuGet 套件管理員**，按一下**瀏覽**連結。 Entity Framework 可能是最上層的套件清單中。 按一下 **安裝**右窗格中，並遵循提示。 [輸出] 視窗會告訴您完成安裝。

     ![Entity Framework NuGet 套件](../data-tools/media/raddata_vs2015_nuget_ef.png)

4.  現在您可以使用 Visual Studio 來建立模型，根據 Northwind 資料庫。

## <a name="create-the-model"></a>建立模型

1. 中的專案節點上按一下滑鼠右鍵**方案總管**，然後選擇**新增** > **新項目**。 在左窗格中，在C#節點，選擇**資料**，然後在中間窗格中，選擇  **ADO.NET 實體資料模型**。

   ![Entity Framework 模型新專案項目](../data-tools/media/raddata-ef-new-project-item.png)

2. 呼叫模型`Northwind_model`，然後選擇  **確定**。 [實體資料模型精靈] 隨即開啟。 選擇**資料庫的 EF Designer** ，然後按一下**下一步**。

   ![從資料庫的 EF 模型](../data-tools/media/raddata-ef-model-from-database.png)

3. 在下一個畫面中，選擇您的 LocalDB Northwind 連接，然後按一下 [**下一步]**。

4. 在精靈的下一個頁面中，選擇哪些資料表、 預存程序，以及要包含在 Entity Framework 模型中其他資料庫物件。 展開樹狀檢視中的 [dbo] 節點，然後選擇**客戶**，**訂單**，並**Order Details**。 保留選取預設值，然後按一下**完成**。

    ![選擇模型的資料庫物件](../data-tools/media/raddata-choose-ef-objects.png)

5. 精靈會產生C#表示 Entity Framework 模型的類別。 類別是純舊C#類別，而且它們是我們繫結至 WPF 使用者介面。 *.Edmx*檔案會描述關聯性和其他中繼資料與資料庫中的物件產生關聯的類別。 *.Tt*檔案會產生運作模型，並將變更儲存到資料庫的程式碼的 T4 範本。 您可以看到所有這些檔案中的**方案總管 中**Northwind_model 節點下：

      ![方案總管 EF 模型檔案](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    設計工具介面 *.edmx*檔案可讓您修改一些屬性和模型中的關聯性。 我們不會在本逐步解說使用設計工具。

6. *.Tt*檔案是一般用途，您需要調整其中一個，才能使用 WPF 資料繫結，需要 ObservableCollections。 在 **方案總管**，展開 Northwind_model 節點，直到您找到*Northwind_model.tt*。 (請確定您不是處於 *。Context.tt*檔案，這是正下方 *.edmx*檔案。)

   -   取代的兩個<xref:System.Collections.ICollection>與<xref:System.Collections.ObjectModel.ObservableCollection%601>。

   -   取代第一個出現<xref:System.Collections.Generic.HashSet%601>與<xref:System.Collections.ObjectModel.ObservableCollection%601>大約是第 51 行。 並不會取代 HashSet 的第二個項目。

   -   取代的唯一相符項目<xref:System.Collections.Generic>（大約是直線 431） 與<xref:System.Collections.ObjectModel>。

7. 按下**Ctrl**+**Shift**+**B**來建置專案。 當組建完成時，模型類別會顯示資料來源精靈。

現在您已準備好將連結至 XAML 頁面的這個模型，讓您可以檢視、 巡覽及修改資料。

## <a name="databind-the-model-to-the-xaml-page"></a>資料繫結至 XAML 頁面模型

可以撰寫自己的資料繫結程式碼，但很容易讓您執行的 Visual Studio。

1.  從主功能表中，選擇**專案** > **新增新的資料來源**以顯示**資料來源組態精靈**。 選擇**物件**因為您要繫結模型類別，不是針對資料庫：

     ![與物件來源的資料來源組態精靈](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2.  選取 **客戶**。 （如訂單的來源會自動產生從客戶的訂單導覽屬性。）

     ![將實體類別加入做為資料來源](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3.  按一下 [ **完成**]。

4.  瀏覽至*MainWindow.xaml*程式碼檢視中。 我們將保留 XAML 簡單基於此範例的目的。 MainWindow 的標題變更為更具描述性，並增加其高度和寬度為 600 x 800 現在。 您之後隨時可以變更它。 現在請將下列三個資料列定義新增至在主要方格中，瀏覽按鈕，一個用於客戶的詳細資訊，，一個用於顯示其訂單的方格中的一個資料列：

    ```xaml
    <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5.  現在，請開啟*MainWindow.xaml* ，讓您在設計工具中檢視它。 這會導致**資料來源**視窗旁邊會出現在 Visual Studio 視窗邊界選項**工具箱**。 若要開啟視窗，否則按  索引標籤上按一下**Shift**+**Alt**+**D** ，或選擇**檢視** > **其他 Windows** > **Zdroje dat**。 我們將客戶類別，在它自己的個別文字 方塊中顯示每個屬性。 首先，請按一下中的箭號**客戶**下拉式方塊，然後選擇**詳細資料**。 讓設計工具可讓您知道您想要在中間的資料列，然後拖曳到設計介面的中間部分節點。 如果您弄丟它，您可以在稍後以手動方式在 XAML 中指定的資料列。 根據預設，控制項置於垂直格線項目中，但到目前為止，您可以加以排列表單上。 比方說，可能會合理放**名稱**文字方塊中，在最上層，上述的位址。 這篇文章的範例應用程式重新排列欄位，而會將它們重新排列成兩個資料行。

     ![客戶的資料來源繫結至個別的控制項](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     在程式碼檢視中，您現在可以看到新`Grid`項目中資料列 1 （中間的資料列） 的父格線。 方格具有父代`DataContext`屬性，會參考至已加入至 CollectionViewSource`Windows.Resources`項目。 指定該資料內容，當第一個文字方塊繫結至**地址**，該名稱會對應至`Address`在目前的屬性`Customer`CollectionViewSource 中的物件。

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6.  客戶在上半部的視窗顯示時，您會想要另外一半查看其在底部的訂單。 您在單一格線檢視控制項中顯示的訂單。 針對主版詳細資料繫結至如預期般運作，很重要，您將繫結至客戶類別，不會以個別的 [訂單] 節點中的 Orders 屬性。 將客戶類別的 Orders 屬性拖曳到表單的下半部，讓設計工具會將它置於第 2 列：

     ![以方格顯示將訂單類別](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7.  Visual Studio 已產生的所有繫結程式碼的 UI 控制項連接至模型中的事件。 您只需要執行動作，才能看到某些資料，是撰寫一些程式碼來擴展模型。 首先，瀏覽至*MainWindow.xaml.cs*並將資料成員新增至 MainWindow 類別的資料內容。 為您產生之後，這個物件是類似的控制項，會追蹤變更以及在模型中的事件。 您也將新增建構函式的初始化邏輯。 類別的頂端應該看起來像這樣：

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     新增`using`Load 擴充方法帶入範圍內的 System.Data.Entity 指示詞：

     ```csharp
     using System.Data.Entity;
     ```

     現在，向下捲動並尋找`Window_Loaded`事件處理常式。 請注意，Visual Studio 新增 CollectionViewSource 物件。 這表示您在建立模型時所選取的 NorthwindEntities 物件。 讓我們將程式碼加入`Window_Loaded`使整個方法現在看起來像這樣：

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8.  請按 **F5**。 您應該會看到針對至 CollectionViewSource 已擷取的第一個客戶詳細資料。 您也應該會看到他們在資料格中的訂單。 格式不太好了，現在讓我們來修正，就行了。 您也可以建立檢視的其他記錄和執行基本 CRUD 作業的方式。

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>調整頁面設計，並加入新的客戶和訂單的方格

Visual Studio 所產生的預設排列方式不適合您的應用程式，因此您會在 XAML 中，以手動方式進行一些變更。 您也會需要某些 「 表單 」 （也就是實際上方格） 可讓使用者加入新的客戶或訂單。 為了能夠加入新的客戶和訂單，您需要一組個別的文字方塊不是資料繫結至`CollectionViewSource`。 您會控制哪些使用者會看到在任何指定時間的處理常式方法中設定的 Visible 屬性的方格。 最後，您可以新增 [刪除] 按鈕，讓使用者刪除個別訂單的訂單方格中的每個資料列。

首先，新增至這些樣式`Windows.Resources`中的項目*MainWindow.xaml*:

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

接下來，有了此標記取代整個外部的方格：

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

在 Windows Forms 應用程式，您取得 BindingNavigator 物件具有按鈕瀏覽資料庫中的資料列，並執行基本 CRUD 作業。 WPF 不會提供 BindingNavigator，但很輕易地建立一個。 您這麼做的水平的 StackPanel 內的按鈕，並會繫結至程式碼後置中方法的命令相關聯的按鈕。

有個四部分的命令邏輯: （1） 命令、 （2） 的繫結、 （3） 按鈕，以及 （4） 命令中的處理常式程式碼後置。

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>在 XAML 中新增命令、 繫結和按鈕

1.  首先，新增中的命令*MainWindow.xaml*檔案內`Windows.Resources`項目：

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

2.  CommandBinding 對應`RoutedUICommand`事件，以在程式碼後置中的方法。 新增這`CommandBindings`之後的項目`Windows.Resources`結尾標記：

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

3.  現在，加入`StackPanel`，導覽中，新增、 刪除和更新 按鈕。 首先，新增到此樣式`Windows.Resources`:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     第二，貼上此程式碼後方`RowDefinitions`外部`Grid`項目中，XAML 頁面的上方：

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

### <a name="add-command-handlers-to-the-mainwindow-class"></a>將命令處理常式新增至 MainWindow 類別

程式碼後置是最基本的新增和刪除方法除外。 瀏覽執行 CollectionViewSource 的 [檢視] 屬性上呼叫方法。 `DeleteOrderCommandHandler`示範如何執行串聯刪除順序。 我們必須先刪除與它相關聯的訂單明細。 `UpdateCommandHandler`將新的客戶或訂單加入至集合中，否則就只是使用者所做的文字方塊中所做的變更會更新現有的客戶或訂單。

這些處理常式方法加入 MainWindow 類別中*MainWindow.xaml.cs*。 如果您針對 Customers 資料表的 CollectionViewSource 會有不同的名稱，您需要調整中每一種方法的名稱：

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>執行應用程式

若要開始偵錯，請按 **F5**。 您應該會看到客戶和訂單資料，在方格中，填入，並瀏覽按鈕應可正常運作。 按一下 **認可**若要將新的客戶或訂單加入至模型之後您所輸入的資料。 按一下 **取消**心意不想新客戶或新的訂單，而不儲存資料。 您可以對現有的 customers 和 orders，直接在 [文字] 方塊中的編輯，以及這些變更會自動寫入至模型。

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Entity Framework 文件](/ef/)