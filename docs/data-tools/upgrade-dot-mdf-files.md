---
title: 升級 .mdf 檔案
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 195cab863554bc60478df4e80319eab80124140a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586090"
---
# <a name="upgrade-mdf-files"></a>升級 .mdf 檔案

本主題描述在安裝較新版本的 Visual Studio 之後，用來升級資料庫檔案（ *.mdf*）的選項。 其中包含下列工作的指示：

- 升級資料庫檔案以使用較新版本的 SQL Server Express LocalDB

- 升級資料庫檔案以使用較新版本的 SQL Server Express

- 在 Visual Studio 中使用資料庫檔案，但保留與舊版 SQL Server Express 或 LocalDB 的相容性

- 將 SQL Server Express 設為預設的資料庫引擎

您可以使用 Visual Studio 開啟專案，其中包含使用舊版 SQL Server Express 或 LocalDB 所建立的資料庫檔案（ *.mdf*）。 不過，若要繼續在 Visual Studio 中開發專案，您必須在與 Visual Studio 相同的電腦上安裝該版本的 SQL Server Express 或 LocalDB，或者您必須升級資料庫檔案。 如果您升級資料庫檔案，您將無法使用舊版的 SQL Server Express 或 LocalDB 來存取該檔案。

如果檔案的版本與目前安裝的 SQL Server Express 或 LocalDB 實例不相容，可能也會提示您升級透過舊版 SQL Server Express 或 LocalDB 所建立的資料庫檔案。 若要解決此問題，Visual Studio 會提示您升級檔案。

> [!IMPORTANT]
> 我們建議您先備份資料庫檔案，然後再進行升級。

> [!WARNING]
> 如果您將 LocalDB 2014 （V12）32位所建立的 *.mdf*檔案升級為 localdb 2016 （V13）或更新版本，您將無法在 localdb 的32版本中再次開啟該檔案。

在您升級資料庫之前，請考慮下列準則：

- 如果您想要在舊版和較新版本的 Visual Studio 中處理專案，請不要升級。

- 如果您的應用程式將用於使用 SQL Server Express 而不是 LocalDB 的環境，請不要升級。

- 如果您的應用程式使用遠端連線，請不要升級，因為 LocalDB 不接受它們。

- 如果您的應用程式依賴 Internet Information Services （IIS），請不要升級。

- 如果您想要在沙箱環境中測試資料庫應用程式，但不想要管理資料庫，請考慮升級。

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>若要升級資料庫檔案以使用 LocalDB 版本

1. 在**伺服器總管**中，選取 [**連接到資料庫]** 按鈕。

2. 在 [**加入連接**] 對話方塊中，指定下列資訊：

    - **資料來源**：`Microsoft SQL Server (SqlClient)`

    - **伺服器名稱**：

        - 若要使用預設版本： `(localdb)\MSSQLLocalDB`。  這會根據安裝的 Visual Studio 版本以及建立第一個 LocalDB 實例的時間，指定 ProjectV12 或 ProjectV13。 **SQL Server 物件總管**中的 [ **MSSQLLocalDB** ] 節點會顯示其指向的版本。

        - 若要使用特定版本： `(localdb)\ProjectsV12` 或 `(localdb)\ProjectsV13`，其中 V12 是 LocalDB 2014，而 V13 是 LocalDB 2016。

    - **附加資料庫**檔案：主要 *.mdf*檔案的實體路徑。

    - 邏輯名稱(&L):您想要使用的檔案名稱。

3. 選取 [確定] 按鈕。

4. 當系統提示您時，請選取 [**是]** 按鈕以升級檔案。

    資料庫已升級、附加至 LocalDB 資料庫引擎，且不再與舊版的 LocalDB 相容。

您也可以藉由開啟連接的快捷方式功能表，然後選取 [**修改連接**]，修改 SQL Server Express 連接以使用 LocalDB。 在 [**修改連接**] 對話方塊中，將伺服器名稱變更為 `(LocalDB)\MSSQLLocalDB`。 在 [**高級屬性**] 對話方塊中，確定 [**使用者實例**] 已設定為 [ **False**]。

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>若要升級資料庫檔案以使用 SQL Server Express 版本

1. 在資料庫連接的快捷方式功能表上，選取 [**修改連接**]。

2. 在 [**修改連接**] 對話方塊中，選取 [ **Advanced** ] 按鈕。

3. 在 [ **Advanced Properties** ] 對話方塊中，選取 [**確定]** 按鈕，而不變更伺服器名稱。

    資料庫檔案會升級，以符合目前的 SQL Server Express 版本。

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>若要在 Visual Studio 中使用資料庫，但保留與 SQL Server Express 的相容性

- 在 Visual Studio 中，開啟專案但不升級。

  - 若要執行專案，請選取**F5**鍵。

  - 若要編輯資料庫，請在**方案總管**中開啟 *.mdf*檔案，然後展開**伺服器總管**中的節點，以使用您的資料庫。

### <a name="to-make-sql-server-express-the-default-database-engine"></a>若要讓 SQL Server Express 預設的資料庫引擎

1. 在功能表列上選取 [工具] > [選項]。

2. 在 [**選項**] 對話方塊中，展開 [**資料庫工具**] 選項，然後選取 [**資料連線**]。

3. 在 [ **SQL Server 實例名稱**] 文字方塊中，指定您想要使用之 SQL Server Express 或 LocalDB 實例的名稱。 如果實例未命名，請指定 `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`。

4. 選取 [確定] 按鈕。

    SQL Server Express 將是您應用程式的預設資料庫引擎。

## <a name="see-also"></a>請參閱

- [存取 Visual Studio 中的資料](accessing-data-in-visual-studio.md)
