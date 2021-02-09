---
title: 自訂插入/更新/刪除行為
description: 在這個逐步解說中，使用 LINQ (語言整合查詢) 至 Visual Studio 中的 SQL 工具，自訂實體類別的插入、更新和刪除行為。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 1aba3b1f00ce65b90f61077673a0b88a3bab0f5e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866134"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>逐步解說：自訂實體類別的插入、更新和刪除行為

[Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)提供視覺化設計介面，可用來建立和編輯以資料庫物件為基礎的 LINQ to SQL (類別) 。 使用 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)，您就可以使用 LINQ 技術來存取 SQL 資料庫。 如需詳細資訊，請參閱 [LINQ (語言整合查詢) ](/dotnet/csharp/linq/)。

根據預設，執行更新的邏輯是由 LINQ to SQL 執行時間提供。 運行 `Insert` `Update` 時間會根據資料表的架構來建立預設、和語句， `Delete` (資料行定義和主鍵資訊) 。 如果您不希望使用預設行為，則可以設定更新行為，並指定用特定的預存程序來執行處理資料庫資料時所需的插入、更新和刪除作業。 未產生預設行為時 (例如，實體類別是對應至檢視時)，同樣可以這樣做。 此外，在資料庫需要透過預存程序進行資料表存取時，也可以覆寫預設更新行為。 如需詳細資訊，請參閱 [使用預存程式自訂作業](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures)。

> [!NOTE]
> 此逐步解說需要使用 Northwind 資料庫的 **InsertCustomer**、**UpdateCustomer** 和 **DeleteCustomer** 預存程序。

本逐步解說提供您必須遵循的步驟，以覆寫預設的 LINQ to SQL 執行時間行為，以使用預存程式將資料儲存回資料庫。

在這個逐步解說中，您將瞭解如何執行下列工作：

- 建立新的 Windows Forms 應用程式，並在其中新增 LINQ to SQL 檔案。

- 建立對應至 Northwind 資料表的實體類別 `Customers` 。

- 建立參考 LINQ to SQL 類別的物件資料來源 `Customer` 。

- 建立包含系結至類別之的 Windows Form <xref:System.Windows.Forms.DataGridView> `Customer` 。

- 實作表單的儲存功能。

- 藉 <xref:System.Data.Linq.DataContext> 由將預存程式加入至 **O/R 設計** 工具來建立方法。

- 將 `Customer` 類別設定為使用預存程式來執行插入、更新和刪除。

## <a name="prerequisites"></a>必要條件

本逐步解說使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1. 如果您沒有 LocalDB SQL Server Express，請從 [SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)或透過 **Visual Studio 安裝程式** 進行安裝。 在 **Visual Studio 安裝程式** 中，您可以安裝 SQL Server Express LocalDB 作為 **資料儲存和處理** 工作負載的一部分，或安裝為個別的元件。

2. 遵循下列步驟來安裝 Northwind 範例資料庫：

    1. 在 Visual Studio 中，開啟 [ **SQL Server 物件總管** ] 視窗。  (**SQL Server 物件總管** 安裝為 **Visual Studio 安裝程式** 中 **資料儲存和處理** 工作負載的一部分。 ) 展開 **SQL Server** 節點。 以滑鼠右鍵按一下您的 LocalDB 實例，然後選取 [追加 **查詢**]。

       [查詢編輯器] 視窗隨即開啟。

    2. 將 [Northwind transact-sql 腳本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 複製到剪貼簿。 此 T-sql 腳本會從頭開始建立 Northwind 資料庫，並在其中填入資料。

    3. 將 T-sql 腳本貼入 [查詢編輯器]，然後選擇 [ **執行** ] 按鈕。

       經過一小段時間之後，查詢就會完成執行，並建立 Northwind 資料庫。

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>建立應用程式和新增 LINQ to SQL 類別

因為您正在使用 LINQ to SQL 類別，並將資料顯示在 Windows Form 上，所以請建立新的 Windows Forms 應用程式，並新增 LINQ to SQL 類別檔案。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>若要建立包含 LINQ to SQL 類別的新 Windows Forms 應用程式專案

1. 在 Visual Studio 中，於 [檔案]  功能表上選取 [新增]   > [專案]  。

2. 展開左側窗格中的 [ **Visual c #** ] 或 [ **Visual Basic** ]，然後選取 [ **Windows 桌面**]。

3. 在中間窗格中，選取 [ **Windows Forms 應用程式** ] 專案類型。

4. 將專案命名為 **updatingwithsprocswalkthrough]**，然後選擇 **[確定]**。

     **UpdatingWithSProcsWalkthrough** 專案已建立並新增至 [方案總管] 中。

4. 在 [專案] 功能表上，按一下 [加入新項目]。

5. 按一下 [LINQ to SQL 類別] 範本，並在 [名稱] 方塊中鍵入 **Northwind.dbml**。

6. 按一下 **[新增]** 。

     將 (**Northwind**) 的空白 LINQ to SQL 類別檔案新增至專案，並開啟 **O/R 設計** 工具。

## <a name="create-the-customer-entity-class-and-object-data-source"></a>建立 Customer 實體類別和物件資料來源

將資料表從 **伺服器總管** 或 **資料庫總管** 拖曳到 **O/R 設計** 工具，以建立對應至資料庫資料表的 LINQ to SQL 類別。 結果會產生對應至資料庫中各資料表的 LINQ to SQL 實體類別。 建立實體類別之後，實體類別就和其他具有公用 (Public) 屬性的類別一樣，可以當成物件資料來源使用。

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>若要建立 Customer 實體類別和將它設為資料來源

1. 在 **伺服器總管** 或 **資料庫總管** 中，于 Northwind 範例資料庫的 SQL Server 版本中找出 [ **Customer** ] 資料表。

2. 從 **伺服器總管** 或 **資料庫總管** 將 [ **Customers** ] 節點拖曳到 **O/R 設計* 工具介面上。

     會建立名為 **Customer** 的實體類別。 它的屬性會對應至 Customers 資料表中的各資料行。 因為這個實體類別代表 Customers 資料表中的單一客戶，所以其名稱為 **Customer** (而非 **Customers**)。

    > [!NOTE]
    > 此重新命名的行為稱為「複數表示」。 可以在 [ [選項] 對話方塊](../ide/reference/options-dialog-box-visual-studio.md)中開啟或關閉。 如需詳細資訊，請參閱 [如何：開啟和關閉複數表示 (O/R 設計工具) ](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)。

3. 按一下 [建置] 功能表上的 [建置 UpdatingwithSProcsWalkthrough] 以建置專案。

4. 若要開啟 [ **資料來源** ] 視窗，請按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。

5. 在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。

6. 按一下 [選擇資料來源類型] 頁面上的 [物件]，然後按一下 [下一步]。

7. 展開 [UpdatingwithSProcsWalkthrough] 節點，然後尋找並選取 [Customer] 類別。

    > [!NOTE]
    > 如果 **客戶** 類別無法使用，請取消精靈、建置專案，然後再次執行精靈。
8. 按一下 [完成] 以建立資料來源，然後將 [客戶] 實體類別新增至 [資料來源] 視窗。

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>建立 DataGridView 以在 Windows Form 上顯示客戶資料

將 LINQ to SQL 資料來源專案從 [ **資料來源** ] 視窗拖曳至 Windows Form，以建立系結至實體類別的控制項。

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>若要加入繫結至實體類別的控制項

1. 在設計檢視中開啟 [Form1]。

2. 將 [Customer] 節點從 [資料來源] 視窗拖曳至 [Form1]。

    > [!NOTE]
    > 若要顯示 [資料來源] 視窗，請按一下 [資料] 功能表上的 [顯示資料來源]。

3. 在程式碼編輯器中開啟 **Form1** 。

4. 將下列程式碼加入至表單中的表單，在任何特定方法之外，但在 `Form1` 類別內：

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();
    ```

5. 建立 `Form_Load` 事件的事件處理常式，並將下列程式碼加入至處理常式中：

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;
    ```

## <a name="implement-save-functionality"></a>執行儲存功能

預設不會啟用儲存按鈕，也不會實作儲存功能。 同時，為物件資料來源建立資料繫結控制項時，並不會自動加入程式碼以將變更的資料儲存至資料庫。 本節說明如何啟用 [儲存] 按鈕，並針對 LINQ to SQL 物件執行儲存功能。

### <a name="to-implement-save-functionality"></a>若要實作儲存功能

1. 在設計檢視中開啟 [Form1]。

2. 選取 **CustomerBindingNavigator** 上的儲存按鈕 (具有磁碟片圖示的按鈕)。

3. 在 [屬性] 視窗中，將 [Enabled] 屬性設定為 [True]。

4. 按兩下儲存按鈕以建立事件處理常式，並切換至 [色彩編輯器]。

5. 將下列程式碼加入至儲存按鈕事件處理常式：

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>覆寫執行更新 (插入、更新和刪除的預設行為) 

### <a name="to-override-the-default-update-behavior"></a>若要覆寫預設更新行為

1. 在 **O/R 設計** 工具中開啟 LINQ to SQL 檔案。 (按兩下 [方案總管] 中的 **Northwind.dbml** 檔案。)

2. 在 [伺服器總管] 或 [資料庫總管] 中展開 Northwind 資料庫的 [預存程序] 節點，找到 **InsertCustomers**、**UpdateCustomers** 和 **DeleteCustomers** 預存程序。

3. 將所有三個預存程式拖曳到 **O/R 設計** 工具上。

     預存程序會加入至方法窗格中做為 <xref:System.Data.Linq.DataContext> 方法。 如需詳細資訊，請參閱 [DataCoNtext 方法 (O/R 設計工具) ](../data-tools/datacontext-methods-o-r-designer.md)。

4. 在 **O/R 設計** 工具中選取 [ **Customer** ] 實體類別。

5. 選取 [屬性] 視窗中的 [Insert] 屬性。

6. 按一下 [使用執行階段] 旁邊的省略符號 (**...**)，以開啟 [設定行為] 對話方塊。

7. 選取 [自訂]。

8. 選取 [自訂] 清單中的 [InsertCustomers] 方法。

9. 按一下 [套用] 儲存所選類別和行為的設定。

    > [!NOTE]
    > 完成每一項變更後按一下 [套用]，即可繼續設定每個類別/行為組合的行為。 如果您 **在按一下 [** 套用] 之前變更了類別或行為，則會出現警告對話方塊，讓您有機會套用任何變更。

10. 選取 [行為] 清單中的 [更新]。

11. 選取 [自訂]。

12. 選取 [自訂] 清單中的 [UpdateCustomers] 方法。

     檢查 [方法引數] 和 [類別屬性] 清單會發現資料表的某些資料行會有兩個 [方法引數] 和兩個 [類別屬性]。 這樣可以更容易追蹤變更，並建立陳述式來檢查並行違規。

13. 將 [Original_CustomerID] 方法引數對應至 [CustomerID (Original)] 類別屬性。

    > [!NOTE]
    > 根據預設，方法引數會對應至同名的類別屬性。 如果屬性名稱變更，使得資料表與實體類別之間不再對應，則您可能需要選取當 **O/R 設計工具** 無法判斷正確的對應時，所要對應的對等類別屬性。 此外，如果方法引數沒有可對應的有效類別屬性，可以將 [類別屬性] 值設定為 [(無)]。

14. 按一下 [套用] 儲存所選類別和行為的設定。

15. 選取 [行為] 清單中的 [刪除]。

16. 選取 [自訂]。

17. 選取 [自訂] 清單中的 [DeleteCustomers] 方法。

18. 將 [Original_CustomerID] 方法引數對應至 [CustomerID (Original)] 類別屬性。

19. 按一下 [確定]  。

> [!NOTE]
> 雖然這不是此特定逐步解說的問題，但值得注意的是，LINQ to SQL 會自動處理身分識別 (自動遞增) 、rowguidcol (資料庫產生的 GUID) ，以及在插入和更新期間的時間戳記資料行的資料庫產生的值。 其他資料行型別的資料庫產生值將非預期地產生 null 值。 若要傳回資料庫產生的值，您應該手動將設定為，並將設定為 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> `true` <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> 下列其中一項： [自動同步. Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>)、 [自動同步](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)或 [自動同步. OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>)。

## <a name="test-the-application"></a>測試應用程式

再次執行應用程式，確認 **UpdateCustomers** 預存程序已正確更新資料庫中的客戶記錄。

1. 按 **F5**。

2. 修改方格內的記錄，以測試更新行為。

3. 新增記錄，以測試插入行為。

4. 按一下儲存按鈕，將變更儲存回資料庫。

5. 關閉表單 

6. 按 **F5**，確認更新的記錄和剛插入的記錄確實存在。

7. 刪除您在步驟 3 建立的新記錄，以測試刪除行為。

8. 按一下儲存按鈕送出變更並從資料庫中移除刪除的記錄。

9. 關閉表單 

10. 按下 **F5** ，並確認已從資料庫中移除刪除的記錄。

    > [!NOTE]
    > 如果應用程式使用 SQL Server Express Edition，則根據資料庫檔案 [複製到輸出目錄] 屬性值的不同，在步驟 10 按 **F5** 時，變更可能不會出現。

## <a name="next-steps"></a>下一步

視您的應用程式需求而定，在建立 LINQ to SQL 實體類別之後，您可能會想要執行幾個步驟。 您可以進行下列作業讓此應用程式發揮更強的功能：

- 在更新期間實作並行檢查。 如需詳細資訊，請參閱 [開放式平行存取：總覽](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview)。

- 加入 LINQ 查詢，以篩選資料。 如需詳細資訊，請參閱 [LINQ 查詢簡介 (c # ) ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext 方法](../data-tools/datacontext-methods-o-r-designer.md)
- [如何：指派用來執行更新、插入和刪除的預存程式](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [LINQ to SQL 查詢](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)
