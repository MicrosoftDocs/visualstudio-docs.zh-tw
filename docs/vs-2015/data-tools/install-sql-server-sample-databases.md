---
title: 安裝 SQL Server 範例資料庫 |Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 056e5d1fad258d063e30cfd97e85529ff3a0c9bd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160206"
---
# <a name="install-sql-server-sample-databases"></a>安裝 SQL Server 範例資料庫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

範例資料庫適合用來試驗 SQL 和 LINQ 查詢、 資料繫結、 Entity Framework 模型等等。  每個資料庫產品都有它自己的範例資料庫。 Northwind 和 AdventureWorks 是兩個熱門的 SQL Server 範例資料庫。  
  
 **AdventureWorks**是目前的 SQL Server 產品而提供的範例資料庫。 您可以將它下載為.mdf 檔案從[Codeplex 上的 AdventureWorks 頁面](http://msftdbprodsamples.codeplex.com/)。 有可用的資料庫的一般和輕量級 (LT) 版本這裡。 大部分的情況下，建議 l 版本，因為它是較不複雜。  
  
 **Northwind**是相當簡單的 SQL Server 資料庫已使用多年。 您可以將它下載為.bak 檔案從[CodePlex 上的 Northwind 資料庫頁面](https://northwinddatabase.codeplex.com/)。 若要避免權限問題，請將檔案解壓縮到不在您的使用者資料夾下的新資料夾。  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>若要從 Visual Studio 中的.bak 檔案中還原資料庫  
  
1. 當您將 Microsoft SQL Server 資料庫備份時，則結果會是.bak 檔案。 若要讓.bak 檔案可使用一次為資料庫檔案，它必須是*還原*。 在主功能表中，選取**檢視** > **SQL Server 物件總管**。 如果您沒有看到它，您可能需要安裝它。 移至**控制台中** > **程式和功能**，尋找 Microsoft Visual Studio 2015 中，按一下 [**變更**] 按鈕。 當已安裝的元件清單隨即出現在安裝程式視窗中時，選取**SQL Server 物件總管**核取方塊，然後繼續進行安裝。  
  
2. 在 [SQL Server 物件總管] 中，以滑鼠右鍵按一下任何 SQL Server 資料庫引擎 (例如，localdb)，然後選取**新的查詢**。  
  
     ![SQL Server 物件總管新查詢](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata SQL Server 物件總管新查詢")  
  
3. 首先，您需要的資料庫和記錄檔的.bak 檔案內的邏輯名稱。 若要取得它，輸入此查詢到 SQL 查詢編輯器 中，然後選取綠色**執行**在視窗頂端的按鈕。 視需要修改的檔案路徑以指向.bak 檔案。  
  
    ```  
    RESTORE FILELISTONLY  
    FROM DISK = 'C:\nw\northwind.bak'  
    GO  
    ```  
  
     記下出現在 [結果] 視窗中的邏輯名稱。  對於 Northwind 資料庫中，Northwind 和 Northwind_log 的兩個的邏輯名稱。  
  
4. 現在執行此查詢來建立資料庫。 替代成您自己的來源和目的地的路徑、 邏輯資料庫名稱和 Northwind 適當的實體檔案名稱。 保留的.mdf 和.ldf 副檔名。  
  
    ```  
    RESTORE DATABASE Northwind  
    FROM DISK = 'c:\nw\northwind.bak'  
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',  
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'  
    ```  
  
5. 在 SQL Server 物件總管 中，以滑鼠右鍵按一下**資料庫** 節點，而且您應該會看到 Northwind 資料庫 節點。 如果沒有，然後以滑鼠右鍵按一下資料庫，然後選取**加入新的資料庫**。 輸入名稱和您剛才建立的.mdf 檔案的位置。  
  
6. 現在準備好要做為 Visual Studio 中的資料來源的資料庫。  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>若要從 SQL Server Management Studio 中的.bak 檔案中還原資料庫  
  
1. 從下載網站下載 SQL Server Management Studio。  
  
2. 在 SSMS**物件總管** 視窗中，以滑鼠右鍵按一下**資料庫**節點中，選取**Restore Database**，並提供.bak 檔案的位置。  
  
     ![SSMS 還原資料庫](../data-tools/media/raddata-ssms-restore-database.png "raddata SSMS 還原資料庫")
