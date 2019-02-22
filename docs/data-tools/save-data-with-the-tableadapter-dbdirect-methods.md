---
title: 使用 TableAdapter DBDirect 方法儲存資料
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5c970fe4cd1bbd87f54e10be85adf37554c10675
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55950535"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>使用 TableAdapter DBDirect 方法儲存資料

本逐步解說提供使用 TableAdapter 的 DBDirect 方法，直接對資料庫執行 SQL 陳述式的詳細的指示。 TableAdapter 的 DBDirect 方法可讓您妥善控制您的資料庫更新。 您可以使用它們來執行特定 SQL 陳述式和預存程序的呼叫個別`Insert`， `Update`，並`Delete`方法，視您的應用程式 (而不是多載`Update`方法，以執行更新INSERT 和 DELETE 陳述式，全都在一個呼叫中的)。

在這個逐步解說期間，您將了解如何：

-   建立新的 **Windows Forms 應用程式**。

-   建立並設定與資料集[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)。

-   從 [資料來源] 視窗拖曳項目時，選取要在表單上建立的控制項。 如需詳細資訊，請參閱 <<c0> [ 設定要從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。

-   從 [資料來源] 視窗將項目拖曳至表單，以建立資料繫結表單。

-   加入方法以直接存取資料庫，並執行插入、 更新和刪除。

## <a name="prerequisites"></a>必要條件

本逐步解說會使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1. 如果您沒有 SQL Server Express LocalDB，請將它安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)，或透過**Visual Studio 安裝程式**。 在  **Visual Studio 安裝程式**，您可以安裝 SQL Server Express LocalDB 做為一部分**資料儲存和處理**工作負載，或作為個別的元件。

2. 安裝 Northwind 範例資料庫執行下列步驟：

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (SQL Server 物件總管 中已安裝的一部分**資料儲存和處理**Visual Studio 安裝程式中的工作負載。)依序展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢**。

       查詢編輯器視窗隨即開啟。

    2. 複製[Northwind 的 TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。

    3. 將 T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。

       短時間之後，查詢完成執行，並建立 Northwind 資料庫。

## <a name="create-a-windows-forms-application"></a>建立 Windows Forms 應用程式

第一個步驟是建立**Windows Forms 應用程式**。

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增** > **專案**。

2. 展開  **Visual C#** 或是**Visual Basic**左窗格中，然後選取**Windows Desktop**。

3. 在中間窗格中，選取**Windows Forms 應用程式**專案類型。

4. 將專案命名為**TableAdapterDbDirectMethodsWalkthrough**，然後選擇**確定**。

     隨即建立 **TableAdapterDbDirectMethodsWalkthrough** 專案，並將其新增至 [方案總管]。

## <a name="create-a-data-source-from-your-database"></a>從您的資料庫建立資料來源

此步驟使用 [資料來源組態精靈]，根據 Northwind 範例資料庫中的 `Region` 資料表建立資料來源。 您必須具有 Northwind 範例資料庫的存取權，才能建立連接。 如需設定 Northwind 範例資料庫的詳細資訊，請參閱[如何： 安裝範例資料庫](../data-tools/installing-database-systems-tools-and-samples.md)。

### <a name="to-create-the-data-source"></a>若要建立資料來源

1. 在 **資料**功能表上，選取**顯示資料來源**。

   [資料來源] 視窗隨即開啟。

2. 在 [資料來源] 視窗中，選取 [新增新資料來源]，以啟動 [資料來源組態精靈]。

3. 在 [**選擇資料來源類型**畫面上，選取**資料庫**，然後選取**下一步]**。

4. 在 **選擇您的資料連接**畫面上，執行下列其中一項：

    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。

         -或-

    -   選取 [新增連線] 啟動 [新增/修改連線] 對話方塊。

5. 如果您的資料庫需要密碼，請選取選項來加入敏感性資料，然後選取**下一步**。

6. 在 [**將連接字串儲存到應用程式組態檔**畫面上，選取**下一步]**。

7. 在 **選擇您的資料庫物件**畫面上，展開**資料表**節點。

8. 選取 `Region`資料表，然後再選取**完成**。

     **NorthwindDataSet** 隨即會新增至您的專案，且 `Region` 資料表會出現在 [資料來源] 視窗中。

## <a name="add-controls-to-the-form-to-display-the-data"></a>將控制項加入表單以顯示資料

從 [資料來源] 視窗將項目拖曳至表單，以建立資料繫結控制項。

若要建立 Windows form 上的資料繫結控制項，拖曳 主**地區**從節點**資料來源**視窗拖曳至表單。

<xref:System.Windows.Forms.DataGridView> 控制項以及用於巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 會出現在表單上。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)， `RegionTableAdapter`， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>會出現在元件匣。

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>加入會呼叫個別 TableAdapter DbDirect 方法的按鈕

1. 從 [工具箱] 將三個 <xref:System.Windows.Forms.Button> 控制項拖曳至 **Form1** (位於 **RegionDataGridView** 下方)。

2. 在每個按鈕上，設定下列 [名稱] 及 [文字] 屬性。

    |名稱|Text|
    |----------|----------|
    |`InsertButton`|**插入**|
    |`UpdateButton`|**更新**|
    |`DeleteButton`|**刪除**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>加入程式碼以將新記錄插入至資料庫

1. 選取  **InsertButton**建立 click 事件的事件處理常式，並在程式碼編輯器中開啟您的表單。

2. 以下列程式碼取代 `InsertButton_Click` 事件處理常式：

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

### <a name="to-add-code-to-update-records-in-the-database"></a>加入程式碼以更新資料庫中的記錄

1. 按兩下 [UpdateButton] 建立 Click 事件的事件處理常式，並在程式碼編輯器中開啟表單。

2. 以下列程式碼取代 `UpdateButton_Click` 事件處理常式：

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

### <a name="to-add-code-to-delete-records-from-the-database"></a>加入程式碼以從資料庫刪除記錄

1. 選取  **DeleteButton**建立 click 事件的事件處理常式，並在程式碼編輯器中開啟您的表單。

2. 以下列程式碼取代 `DeleteButton_Click` 事件處理常式：

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>執行應用程式

-   選取  **F5**執行應用程式。

-   選取 **插入**按鈕，並確認新的記錄會出現在方格中。

-   選取 **更新**按鈕，並確認更新的記錄時，會在方格中。

-   選取 **刪除**按鈕，並確認該記錄移除時的方格中。

## <a name="next-steps"></a>後續步驟

根據您的應用程式的需求，有幾個步驟，您可能想要建立資料繫結表單之後執行。 一些您可以加強這個逐步解說的部分包括：

-   將搜尋功能加入至表單。

-   在 [資料來源] 視窗中選取 [使用精靈設定資料集]，將其他資料表新增至資料集。 您可以藉由將關聯節點拖曳至表單，加入顯示關聯資料的控制項。 如需詳細資訊，請參閱 <<c0> [ 中的資料集的關聯性](relationships-in-datasets.md)。

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)