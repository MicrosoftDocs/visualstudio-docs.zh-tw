---
title: 使用 DataSet 設計工具建立資料集
description: 在這個逐步解說中，請使用 DataSet 設計工具建立資料集。 瞭解建立新專案的程式，並在其中加入新的資料集專案。
ms.custom: SEO-VS-2020
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b1fe1d75673dc47f423cf398118230cd1530def0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866225"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>逐步解說：使用 DataSet 設計工具建立資料集

在這個逐步解說中，您會使用 **DataSet 設計工具** 來建立資料集。 本文會引導您完成建立新專案的程式，並在其中加入新的 **資料集** 專案。 您將瞭解如何在不使用 wizard 的情況下，根據資料庫中的資料表建立資料表。

## <a name="prerequisites"></a>必要條件

本逐步解說使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1. 如果您沒有 LocalDB SQL Server Express，請從 [SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)或透過 **Visual Studio 安裝程式** 進行安裝。 在 Visual Studio 安裝程式中，SQL Server Express LocalDB 可以安裝為 **資料儲存和處理** 工作負載的一部分，或作為個別的元件。

2. 遵循下列步驟來安裝 Northwind 範例資料庫：

    1. 在 Visual Studio 中，開啟 [ **SQL Server 物件總管** ] 視窗。  (SQL Server 物件總管會安裝為 Visual Studio 安裝程式中 **資料儲存和處理** 工作負載的一部分。 ) 展開 **SQL Server** 節點。 以滑鼠右鍵按一下您的 LocalDB 實例，然後選取 [追加 **查詢**]。

       [查詢編輯器] 視窗隨即開啟。

    2. 將 [Northwind transact-sql 腳本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 複製到剪貼簿。 此 T-sql 腳本會從頭開始建立 Northwind 資料庫，並在其中填入資料。

    3. 將 T-sql 腳本貼入 [查詢編輯器]，然後選擇 [ **執行** ] 按鈕。

       經過一小段時間之後，查詢就會完成執行，並建立 Northwind 資料庫。

## <a name="create-a-new-windows-forms-application-project"></a>建立新的 Windows Forms 應用程式專案

1. 在 Visual Studio 中，於 [檔案]  功能表上選取 [新增]   > [專案]  。

2. 展開左側窗格中的 [ **Visual c #** ] 或 [ **Visual Basic** ]，然後選取 [ **Windows 桌面**]。

3. 在中間窗格中，選取 [ **Windows Forms 應用程式** ] 專案類型。

4. 將專案命名為 **DatasetDesignerWalkthrough**，然後選擇 **[確定]**。

     Visual Studio 將專案加入至 **方案總管** ，並在設計工具中顯示新表單。

## <a name="add-a-new-dataset-to-the-application"></a>將新的資料集新增至應用程式

1. 在 [專案] 功能表上，選取 [新增項目]。

     [加入新項目]  對話方塊隨即出現。

2. 在左窗格中，選取 [ **資料**]，然後在中間窗格中選取 [資料 **集** ]。

3. 將資料集命名為 **NorthwindDataset**，然後選擇 [ **加入**]。

     Visual Studio 會將名為 **NorthwindDataset** 的檔案新增至專案，並在 **DataSet 設計工具** 中開啟。

## <a name="create-a-data-connection-in-server-explorer"></a>在伺服器總管中建立資料連線

1. 在 [檢視] 功能表上按一下 [伺服器總管]。

2. 在 **伺服器總管** 中，按一下 [ **連接到資料庫]** 按鈕。

3. 建立與 Northwind 範例資料庫的連接。

## <a name="create-the-tables-in-the-dataset"></a>在資料集中建立資料表

本節說明如何將資料表加入至資料集。

### <a name="to-create-the-customers-table"></a>若要建立 Customers 資料表

1. 展開您在 **伺服器總管** 中建立的資料連線，然後展開 [ **資料表]** 節點。

2. 將 **Customers** 資料表從 **伺服器總管** 拖曳至 **DataSet 設計工具**。

     **客戶** 資料表和 **CustomersTableAdapter** 會加入至資料集。

### <a name="to-create-the-orders-table"></a>若要建立 Orders 資料表

- 將 **Orders** 資料表從 **伺服器總管** 拖曳至 **DataSet 設計工具**。

     **Orders** 資料表、 **OrdersTableAdapter**，以及 **Customers** 與 **Orders** 資料表之間的資料關聯性會新增至資料集。

### <a name="to-create-the-orderdetails-table"></a>若要建立 OrderDetails 資料表

- 將 [ **Order Details** ] 資料表從 **伺服器總管** 拖曳至 **DataSet 設計工具**。

     訂單 **詳細** 資料資料表、 **OrderDetailsTableAdapter**，以及 **Orders** 和 **OrderDetails** 資料表之間的資料關聯性會新增至資料集。

## <a name="next-steps"></a>後續步驟

- 儲存資料集。

- 在 [ **資料來源** ] 視窗中選取專案，並將它們拖曳到表單上。 如需詳細資訊，請參閱 [將 Windows Forms 控制項系結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)。

- 將更多查詢加入至 Tableadapter。

- 將驗證邏輯加入至 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> 資料集內資料表的或事件。 如需詳細資訊，請參閱 [驗證資料集中的資料](../data-tools/validate-data-in-datasets.md)。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [驗證資料](../data-tools/validate-data-in-datasets.md)
