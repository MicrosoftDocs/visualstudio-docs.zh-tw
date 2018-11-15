---
title: 將 WPF 控制項繫結至資料集
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3450671c32cb7cfa03ade49bffcbecea728ddacf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917515"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>將 WPF 控制項繫結至資料集

在此逐步解說中，您可以建立包含資料繫結控制項的 WPF 應用程式。 這些控制項會繫結至封裝於資料集中的產品記錄。 您也加入按鈕來瀏覽產品，並將變更儲存至產品記錄。

這個逐步解說將說明下列工作：

- 建立 WPF 應用程式，以及建立從 AdventureWorksLT 範例資料庫中的資料產生的資料集。

- 建立一組資料繫結控制項中資料的資料表**Zdroje dat**至 WPF 設計工具中的視窗的視窗。

- 建立可向前及向後巡覽產品記錄的按鈕。

- 建立可將使用者對產品記錄所做的變更儲存至資料表和基礎資料來源的按鈕。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成此逐步解說：

- Visual Studio

- SQL Server 或 SQL Server Express 具有附加的 AdventureWorks Light (AdventureWorksLT) 範例資料庫的執行個體的存取。 您可以下載 AdventureWorksLT 資料庫，從[CodePlex 封存](https://archive.codeplex.com/?p=awlt2008dbscript)。

預先了解下列概念也有助於完成此逐步解說 (但非必要)：

- 資料集和 TableAdapter。 如需詳細資訊，請參閱 < [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)並[TableAdapters](../data-tools/create-and-configure-tableadapters.md)。

- WPF 資料繫結。 如需詳細資訊，請參閱 [資料繫結概觀](/dotnet/framework/wpf/data/data-binding-overview)。

## <a name="create-the-project"></a>建立專案

建立新的 WPF 專案，以顯示產品記錄。

1. 啟動 Visual Studio。

2. 在 [檔案] 功能表上選取 [新增] > [專案]。

3. 依序展開**Visual Basic**或是**Visual C#**，然後選取**Windows**。

4. 選取  **WPF 應用程式**專案範本。

5. 在 **名稱**方塊中，輸入**AdventureWorksProductsEditor** ，然後選取**確定**。

   Visual Studio 建立 AdventureWorksProductsEditor 專案。

## <a name="create-a-dataset-for-the-application"></a>建立應用程式的資料集

您可以建立資料繫結控制項之前，您必須為您的應用程式定義資料模型，並將它加入**Zdroje dat**視窗。 在此逐步解說中，您會建立資料集做為資料模型。

1.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。

     **Zdroje dat**視窗隨即開啟。

2.  在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。

     **資料來源組態**精靈 隨即開啟。

3.  在 [**選擇資料來源類型**頁面上，選取**資料庫**，然後按一下**下一步]**。

4.  在 [**選擇資料庫模型**頁面上，選取**資料集**，然後按一下**下一步]**。

5.  在 **選擇資料連接**頁面上，選取下列選項之一：

    - 如果 AdventureWorksLT 範例資料庫的資料連接是在下拉式清單中，選取它，然後按一下**下一步**。

    - 按一下 **新的連接**，並建立 AdventureWorksLT 資料庫的連接。

6.  上**儲存連接字串儲存到應用程式設定檔**頁面上，選取**做為連接的是，儲存**核取方塊，然後按一下**下一步**。

7.  在 **選擇您的資料庫物件**頁面上，展開**資料表**，然後選取**Product (SalesLT)** 資料表。

8.  按一下 [ **完成**]。

     Visual Studio 會加入新`AdventureWorksLTDataSet.xsd`專案，而且檔案會加入對應**AdventureWorksLTDataSet**項目**Zdroje dat**視窗。 `AdventureWorksLTDataSet.xsd`檔案會定義名為具類型資料集`AdventureWorksLTDataSet`和名為 TableAdapter `ProductTableAdapter`。 在此逐步解說稍後的內容中，您會使用 `ProductTableAdapter` 將資料填入資料集，並將變更儲存回資料庫。

9. 建置專案。

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>編輯 TableAdapter 的預設填滿方法

若要將資料填入資料集，請使用 `Fill` 的 `ProductTableAdapter` 方法。 根據預設，`Fill` 方法會使用 Product 資料表的所有資料列，填入 `ProductDataTable` 中的 `AdventureWorksLTDataSet`。 您可以修改此方法，使其只傳回資料列的子集。 在此逐步解說中，會修改 `Fill` 方法，使其只針對具有相片的產品傳回資料列。

1.  在 **方案總管**，按兩下*AdventureWorksLTDataSet.xsd*檔案。

     DataSet 設計工具隨即開啟。

2.  在設計師中，以滑鼠右鍵按一下**填滿**， **getdata （)** 查詢，然後選取**設定**。

     **TableAdapter 組態**精靈 隨即開啟。

3.  在 **輸入 SQL 陳述式**頁面上，新增下列 WHERE 子句之後`SELECT`陳述式，在文字方塊中。

    ```sql
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4.  按一下 [ **完成**]。

## <a name="define-the-user-interface"></a>定義使用者介面

透過在 WPF 設計工具中修改 XAML，將數個按鈕加入至視窗。 在此逐步解說稍後的內容中，您會加入程式碼，讓使用者使用這些按鈕捲動及儲存產品記錄的變更。

1. 在 **方案總管**，按兩下*MainWindow.xaml*。

    視窗中開啟**WPF 設計工具**。

2. 在設計工具的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 檢視中，在 `<Grid>` 標記之間加入下列程式碼：

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="625" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. 建置專案。

## <a name="create-data-bound-controls"></a>建立資料繫結控制項

建立顯示客戶記錄的拖曳的控制項`Product`資料表中**Zdroje dat**至 WPF 設計工具 視窗。

1.  在 [**資料來源**] 視窗中，按一下下拉式選單，如**產品**節點，然後選取**詳細資料**。

2.  依序展開**產品**節點。

3.  針對此範例中，某些欄位不會顯示，因此按一下下列節點旁邊的下拉式選單，然後選取**無**:

    - ProductCategoryID

    - ProductModelID

    - ThumbnailPhotoFileName

    - rowguid

    - ModifiedDate

4.  旁按一下下拉式選單**ThumbNailPhoto**節點，然後選取**映像**。

    > [!NOTE]
    > 根據預設中的項目**資料來源**視窗中表示圖片將設為其預設控制項**無**。 這是因為圖片是以位元組陣列儲存在資料庫中，且位元組陣列可以包含任何項目，從簡單位元組陣列到大型應用程式的可執行檔。

5.  從**資料來源** 視窗中，拖曳**產品**包含按鈕的資料列底下的方格資料列的節點。

     Visual Studio 會產生定義一組中的資料繫結控制項的 XAML**產品**資料表。 此外還會產生載入資料的程式碼。 如需有關產生的 XAML 和程式碼的詳細資訊，請參閱 <<c0> [ 繫結 WPF 控制項新增至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)。

6.  在設計工具中，按一下 [文字] 方塊旁**產品識別碼**標籤。

7.  在 **屬性**視窗中，選取旁邊的核取方塊**IsReadOnly**屬性。

## <a name="navigate-product-records"></a>巡覽產品記錄

加入可讓使用者捲動產品記錄所使用的程式碼**\<** 並**>** 按鈕。

1.  在設計工具中，按兩下**<** 視窗介面上的按鈕。

     Visual Studio 會開啟程式碼後置檔案中，並建立新`backButton_Click`事件處理常式<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。

2.  修改`Window_Loaded`事件處理常式，因此`ProductViewSource`， `AdventureWorksLTDataSet`，和`AdventureWorksLTDataSetProductTableAdapter`已在方法之外且可存取整個表單。 這些只是加入表單，全域宣告，並將它們內指派`Window_Loaded`事件處理常式如下所示：

     [!code-csharp[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]
     [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]

3.  將下列程式碼加入至 `backButton_Click` 事件處理常式：

     [!code-csharp[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]
     [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]

4.  返回 [設計工具，然後按兩下**>** ] 按鈕。

5.  將下列程式碼加入至 `nextButton_Click` 事件處理常式：

     [!code-csharp[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]
     [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]

## <a name="save-changes-to-product-records"></a>將變更儲存至產品記錄

加入程式碼，可讓使用者使用，將變更儲存至產品記錄**儲存變更** 按鈕。

1.  在設計工具中，按兩下**儲存變更** 按鈕。

     Visual Studio 會開啟程式碼後置檔案中，並建立新`saveButton_Click`事件處理常式<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。

2.  將下列程式碼加入至 `saveButton_Click` 事件處理常式：

     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]

    > [!NOTE]
    > 此範例使用 `Save` 的 `TableAdapter` 方法來儲存變更。 在此逐步解說中，這是適當的方法，因為只會變更一個資料表。 若您必須將變更儲存至多個資料表，可以改用 Visual Studio 以您的資料集所產生之 `UpdateAll` 的 `TableAdapterManager` 方法。 如需詳細資訊，請參閱 < [Tableadapter](../data-tools/create-and-configure-tableadapters.md)。

## <a name="test-the-application"></a>測試應用程式

建置並執行應用程式。 驗證您是否可以檢視及更新產品記錄。

1.  請按 **F5**。

     隨即建置應用程式並執行。 驗證下列各項：

    - 文字方塊會從具有相片的第一個產品記錄顯示資料。 此產品具有產品 ID 713，以及名稱**Long-sleeve Logo Jersey，S**。

    - 您可以按一下**>** 或是**<** 按鈕，巡覽其他產品記錄。

2.  在其中一個產品記錄，變更**大小**值，然後按一下**儲存變更**。

3.  關閉應用程式，並再重新啟動應用程式，藉由按下**F5** Visual Studio 中。

4.  巡覽至您剛變更的產品記錄，確認變更已保存。

5.  關閉應用程式。

## <a name="next-steps"></a>後續步驟

完成本逐步解說之後, 您可以嘗試下列的相關的工作：

- 了解如何使用**Zdroje dat**視窗在 Visual Studio 中要繫結 WPF 控制項新增至其他類型的資料來源。 如需詳細資訊，請參閱 <<c0> [ 繫結 WPF 控制項新增至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)。

- 了解如何使用**Zdroje dat** WPF 控制項中顯示相關的資料 （也就是父子式關聯性中的資料） 的 Visual Studio 中的視窗。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 在 WPF 應用程式中顯示相關的資料](../data-tools/display-related-data-in-wpf-applications.md)。

## <a name="see-also"></a>另請參閱

- [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
- [資料繫結概觀](/dotnet/framework/wpf/data/data-binding-overview)
