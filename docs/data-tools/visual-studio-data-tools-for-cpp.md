---
title: 適用于 c + + 的資料工具
description: 探索適用于 c + + 的 Visual Studio data tools。 從 c + + 應用程式透過 ODBC 和 SQL native client 連接到 localDB。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
dev_langs:
- CPP
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 4cf316e0d892e8c6ba229a7a46ee0439797d032f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866342"
---
# <a name="visual-studio-data-tools-for-c"></a>適用於 C++ 的 Visual Studio 資料工具

當您存取資料來源時，原生 c + + 通常可以提供最快的效能。 不過，在 Visual Studio 中，c + + 應用程式的資料工具不像 .NET 應用程式一樣豐富。 例如，[ **資料來源** ] 視窗無法用來將資料來源拖放至 c + + 設計介面。 如果您需要物件關聯式層，您必須自行撰寫，或使用協力廠商產品。 這同樣適用于資料系結功能，雖然使用 Microsoft Foundation Class 程式庫的應用程式可以使用一些資料庫類別（以及檔和視圖）來將資料儲存在記憶體中，並將資料顯示給使用者。 如需詳細資訊，請參閱 [Visual C++ 中的資料存取](/cpp/data/data-access-in-cpp)。

若要連接到 SQL database，原生 c + + 應用程式可以使用 ODBC 和 OLE DB 驅動程式，以及 Windows 隨附的 ADO 提供者。 這些可以連接到任何支援這些介面的資料庫。 ODBC 驅動程式是標準的。 OLE DB 是為了回溯相容性而提供。 如需這些資料技術的詳細資訊，請參閱 [Windows Data Access Components](/previous-versions/windows/desktop/ms692897(v=vs.85))。

若要利用 SQL Server 2005 和更新版本中的自訂功能，請使用 [SQL Server native client](/sql/relational-databases/native-client/sql-server-native-client)。 原生用戶端也包含 SQL Server ODBC 驅動程式，以及一個原生動態連結程式庫 (DLL) 中的 SQL Server OLE DB 提供者。 這些支援使用原生程式碼 Api 的應用程式 (ODBC、OLE DB 和 ADO) Microsoft SQL Server。 SQL Server Native Client 使用 SQL Server Data Tools 進行安裝。 程式設計指南如下： [SQL Server native client 程式設計](/sql/relational-databases/native-client/sql-server-native-client-programming)。

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>透過 ODBC 連接至 localDB，並從 c + + 應用程式 SQL Native Client

1. 安裝 SQL Server Data Tools。

2. 如果您需要可連接的範例 SQL database，請下載 Northwind 資料庫，並將它解壓縮至新的位置。

3. 使用 SQL Server Management Studio 將解壓縮的 *Northwind .mdf* 檔案附加至 localDB。 當 SQL Server Management Studio 啟動時，連接到 (localdb) \MSSQLLocalDB。

   ![SSMS 連接對話方塊](../data-tools/media/raddata-ssms-connect-dialog.png)

   然後以滑鼠右鍵按一下左窗格中的 localdb 節點，然後選擇 [ **附加**]。

   ![SSMS 附加資料庫](../data-tools/media/raddata-ssms-attach-database.png)

4. 下載 ODBC Windows SDK 範例，並將它解壓縮至新的位置。 這個範例會顯示用來連接到資料庫併發出查詢和命令的基本 ODBC 命令。 您可以在 [Microsoft 開放式資料庫連接 (ODBC) ](/sql/odbc/microsoft-open-database-connectivity-odbc)中深入瞭解這些功能。 當您第一次載入方案時 (它會在 c + + 資料夾) 中，Visual Studio 將會提供將解決方案升級為目前版本的 Visual Studio。 按一下 [是]  。

5. 若要使用 native client，您需要它的 *頭* 檔和 *lib* 檔。 這些檔案包含在 SQL 中所定義之 ODBC 函數以外 SQL Server 的函數和定義。 在 [**專案** 屬性] 的 [  >    >  **VC + + 目錄**] 中，新增下列 include 目錄：

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   和這個程式庫目錄：

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. 在 *odbcsql* 中新增這些行。 #Define 防止編譯不相關的 OLE DB 定義。

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    請注意，此範例不會實際使用任何原生用戶端功能，因此不需要使用上述步驟來編譯和執行。 但現在已將專案設定為使用這項功能。 如需詳細資訊，請參閱 [SQL Server Native Client 程式設計](/sql/relational-databases/native-client/sql-server-native-client)。

7. 指定要在 ODBC 子系統中使用的驅動程式。 此範例會將中的驅動程式連接字串屬性傳遞為命令列引數。 在 [**專案**  >  **屬性**]  >  **調試** 中，加入下列命令引數：

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. 按 **F5** 以建置並執行應用程式。 您應該會看到驅動程式提示您輸入資料庫的對話方塊。 輸入 `(localdb)\MSSQLLocalDB` ，並核取 [ **使用信任的連接**]。 按下 **[確定]**。 您應該會看到主控台顯示訊息，指出連接成功。 您也應該會看到命令提示字元，您可以在其中輸入 SQL 語句。 下列畫面顯示範例查詢和結果：

   ![ODBC 範例查詢輸出](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>另請參閱

- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
