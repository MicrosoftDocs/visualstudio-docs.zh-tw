---
title: 逐步解說：儲存異動中的資料
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ea312ca2858a02bc8a70c3e41dbb525c9d222adc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099048"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>逐步解說：儲存異動中的資料

本逐步解說示範如何將資料儲存在交易中，使用<xref:System.Transactions>命名空間。 在本逐步解說中，您將建立在 Windows Forms 應用程式。 若要在 Northwind 範例資料庫中建立兩個資料表的資料集，您將使用資料來源組態精靈。 您將新增到 Windows 表單時，資料繫結的控制項和您將修改 BindingNavigator 的按鈕儲存更新了一個 TransactionScope 內資料庫的程式碼。

## <a name="prerequisites"></a>必要條件

本逐步解說會使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1. 如果您沒有 SQL Server Express LocalDB，請將它安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)，或透過**Visual Studio 安裝程式**。 在 Visual Studio 安裝程式，可以安裝 SQL Server Express LocalDB 的一部份 **.NET 桌面開發**工作負載，或作為個別的元件。

2. 安裝 Northwind 範例資料庫執行下列步驟：

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (SQL Server 物件總管 中已安裝的一部分**資料儲存和處理**Visual Studio 安裝程式中的工作負載。)依序展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢**。

       查詢編輯器視窗隨即開啟。

    2. 複製[Northwind 的 TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。

    3. 將 T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。

       短時間之後，查詢完成執行，並建立 Northwind 資料庫。

## <a name="create-a-windows-forms-application"></a>建立 Windows Forms 應用程式

第一個步驟是建立**Windows Forms 應用程式**。

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增** > **專案**。

2. 展開  **Visual C#** 或是**Visual Basic**的左側窗格中，然後選取**Windows Desktop**。

3. 在中間窗格中，選取**Windows Forms 應用程式**專案類型。

4. 將專案命名為**SavingDataInATransactionWalkthrough**，然後選擇**確定**。

     隨即建立 **SavingDataInATransactionWalkthrough** 專案，並將其新增至 [方案總管]。

## <a name="create-a-database-data-source"></a>建立資料庫資料來源

此步驟中使用**資料來源組態精靈**來建立資料來源，根據`Customers`和`Orders`Northwind 範例資料庫中的資料表。

1. 若要開啟 [**資料來源**] 視窗，請在**資料**功能表上，選取**顯示資料來源**。

2. 在 [資料來源] 視窗中，選取 [新增新資料來源]，以啟動 [資料來源組態精靈]。

3. 在 [**選擇資料來源類型**畫面上，選取**資料庫**，然後選取**下一步]**。

4. 在 **選擇您的資料連接**畫面執行下列其中一項：

    - 如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。

         -或-

    - 選取 [新增連線] 以啟動 [新增/修改連線] 對話方塊，並建立 Northwind 資料庫的連線。

5. 如果您的資料庫需要密碼，請選取選項來加入敏感性資料，然後選取**下一步**。

6. 在 [**將連接字串儲存到應用程式組態檔**畫面上，選取**下一步]**。

7. 在 **選擇您的資料庫物件**畫面上，展開**資料表**節點。

8. 選取 `Customers`並`Orders`資料表，然後選取**完成**。

     **NorthwindDataSet** 會新增至您的專案中，且 `Customers` 和 `Orders` 資料表會出現在 [資料來源] 視窗中。

## <a name="add-controls-to-the-form"></a>將控制項加入表單

您可以從 [資料來源] 視窗將項目拖曳至表單，以建立資料繫結控制項。

1. 在 [**資料來源**] 視窗中，展開**客戶**節點。

2. 從 [資料來源] 視窗，將 [客戶] 主節點拖曳至 **Form1**。

   <xref:System.Windows.Forms.DataGridView> 控制項以及巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 會出現在表單上。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)， `CustomersTableAdapter`， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>會出現在元件匣。

3. 將相關**訂單**節點 (不是主**訂單**節點，但是相關的子資料表節點下方**傳真**資料行) 至下面的表單**CustomersDataGridView**。

   <xref:System.Windows.Forms.DataGridView> 隨即出現在表單上。 `OrdersTableAdapter`和<xref:System.Windows.Forms.BindingSource>會出現在元件匣。

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>加入 System.Transactions 組件的參考

交易會使用 <xref:System.Transactions> 命名空間。 預設不會加入 system.transactions 組件的專案參考，所以您必須手動加入。

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>加入 System.Transactions DLL 檔案的參考

1. 在 **專案**功能表上，選取**加入參考**。

2. 選取 [ **System.Transactions** (在 **.NET** ] 索引標籤)，然後選取**確定**。

     隨即會將 **System.Transactions** 的參考新增至專案。

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>修改 BindingNavigator 的 SaveItem 按鈕中的程式碼

預設為第一個資料表拖曳至表單，加入程式碼`click`事件的儲存按鈕<xref:System.Windows.Forms.BindingNavigator>。 您必須手動加入程式碼以更新所有其他資料表。 此逐步解說中，我們重構現有儲存程式碼，從儲存按鈕的 click 事件處理常式。 我們也會建立幾個方法，以提供特定的更新功能，根據是否需要新增或刪除資料列。

### <a name="to-modify-the-auto-generated-save-code"></a>修改自動產生的儲存程式碼

1. 選取 **儲存**按鈕**CustomersBindingNavigator** （磁碟片圖示的按鈕）。

2. 以下列程式碼取代 `CustomersBindingNavigatorSaveItem_Click` 方法：

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

對關聯資料變更的協調順序如下：

- 刪除子記錄。 (在此情況下，刪除資料錄`Orders`資料表。)

- 刪除父記錄。 (在此情況下，刪除資料錄`Customers`資料表。)

- 插入父記錄。 (在此情況下，將記錄插入`Customers`資料表。)

- 插入子記錄。 (在此情況下，將記錄插入`Orders`資料表。)

### <a name="to-delete-existing-orders"></a>刪除現有訂單

- 將下列 `DeleteOrders` 方法新增至 **Form1**：

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

### <a name="to-delete-existing-customers"></a>刪除現有客戶

- 將下列 `DeleteCustomers` 方法新增至 **Form1**：

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

### <a name="to-add-new-customers"></a>加入新客戶

- 將下列 `AddNewCustomers` 方法新增至 **Form1**：

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

### <a name="to-add-new-orders"></a>加入新訂單

- 將下列 `AddNewOrders` 方法新增至 **Form1**：

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>執行應用程式

按 **F5** 執行應用程式。

## <a name="see-also"></a>另請參閱

- [如何：使用交易儲存資料](../data-tools/save-data-by-using-a-transaction.md)
- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)