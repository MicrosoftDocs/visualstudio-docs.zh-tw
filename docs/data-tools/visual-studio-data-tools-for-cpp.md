---
title: 適用于的資料工具C++
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 2be19729b61831e6f15ff40b6b4e1d7b4b0bb541
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586051"
---
# <a name="visual-studio-data-tools-for-c"></a>適用於 C++ 的 Visual Studio 資料工具

當C++您存取資料來源時，原生通常可以提供最快的效能。 不過，Visual Studio 中應用C++程式的資料工具不像 .net 應用程式一樣豐富。 例如，[**資料來源**] 視窗無法用來將資料來源拖放到C++設計介面上。 如果您需要物件關係圖層，您必須撰寫自己的，或使用協力廠商產品。 雖然使用 mfc 程式庫的應用程式可以將資料儲存在記憶體中，並向使用者顯示，但這也適用于資料系結功能。 如需詳細資訊，請參閱[Visual C++中的資料存取](/cpp/data/data-access-in-cpp)。

若要連接到 SQL 資料庫， C++原生應用程式可以使用 ODBC 和 OLE DB 驅動程式，以及 Windows 隨附的 ADO 提供者。 這些可以連接到任何支援這些介面的資料庫。 ODBC 驅動程式是標準的。 針對回溯相容性提供 OLE DB。 如需這些資料技術的詳細資訊，請參閱[Windows 資料存取元件](/previous-versions/windows/desktop/ms692897(v=vs.85))。

若要利用 SQL Server 2005 和更新版本中的自訂功能，請使用[SQL Server native client](/sql/relational-databases/native-client/sql-server-native-client)。 Native client 也包含 SQL Server ODBC 驅動程式，以及一個原生動態連結程式庫（DLL）中的 SQL Server OLE DB 提供者。 這些支援使用原生程式碼 Api （ODBC、OLE DB 和 ADO）來 Microsoft SQL Server。 SQL Server Native Client 會隨 SQL Server Data Tools 安裝。 程式設計指南如下： [SQL Server native client 程式設計](/sql/relational-databases/native-client/sql-server-native-client-programming)。

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>透過 ODBC 連接到 localDB，並從C++應用程式 SQL Native Client

1. 安裝 SQL Server Data Tools。

2. 如果您需要可連接的範例 SQL 資料庫，請下載 Northwind 資料庫，並將它解壓縮到新的位置。

3. 使用 SQL Server Management Studio 將已解壓縮的*Northwind .mdf*檔案附加至 localDB。 當 SQL Server Management Studio 啟動時，連接到（localdb） \MSSQLLocalDB。

   ![SSMS [連線] 對話方塊](../data-tools/media/raddata-ssms-connect-dialog.png)

   然後以滑鼠右鍵按一下左窗格中的 localdb 節點，然後選擇 [**附加**]。

   ![SSMS 附加資料庫](../data-tools/media/raddata-ssms-attach-database.png)

4. 下載 ODBC Windows SDK 範例，並將它解壓縮到新的位置。 這個範例會顯示用來連接到資料庫併發出查詢和命令的基本 ODBC 命令。 您可以在[Microsoft 開放式資料庫連接（ODBC）](/sql/odbc/microsoft-open-database-connectivity-odbc)中深入瞭解這些功能。 當您第一次載入方案時（它位於C++資料夾中），Visual Studio 將會提供將解決方案升級至目前 Visual Studio 版本的功能。 按一下 [ **是**]。

5. 若要使用 native client，您需要它的*頭*檔和*lib*檔案。 這些檔案包含 SQL Server 所特有的函式和定義，除了 SQL .h 中定義的 ODBC 函數之外。 在 [**專案** > **屬性**] > [ **VC + + 目錄**] 中，新增下列 include 目錄：

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   和這個程式庫目錄：

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. 在*odbcsql*中新增這些行。 #Define 可防止編譯不相關的 OLE DB 定義。

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    請注意，此範例不會實際使用任何 native client 功能，因此不需要執行上述步驟來進行編譯和執行。 但是專案現在已設定為可供您使用這種功能。 如需詳細資訊，請參閱 [SQL Server Native Client 程式設計](/sql/relational-databases/native-client/sql-server-native-client)。

7. 指定要在 ODBC 子系統中使用的驅動程式。 此範例會將中的驅動程式連接字串屬性傳遞為命令列引數。 在 [**專案** > **屬性**] > [**調試**] 中，新增下列命令引數：

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. 按 **F5** 鍵建置並執行應用程式。 您應該會看到驅動程式中的對話方塊，提示您輸入資料庫。 輸入 `(localdb)\MSSQLLocalDB`，然後勾選 [**使用信任**的連線]。 按 [確定]。 您應該會看到一個主控台，其中包含指出連線成功的訊息。 您也應該會看到可在其中輸入 SQL 語句的命令提示字元。 下列畫面顯示範例查詢和結果：

   ![ODBC 範例查詢輸出](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>請參閱

- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
