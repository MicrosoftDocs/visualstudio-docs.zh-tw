---
title: 安裝 SQL Server 範例資料庫 |Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3915351bff74f35ceb5fc462cb29dfd2f322fb6a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299637"
---
# <a name="install-sql-server-sample-databases"></a>安裝 SQL Server 範例資料庫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

範例資料庫適用于試驗 SQL 和 LINQ 查詢、資料系結、Entity Framework 模型等。  每個資料庫產品都有自己的範例資料庫。 Northwind 和 AdventureWorks 是兩個熱門的 SQL Server 範例資料庫。

 **AdventureWorks**是目前為 SQL Server 產品提供的範例資料庫。 您可以從[Codeplex 上的 AdventureWorks 頁面](https://archive.codeplex.com/?p=msftdbprodsamples)將它下載為 .mdf 檔案。 這裡有一般和輕量（LT）版本的資料庫可用。 在大部分的情況下，最好是 LT 版本，因為它比較不復雜。

 **Northwind**是一個相當簡單的 SQL Server 資料庫，已經用過多年了。 您可以從[CodePlex 上的 Northwind 資料庫頁面](https://northwinddatabase.codeplex.com/)，將它下載為 .bak 檔案。 為避免許可權問題，請將檔案解壓縮至不在您的使用者資料夾底下的新資料夾。

#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>若要從中的 .bak 檔案還原資料庫 Visual Studio

1. 當您備份 Microsoft SQL Server 資料庫時，結果會是 .bak 檔案。 若要將 .bak 檔案當做資料庫檔案再次使用，則必須將它*還原*。 在主功能表上，選取 [ **View** > **SQL Server 物件總管**]。 如果看不到，您可能需要安裝它。 移至 [**控制台**] > [**程式和功能**]，尋找 Microsoft Visual Studio 2015，然後按一下 [**變更**] 按鈕。 當安裝的元件清單出現在安裝程式視窗中時，請選取 [ **SQL Server 物件總管**] 核取方塊，然後繼續進行安裝。

2. 在 SQL Server 物件總管中，以滑鼠右鍵按一下任何 SQL Server 的資料庫引擎（例如 localdb），然後選取 [追加**查詢**]。

     ![SQL Server 物件總管新查詢](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata SQL Server 物件總管新查詢")

3. 首先，您需要資料庫的邏輯名稱和 .bak 檔案中的記錄檔。 若要取得它，請在 [SQL 查詢編輯器] 中輸入此查詢，然後選取視窗頂端的綠色 [**執行**] 按鈕。 視需要修改檔案路徑，以指向 .bak 檔案。

    ```
    RESTORE FILELISTONLY
    FROM DISK = 'C:\nw\northwind.bak'
    GO
    ```

     記下 [結果] 視窗中出現的邏輯名稱。  在 Northwind 資料庫中，兩個邏輯名稱是 Northwind 和 Northwind_log。

4. 現在執行此查詢來建立資料庫。 適當地取代您自己的來源和目的地路徑、邏輯資料庫名稱，以及 Northwind 的實體檔案名。 保留 .mdf 和 .ldf 副檔名。

    ```
    RESTORE DATABASE Northwind
    FROM DISK = 'c:\nw\northwind.bak'
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'
    ```

5. 在 SQL Server 物件總管中，以滑鼠右鍵按一下 [**資料庫**] 節點，您應該會看到 Northwind 資料庫節點。 如果沒有，請以滑鼠右鍵按一下 [資料庫]，然後選取 [**加入新的資料庫**]。 輸入您剛才建立之 .mdf 檔案的名稱和位置。

6. 資料庫現在已準備好用來做為 Visual Studio 中的資料來源。

#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>若要從中的 .bak 檔案還原資料庫 SQL Server Management Studio

1. 從下載網站下載 SQL Server Management Studio。

2. 在 SSMS**物件總管** 視窗中，以滑鼠右鍵按一下 **資料庫** 節點，選取 **還原資料庫**，然後提供 .bak 檔案的位置。

     ![SSMS 還原資料庫](../data-tools/media/raddata-ssms-restore-database.png "raddata SSMS 還原資料庫")
