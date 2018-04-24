---
title: 逐步解說： 在交易中儲存資料
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
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6fd36ace8949774c755a7a192e201b6d9011ff8b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-save-data-in-a-transaction"></a>逐步解說： 在交易中儲存資料
本逐步解說示範如何將資料儲存在交易中，使用<xref:System.Transactions>命名空間。 在本逐步解說中，您將建立 Windows Forms 應用程式。 您將使用資料來源組態精靈，在 Northwind 範例資料庫中建立兩個資料表的資料集。 您會將資料繫結控制項加入 Windows form，以及您將修改 BindingNavigator 的儲存按鈕以更新資料庫在 TransactionScope 內部的程式碼。

## <a name="prerequisites"></a>必要條件
本逐步解說會使用 SQL Server Express LocalDB 與 Northwind 範例資料庫。

1.  如果您沒有 SQL Server Express LocalDB，將其安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)，或透過**Visual Studio 安裝程式**。 在 Visual Studio 安裝程式，可以安裝 SQL Server Express LocalDB 的一部份 **.NET 桌面開發**工作負載，或做為個別的元件。

2.  安裝 Northwind 範例資料庫執行下列步驟：

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (SQL Server 物件總管 中安裝的一部份**資料儲存和處理**在 Visual Studio 安裝程式工作負載。)展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢...**.

       查詢編輯器視窗隨即開啟。

    2. 複製[Northwind TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。

    3. T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。

       在一段時間之後, 查詢完成執行，並建立 Northwind 資料庫。

## <a name="create-a-windows-forms-application"></a>建立 Windows Forms 應用程式
 第一個步驟是建立**Windows Forms 應用程式**。

#### <a name="to-create-the-new-windows-project"></a>建立新的 Windows 專案

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增**，**專案...**.

2. 展開  **Visual C#** 或**Visual Basic**左窗格中，然後選取**的傳統 Windows 桌面**。

3. 在中間窗格中，選取**Windows Form 應用程式**專案類型。

4. 將專案命名**命名為 SavingDataInATransactionWalkthrough**，然後選擇 **確定**。

     **命名為 SavingDataInATransactionWalkthrough**建立專案並將其加入**方案總管 中**。

## <a name="create-a-database-data-source"></a>建立資料庫資料來源
 這個步驟會使用**資料來源組態精靈**來建立資料來源為基礎`Customers`和`Orders`Northwind 範例資料庫中的資料表。

#### <a name="to-create-the-data-source"></a>若要建立資料來源

1.  在**資料**功能表上，選取**顯示資料來源**。

2.  在**資料來源**視窗中，選取**加入新資料來源**啟動**資料來源組態精靈**。

3.  在**選擇資料來源類型**畫面上，選取**資料庫**，然後選取**下一步**。

4.  在**選擇資料連線**螢幕執行下列其中一項：

    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。

         -或-

    -   選取**新連線**啟動**新增/修改連接**對話方塊並建立 Northwind 資料庫的連接。

5.  如果您的資料庫需要密碼，選取選項來加入敏感性資料，然後選取**下一步**。

6.  在**將連接字串儲存到應用程式組態檔**畫面上，選取**下一步**。

7.  在**選擇您的資料庫物件**畫面上，依序展開**資料表**節點。

8.  選取`Customers`和`Orders`資料表，然後選取**完成**。

     **NorthwindDataSet**加入至您的專案和`Customers`和`Orders`資料表會出現在**資料來源**視窗。

## <a name="add-controls-to-the-form"></a>將控制項加入表單
 您可以建立資料繫結控制項項目從**資料來源**視窗拖曳至表單。

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>若要建立資料繫結 Windows form 上的控制項

-   在**資料來源**視窗中，展開 **客戶**節點。

-   將主要**客戶**節點從**資料來源**視窗拖曳至**Form1**。

     <xref:System.Windows.Forms.DataGridView> 控制項以及用於巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 會出現在表單上。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)， `CustomersTableAdapter`， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>出現在元件匣中。

-   將關聯**訂單**節點 (不是主**訂單**節點，但是相關的子資料表節點下面的**傳真**資料行) 拖曳至表單下方**CustomersDataGridView**。

     <xref:System.Windows.Forms.DataGridView> 隨即出現在表單上。 `OrdersTableAdapter`和<xref:System.Windows.Forms.BindingSource>出現在元件匣中。

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>加入 System.Transactions 組件的參考
 交易會使用 <xref:System.Transactions> 命名空間。 預設不會加入 system.transactions 組件的專案參考，所以您必須手動加入。

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>加入 System.Transactions DLL 檔案的參考

1.  在**專案**功能表上，選取**加入參考**。

2.  選取**System.Transactions** (上 **.NET**  索引標籤)，然後選取**確定**。

     若要參考**System.Transactions**加入至專案。

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>修改 BindingNavigator 的 SaveItem 按鈕中的程式碼
 預設為第一個資料表卸除拖曳至表單，加入程式碼`click`事件的儲存按鈕<xref:System.Windows.Forms.BindingNavigator>。 您必須手動加入程式碼以更新所有其他資料表。 這個逐步解說中，我們重構現有儲存程式碼的儲存按鈕的 click 事件處理常式。 我們也建立了幾個方法，以提供根據是否需要新增或刪除資料列的特定更新功能。

#### <a name="to-modify-the-auto-generated-save-code"></a>修改自動產生的儲存程式碼

1.  選取**儲存**按鈕**CustomersBindingNavigator** （磁片圖示的按鈕）。

2.  以下列程式碼取代 `CustomersBindingNavigatorSaveItem_Click` 方法：

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

對關聯資料變更的協調順序如下：

-   刪除子記錄。 (在此情況下，刪除資料錄`Orders`資料表。)

-   刪除父記錄。 (在此情況下，刪除資料錄`Customers`資料表。)

-   插入父記錄。 (在此情況下，將記錄插入`Customers`資料表。)

-   插入子記錄。 (在此情況下，將記錄插入`Orders`資料表。)

#### <a name="to-delete-existing-orders"></a>刪除現有訂單

-   加入下列`DeleteOrders`方法**Form1**:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

#### <a name="to-delete-existing-customers"></a>刪除現有客戶

-   加入下列`DeleteCustomers`方法**Form1**:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

#### <a name="to-add-new-customers"></a>加入新客戶

-   加入下列`AddNewCustomers`方法**Form1**:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

#### <a name="to-add-new-orders"></a>加入新訂單

-   加入下列`AddNewOrders`方法**Form1**:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>執行應用程式

#### <a name="to-run-the-application"></a>若要執行應用程式

-   選取**F5**執行應用程式。

## <a name="see-also"></a>另請參閱

- [如何： 使用異動儲存資料](../data-tools/save-data-by-using-a-transaction.md)
- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)