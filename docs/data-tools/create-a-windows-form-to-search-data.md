---
title: 建立 Windows Form 以搜尋資料
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ecbdd8b9f1fb1696986672bb621567944910660f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567607"
---
# <a name="create-a-windows-form-to-search-data"></a>建立 Windows Form 以搜尋資料

顯示表單上選取的資料是常見的應用程式案例。 例如，您可能想要顯示特定客戶的訂單，或是特定訂單的詳細資料。 在此案例中，使用者將資訊輸入至表單，然後利用使用者的輸入做為參數執行查詢；這就是根據參數型查詢而選取資料。 查詢只會傳回符合使用者輸入之準則的資料。 此逐步解說會示範如何建立會傳回特定城市中客戶的查詢，以及如何修改使用者介面，讓使用者可以輸入城市名稱，然後按下按鈕即可執行查詢。

使用參數型查詢可讓資料庫在快速篩選記錄時能有最好的表現，進而使應用程式更有效率。 相較下，當您要求整個資料庫資料表，再透過網路傳送該資料表，然後使用應用程式邏輯尋找您要的記錄時，應用程式可能會變得緩慢且無效率。

您可以加入任何 TableAdapter （和控制項接受參數值，並執行查詢），使用參數化的查詢**搜尋準則產生器** 對話方塊。 選取 [資料] 功能表 (或任何 TableAdapter 智慧標籤) 中的 [新增查詢] 命令，以開啟對話方塊。

這個逐步解說中所述的工作包括：

- 建立及設定您的應用程式中的資料來源**資料來源組態**精靈。

- 設定中的項目卸除類型**Zdroje dat**視窗。

- 從 [資料來源] 視窗將項目拖曳至表單，以建立顯示資料的控制項。

- 加入控制項以在表單上顯示資料。

- 完成**搜尋準則產生器** 對話方塊。

- 在表單中輸入參數和執行參數化的查詢。

## <a name="prerequisites"></a>必要條件

本逐步解說會使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1. 如果您沒有 SQL Server Express LocalDB，請將它安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)，或透過**Visual Studio 安裝程式**。 在  **Visual Studio 安裝程式**，您可以安裝 SQL Server Express LocalDB 做為一部分**資料儲存和處理**工作負載，或作為個別的元件。

2. 安裝 Northwind 範例資料庫執行下列步驟：

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (SQL Server 物件總管 中已安裝的一部分**資料儲存和處理**中的工作負載**Visual Studio 安裝程式**。)依序展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢**。

       查詢編輯器視窗隨即開啟。

    2. 複製[Northwind 的 TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。

    3. 將 T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。

       短時間之後，查詢完成執行，並建立 Northwind 資料庫。

## <a name="create-the-windows-forms-application"></a>建立 Windows Forms 應用程式

建立新**Windows Forms 應用程式**專案，或C#或 Visual Basic。 將專案命名為 **WindowsSearchForm**。

## <a name="create-the-data-source"></a>建立資料來源

此步驟會使用 [資料來源組態精靈]，從資料庫建立資料來源：

1. 若要開啟 **資料來源** 視窗，請在**資料**功能表上，按一下 **顯示資料來源**。

2. 在 [資料來源] 視窗中，選取 [新增新資料來源]，以啟動 [資料來源組態精靈]。

3. 請選取 [ **選擇資料來源類型** ] 頁面上的 [ **資料庫** ]，再按 [ **下一步**]。

4. 在 [選擇您的資料連線] 頁面上，執行下列其中一項：

    - 如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。

    - 選取 [新增連線] 啟動 [新增/修改連線] 對話方塊。

5. 如果資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下 [下一步]。

6. 在 [**將連接字串儲存到應用程式組態檔**頁面上，按一下**下一步]**。

7. 展開 [選擇您的資料庫物件] 頁面上的 [資料表] 節點。

8. 選取 [Customers] 資料表，然後按一下 [完成]。

     [NorthwindDataSet] 會新增至專案中，且 [Customers] 資料表會出現在 [資料來源] 視窗中。

## <a name="create-the-form"></a>建立表單

您可以從 [資料來源] 視窗將項目拖曳至表單，以建立資料繫結控制項：

1. 在 [資料來源] 視窗中，展開 [客戶] 節點。

2. 從 [資料來源] 視窗，將 [Customers] 節點拖曳至表單。

     <xref:System.Windows.Forms.DataGridView> 以及用於巡覽資料錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 會出現在表單上。 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、CustomersTableAdapter、<xref:System.Windows.Forms.BindingSource> 及 <xref:System.Windows.Forms.BindingNavigator> 會顯示在元件匣中。

## <a name="add-parameterization-search-functionality-to-the-query"></a>加入至查詢參數化 （搜尋功能）

您可以加入原始的查詢使用 WHERE 子句**搜尋準則產生器** 對話方塊中：

1. 選取 <xref:System.Windows.Forms.DataGridView> 控制項，然後選取 [資料] 功能表中的 [新增查詢]。

2. 型別**FillByCity**中**新的查詢名稱**區域**搜尋準則產生器** 對話方塊。

3. 將 `WHERE City = @City` 新增至 [查詢文字] 區域中的查詢。

     查詢應與下列類似：

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > 存取與 OLE DB 資料來源使用問號 ('？ ') 代表參數，所以 WHERE 子句看起來會像這樣： `WHERE City = ?`。

4. 按一下 [確定] 以關閉 [搜尋準則產生器] 對話方塊。

     **FillByCityToolStrip** 隨即會新增至表單。

## <a name="test-the-application"></a>測試應用程式

執行應用程式時，會開啟表單，並讓它準備好要接受做為輸入參數：

1. 按 **F5** 執行應用程式。

2. 在 [City] 文字方塊中鍵入 **London**，然後按一下 [FillByCity]。

     資料格會填入符合準則的客戶。 在此範例中，資料格只會顯示在 [City] 資料行中具有 **London** 值的客戶。

## <a name="next-steps"></a>後續步驟

視應用程式的需求而定，在建立參數型表單後，您可能會有幾個想要執行的步驟。 一些您可以加強這個逐步解說的部分包括：

- 加入顯示關聯資料的控制項。 如需詳細資訊，請參閱 <<c0> [ 中的資料集的關聯性](relationships-in-datasets.md)。

- 編輯資料集，以加入或移除資料庫物件。 如需詳細資訊，請參閱[建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
