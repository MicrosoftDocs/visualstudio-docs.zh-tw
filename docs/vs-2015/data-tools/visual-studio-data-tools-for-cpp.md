---
title: 適用于 c + + 的 Visual Studio data tools |Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: ec68d54ced85737d66c64ca2dbf7942ca81e5314
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621215"
---
# <a name="visual-studio-data-tools-for-c"></a>適用於 C++ 的 Visual Studio 資料工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您存取資料來源時，原生 c + + 通常可以提供最快的效能。 不過，在 Visual Studio 中，c + + 應用程式的資料工具不像 .NET 應用程式一樣豐富。 例如，[資料來源] 視窗無法用來將資料來源拖放至 c + + 設計介面。 如果您需要物件關聯式層，您必須自行撰寫，或使用協力廠商產品。  這同樣適用于資料系結功能，雖然使用 Microsoft Foundation Class 程式庫的應用程式可以使用一些資料庫類別（以及檔和視圖）來將資料儲存在記憶體中，並將資料顯示給使用者。 如需詳細資訊，請參閱 [Visual C++ 中的資料存取](https://msdn.microsoft.com/library/7wtdsdkh.aspx) 。

 若要連接到 SQL database，原生 c + + 應用程式可以使用 ODBC 和 OLE DB 驅動程式，以及 Windows 隨附的 ADO 提供者。     這些可以連接到任何支援這些介面的資料庫。 ODBC 驅動程式是標準的。 OLE DB 是為了回溯相容性而提供。 如需這些資料技術的詳細資訊，請參閱 [Windows 資料存取元件](https://msdn.microsoft.com/library/windows/desktop/aa968814\(v=vs.85\).aspx)

 若要利用 SQL Server 2005 和更新版本中的自訂功能，請使用 [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733)。 原生用戶端也包含 SQL Server ODBC 驅動程式，以及一個原生動態連結程式庫 (DLL) 中的 SQL Server OLE DB 提供者。 這些支援使用原生程式碼 Api 的應用程式 (ODBC、OLE DB 和 ADO) Microsoft SQL Server。  SQL Server Native Client 使用 SQL Server Data Tools 進行安裝。 程式設計指南如下： [SQL Server Native Client 程式設計](https://msdn.microsoft.com/library/ms130892.aspx)。

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>透過 ODBC 連接至 localDB，並從 c + + 應用程式 SQL Native Client

1. 安裝 SQL Server Data Tools。

2. 如果您需要可連接的範例 SQL database，請下載 Northwind 資料庫，並將它解壓縮至新的位置。

3. 使用 SQL Server Management Studio 將解壓縮的 Northwind .mdf 檔案附加至 localDB。 當 SQL Server Management Studio 啟動時，連接到 (localdb) \MSSQLLocalDB。

    ![SSMS 連接對話方塊](../data-tools/media/raddata-ssms-connect-dialog.png "raddata SSMS connect 對話方塊")

    然後以滑鼠右鍵按一下左窗格中的 localdb 節點，然後選擇 [ **附加**]。

    ![SSMS 附加資料庫](../data-tools/media/raddata-ssms-attach-database.png "raddata SSMS 附加資料庫")

4. 下載 ODBC Windows SDK 範例，並將它解壓縮至新的位置。 這個範例會顯示用來連接到資料庫併發出查詢和命令的基本 ODBC 命令。 您可以在 [Microsoft 開放式資料庫連接 (ODBC) ](https://msdn.microsoft.com/library/windows/desktop/ms710252\(v=vs.85\).aspx)中深入瞭解這些功能。 當您第一次載入方案時 (它會在 c + + 資料夾) 中，Visual Studio 將會提供將解決方案升級為目前版本的 Visual Studio。 按一下 [是]  。

5. 若要使用 native client，您需要它的標頭檔和 lib 檔。 這些檔案包含在 SQL 中所定義之 ODBC 函數以外 SQL Server 的函數和定義。 在 [**專案**屬性] 的 [  >  **Properties**  >  **VC + + 目錄**] 中，新增下列 include 目錄：

   ** \<system drive> ： \PROGRAM Files\Microsoft SQL Server\110\SDK\Include**和這個程式庫目錄：

   **c:\Program Files\Microsoft SQL Server\110\SDK\Lib**

6. 在 odbcsql 中新增這些行。 #Define 防止編譯不相關的 OLE DB 定義。

   ```
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    請注意，此範例不會實際使用任何原生用戶端功能，因此不需要使用上述步驟來編譯和執行。 但現在已將專案設定為使用這項功能。 如需詳細資訊，請參閱 [SQL Server Native Client 程式設計](https://msdn.microsoft.com/library/ms130892\(v=sql.130\).aspx)。

7. 指定要在 ODBC 子系統中使用的驅動程式。 此範例會將中的驅動程式連接字串屬性傳遞為命令列引數。 在 [**專案**  >  **屬性**]  >  **調試**中，加入下列命令引數：

   ```
   DRIVER="SQL Server Native Client 11.0"
   ```

8. 按 F5 以建置並執行應用程式。 您應該會看到驅動程式提示您輸入資料庫的對話方塊。 輸入 `(localdb)\MSSQLLocalDB` ，並核取 [ **使用信任的連接**]。 按下 **[確定]**。 您應該會看到主控台顯示訊息，指出連接成功。 您也應該會看到命令提示字元，您可以在其中輸入 SQL 語句。 下列畫面顯示範例查詢和結果：

    ![ODBC 範例查詢輸出](../data-tools/media/raddata-odbc-sample-query-output.png "raddata ODBC 範例查詢輸出")

## <a name="see-also"></a>另請參閱
 [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
