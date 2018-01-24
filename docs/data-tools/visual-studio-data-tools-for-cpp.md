---
title: "C + + 的 visual Studio data tools |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CPP
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 0b7f49708c00bd02fb8c74bc3ed6258d41729bf2
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2018
---
# <a name="visual-studio-data-tools-for-c"></a>C + + 的 visual Studio data tools

當您存取資料來源時，原生 c + + 通常可以提供最快的效能。 不過，Visual Studio 中的 c + + 應用程式的工具的資料不是因為其適用於.NET 應用程式的豐富。 例如，資料來源視窗無法使用拖放到 c + + 設計介面上的資料來源。 如果您需要物件關聯的圖層，您必須自行撰寫，或使用協力廠商產品。  也適用於資料繫結功能，雖然使用 Microsoft Foundation 類別庫的應用程式可以使用某些資料庫類別，以及文件和檢視，可在記憶體中儲存資料，並顯示給使用者。 如需詳細資訊，請參閱[Visual c + + 中的資料存取](/cpp/data/data-access-in-cpp)。

若要連接到 SQL 資料庫，ODBC 和 OLE DB 驅動程式和 ADO 提供者隨附於 Windows，可以使用原生 c + + 應用程式。 這些可以連接到任何支援這些介面的資料庫。 ODBC 驅動程式是標準。 OLE DB 會提供回溯相容性。 如需有關這些資料技術的詳細資訊，請參閱[Windows Data Access Components](https://msdn.microsoft.com/library/windows/desktop/aa968814.aspx)。

利用 SQL Server 2005 中的自訂功能和更新版本中，使用[SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client)。 原生用戶端也會包含 SQL Server ODBC 驅動程式與一個原生動態連結程式庫 (DLL) 中的 SQL Server OLE DB 提供者。 這些項目支援使用 Microsoft SQL server （ODBC、 OLE DB 和 ADO） 的原生程式碼 Api 應用程式。  SQL Server Native Client 會使用 SQL Server Data Tools 安裝。 以下是程式設計指南： [SQL Server Native Client 程式設計](/sql/relational-databases/native-client/sql-server-native-client-programming)。

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>若要從 c + + 應用程式連接到 localDB 透過 ODBC 和 SQL Native Client  
  
1.  安裝 SQL Server Data Tools。  
  
2.  如果您需要連線到範例 SQL 資料庫時，下載 Northwind 資料庫，並將它解壓縮至新位置。  
  
3.  您可以使用 SQL Server Management Studio 來將解壓縮的 Northwind.mdf 檔案附加到 localDB。 SQL Server Management Studio 啟動時，連接到 (localdb) \MSSQLLocalDB。  
  
     ![SSMS 連接對話方塊](../data-tools/media/raddata-ssms-connect-dialog.png "raddata SSMS 連接對話方塊")  
  
     然後以滑鼠右鍵按一下左窗格中的 localdb 節點，並選擇 **附加**。  
  
     ![SSMS 附加資料庫](../data-tools/media/raddata-ssms-attach-database.png "raddata SSMS 附加資料庫")  
  
4.  下載 ODBC Windows SDK 範例中，並將它解壓縮至新位置。 這個範例會示範用來連接到資料庫以及發出查詢命令的基本 ODBC 命令。 您可以進一步了解這些函式[Microsoft 開放式資料庫連接 (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc)。 當您第一次載入的方案 （位於 c + + 資料夾） 時，Visual Studio 會提供升級至目前版本的 Visual Studio 方案。 按一下 [ **是**]。
  
5.  若要使用原生用戶端，您需要它的標頭檔和 lib 檔案。 這些檔案包含函式和 SQL server，超出 sql.h 中定義的 ODBC 函數的專屬定義。 在**專案** > **屬性** > **VC + + 目錄**，加入下列 include 目錄：

**%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

與此程式庫目錄：

**%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6.  將下列幾行 odbcsql.cpp 中。 #Define 可防止不相關的 OLE DB 定義無法進行編譯。  
  
    ```cpp
    #define _SQLNCLI_ODBC_  
    #include <sqlncli.h>  
    ```  
  
    請注意，此範例不實際使用任何原生用戶端功能，因此上述的步驟不需要為其編譯和執行。 但專案現在已設定讓您可以使用這項功能。 如需詳細資訊，請參閱[SQL Server Native Client 程式設計](/sql/relational-databases/native-client/sql-server-native-client)。  
  
7.  指定要使用 ODBC 子系統中的驅動程式。 此範例會將驅動程式連接字串屬性中的傳遞做為命令列引數。 在**專案** > **屬性** > **偵錯**，新增此命令引數：  
  
    ```cpp
    DRIVER="SQL Server Native Client 11.0"  
    ```  
  
8.  按 F5 鍵建置並執行應用程式。 您應該會看到對話方塊，從驅動程式提示您輸入的資料庫。 輸入`(localdb)\MSSQLLocalDB`，並檢查**使用信任連接**。 Press **OK**. 您應該會看到訊息，指出成功連線的主控台。 您也應該看到命令提示字元中您可以在這裡輸入 SQL 陳述式。 下列畫面顯示一個範例查詢和結果：  
  
     ![ODBC 範例查詢輸出](../data-tools/media/raddata-odbc-sample-query-output.png "raddata ODBC 範例查詢輸出")  
  
## <a name="see-also"></a>另請參閱

[存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)