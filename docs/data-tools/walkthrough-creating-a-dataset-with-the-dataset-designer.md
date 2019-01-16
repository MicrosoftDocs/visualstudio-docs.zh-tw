---
title: 逐步解說：以 Dataset 設計工具建立資料集
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
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: e79646609bf592b7a8d71d3e0ba8660c65520715
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868510"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>逐步解說：以 Dataset 設計工具建立資料集

在本逐步解說中您建立資料集，使用**Dataset 設計工具**。 本文會引導您完成建立新的專案並加入新的程序**資料集**給它的項目。 您將了解如何建立基礎資料庫中的資料表，而不需使用精靈的資料表。

## <a name="prerequisites"></a>必要條件

本逐步解說會使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1.  如果您沒有 SQL Server Express LocalDB，請將它安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)，或透過**Visual Studio 安裝程式**。 在 Visual Studio 安裝程式，可以安裝 SQL Server Express LocalDB 的一部份**資料儲存和處理**工作負載，或作為個別的元件。

2.  安裝 Northwind 範例資料庫執行下列步驟：

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (SQL Server 物件總管 中已安裝的一部分**資料儲存和處理**Visual Studio 安裝程式中的工作負載。)依序展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢**。

       查詢編輯器視窗隨即開啟。

    2. 複製[Northwind 的 TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。

    3. 將 T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。

       短時間之後，查詢完成執行，並建立 Northwind 資料庫。

## <a name="create-a-new-windows-forms-application-project"></a>建立新的 Windows Forms 應用程式專案

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增** > **專案**。

2. 展開  **Visual C#** 或是**Visual Basic**左窗格中，然後選取**Windows Desktop**。

3. 在中間窗格中，選取**Windows Forms 應用程式**專案類型。

4. 將專案命名為**DatasetDesignerWalkthrough**，然後選擇**確定**。

     Visual Studio 將專案加入**方案總管 中**並顯示新的表單設計工具中。

## <a name="add-a-new-dataset-to-the-application"></a>將新的資料集新增至應用程式

1.  在 [專案] 功能表中，選取 [新增新項目]。

     [新增項目] 對話方塊隨即出現。

2.  在左側窗格中，選取**資料**，然後選取**DataSet**在中間窗格中。

3.  命名資料集**NorthwindDataset**，然後選擇**新增**。

     Visual Studio 會加入名為的檔案**NorthwindDataset.xsd**專案中開啟它並**Dataset 設計工具**。

## <a name="create-a-data-connection-in-server-explorer"></a>在 [伺服器總管] 中建立資料連接

1.  在 [檢視] 功能表上按一下 [伺服器總管]。

2.  在 [**伺服器總管**，按一下**連接到資料庫**] 按鈕。

3.  建立 Northwind 範例資料庫的連接。

## <a name="create-the-tables-in-the-dataset"></a>建立資料集內的資料表

本節說明如何將資料表加入至資料集。

### <a name="to-create-the-customers-table"></a>若要建立 Customers 資料表

1.  展開您在中建立的資料連接**伺服器總管**，然後展開**資料表**節點。

2.  拖曳**客戶**資料表中**伺服器總管**拖曳至**Dataset 設計工具**。

     A**客戶**資料表並**CustomersTableAdapter**加入資料集。

### <a name="to-create-the-orders-table"></a>若要建立 Orders 資料表

-   拖曳**訂單**資料表中**伺服器總管**拖曳至**Dataset 設計工具**。

     **訂單**資料表格**OrdersTableAdapter**，和資料之間的關聯性**客戶**並**訂單**資料表會加入至資料集。

### <a name="to-create-the-orderdetails-table"></a>若要建立 [OrderDetails] 資料表

-   拖曳**訂單明細**資料表中**伺服器總管**拖曳至**Dataset 設計工具**。

     **訂單明細**資料表中， **OrderDetailsTableAdapter**，和之間的資料關聯**訂單**並**OrderDetails**資料表會加入至資料集。

## <a name="next-steps"></a>後續步驟

-   儲存的資料集。

-   選取中的項目**Zdroje dat**視窗並將其拖曳到表單上。 如需詳細資訊，請參閱 <<c0> [ 繫結 Windows Form 控制項加入 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)。

-   加入 Tableadapter 的更多查詢。

-   將驗證邏輯加入<xref:System.Data.DataTable.ColumnChanging>或<xref:System.Data.DataTable.RowChanging>事件的資料集內的資料表。 如需詳細資訊，請參閱 <<c0> [ 驗證資料集中](../data-tools/validate-data-in-datasets.md)。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [驗證資料](../data-tools/validate-data-in-datasets.md)