---
title: 逐步解說：儲存異動中的資料
description: 在這個逐步解說中，請參閱如何使用 Visual Studio 中的 [system.string] 命名空間來儲存交易中的資料。
ms.custom: SEO-VS-2020
ms.date: 09/08/2017
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: a5933a8713a1d4b371672be83a56d0323f5043b9
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216081"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>逐步解說：儲存異動中的資料

本逐步解說示範如何使用命名空間來儲存交易中的資料 <xref:System.Transactions> 。 在這個逐步解說中，您將建立 Windows Forms 應用程式。 您將使用 [資料來源設定] 建立資料集，在 Northwind 範例資料庫中建立兩個數據表的資料集。 您會將資料繫結控制項加入至 Windows form，並修改 BindingNavigator 的 [儲存] 按鈕的程式碼，以更新 TransactionScope 內的資料庫。

## <a name="prerequisites"></a>必要條件

本逐步解說使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1. 如果您沒有 LocalDB SQL Server Express，請從 [SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)或透過 **Visual Studio 安裝程式** 進行安裝。 在 Visual Studio 安裝程式中，SQL Server Express LocalDB 可以安裝為 **.net 桌面開發** 工作負載的一部分，或安裝為個別的元件。

2. 遵循下列步驟來安裝 Northwind 範例資料庫：

    1. 在 Visual Studio 中，開啟 [ **SQL Server 物件總管** ] 視窗。  (SQL Server 物件總管會安裝為 Visual Studio 安裝程式中 **資料儲存和處理** 工作負載的一部分。 ) 展開 **SQL Server** 節點。 以滑鼠右鍵按一下您的 LocalDB 實例，然後選取 [追加 **查詢**]。

       [查詢編輯器] 視窗隨即開啟。

    2. 將 [Northwind transact-sql 腳本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 複製到剪貼簿。 此 T-sql 腳本會從頭開始建立 Northwind 資料庫，並在其中填入資料。

    3. 將 T-sql 腳本貼入 [查詢編輯器]，然後選擇 [ **執行** ] 按鈕。

       經過一小段時間之後，查詢就會完成執行，並建立 Northwind 資料庫。

## <a name="create-a-windows-forms-application"></a>建立 Windows Forms 應用程式

第一個步驟是建立 **Windows Forms 應用程式**。

1. 在 Visual Studio 中，於 [檔案]  功能表上選取 [新增]   > [專案]  。

2. 展開左側窗格中的 [ **Visual c #** ] 或 [ **Visual Basic** ]，然後選取 [ **Windows 桌面**]。

3. 在中間窗格中，選取 [ **Windows Forms 應用程式** ] 專案類型。

4. 將專案命名為 **SavingDataInATransactionWalkthrough**，然後選擇 **[確定]**。

     隨即建立 **SavingDataInATransactionWalkthrough** 專案，並將其新增至 [方案總管]。

## <a name="create-a-database-data-source"></a>建立資料庫資料來源

此步驟會使用 [ **資料來源設定向導]** ，根據 `Customers` `Orders` Northwind 範例資料庫中的和資料表建立資料來源。

1. 若要開啟 [ **資料來源** ] 視窗，請選取 [ **資料** ] 功能表上的 [ **顯示資料來源**]。

2. 在 [資料來源] 視窗中，選取 [新增新資料來源]，以啟動 [資料來源組態精靈]。

3. 在 [ **選擇資料來源類型** ] 畫面上，選取 [ **資料庫**]，然後選取 **[下一步]**。

4. 在 [ **選擇您的資料連線** ] 畫面上，執行下列其中一項：

    - 如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。

         -或-

    - 選取 [新增連線] 以啟動 [新增/修改連線] 對話方塊，並建立 Northwind 資料庫的連線。

5. 如果您的資料庫需要密碼，請選取包含機密資料的選項，然後選取 **[下一步]**。

6. 在 [ **將連接字串儲存到應用程式佈建檔** ] 畫面上，選取 [ **下一步]**。

7. 在 [ **選擇您的資料庫物件** ] 畫面上，展開 [ **資料表]** 節點。

8. 選取 `Customers` 和 `Orders` 資料表，然後選取 **[完成]**。

     **NorthwindDataSet** 會新增至您的專案中，且 `Customers` 和 `Orders` 資料表會出現在 [資料來源] 視窗中。

## <a name="add-controls-to-the-form"></a>將控制項新增至表單

您可以從 [ **資料來源** ] 視窗將專案拖曳至表單，以建立資料繫結控制項。

1. 在 [ **資料來源** ] 視窗中，展開 [ **Customers** ] 節點。

2. 從 [資料來源] 視窗，將 [客戶] 主節點拖曳至 **Form1**。

   <xref:System.Windows.Forms.DataGridView> 控制項以及巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 會出現在表單上。 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、、 `CustomersTableAdapter` <xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator> 都會出現在元件匣中。

3. 拖曳 [相關 **Orders** ] 節點 (不是 [主要 **orders** ] 節點，但 [ **Fax** ] 資料行下方的相關子資料工作表節點) 至 **CustomersDataGridView** 底下的表單。

   <xref:System.Windows.Forms.DataGridView> 隨即出現在表單上。 `OrdersTableAdapter`並 <xref:System.Windows.Forms.BindingSource> 顯示在元件匣中。

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>將參考加入至 System.object 元件

交易會使用 <xref:System.Transactions> 命名空間。 預設不會加入 system.transactions 組件的專案參考，所以您必須手動加入。

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>加入 System.Transactions DLL 檔案的參考

1. 在 [專案] 功能表上，選取 [新增參考]。

2. 選取 [ **.net** ] 索引標籤上的 [ (的 **交易**]) ，然後選取 **[確定]**。

     隨即會將 **System.Transactions** 的參考新增至專案。

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>修改 BindingNavigator 的 SaveItem 按鈕中的程式碼

若為放入表單的第一個資料表，則預設會將程式碼新增至的 [ `click` 儲存] 按鈕的事件 <xref:System.Windows.Forms.BindingNavigator> 。 您必須手動加入程式碼以更新所有其他資料表。 在這個逐步解說中，我們會從 [儲存] 按鈕的 click 事件處理常式中重構現有的儲存程式碼。 我們也會建立一些方法，根據是否需要新增或刪除資料列，提供特定的更新功能。

### <a name="to-modify-the-auto-generated-save-code"></a>修改自動產生的儲存程式碼

1. 在 **CustomersBindingNavigator** 上選取 [**儲存**] 按鈕， (具有磁碟片圖示的按鈕) 。

2. 以下列程式碼取代 `CustomersBindingNavigatorSaveItem_Click` 方法：

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet4":::

對關聯資料變更的協調順序如下：

- 刪除子記錄。  (在這種情況下，請從資料表中刪除記錄 `Orders` 。 ) 

- 刪除父記錄。  (在這種情況下，請從資料表中刪除記錄 `Customers` 。 ) 

- 插入父記錄。  (在這種情況下，請在資料表中插入記錄 `Customers` 。 ) 

- 插入子記錄。  (在這種情況下，請在資料表中插入記錄 `Orders` 。 ) 

### <a name="to-delete-existing-orders"></a>刪除現有訂單

- 將下列 `DeleteOrders` 方法新增至 **Form1**：

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet5":::

### <a name="to-delete-existing-customers"></a>刪除現有客戶

- 將下列 `DeleteCustomers` 方法新增至 **Form1**：

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet6":::

### <a name="to-add-new-customers"></a>加入新客戶

- 將下列 `AddNewCustomers` 方法新增至 **Form1**：

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet7":::

### <a name="to-add-new-orders"></a>加入新訂單

- 將下列 `AddNewOrders` 方法新增至 **Form1**：

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet8":::

## <a name="run-the-application"></a>執行應用程式

按 **F5** 執行應用程式。

## <a name="see-also"></a>另請參閱

- [如何：使用交易儲存資料](../data-tools/save-data-by-using-a-transaction.md)
- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
