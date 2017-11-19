---
title: "建立 Windows Form 以搜尋資料 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 2799e2425ec9748075fc082881243658c363e327
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="create-a-windows-form-to-search-data"></a>建立 Windows Form 以搜尋資料
顯示表單上選取的資料是常見的應用程式案例。 例如，您可能想要顯示特定客戶的訂單，或是特定訂單的詳細資料。 在此案例中，使用者將資訊輸入至表單，然後利用使用者的輸入做為參數執行查詢；這就是根據參數型查詢而選取資料。 查詢只會傳回符合使用者輸入之準則的資料。 此逐步解說會示範如何建立會傳回特定城市中客戶的查詢，以及如何修改使用者介面，讓使用者可以輸入城市名稱，然後按下按鈕即可執行查詢。  
  
 使用參數型查詢可讓資料庫在快速篩選記錄時能有最好的表現，進而使應用程式更有效率。 相反地，如果您要求整個資料庫資料表、 透過網路傳輸金鑰，然後使用應用程式邏輯尋找您要的記錄，您的應用程式就會變慢且效率不佳。  
  
 您可以加入任何 TableAdapter （和控制項接受參數值，並執行查詢），使用參數化的查詢**搜尋準則產生器** 對話方塊。 選取 [開啟] 對話方塊**加入查詢**命令**資料**功能表 （或任何 TableAdapter 智慧標籤）。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立新的 Windows Forms 應用程式專案。  
  
-   建立及設定您的應用程式中的資料來源**資料來源組態**精靈。  
  
-   設定中的項目卸除類型**資料來源**視窗。  
  
-   建立控制項顯示資料的項目從**資料來源**視窗拖曳至表單。  
  
-   加入控制項以在表單上顯示資料。  
  
-   完成**搜尋準則產生器** 對話方塊。  
  
-   參數輸入至表單，並執行參數化的查詢。  
  
## <a name="prerequisites"></a>必要條件  
本逐步解說會使用 SQL Server Express LocalDB 與 Northwind 範例資料庫。  
  
1.  如果您沒有 SQL Server Express LocalDB，將其安裝從[SQL Server 版本的下載頁面](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)，或透過**Visual Studio 安裝程式**。 在 Visual Studio 安裝程式，可以安裝 SQL Server Express LocalDB 的一部份**資料儲存和處理**工作負載，或做為個別的元件。  
  
2.  安裝 Northwind 範例資料庫執行下列步驟：  

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (SQL Server 物件總管 中安裝的一部份**資料儲存和處理**在 Visual Studio 安裝程式工作負載。)展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢...**.  

       查詢編輯器視窗隨即開啟。  

    2. 複製[Northwind TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。  

    3. T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。  

       在一段時間之後, 查詢完成執行，並建立 Northwind 資料庫。  
  
## <a name="create-the-windows-forms-application"></a>建立 Windows Forms 應用程式  
 第一個步驟是建立**Windows Forms 應用程式**。 在此步驟中，選擇指派名稱給專案，但您將會賦予它的名稱會在稍後儲存專案，因為。  
  
#### <a name="to-create-the-new-windows-forms-application-project"></a>若要建立新的 Windows Forms 應用程式專案  
  
1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增**，**專案...**.  
  
2. 展開  **Visual C#**或**Visual Basic**左窗格中，然後選取**的傳統 Windows 桌面**。  

3. 在中間窗格中，選取**Windows Form 應用程式**專案類型。  

4. 將專案命名**WindowsSearchForm**，然後選擇 **確定**。 
  
     **WindowsSearchForm**建立專案並將其加入**方案總管 中**。  
  
## <a name="create-the-data-source"></a>建立資料來源  
此步驟中建立資料來源從資料庫使用**資料來源組態**精靈。  
  
#### <a name="to-create-the-data-source"></a>若要建立資料來源  
  
1.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。  
  
2.  在**資料來源**視窗中，選取**加入新資料來源**啟動**資料來源組態**精靈。  
  
3.  請選取 [ **選擇資料來源類型** ] 頁面上的 [ **資料庫** ]，再按 [ **下一步**]。  
  
4.  在**選擇資料連線**頁面上，執行下列其中之一：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
    -   選取**新連線**啟動**新增/修改連接** 對話方塊。  
  
5.  如果您的資料庫需要密碼，選取選項來加入敏感性資料，然後按一下 **下一步**。  
  
6.  在**將連接字串儲存到應用程式組態檔**頁面上，按一下**下一步**。  
  
7.  在**選擇您的資料庫物件**頁面上，展開**資料表**節點。  
  
8.  選取**客戶**資料表，然後按一下 **完成**。  
  
     **NorthwindDataSet**加入至您的專案，而**客戶**資料表會出現在**資料來源**視窗。  
  
## <a name="create-the-form"></a>建立表單  
 您可以建立資料繫結控制項項目從**資料來源**視窗拖曳至表單。  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>在表單上建立資料繫結控制項  
  
1.  展開**客戶**節點**資料來源**視窗。  
  
2.  拖曳**客戶**節點從**資料來源**加入至表單的視窗。  
  
     <xref:System.Windows.Forms.DataGridView> 以及用於巡覽資料錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 會出現在表單上。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)，CustomersTableAdapter， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>出現在元件匣中。  
  
## <a name="add-parameterization-search-functionality-to-the-query"></a>加入至查詢參數化 （搜尋功能）  
 您可以將 WHERE 子句加入至原始查詢使用**搜尋準則產生器** 對話方塊。  
  
#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>建立參數型查詢及控制項以輸入參數  
  
1.  選取<xref:System.Windows.Forms.DataGridView>控制項，然後再選擇**加入查詢**上**資料**功能表。  
  
2.  型別`FillByCity`中**新的查詢名稱**區域**搜尋準則產生器** 對話方塊。  
  
3.  新增`WHERE City = @City`中查詢**查詢文字**區域。  
  
     查詢應與下列類似：  
  
     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,  
          Address, City, Region, PostalCode, Country, Phone, Fax  
     FROM Customers
     WHERE City = @City  
     ```
  
    > [!NOTE]
    >  存取和 OLE DB 資料來源使用問號 ('？ ') 代表參數，所以 WHERE 子句看起來會像這樣： `WHERE City = ?`。  
  
4.  按一下**確定**關閉**搜尋準則產生器** 對話方塊。  
  
     A **FillByCityToolStrip**加入至表單。  
  
## <a name="testing-the-application"></a>測試應用程式  
 執行應用程式以開啟表單，使表單準備好在輸入時接受參數。  
  
#### <a name="to-test-the-application"></a>若要測試應用程式  
  
1.  按 F5 執行應用程式。  
  
2.  型別**倫敦**到**縣 （市)**文字方塊，然後再按一下**FillByCity**。  
  
     資料格會填入符合準則的客戶。 在此範例中，資料格只顯示有值的客戶**倫敦**中其**縣 （市)**資料行。  
  
## <a name="next-steps"></a>後續步驟  
 視應用程式的需求而定，在建立參數型表單後，您可能會有幾個想要執行的步驟。 一些您可以加強這個逐步解說的部分包括：  
  
-   加入顯示關聯資料的控制項。 如需詳細資訊，請參閱[集中的關聯性](relationships-in-datasets.md)。  
  
-   編輯資料集，以加入或移除資料庫物件。 如需詳細資訊，請參閱[建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)