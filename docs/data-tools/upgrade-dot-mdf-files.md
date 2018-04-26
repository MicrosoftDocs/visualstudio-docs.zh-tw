---
title: 升級的.mdf 檔案
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fa7fac39e8f198c473bf79a68a48feb136eccda3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="upgrade-mdf-files"></a>升級的.mdf 檔案

本主題說明安裝較新版的 Visual Studio 之後，升級資料庫檔案 (.mdf) 選項。 它包含下列工作的指示：

- 升級使用較新版的 SQL Server Express LocalDB 資料庫檔案

- 升級使用較新版的 SQL Server Express 資料庫檔案

- 使用 Visual Studio 中的資料庫檔案，但會保留與舊版的 SQL Server Express 或 LocalDB 的相容性

- 讓 SQL Server Express 的預設資料庫引擎

您可以使用 Visual Studio 開啟包含資料庫檔案 (.mdf)，以使用較舊版本的 SQL Server Express 或 LocalDB 所建立的專案。 不過，若要繼續開發您的專案，Visual Studio 中，您必須具有該版本的 SQL Server Express 或 LocalDB 安裝在與 Visual Studio 中，在相同電腦上，或者您必須升級資料庫檔案。 如果您升級資料庫檔案，您將無法使用舊版的 SQL Server Express 或 LocalDB 存取它。

您可能也會提示您升級的檔案版本不相容的 SQL Server Express 或目前已安裝的 LocalDB 執行個體，如果是舊版的 SQL Server Express 或 LocalDB 透過建立的資料庫檔案。 若要解決此問題，Visual Studio 會提示您升級檔。

> [!IMPORTANT]
> 我們建議您在升級之前備份的資料庫檔案。

> [!WARNING]
> 如果您升級至 LocalDB 2016 (V13) 的 32 位元 LocalDB 2014 (V12) 中所建立的.mdf 檔案或更新版本中，您將無法在 32 位元版本的 LocalDB 再次開啟檔案。

當您升級資料庫之前，請考慮下列準則：

-   如果您要使用舊版和新版的 Visual Studio 中的專案不升級。

-   如果您的應用程式會使用 SQL Server Express 而非 LocalDB 的環境中使用不升級。

-   不升級您的應用程式會使用遠端連線，如果，因為 LocalDB 不同意這些授權條款。

-   如果應用程式都需要網際網路資訊服務 (IIS) 上不升級。

-   如果您想要在沙箱環境中測試的資料庫應用程式，但不想要管理資料庫，請考慮升級。

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>若要升級為使用 LocalDB 版本的資料庫檔案

1.  在**伺服器總管**，選取**連接至資料庫** 按鈕。

2.  在**加入連接**對話方塊方塊中，指定下列資訊：

    -   **資料來源**: `Microsoft SQL Server (SqlClient)`

    -   **伺服器名稱**:

        -   若要使用的預設版本： `(localdb)\MSSQLLocalDB`。  這會指定 ProjectV12 或 ProjectV13，視所安裝的 Visual Studio 版本，以及第一個 LocalDB 執行個體的建立時間而定。 **MSSQLLocalDB**節點**SQL Server 物件總管**顯示哪一個版本指向。

        -   若要使用的特定版本：`(localdb)\ProjectsV12`或`(localdb)\ProjectsV13`，其中 V12 是 LocalDB 2014 而 V13 是 LocalDB 2016。

    -   **附加資料庫檔案**： 於主要.mdf 檔案的實體路徑。

    -   **邏輯名稱**： 您想要使用與檔案的名稱。

3.  選取 [確定] 按鈕。

4.  當提示您時，請選取**是**升級檔的按鈕。

    資料庫會升級、 附加至 LocalDB 資料庫引擎，而不再使用 LocalDB 的舊版本相容。

您也可以修改 SQL Server Express 要使用的連線 LocalDB 的開啟連接的捷徑功能表，然後選取**修改連接**。 在**修改連接**對話方塊方塊中，變更伺服器名稱以`(LocalDB)\MSSQLLocalDB`。 在**進階屬性**對話方塊方塊中，請確定**使用者執行個體**設**False**。

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>若要升級的資料庫檔案，若要使用的 SQL Server Express 版本

1.  在資料庫連接的捷徑功能表，選取**修改連接**。

2.  在**修改連接**對話方塊中，選取**進階** 按鈕。

3.  在**進階屬性**對話方塊中，選取**確定**按鈕而不需要變更伺服器名稱。

    要比對目前版本的 SQL Server Express 升級資料庫檔案。

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>若要使用 Visual Studio 中的資料庫，但會保留與 SQL Server Express 的相容性

-   在 Visual Studio 中開啟，而不升級專案。

    -   若要執行專案時，選取**F5**索引鍵。

    -   若要編輯資料庫中，開啟 [.mdf 檔案的**方案總管] 中**，並展開中的節點**伺服器總管**才能使用您的資料庫。

### <a name="to-make-sql-server-express-the-default-database-engine"></a>若要讓 SQL Server Express 的預設資料庫引擎

1.  在功能表列上，選取**工具**，**選項**。

2.  在**選項**對話方塊方塊中，展開 [**資料庫工具**選項]，然後選取**資料連接**。

3.  在**SQL Server 執行個體名稱**文字中，指定 SQL Server Express 或您想要使用的 LocalDB 執行個體的名稱。 如果不具名執行個體，指定`.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`。

4.  選取 [確定] 按鈕。

    SQL Server Express，將會是您的應用程式的預設 database engine。

## <a name="see-also"></a>另請參閱

- [存取 Visual Studio 中的資料](accessing-data-in-visual-studio.md)