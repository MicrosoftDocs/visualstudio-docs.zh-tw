---
title: 將 WPF 控制項繫結至資料集
description: 在包含資料繫結控制項的 Visual Studio 中建立 WPF 應用程式，這些控制項系結至封裝于資料集中的產品記錄。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b67e70792f6e7864749b603f30ab868ef177336a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215561"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>將 WPF 控制項繫結至資料集

在這個逐步解說中，您會建立包含資料繫結控制項的 WPF 應用程式。 這些控制項會繫結至封裝於資料集中的產品記錄。 您也可以加入按鈕，以流覽產品並儲存產品記錄的變更。

本逐步解說將說明下列工作：

- 建立 WPF 應用程式，以及建立從 AdventureWorksLT 範例資料庫中的資料產生的資料集。

- 從 [資料來源] 視窗將資料表拖曳至 WPF 設計工具的視窗，以建立一組資料繫結控制項。

- 建立可向前及向後巡覽產品記錄的按鈕。

- 建立可將使用者對產品記錄所做的變更儲存至資料表和基礎資料來源的按鈕。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成這個逐步解說：

- Visual Studio

- SQL Server 或 SQL Server Express 的執行中實例的存取權，該實例具有 AdventureWorks Light (AdventureWorksLT) 範例資料庫附加至該實例。 您可以從 [CodePlex](https://archive.codeplex.com/?p=awlt2008dbscript)封存下載 AdventureWorksLT 資料庫。

預先了解下列概念也有助於完成此逐步解說 (但非必要)：

- 資料集和 TableAdapter。 如需詳細資訊，請參閱 Visual Studio 和[tableadapter](../data-tools/create-and-configure-tableadapters.md)[中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)。

- WPF 資料繫結。 如需詳細資訊，請參閱資料系結 [總覽](/dotnet/desktop-wpf/data/data-binding-overview)。

## <a name="create-the-project"></a>建立專案

建立新的 WPF 專案以顯示產品記錄。

::: moniker range="vs-2017"

1. 開啟 Visual Studio。

2. **在 [檔案**] 功能表上選取 [**新增** > **專案**]。

3. 展開 [Visual Basic] 或 [Visual C#]，然後選取 **Windows**。

4. 選取 [ **WPF 應用程式** ] 專案範本。

5. 在 [ **名稱** ] 方塊中，輸入 **AdventureWorksProductsEditor** ，然後選取 **[確定]**。

::: moniker-end

::: moniker range=">=vs-2019"

1. 開啟 Visual Studio。

2. 在 [開始] 視窗中，選擇 [ **建立新專案**]。

3. 搜尋 c # **WPF 應用程式** 專案範本，並遵循步驟來建立專案，並將專案命名為 **AdventureWorksProductsEditor**。

::: moniker-end

   Visual Studio 隨即建立 AdventureWorksProductsEditor 專案。

## <a name="create-a-dataset-for-the-application"></a>建立應用程式的資料集

建立資料繫結控制項之前，您必須先定義應用程式的資料模型，並將其新增至 [資料來源] 視窗。 在此逐步解說中，您會建立資料集做為資料模型。

1. 按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。

   [資料來源] 視窗隨即開啟。

2. 在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。

   [資料來源組態精靈] 隨即開啟。

3. 在 [選擇資料來源類型] 頁面上，選取 [資料庫]，然後按一下 [下一步]。

4. 在 [選擇資料庫模型] 頁面上，選取 [資料集]，然後按一下 [下一步]。

5. 在 [選擇資料連線] 頁面中，選取下列其中一個選項：

   - 若下拉式清單中有提供 AdventureWorksLT 範例資料庫的資料連線，請選取此資料連線，然後按一下 [下一步]。

   - 按一下 [新增連線]，建立與 AdventureWorksLT 資料庫的連線。

6. 在 [將連接字串儲存到應用程式設定檔] 頁面中，選取 [是，將連線儲存為] 核取方塊，然後按一下 [下一步]。

7. 在 [選擇您的資料庫物件] 頁面中，展開 [資料表]，然後選取 **Product (SalesLT)** 資料表。

8. 按一下 [完成] 。

   Visual Studio 將新檔案加入 `AdventureWorksLTDataSet.xsd` 至專案，並將對應的 **adventureworksltdataset.xsd** 專案加入至 [ **資料來源** ] 視窗。 檔案會 `AdventureWorksLTDataSet.xsd` 定義名為的具類型資料集 `AdventureWorksLTDataSet` ，以及名為的 TableAdapter `ProductTableAdapter` 。 在此逐步解說稍後的內容中，您會使用 `ProductTableAdapter` 將資料填入資料集，並將變更儲存回資料庫。

9. 建置專案。

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>編輯 TableAdapter 的預設 fill 方法

若要將資料填入資料集，請使用 `Fill` 的 `ProductTableAdapter` 方法。 根據預設，`Fill` 方法會使用 Product 資料表的所有資料列，填入 `ProductDataTable` 中的 `AdventureWorksLTDataSet`。 您可以修改此方法，使其只傳回資料列的子集。 在此逐步解說中，會修改 `Fill` 方法，使其只針對具有相片的產品傳回資料列。

1. 在 [方案總管] 中，按兩下 *AdventureWorksLTDataSet.xsd* 檔案。

     DataSet 設計工具隨即開啟。

2. 在設計工具中，以滑鼠右鍵按一下 [填滿]、**GetData()** 查詢，然後選取 [設定]。

     [TableAdapter 組態精靈] 隨即開啟。

3. 在 [輸入 SQL 陳述式] 頁面中，將下列 WHERE 子句新增至文字方塊中 `SELECT` 陳述式的後面。

    ```sql
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. 按一下 [完成] 。

## <a name="define-the-user-interface"></a>定義使用者介面

透過在 WPF 設計工具中修改 XAML，將數個按鈕加入至視窗。 在此逐步解說稍後的內容中，您會加入程式碼，讓使用者使用這些按鈕捲動及儲存產品記錄的變更。

1. 在 [方案總管] 中，按兩下 *MainWindow.xaml*。

    視窗會在 **WPF 設計** 工具中開啟。

2. 在設計工具的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 檢視中，在 `<Grid>` 標記之間加入下列程式碼：

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="625" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75">&lt;</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">&gt;</Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. 建置專案。

## <a name="create-data-bound-controls"></a>建立資料繫結控制項

`Product`從 [**資料來源**] 視窗將資料表拖曳至 WPF 設計工具，以建立顯示客戶記錄的控制項。

1. 在 [資料來源] 視窗中，按一下 [產品] 節點的下拉式功能表，然後選取 [詳細資料]。

2. 展開 [產品] 節點。

3. 在此範例中，某些欄位不會顯示，因此請按一下下列節點旁邊的下拉式功能表，然後選取 [無]：

    - ProductCategoryID

    - ProductModelID

    - ThumbnailPhotoFileName

    - rowguid

    - ModifiedDate

4. 按一下 [ThumbNailPhoto] 節點旁邊的下拉式功能表，並選取 [影像]。

    > [!NOTE]
    > 根據預設，[資料來源] 視窗中表示圖片的項目，會將其預設控制項設定為 [無]。 這是因為圖片是以位元組陣列儲存在資料庫中，且位元組陣列可以包含任何項目，從簡單位元組陣列到大型應用程式的可執行檔。

5. 從 [資料來源] 視窗將 [產品] 節點拖曳至包含按鈕之資料列下方的資料格列。

     Visual Studio 會產生 XAML，其定義一組繫結至 [產品] 資料表之資料的控制項。 此外還會產生載入資料的程式碼。 如需有關產生的 XAML 和程式碼的詳細資訊，請參閱將 [WPF 控制項系結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。

6. 在設計工具中，按一下 [Product ID] 標籤旁邊的文字方塊。

7. 在 [屬性] 視窗中，選取 **IsReadOnly** 屬性旁邊的核取方塊。

## <a name="navigate-product-records"></a>流覽產品記錄

加入可讓使用者使用按鈕來滾動產品記錄的程式碼 **\<** and **>** 。

1. 在設計工具中，按兩下 **<** 視窗介面上的按鈕。

     Visual Studio 會開啟程式碼後置檔案，並建立 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的新 `backButton_Click` 事件處理常式。

2. 修改 `Window_Loaded` 事件處理常式，使 `ProductViewSource`、`AdventureWorksLTDataSet` 和 `AdventureWorksLTDataSetProductTableAdapter` 位於方法之外，且整個表單都可以存取。 請只將這些視為表單的全域宣告，然後在事件處理常式內指派它們，如下 `Window_Loaded` 所示：

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet1":::

3. 將下列程式碼加入至 `backButton_Click` 事件處理常式：

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet2":::

4. 返回設計工具，然後按兩下 **>** 按鈕。

5. 將下列程式碼加入至 `nextButton_Click` 事件處理常式：

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet3":::

## <a name="save-changes-to-product-records"></a>儲存產品記錄的變更

新增程式碼，讓使用者可以使用 [儲存變更] 按鈕儲存產品記錄的變更。

1. 在設計工具中，按兩下 [儲存變更] 按鈕。

     Visual Studio 會開啟程式碼後置檔案，並建立 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的新 `saveButton_Click` 事件處理常式。

2. 將下列程式碼加入至 `saveButton_Click` 事件處理常式：

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet4":::

    > [!NOTE]
    > 此範例使用 `Save` 的 `TableAdapter` 方法來儲存變更。 在此逐步解說中，這是適當的方法，因為只會變更一個資料表。 若您必須將變更儲存至多個資料表，可以改用 Visual Studio 以您的資料集所產生之 `UpdateAll` 的 `TableAdapterManager` 方法。 如需詳細資訊，請參閱 [tableadapter](../data-tools/create-and-configure-tableadapters.md)。

## <a name="test-the-application"></a>測試應用程式

建置並執行應用程式。 驗證您是否可以檢視及更新產品記錄。

1. 按 **F5**。

     隨即建置應用程式並執行。 驗證下列項目：

    - 文字方塊會從具有相片的第一個產品記錄顯示資料。 此產品具有產品識別碼 713，以及名稱 **Long-Sleeve Logo Jersey, S**。

    - 您可以按一下 **>** 或 **<** 按鈕，以流覽其他產品記錄。

2. 在其中一個產品記錄中，變更 [大小] 值，然後按一下 [儲存變更]。

3. 關閉應用程式，然後在 Visual Studio 中按 **F5**，以重新啟動應用程式。

4. 巡覽至您剛變更的產品記錄，確認變更已保存。

5. 關閉應用程式。

## <a name="next-steps"></a>下一步

完成此逐步解說之後，您可以嘗試下列相關工作：

- 了解如何使用 Visual Studio 中的 [資料來源] 視窗，將 WPF 控制項繫結程序至其他資料來源類型。 如需詳細資訊，請參閱 [將 WPF 控制項系結至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)。

- 了解如何使用 Visual Studio 中的 [資料來源] 視窗，顯示 WPF 控制項中的相關資料 (也就是父子關聯性中的資料)。 如需詳細資訊，請參閱 [逐步解說：在 WPF 應用程式中顯示相關資料](../data-tools/display-related-data-in-wpf-applications.md)。

## <a name="see-also"></a>另請參閱

- [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
- [資料系結總覽](/dotnet/desktop-wpf/data/data-binding-overview)
