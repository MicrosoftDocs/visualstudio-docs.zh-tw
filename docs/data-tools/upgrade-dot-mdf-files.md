---
title: 升級 .mdf 檔案
description: 在安裝較新版本的 Visual Studio 之後，請參閱將資料庫檔案升級 ( .mdf) 的選項。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: cbea7761ed5f36265464f2afe9a64550ddc5e62a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866303"
---
# <a name="upgrade-mdf-files"></a>升級 .mdf 檔案

本主題說明在安裝較新版本的 Visual Studio 之後，將資料庫檔案升級 (.mdf) 的選項 *。* 其中包含下列工作的指示：

- 升級資料庫檔案以使用較新版本的 SQL Server Express LocalDB

- 將資料庫檔案升級為使用較新版本的 SQL Server Express

- 使用 Visual Studio 中的資料庫檔案，但保留與舊版 SQL Server Express 或 LocalDB 的相容性

- 使 SQL Server Express 預設的資料庫引擎

您可以使用 Visual Studio 來開啟包含資料庫檔案的專案， (.mdf) 是使用舊版 SQL Server Express 或 LocalDB 所建立的 *。* 不過，若要繼續在 Visual Studio 中開發專案，您必須將該版本的 SQL Server Express 或 LocalDB 安裝在與 Visual Studio 相同的電腦上，或者您必須升級資料庫檔案。 如果您升級資料庫檔案，將無法使用舊版 SQL Server Express 或 LocalDB 來存取它。

如果檔案的版本與目前安裝的 SQL Server Express 或 LocalDB 實例不相容，系統可能也會提示您升級透過舊版 SQL Server Express 或 LocalDB 所建立的資料庫檔案。 若要解決此問題，Visual Studio 會提示您升級檔案。

> [!IMPORTANT]
> 建議您在升級之前先備份資料庫檔案。

> [!WARNING]
> 如果您將在 LocalDB 2014 (V12) 32 位中建立的 *.mdf* 檔案升級至 localdb 2016 (V13) 或更新版本，您將無法在 localdb 的32位版本中再次開啟該檔案。

升級資料庫之前，請考慮下列準則：

- 如果您想要在舊版和較新版本的 Visual Studio 中處理專案，請不要升級。

- 如果您的應用程式將用於使用 SQL Server Express 而非 LocalDB 的環境中，請不要升級。

- 如果您的應用程式使用遠端連線，請不要升級，因為 LocalDB 不接受這些連接。

- 如果您的應用程式依賴 Internet Information Services (IIS) ，則請勿升級。

- 如果您想要在沙箱環境中測試資料庫應用程式，但不想管理資料庫，請考慮升級。

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>升級資料庫檔案以使用 LocalDB 版本

1. 在 **伺服器總管** 中，選取 [ **連接到資料庫]** 按鈕。

2. 在 [ **加入連接** ] 對話方塊中，指定下列資訊：

    - **資料來源**： `Microsoft SQL Server (SqlClient)`

    - **伺服器名稱**：

        - 若要使用預設版本： `(localdb)\MSSQLLocalDB` 。  這會指定 ProjectV12 或 ProjectV13，視安裝的 Visual Studio 版本以及第一個 LocalDB 實例的建立時間而定。 **SQL Server 物件總管** 中的 [ **MSSQLLocalDB** ] 節點會顯示其所指向的版本。

        - 若要使用特定版本： `(localdb)\ProjectsV12` 或 `(localdb)\ProjectsV13` ，其中 V12 是 localdb 2014，而 V13 是 localdb 2016。

    - **附加資料庫** 檔案：主要 *.mdf* 檔案的實體路徑。

    - 邏輯名稱(&L):您想要使用的檔案名稱。

3. 選取 [ **確定]** 按鈕。

4. 當系統提示您時，請選取 [ **是]** 按鈕升級檔案。

    資料庫已升級、附加至 LocalDB 資料庫引擎，且不再與舊版 LocalDB 相容。

您也可以藉由開啟連接的快捷方式功能表，然後選取 [ **修改連接**]，來修改 SQL Server Express 連接以使用 LocalDB。 在 [ **修改連接** ] 對話方塊中，將伺服器名稱變更為 `(LocalDB)\MSSQLLocalDB` 。 在 [ **Advanced Properties** ] 對話方塊中，確定 [ **使用者實例** ] 設定為 [ **False**]。

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>升級資料庫檔案以使用 SQL Server Express 版本

1. 在連接至資料庫的快捷方式功能表上，選取 [ **修改連接**]。

2. 在 [ **修改連接** ] 對話方塊中，選取 [ **Advanced** ] 按鈕。

3. 在 [ **Advanced Properties** ] 對話方塊中，選取 [ **確定]** 按鈕，而不變更伺服器名稱。

    資料庫檔案會升級，以符合目前的 SQL Server Express 版本。

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>若要在 Visual Studio 中使用資料庫，但維持與 SQL Server Express 的相容性

- 在 Visual Studio 中，開啟專案而不進行升級。

  - 若要執行專案，請選取 **F5** 鍵。

  - 若要編輯資料庫，請在 **方案總管** 中開啟 *.mdf* 檔案，然後在 **伺服器總管** 中展開該節點，以使用您的資料庫。

### <a name="to-make-sql-server-express-the-default-database-engine"></a>使 SQL Server Express 預設的資料庫引擎

1. 在功能表列上選取 [工具] > [選項]。

2. 在 [ **選項** ] 對話方塊中，展開 [ **資料庫工具** ] 選項，然後選取 [ **資料連線**]。

3. 在 [ **SQL Server 實例名稱** ] 文字方塊中，指定您要使用之 SQL Server Express 或 LocalDB 實例的名稱。 如果實例未命名，請指定 `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB` 。

4. 選取 [ **確定]** 按鈕。

    SQL Server Express 將會是應用程式的預設資料庫引擎。

## <a name="see-also"></a>另請參閱

- [存取 Visual Studio 中的資料](accessing-data-in-visual-studio.md)
