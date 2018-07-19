---
title: C + + 的 visual Studio 資料工具
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: fe50ecd01b8f3112340510a78f76d6e380ec3136
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117026"
---
# <a name="visual-studio-data-tools-for-c"></a>C + + 的 visual Studio 資料工具

當您存取資料來源時，原生 c + + 通常可以提供最快的效能。 不過，不是因為它是.NET 應用程式的豐富工具在 Visual Studio 中的 c + + 應用程式的資料。 比方說，不能使用資料來源視窗，拖放到 c + + 設計介面上的資料來源。 如果您需要物件關聯式層次，您必須自行撰寫，或使用協力廠商產品。  這也適用於資料繫結功能，雖然使用 Microsoft Foundation Class 程式庫的應用程式可以使用一些資料庫類別，以及文件和檢視儲存在記憶體中的資料，並顯示給使用者。 如需詳細資訊，請參閱 < [Visual c + + 中的資料存取](/cpp/data/data-access-in-cpp)。

若要連接到 SQL database，ODBC 和 OLE DB 驅動程式和隨附於 Windows 而 ADO 提供者，可以使用原生 c + + 應用程式。 這些可以連線到任何資料庫，可支援這些介面。 ODBC 驅動程式是標準。 OLE DB 提供回溯相容性。 如需有關這些資料技術的詳細資訊，請參閱 < [Windows Data Access Components](https://msdn.microsoft.com/library/windows/desktop/aa968814.aspx)。

利用 SQL Server 2005 中的自訂功能和更新版本中，使用[SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client)。 原生用戶端也包含 SQL Server ODBC 驅動程式，並在單一原生動態連結程式庫 (DLL) 的 SQL Server OLE DB 提供者。 這些支援使用 Microsoft SQL server （ODBC、 OLE DB 和 ADO） 的原生程式碼 Api 應用程式。  SQL Server Native Client 會使用 SQL Server Data Tools 安裝。 程式設計指南已正式推出： [SQL Server Native Client 程式設計](/sql/relational-databases/native-client/sql-server-native-client-programming)。

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>從 c + + 應用程式連接到 localDB 透過 ODBC 和 SQL Native Client

1.  安裝 SQL Server Data Tools。

2.  如果您需要連接到範例 SQL 資料庫，請下載 Northwind 資料庫，並將它解壓縮到新位置。

3.  使用 SQL Server Management Studio 附加解壓縮*Northwind.mdf* localDB 的檔案。 SQL Server Management Studio 啟動時，連接到 (localdb) \MSSQLLocalDB。

     ![SSMS 連線對話方塊](../data-tools/media/raddata-ssms-connect-dialog.png)

     然後以滑鼠右鍵按一下左窗格中的 [localdb] 節點，然後選擇**附加**。

     ![SSMS 附加資料庫](../data-tools/media/raddata-ssms-attach-database.png)

4.  下載 ODBC Windows SDK 範例中，並將它解壓縮到新位置。 此範例示範用來連接到資料庫並發出查詢命令的基本 ODBC 命令。 您可以深入了解在這些函式[Microsoft 開放式資料庫連接 (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc)。 當您第一次載入的方案 （位於 c + + 資料夾） 時，Visual Studio 將會提供升級至目前版本的 Visual Studio 的方案。 按一下 [ **是**]。

5.  若要使用原生用戶端，您需要其*標頭*檔案並*lib*檔案。 這些檔案包含函式和 SQL server 之外定義 sql.h 的 ODBC 函式的專屬定義。 在 **專案** > **屬性** > **VC + + 目錄**，加入下列 include 目錄：

**%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

與此程式庫目錄：

**%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6.  將下列行中的新增*odbcsql.cpp*。 #Define 可防止不相關的 OLE DB 定義，從正在進行編譯。

    ```cpp
    #define _SQLNCLI_ODBC_
    #include <sqlncli.h>
    ```

    請注意，範例不會實際使用的任何原生用戶端功能，因此上述的步驟不需要讓它編譯並執行。 但您可以使用這項功能現在已設定專案。 如需詳細資訊，請參閱 < [SQL Server Native Client 程式設計](/sql/relational-databases/native-client/sql-server-native-client)。

7.  指定要使用 ODBC 子系統中的驅動程式。 此範例會將驅動程式連接字串屬性中的傳遞做為命令列引數。 在 **專案** > **屬性** > **偵錯**，加入這個命令引數：

    ```cpp
    DRIVER="SQL Server Native Client 11.0"
    ```

8.  按 **F5** 鍵建置並執行應用程式。 您應該會看到一個對話方塊會提示您輸入資料庫的驅動程式。 請輸入`(localdb)\MSSQLLocalDB`，並檢查**使用信任連接**。 按下**確定**。 您應該會看到主控台中，使用訊息，指出成功的連線。 您也應該看到命令提示字元中。 您可以在這裡輸入 SQL 陳述式。 下列畫面顯示一個範例查詢和結果：

     ![ODBC 範例查詢的輸出](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>另請參閱

- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)