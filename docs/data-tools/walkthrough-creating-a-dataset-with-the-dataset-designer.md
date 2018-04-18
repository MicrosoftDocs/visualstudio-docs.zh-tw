---
title: 逐步解說： 以 Dataset 設計工具建立資料集 |Microsoft 文件
ms.custom: ''
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 31383f3dc2c966e8f2ec1cf3b39ebecb086ac7fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>逐步解說：以 DataSet 設計工具建立資料集

在此逐步解說中您將建立資料集使用**Dataset 設計工具**。 它將引導您建立新的專案，並加入新的程序**資料集**給它的項目。 您將學習如何建立根據資料庫中的資料表，而不使用精靈的資料表。  

這個逐步解說中所述的工作包括：  

-   建立新**Windows Forms 應用程式**專案。  

-   加入空**資料集**項目加入專案。  

-   建立及設定您的應用程式中的資料來源，建置與資料集**Dataset 設計工具**。  
 
-   建立 Northwind 資料庫中的連接**伺服器總管**。  

-   使用 Tableadapter 建立資料表，在基礎資料庫中資料表的資料集。  

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>必要條件  
本逐步解說會使用 SQL Server Express LocalDB 與 Northwind 範例資料庫。  
  
1.  如果您沒有 SQL Server Express LocalDB，將其安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)，或透過**Visual Studio 安裝程式**。 在 Visual Studio 安裝程式，可以安裝 SQL Server Express LocalDB 的一部份**資料儲存和處理**工作負載，或做為個別的元件。  
  
2.  安裝 Northwind 範例資料庫執行下列步驟：  

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (SQL Server 物件總管 中安裝的一部份**資料儲存和處理**在 Visual Studio 安裝程式工作負載。)展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢...**.  

       查詢編輯器視窗隨即開啟。  

    2. 複製[Northwind TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。  

    3. T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。  

       在一段時間之後, 查詢完成執行，並建立 Northwind 資料庫。  
  
## <a name="creating-a-new-windows-forms-application-project"></a>建立新的 Windows Form 應用程式專案  
  
#### <a name="to-create-a-new-windows-forms-application-project"></a>若要建立新的 Windows Forms 應用程式專案  
  
1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增**，**專案...**.  
  
2. 展開  **Visual C#**或**Visual Basic**左窗格中，然後選取**的傳統 Windows 桌面**。  

3. 在中間窗格中，選取**Windows Form 應用程式**專案類型。  

4. 將專案命名**DatasetDesignerWalkthrough**，然後選擇 **確定**。  
  
     Visual Studio 將專案加入**方案總管 中**和設計工具中顯示新的表單。  
  
## <a name="adding-a-new-dataset-to-the-application"></a>將新的資料集加入至應用程式  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>將新的資料集項目加入至專案  
  
1.  在**專案**功能表上，選取**加入新項目...**.  
  
     [新增項目] 對話方塊隨即出現。  
  
2.  在左窗格中，選取**資料**，然後選取**資料集**中間窗格內。  
  
3.  命名集**NorthwindDataset**，然後選擇 **新增**。  
  
     Visual Studio 會加入名為的檔案**NorthwindDataset.xsd**至專案，並在開啟**Dataset 設計工具**。  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>在伺服器總管 中建立資料連接  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>若要建立 Northwind 資料庫的連接  
  
1.  在**檢視**功能表上，按一下 **伺服器總管**。  
  
2.  在**伺服器總管**，按一下 [**連接至資料庫**] 按鈕。  
  
3.  建立 Northwind 範例資料庫的連接。  
  
## <a name="creating-the-tables-in-the-dataset"></a>建立資料集內的資料表  
本節說明如何將資料表加入至資料集。  
  
#### <a name="to-create-the-customers-table"></a>若要建立 Customers 資料表  
  
1.  展開您在中建立的資料連接**伺服器總管**，然後展開**資料表**節點。  
  
2.  拖曳**客戶**資料表中**伺服器總管**到**Dataset 設計工具**。  
  
     A**客戶**資料表和**CustomersTableAdapter**加入到資料集。  
  
#### <a name="to-create-the-orders-table"></a>若要建立 Orders 資料表  
  
-   拖曳**訂單**資料表中**伺服器總管**到**Dataset 設計工具**。  
  
     **訂單**資料表格**OrdersTableAdapter**，和資料之間的關聯性**客戶**和**訂單**資料表會加入至資料集。  
  
#### <a name="to-create-the-orderdetails-table"></a>若要建立 OrderDetails 資料表  
  
-   拖曳**Order Details**資料表中**伺服器總管**到**Dataset 設計工具**。  
  
     **Order Details**資料表格**OrderDetailsTableAdapter**，和之間的資料關聯**訂單**和**OrderDetails**資料表會加入至資料集。  
  
## <a name="next-steps"></a>後續步驟  
  
### <a name="to-add-functionality-to-your-application"></a>加入應用程式的功能  
  
-   儲存資料集。  
  
-   選取項目中的**資料來源**視窗並將其拖曳到表單上。 如需詳細資訊，請參閱[繫結 Windows Form 控制項加入 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)。  
  
-   將多個查詢加入至 Tableadapter。 
  
-   將驗證邏輯加入<xref:System.Data.DataTable.ColumnChanging>或<xref:System.Data.DataTable.RowChanging>資料中之資料表的資料集的事件。 如需詳細資訊，請參閱[驗證資料在資料集中](../data-tools/validate-data-in-datasets.md)。  
  
## <a name="see-also"></a>另請參閱
[在 Visual Studio 中建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)  
[將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
[將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
[驗證資料](../data-tools/validate-data-in-datasets.md)   
[儲存資料](../data-tools/saving-data.md)