---
title: R 與 SQL Server 整合
description: Visual Studio 支援使用 R 建立及執行 SQL 查詢，以及讓 R 使用預存程序的功能。
ms.date: 06/25/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: c0aedbccdb82bd91fe201a23b6201a3cdd7db283
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908689"
---
# <a name="work-with-sql-server-and-r"></a>使用 SQL Server 和 R

Visual Studio 對於 SQL Server 有絕佳的支援，可讓資料科學家建立和執行 SQL 查詢以及使用預存程序，進而協助使用 R 和 SQL 資料庫。

> [!Note]
> 若要一起使用 SQL 和 R，您必須安裝 SQL Server Data Tools：
> - Visual Studio 2017︰執行 Visual Studio 安裝程式，並選取資料儲存和處理工作負載，包括 SQL Server Data Tools。
> - Visual Studio 2015：依[下載 SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt) 中的指示執行。

:::row:::
    :::column:::
        ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片")
    :::column-end:::
    :::column:::
        如需 SQL Server 與 R 的概觀，[請觀看影片 (youtube.com)](https://www.youtube.com/watch?v=n4AYr0QIwdQ) (3 分 03 秒)。
    :::column-end:::
:::row-end:::

## <a name="create-and-run-sql-queries"></a>建立和執行 SQL 查詢

RTVS 支援將 SQL 查詢新增到 R 專案，讓您在不同的內容中反覆開發 SQL 查詢，直到達到您想要的結果。

若要新增 SQL 查詢檔案，請以滑鼠右鍵按一下方案總管中的專案，選取 [**加入**  >  **新專案**]，然後選取 [ **SQL 查詢** 檔案類型]：

![將 SQL 查詢項目新增至專案](media/sql-add-item.png)

此命令會在 Visual Studio 的 Transact-SQL 編輯器中開啟檔案，提供完整的 IntelliSense for SQL 及執行查詢的能力。 若要讓這些功能運作，您需要使用編輯器工具列的 [連接] 按鈕連接到資料庫，或嘗試執行 (**Ctrl** + **Shift** + **E** 的查詢，這也適用于選取的) 。 任一方式都會顯示 [連線] 對話方塊︰

![SQL 連線對話方塊](media/sql-connection-dialog.png)

一旦建立連線，您就可以執行查詢並查看結果︰

![SQL 視窗查詢結果](media/sql-query-results.png)

Transact-SQL 編輯器支援各種不同的其他功能，例如檢視查詢執行計劃以及查詢偵錯工具。
如需詳細資訊，請參閱[使用 Transact-SQL 編輯器，編輯及執行指令碼](/previous-versions/sql/sql-server-data-tools/hh272706(v=vs.103))。

## <a name="work-with-sql-server-stored-procedures"></a>使用 SQL Server 預存程序

[SQL Server R 服務](/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 和更新版本) 讓您從 T-SQL 預存程序內嵌及執行 R 程式碼。 您可以在 SQL Server 電腦上執行 R 程式碼、操作從 SQL 查詢傳回的資料，以及產生 SQL 結果集，供日後的 SQL 處理或傳回給用戶端。

如下列各節所述，RTVS 簡化因將 SQL 和 R 程式碼結合在單一的 SQL 陳述式中，本來會很龐大且容易發生錯誤的程序︰

- [新增資料庫連接](#add-a-database-connection)
- [撰寫及測試 SQL 預存程序](#write-and-test-a-sql-stored-procedure)
- [發行 SQL 預存程序](#publish-a-sql-stored-procedure)

:::row:::
    :::column:::
        ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片")
    :::column-end:::
    :::column:::
        如需 R 和 SQL 預存程序的概觀，[請觀看影片 (youtube.com)](https://www.youtube.com/watch?v=dFKIT2OitWQ) (6 分 09 秒).
    :::column-end:::
:::row-end:::

### <a name="add-a-database-connection"></a>新增資料庫連接

1. 選取 [ **R 工具**  >  **資料**  >  **加入資料庫連接**]，以顯示 [**連接屬性**] 對話方塊。 您可以在這裡指定資料來源名稱 (在此情況下是 SQL Server)、伺服器名稱、驗證模式，以及資料庫名稱。 選取 [測試連接] 先驗證您的輸入，再關閉對話方塊。

    ![SQL 連線對話方塊](media/sql-connection-string-dialog.png)

1. 一旦您對有效的連線選取 [確定]，Visual Studio 就會在新的 *settings.R* 檔案中產生名為 `dbConnection` 的連接字串。 RTVS 自動將此檔案設為來源 (執行)，因此您可以立即使用 R 指令碼中的連接︰

![SQL Settings.R 檔案](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>撰寫及測試 SQL 預存程序

若要加入新的 SQL 預存程式，請在專案上按一下滑鼠右鍵、選取 [**加入**  >  **新專案**]、從範本清單中選取 [**具有 R 的 SQL 預存** 程式]、為檔案命名，然後選取 **[確定]**。 預設檔名為 *SqlSProc.R*；為了便於閱讀，本節的其餘部分會使用檔名 *StoredProcedure.R*。 如果您有多個預存程序，每個檔案必須具有唯一的檔名。

RTVS 會為預存程序建立三個檔案：*.R* 檔案供 R 程式碼使用、*.Query.sql* 檔案供 SQL 程式碼使用，而 *.Template.sql* 檔案則結合這兩者。 後面兩個會出現在 [方案總管] 中，作為 *.R* 檔案的子系：

![使用 R 之 SQL 預存程序的方案總管展開檢視](media/sql-solution-explorer-expanded.png)

*.R* 檔案 (在此範例中為 *StoredProcedure.R*) 是您撰寫 R 程式碼的位置。 預設內容如下︰

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

簡言之，程式碼會接收稱為 `InputDataSet` 的 R 資料框架，並使用 `OutputDataSet` 傳回其結果，範本程式碼只將輸入複製到輸出。

> [!Note]
> 這些資料框架的名稱是由 `sp_execute_external_script` 系統預存程序呼叫中的 `@input_data_1_name` 和 `@output_data_1_name` 參數所控制。 如需此呼叫慣例設計及其用法範例的詳細資訊，請參閱 [sp_execute_external_script (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)。

在註解中產生的其他程式碼會提供小型測試指令碼，以使用 [RODBC 套件](https://cran.r-project.org/web/packages/RODBC/index.html) 將 SQL 陳述式傳輸至 SQL Server、執行它，並擷取其結果集為 R 資料框架。 您可以取消註解此測試程式碼，以互動方式針對您從 SQL Server 中取得的結果集撰寫 R 程式碼。

*.Query.sql* 檔案 (在此範例中為 *StoredProcedure.Query.sql*) 是您撰寫和測試 SQL 查詢以產生 `InputDataSet` 資料的位置。 使用此 *.sql* 檔案，編輯器可將所有一般 Transact-SQL 功能提供給您。

對 SQL 程式碼感到滿意後，請將 *.sql* 檔案拖曳至 *.R* 檔案的開放式編輯器，以將它與 R 程式碼整合。 在下圖中，*StoredProcedure.Query.sql* 已拖曳到 `sqlQuery(channel, )` 逗號後 *StoredProcedure.R* 的點中：

![將 SQL 檔案讀入 R 字串變數](media/sql-reference-sql-file-from-r.png)

如您所見，這個簡單的步驟會自動產生 R 程式碼以開啟 *.sql* 檔案，並將其內容讀入字串，然後將它傳遞給 RODBC 套件以傳送給 SQL Server。

您現在可以透過互動方式撰寫 R 程式碼，以操作所需的 `InputDataSet` 資料框架。 請記住，您可以在編輯器中只選取 R 程式碼，並按 **Ctrl**+**Enter** 將它傳送至 [互動式視窗](interactive-repl-for-r-in-visual-studio.md)。

最後，*.Template.sql* 檔案 (在此範例中為 *StoredProcedure.Template.sql*) 會包含用於產生 SQL 預存程序的範本：

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- `_RCODE_` 預留位置會取代為 *.R* 檔案 (例如 *StoredProcedure.R*) 的內容。
- `_INPUT_QUERY_` 預留位置會取代為 *.Query.sql* 檔案 (例如 *StoredProcedure.Query.sql*) 的內容。
- 編輯 `WITH RESULT SETS` 子句，描述預存程序所傳回結果集的結構描述。 特別要識別來自您想要傳回給預存程序呼叫端的 `OutputDataSet` 資料框架的資料行。

以下列查詢為例：

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

您可以使用下列 `WITH RESULT SETS` 子句來指定傳回值的資料類型︰

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>發行 SQL 預存程序

1. 選取 [ **R 工具**  >  **資料**  >  **發佈與選項**] 功能表命令。
1. 在出現的對話方塊中，將 [Publish to:] (發行到:) 變更為 [資料庫]，並指定目標，然後選取 [發行]，RTVS 就會建置及發行預存程序︰

    ![發行預存程序對話方塊](media/sql-publish-with-options.png)

1. 若要發行專案中的所有預存程式，您可以使用 [ **R 工具**  >  **資料**  >  **發佈預存程式**] 命令，此命令也適用于以滑鼠右鍵按一下方案總管中的專案時。

> [!Tip]
> 如果 SQL Server 物件總管在 Visual Studio 中開啟，則您已發行的預存程式會出現在資料庫 **的 [可**  >  程式性 **預存程式**] 資料夾中。 以滑鼠右鍵按一下並選取 [執行程序]，或在 *.sql* 查詢視窗中以互動方式呼叫它，即可從物件總管中執行它。