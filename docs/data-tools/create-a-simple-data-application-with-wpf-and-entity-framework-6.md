---
title: 使用 WPF 和 Entity Framework 6 的簡單資料應用程式
description: 在本逐步解說中，請參閱如何使用 Windows Presentation Foundation (WPF) 和 Entity Framework 6，在 Visual Studio 中建立簡單的表單資料應用程式。
ms.custom: SEO-VS-2020
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: e3432dd9a72fa71ea1e749dd28e80a3d55cce19c
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216055"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>使用 WPF 和 Entity Framework 6 建立簡單的資料應用程式

本逐步解說示範如何在 Visual Studio 中建立基本的「表單資料」應用程式。 應用程式會使用 SQL Server LocalDB、Northwind 資料庫、Entity Framework 6 (不 Entity Framework Core) 和 Windows Presentation Foundation .NET Framework 不 (.NET Core) 。 它會示範如何使用主從階層查看來進行基本資料系結，而且也有一個自訂系結導覽器，其中有按鈕可供 **移動**、 **上移**、移 **至開始**、 **移至結尾**、 **更新** 及 **刪除**。

本文著重于在 Visual Studio 中使用資料工具，而不會嘗試以任何深度解釋基礎技術。 它假設您已對 XAML、Entity Framework 和 SQL 有基本的熟悉程度。 此範例也不會示範模型視圖 ViewModel (MVVM) 架構，這是 WPF 應用程式的標準。 不過，您可以將此程式碼複製到您自己的 MVVM 應用程式中，但有一些修改。

## <a name="install-and-connect-to-northwind"></a>安裝並連接到 Northwind

此範例使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。 如果該產品的 ADO.NET 資料提供者支援 Entity Framework，則也應該與其他 SQL database 產品搭配使用。

1. 如果您沒有 LocalDB SQL Server Express，請從 [SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)或透過 **Visual Studio 安裝程式** 進行安裝。 在 Visual Studio 安裝程式中，您可以安裝 SQL Server Express LocalDB 作為 **.NET 桌面開發** 工作負載的一部分，或是作為個別的元件。

2. 遵循下列步驟來安裝 Northwind 範例資料庫：

    1. 在 Visual Studio 中，開啟 [ **SQL Server 物件總管** ] 視窗。  (**SQL Server 物件總管** 會安裝為 **Visual Studio 安裝程式** 中 **資料儲存和處理** 工作負載的一部分。 ) 展開 **SQL Server** 節點。 以滑鼠右鍵按一下您的 LocalDB 實例，然後選取 [追加 **查詢**]。

       [查詢編輯器] 視窗隨即開啟。

    2. 將 [Northwind transact-sql 腳本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 複製到剪貼簿。 此 T-sql 腳本會從頭開始建立 Northwind 資料庫，並在其中填入資料。

    3. 將 T-sql 腳本貼入 [查詢編輯器]，然後選擇 [ **執行** ] 按鈕。

       經過一小段時間之後，查詢就會完成執行，並建立 Northwind 資料庫。

3. [新增 Northwind 的新連接](../data-tools/add-new-connections.md) 。

## <a name="configure-the-project"></a>設定專案

1. 在 Visual Studio 中，建立新的 c # **WPF 應用程式** 專案。

2. 新增 Entity Framework 6 的 NuGet 套件。 在 **方案總管** 中，選取專案節點。 在主功能表中，選擇 [ **Project**  >  **管理 NuGet 封裝**]。

     ![[管理 NuGet 套件] 功能表項目](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3. 在 [ **NuGet 封裝管理員** 中，按一下 [ **流覽]** 連結。 Entity Framework 可能是清單中的最上層套件。 按一下右窗格中的 [ **安裝** ]，然後遵循提示進行。 [輸出] 視窗會告訴您安裝完成的時間。

     ![Entity Framework NuGet 套件](../data-tools/media/raddata_vs2015_nuget_ef.png)

4. 現在您可以使用 Visual Studio 來根據 Northwind 資料庫建立模型。

## <a name="create-the-model"></a>建立模型

1. 在 **方案總管** 中，以滑鼠右鍵按一下專案節點，然後選擇 [**加入**  >  **新專案**]。 在左窗格的 [c #] 節點下，選擇 [ **資料** ]，然後在中間窗格中選擇 [ **ADO.NET 實體資料模型**]。

   ![Entity Framework 模型新專案](../data-tools/media/raddata-ef-new-project-item.png)

2. 呼叫模型 `Northwind_model` ，然後選擇 **[確定]**。 **實體資料模型 Wizard** 隨即開啟。 **從資料庫中選擇 [EF Designer** ]，然後按 **[下一步]**。

   ![來自資料庫的 EF 模型](../data-tools/media/raddata-ef-model-from-database.png)

3. 在下一個畫面中，輸入或選擇 LocalDB Northwind 連接 (例如 (localdb) \MSSQLLocalDB) 、指定 Northwind 資料庫，然後按 **[下一步]**。

4. 在嚮導的下一頁中，選擇要包含在 Entity Framework 模型中的資料表、預存程式和其他資料庫物件。 展開樹狀檢視中的 dbo 節點，然後選擇 [ **客戶**]、[ **訂單**] 和 [ **訂單詳細資料**]。 將預設值保留為核取，然後按一下 **[完成]**。

    ![選擇模型的資料庫物件](../data-tools/media/raddata-choose-ef-objects.png)

5. Wizard 會產生代表 Entity Framework 模型的 c # 類別。 這些類別是簡單的 c # 類別，而這些類別是我們對 WPF 使用者介面進行 databind 的。 *.Edmx* 檔案會描述關聯性和其他中繼資料，這些中繼資料會將類別與資料庫中的物件產生關聯。 *Tt* 檔是 T4 範本，會產生可在模型上運作的程式碼，並將變更儲存至資料庫。 您可以在 [Northwind_model] 節點下的 **方案總管** 中看到所有這些檔案：

      ![方案總管 EF 模型檔案](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    *.Edmx* 檔的設計工具介面可讓您修改模型中的某些屬性和關聯性。 我們不會在此逐步解說中使用設計工具。

6. *Tt* 檔案是一般用途，您必須調整其中一個檔案，才能使用 WPF 資料系結，這需要 ObservableCollections。 在 **方案總管** 中，展開 [Northwind_model] 節點，直到您找到 *Northwind_model tt* 為止。  (確認您不在中 *。CoNtext.tt* 檔案，其位於 *.edmx* 檔案的正下方。 ) 

   - 將兩個出現的取代為 <xref:System.Collections.ICollection> <xref:System.Collections.ObjectModel.ObservableCollection%601> 。

   - 將第一個出現的取代為 <xref:System.Collections.Generic.HashSet%601> <xref:System.Collections.ObjectModel.ObservableCollection%601> 大約行51。 請勿取代第二次出現的 HashSet。

   - <xref:System.Collections.Generic>以行 431) 的 (取代唯一出現的 <xref:System.Collections.ObjectModel> 。

7. 按 **Ctrl** + **Shift** + **B** 以建立專案。 當組建完成時，[資料來源] wizard 可以看到模型類別。

現在您已準備好將此模型連結到 XAML 頁面，以便您可以查看、流覽和修改資料。

## <a name="databind-the-model-to-the-xaml-page"></a>將模型 Databind 至 XAML 頁面

您可以撰寫自己的資料系結程式碼，但更容易讓 Visual Studio 為您進行。

1. 從主功能表中，選擇 [**專案**  >  **加入新資料來源**]，以顯示 [**資料來源設定向導]**。 選擇 [ **物件** ] 是因為您系結至模型類別，而不是系結至資料庫：

     ![具有物件來源的資料來源設定 Wizard](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2. 展開專案的節點，然後選取 [ **Customer**]。 訂單的 (來源會從客戶的 Orders 導覽屬性自動產生。 ) 

     ![將實體類別新增為數據源](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3. 按一下 [完成] 。

4. 在程式碼查看中流覽至 *MainWindow。* 基於此範例的目的，我們會將 XAML 保持簡單。 將 MainWindow 的標題變更為更具描述性的專案，並將其高度和寬度增加到目前的 600 x 800。 您稍後可以隨時變更。 現在將這三個數據列定義新增至主要方格、導覽按鈕的一個資料列、客戶的詳細資料，以及一個顯示其訂單的方格：

    ```xaml
        <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5. 現在開啟 *MainWindow* ，讓您在設計工具中進行流覽。 這會導致 [ **資料來源** ] 視窗顯示為 [ **工具箱**] 旁邊 Visual Studio 視窗邊界中的選項。 按一下索引標籤以開啟視窗，或按 **Shift** + **Alt** + **D** 或選擇 [ **View**  >  **Other Windows**  >  **資料來源**]。 我們將在 [Customers] 類別的個別文字方塊中顯示每個屬性。 首先，按一下 [ **客戶** ] 下拉式方塊中的箭號，然後選擇 [ **詳細資料**]。 然後，將節點拖曳至設計介面的中間部分，讓設計工具知道您要將它移至中間列。 如果您錯置此資料列，您可以稍後在 XAML 中以手動方式指定該資料列。 根據預設，控制項會以垂直方式放在方格專案中，但現在您可以視需要在表單上排列它們。 例如，將 [ **名稱** ] 文字方塊放在位址上方的上方可能是合理的。 本文的範例應用程式會重新排序欄位，並將它們重新排列成兩個數據行。

     ![客戶資料來源系結至個別控制項](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     在程式碼窗格中，您現在可以在 [資料列 1] 中看到新的 `Grid` 元素， (父方格的中間資料列) 。 父方格具有 `DataContext` 參考已新增至元素之 CollectionViewSource 的屬性 `Windows.Resources` 。 假設該資料內容，當第一個文字方塊系結至 **位址** 時，該名稱會對應至 `Address` CollectionViewSource 中目前物件的屬性 `Customer` 。

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. 當您在視窗的上半部看到客戶時，您想要在下半部看到其訂單。 您可以在單一方格視圖控制項中顯示訂單。 若要讓主從階層資料系結能夠如預期般運作，請務必系結至 Customers 類別中的 Orders 屬性，而不要系結至個別 Orders 節點。 將 Customers 類別的 Orders 屬性拖曳到表單的下半部，讓設計工具將它放在第2列：

     ![將 Orders 類別拖曳為方格](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7. Visual Studio 已產生將 UI 控制項連接到模型中事件的所有系結程式碼。 您只需要撰寫一些程式碼來填入模型，就可以查看某些資料。 首先，流覽至 *MainWindow* ，並將資料成員加入至資料內容的 MainWindow 類別。 這個物件是為您產生的，它的作用就像是追蹤模型中變更和事件的控制項。 您也會新增客戶和訂單的 CollectionViewSource 資料成員，以及相關聯的函式初始化邏輯。 類別的最上層應如下所示：

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs" id="Snippet1":::

     新增 system.string 的指示詞 `using` ，以將載入延伸方法帶入範圍中：

     ```csharp
     using System.Data.Entity;
     ```

     現在，向下滾動並尋找 `Window_Loaded` 事件處理常式。 請注意，Visual Studio 已新增 CollectionViewSource 物件。 這代表您在建立模型時選取的 Northwindentities] 物件。 您已新增該檔案，因此您不需要它。 讓我們取代中的程式碼，讓 `Window_Loaded` 方法現在看起來像這樣：

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs" id="Snippet2":::


8. 按 **F5**。 您應該會看到第一個已抓取到 CollectionViewSource 的客戶詳細資料。 您也應該會在資料方格中看到其訂單。 格式不太好，所以讓我們來修正這個問題。 您也可以建立一種方式來查看其他記錄，並進行基本的 CRUD 作業。

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>調整頁面設計，並為新的客戶和訂單新增格線

Visual Studio 所產生的預設相片順序並不適合您的應用程式，因此我們將在此提供最後的 XAML，以將其複製到您的程式碼中。 您也需要一些「表單」 (實際上是方格) ，讓使用者能夠加入新的客戶或訂單。 若要能夠加入新的客戶和訂單，您需要一組不是資料系結至的不同文字方塊 `CollectionViewSource` 。 您將藉由在處理常式方法中設定 Visible 屬性，來控制使用者在任何給定時間看到的方格。 最後，您會將 [刪除] 按鈕新增至 [訂單] 方格中的每個資料列，讓使用者能夠刪除個別訂單。

首先，將這些樣式新增至 `Windows.Resources` *MainWindow* 中的元素：

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

接下來，將整個外部方格取代為此標記：

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
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
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
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
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

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>新增按鈕以流覽、新增、更新和刪除

在 Windows Forms 應用程式中，您會取得 BindingNavigator 物件，其中包含可在資料庫中流覽資料列並執行基本 CRUD 作業的按鈕。 WPF 不提供 BindingNavigator，但很容易建立。 您可以使用水準 StackPanel 中的按鈕，並將按鈕與系結至程式碼後向中方法的命令產生關聯。

命令邏輯有四個部分： (1) 命令、 (2) 系結、 (3) 按鈕，以及 (4) 程式碼後端中的命令處理常式。

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>在 XAML 中新增命令、系結和按鈕

1. 首先，將 *MainWindow* 中的命令新增至元素內的 `Windows.Resources` ：

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

2. >commandbinding 會將 `RoutedUICommand` 事件對應至程式碼後置於中的方法。 `CommandBindings`在結束記號之後新增此元素 `Windows.Resources` ：

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

3. 現在， `StackPanel` 使用 [流覽]、[新增]、[刪除] 和 [更新] 按鈕加入。 首先，將此樣式新增至 `Windows.Resources` ：

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     其次，將此程式碼貼在 `RowDefinitions` 專用項目的後面 `Grid` ，指向 XAML 頁面的頂端：

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

程式碼後端是最基本的，但 add 和 delete 方法除外。 在 CollectionViewSource 的 View 屬性上呼叫方法來執行導覽。 `DeleteOrderCommandHandler`顯示如何針對訂單執行 cascade delete。 我們必須先刪除與其相關聯的 Order_Details。 會 `UpdateCommandHandler` 將新的客戶或訂單加入至集合，否則只會以使用者在文字方塊中所做的變更來更新現有的客戶或訂單。

將這些處理常式方法新增至 *MainWindow* 中的 MainWindow 類別。 如果您的 [Customers] 資料表的 CollectionViewSource 有不同的名稱，則您需要在下列每個方法中調整名稱：

:::code language="csharp" source="../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs" id="Snippet3":::


## <a name="run-the-application"></a>執行應用程式

若要開始偵錯，請按 **F5**。 您應該會看到在方格中填入客戶和訂單資料，而且導覽按鈕應該如預期般運作。 按一下 [ **認可** ]，在您輸入資料之後，將新的客戶或訂單加入至模型。 按一下 [ **取消** ] 以返回新客戶或新訂單表單，而不儲存資料。 您可以直接在文字方塊中對現有的客戶和訂單進行編輯，而這些變更會自動寫入至模型。

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Entity Framework 文件](/ef/)
