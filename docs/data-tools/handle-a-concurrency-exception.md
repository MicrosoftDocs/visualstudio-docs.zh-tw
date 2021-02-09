---
title: 處理並行例外狀況
description: 處理 (System.data.dbconcurrencyexception) 的並行例外狀況，這會在兩個使用者同時嘗試變更資料庫中的相同資料時引發。
ms.custom: SEO-VS-2020
ms.date: 09/11/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c410d9290b7e377654a9cff87f8df7524a1b7149
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866875"
---
# <a name="handle-a-concurrency-exception"></a>處理並行例外狀況

<xref:System.Data.DBConcurrencyException?displayProperty=fullName>當兩位使用者嘗試同時變更資料庫中的相同資料時，會引發並行例外狀況 () 。 在這個逐步解說中，您會建立 Windows 應用程式來說明如何捕捉 <xref:System.Data.DBConcurrencyException> 、找出造成錯誤的資料列，以及瞭解如何處理它的策略。

本逐步解說會引導您完成下列程式：

1. 建立新的 **Windows Forms 應用程式** 專案。

2. 建立以 Northwind Customers 資料表為基礎的新資料集。

3. 使用來建立表單， <xref:System.Windows.Forms.DataGridView> 以顯示資料。

4. 使用 Northwind 資料庫中 Customers 資料表的資料來填滿資料集。

5. 使用 **伺服器總管** 中的 [**顯示資料表資料**] 功能來存取 Customers 資料表的資料並變更記錄。

6. 將相同的記錄變更為不同的值、更新資料集，並嘗試將變更寫入資料庫，這會導致引發並行處理錯誤。

7. 攔截錯誤，然後顯示記錄的不同版本，讓使用者判斷是否要繼續並更新資料庫，或取消更新。

## <a name="prerequisites"></a>必要條件

本逐步解說使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1. 如果您沒有 LocalDB SQL Server Express，請從 [SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)或透過 **Visual Studio 安裝程式** 進行安裝。 在 **Visual Studio 安裝程式** 中，您可以安裝 SQL Server Express LocalDB 作為 **資料儲存和處理** 工作負載的一部分，或安裝為個別的元件。

2. 遵循下列步驟來安裝 Northwind 範例資料庫：

    1. 在 Visual Studio 中，開啟 [ **SQL Server 物件總管** ] 視窗。  (SQL Server 物件總管會安裝為 Visual Studio 安裝程式中 **資料儲存和處理** 工作負載的一部分。 ) 展開 **SQL Server** 節點。 以滑鼠右鍵按一下您的 LocalDB 實例，然後選取 [追加 **查詢**]。

       [查詢編輯器] 視窗隨即開啟。

    2. 將 [Northwind transact-sql 腳本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 複製到剪貼簿。 此 T-sql 腳本會從頭開始建立 Northwind 資料庫，並在其中填入資料。

    3. 將 T-sql 腳本貼入 [查詢編輯器]，然後選擇 [ **執行** ] 按鈕。

       經過一小段時間之後，查詢就會完成執行，並建立 Northwind 資料庫。

## <a name="create-a-new-project"></a>建立新專案

從建立新的 Windows Forms 應用程式開始：

1. 在 Visual Studio 中，於 [檔案]  功能表上選取 [新增]   > [專案]  。

2. 展開左側窗格中的 [ **Visual c #** ] 或 [ **Visual Basic** ]，然後選取 [ **Windows 桌面**]。

3. 在中間窗格中，選取 [ **Windows Forms 應用程式** ] 專案類型。

4. 將專案命名為 **ConcurrencyWalkthrough**，然後選擇 **[確定]**。

     隨即建立 **ConcurrencyWalkthrough** 專案，並將其加入至 **方案總管**，並在設計工具中開啟新的表單。

## <a name="create-the-northwind-dataset"></a>建立 Northwind 資料集

接著，建立名為 **NorthwindDataSet** 的資料集：

1. 在 [ **資料** ] 功能表上，選擇 [ **加入新資料來源**]。

   [資料來源組態精靈] 隨即開啟。

2. 在 [ **選擇資料來源類型** ] 畫面上，選取 [ **資料庫**]。

   ![Visual Studio 中的資料來源設定 Wizard](media/data-source-configuration-wizard.png)

3. 從可用的連接清單中，選取 Northwind 範例資料庫的連接。 如果連接清單中沒有連接可用，請選取 [ **新增連接**]。

    > [!NOTE]
    > 如果您要連接至本機資料庫檔案，則當系統詢問您是否要將檔案加入至專案時，請選取 [ **否** ]。

4. 在 [ **將連接字串儲存到應用程式佈建檔** ] 畫面上，選取 [ **下一步]**。

5. 展開 [ **資料表]** 節點，然後選取 [ **Customers** ] 資料表。 資料集的預設名稱應該是 **NorthwindDataSet**。

6. 選取 **[完成]** 將資料集加入至專案。

## <a name="create-a-data-bound-datagridview-control"></a>建立資料系結 DataGridView 控制項

在本節中，您會 <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> 從 [**資料來源**] 視窗將 [ **Customers** ] 專案拖曳至 Windows Form，藉以建立。

1. 若要開啟 [ **資料來源** ] 視窗，請選擇 [ **資料** ] 功能表上的 [ **顯示資料來源**]。

2. 在 [ **資料來源** ] 視窗中，展開 [ **NorthwindDataSet** ] 節點，然後選取 [ **Customers** ] 資料表。

3. 選取 [資料表] 節點上的向下箭號，然後在下拉式清單中選取 [ **DataGridView** ]。

4. 將資料表拖曳至表單的空白區域。

     <xref:System.Windows.Forms.DataGridView>名為 **CustomersDataGridView** 的控制項和 <xref:System.Windows.Forms.BindingNavigator> 名為 **CustomersBindingNavigator** 的會加入至系結至的表單 <xref:System.Windows.Forms.BindingSource> 。 接著，它會系結至 NorthwindDataSet 中的 Customers 資料表。

## <a name="test-the-form"></a>測試表單

您現在可以測試表單，以確定其在目前為止的運作方式如下所示：

1. 選取 **F5** 以執行應用程式。

     表單隨即出現，並以 <xref:System.Windows.Forms.DataGridView> 其控制項填入 Customers 資料表中的資料。

2. 在 [偵錯] 功能表上，選取 [停止偵錯]。

## <a name="handle-concurrency-errors"></a>處理並行錯誤

處理錯誤的方式取決於管理您應用程式的特定商務規則。 在這個逐步解說中，我們會使用下列策略作為如何處理並行錯誤的範例。

應用程式會向使用者呈現三個版本的記錄：

- 資料庫中的目前記錄

- 載入至資料集的原始記錄

- 資料集中建議的變更

使用者接著可以使用建議的版本來覆寫資料庫，或取消更新，並使用資料庫中的新值重新整理資料集。

### <a name="to-enable-the-handling-of-concurrency-errors"></a>若要啟用並行錯誤的處理

1. 建立自訂錯誤處理常式。

2. 顯示使用者的選項。

3. 處理使用者的回應。

4. 重新傳送更新，或重設資料集中的資料。

### <a name="add-code-to-handle-the-concurrency-exception"></a>加入程式碼以處理並行例外狀況

當您嘗試執行更新並引發例外狀況時，您通常會想要使用引發之例外狀況所提供的資訊來執行某些動作。 在本節中，您會加入嘗試更新資料庫的程式碼。 您也可以處理 <xref:System.Data.DBConcurrencyException> 可能引發的任何例外狀況，以及任何其他例外狀況。

> [!NOTE]
> `CreateMessage`和 `ProcessDialogResults` 方法稍後會在逐步解說中新增。

1. 在方法下方新增下列程式碼 `Form1_Load` ：

   [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
   [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2. 取代 `CustomersBindingNavigatorSaveItem_Click` 方法以呼叫 `UpdateDatabase` 方法，使其看起來如下所示：

   [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
   [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>顯示選項給使用者

您剛剛撰寫的程式碼會呼叫程式， `CreateMessage` 向使用者顯示錯誤資訊。 在這個逐步解說中，您可以使用訊息方塊來顯示使用者的不同記錄版本。 這可讓使用者選擇是否要使用變更來覆寫記錄，或取消編輯。 當使用者選取選項 (按一下訊息方塊中的按鈕) ，回應就會傳遞給 `ProcessDialogResult` 方法。

在程式 **代碼編輯器** 中加入下列程式碼，以建立訊息。 在方法下方輸入此程式碼 `UpdateDatabase` ：

[!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
[!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>處理使用者的回應

您也需要程式碼來處理使用者對訊息方塊的回應。 選項是使用建議的變更來覆寫資料庫中目前的記錄，或放棄本機變更，並使用目前在資料庫中的記錄來重新整理資料表。 如果使用者選擇 [ **是]**，則 <xref:System.Data.DataTable.Merge%2A> 會呼叫方法，並將 *preserveChanges* 引數設定為 **true**。 這會導致更新嘗試成功，因為原始版本的記錄現在會符合資料庫中的記錄。

在上一節中新增的程式碼下方新增下列程式碼：

[!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
[!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form-behavior"></a>測試表單行為

您現在可以測試表單，以確保其行為如預期般運作。 若要模擬平行存取違規，您可以在填妥 NorthwindDataSet 之後變更資料庫中的資料。

1. 選取 **F5** 以執行應用程式。

2. 表單出現後，請讓它保持執行並切換至 Visual Studio IDE。

3. 在 [檢視] 功能表上，選擇 [伺服器總管]。

4. 在 **伺服器總管** 中，展開您的應用程式所使用的連接，然後展開 [ **資料表]** 節點。

5. 以滑鼠右鍵按一下 [ **Customers** ] 資料表，然後選取 [ **顯示資料表資料**]。

6. 在第一個記錄 (**ALFKI**) 中，將 [ **連絡人姓名** ] 變更為 [ **Maria Anders2**]。

    > [!NOTE]
    > 流覽至不同的資料列來認可變更。

7. 切換至 ConcurrencyWalkthrough 執行的表單。

8. 在表單 (**ALFKI**) 的第一筆記錄中，將 [ **連絡人** 資訊] 變更為 [ **Maria Anders1**]。

9. 選取 [儲存] 按鈕。

     並行錯誤會引發，並顯示訊息方塊。

   選取 [ **否** ] 會取消更新，並使用目前在資料庫中的值來更新資料集。 選取 [ **是]** 會將建議的值寫入資料庫。

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
