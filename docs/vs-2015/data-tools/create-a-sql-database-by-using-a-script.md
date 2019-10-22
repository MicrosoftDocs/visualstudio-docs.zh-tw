---
title: 使用腳本建立 SQL 資料庫 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3bef7c4be2f38d0f50b2a13c7745cb212204769b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670084"
---
# <a name="create-a-sql-database-by-using-a-script"></a>使用指令碼建立 SQL 資料庫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在此逐步解說中，您會使用 Visual Studio 來建立一個小型資料庫，其中包含[使用 ADO.NET 建立簡單資料應用程式](../data-tools/create-a-simple-data-application-by-using-adonet.md)的範例程式碼。

 **本主題內容**

- [建立包含資料庫架構的腳本](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)

- [建立資料庫專案並匯入架構](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)

- [部署資料庫](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)

## <a name="prerequisites"></a>Prerequisites
 若要完成此逐步解說，您必須安裝 SQL Server Express LocalDB 或另一個 SQL database。

## <a name="CreateScript"></a>建立包含資料庫架構的腳本

#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>建立可從中匯入架構的腳本

1. 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的功能表列上 **，選取 [** 檔案  > **新增** > **檔案**]。

     [**新增**檔案] 對話方塊隨即出現。

2. 在 [**類別**] 清單中，選取 **[一般**]。

3. 在 [**範本**] 清單中，選取 [ **Sql**檔案]，然後選取 [**開啟**] 按鈕。

     隨即開啟 [Transact-sql 編輯器]。

4. 複製下列 Transact-sql 程式碼，然後將它貼入 Transact-sql 編輯器中。

    ```
    PRINT N'Creating Sales...';
    GO
    CREATE SCHEMA [Sales]
        AUTHORIZATION [dbo];
    GO
    PRINT N'Creating Sales.Customer...';
    GO
    CREATE TABLE [Sales].[Customer] (
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,
        [CustomerName] NVARCHAR (40) NOT NULL,
        [YTDOrders]    INT           NOT NULL,
        [YTDSales]     INT           NOT NULL
    );
    GO
    PRINT N'Creating Sales.Orders...';
    GO
    CREATE TABLE [Sales].[Orders] (
        [CustomerID] INT      NOT NULL,
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,
        [OrderDate]  DATETIME NOT NULL,
        [FilledDate] DATETIME NULL,
        [Status]     CHAR (1) NOT NULL,
        [Amount]     INT      NOT NULL
    );
    GO
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';
    GO
    ALTER TABLE [Sales].[Customer]
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];
    GO
    PRINT N'Creating Sales.Def_Customer_YTDSales...';
    GO
    ALTER TABLE [Sales].[Customer]
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];
    GO
    PRINT N'Creating Sales.Def_Orders_OrderDate...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];
    GO
    PRINT N'Creating Sales.Def_Orders_Status...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];
    GO
    PRINT N'Creating Sales.PK_Customer_CustID...';
    GO
    ALTER TABLE [Sales].[Customer]
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);
    GO
    PRINT N'Creating Sales.PK_Orders_OrderID...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);
    GO
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;
    GO
    PRINT N'Creating Sales.CK_Orders_FilledDate...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));
    GO
    PRINT N'Creating Sales.CK_Orders_OrderDate...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));
    GO
    PRINT N'Creating Sales.uspCancelOrder...';
    GO
    CREATE PROCEDURE [Sales].[uspCancelOrder]
    @OrderID INT
    AS
    BEGIN
    DECLARE @Delta INT, @CustomerID INT
    BEGIN TRANSACTION
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;

    UPDATE [Sales].[Orders]
       SET [Status] = 'X'
    WHERE [OrderID] = @OrderID;

    UPDATE [Sales].[Customer]
       SET
       YTDOrders = YTDOrders - @Delta
        WHERE [CustomerID] = @CustomerID
    COMMIT TRANSACTION
    END
    GO
    PRINT N'Creating Sales.uspFillOrder...';
    GO
    CREATE PROCEDURE [Sales].[uspFillOrder]
    @OrderID INT, @FilledDate DATETIME
    AS
    BEGIN
    DECLARE @Delta INT, @CustomerID INT
    BEGIN TRANSACTION
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;

    UPDATE [Sales].[Orders]
       SET [Status] = 'F',
           [FilledDate] = @FilledDate
    WHERE [OrderID] = @OrderID;

    UPDATE [Sales].[Customer]
       SET
       YTDSales = YTDSales + @Delta
        WHERE [CustomerID] = @CustomerID
    COMMIT TRANSACTION
    END
    GO
    PRINT N'Creating Sales.uspNewCustomer...';
    GO
    CREATE PROCEDURE [Sales].[uspNewCustomer]
    @CustomerName NVARCHAR (40),
    @CustomerID INT OUTPUT
    AS
    BEGIN
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);
    SET @CustomerID = SCOPE_IDENTITY();
    RETURN @@ERROR
    END
    GO
    PRINT N'Creating Sales.uspPlaceNewOrder...';
    GO
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'
    AS
    BEGIN
    DECLARE @RC INT
    BEGIN TRANSACTION
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)
    SELECT @RC = SCOPE_IDENTITY();
    UPDATE [Sales].[Customer]
       SET
       YTDOrders = YTDOrders + @Amount
        WHERE [CustomerID] = @CustomerID
    COMMIT TRANSACTION
    RETURN @RC
    END
    GO
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]
    @CustomerID INT=0
    AS
    BEGIN
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]
      FROM [Sales].[Customer] AS C
      INNER JOIN [Sales].[Orders] AS O
         ON [O].[CustomerID] = [C].[CustomerID]
      WHERE [C].[CustomerID] = @CustomerID
    END
    GO
    ```

5. 在功能表列上 **，選取 [** 檔案]  >  **[將 SqlQuery_1 儲存為**]。

     [**另存**新檔] 對話方塊隨即出現。

6. 在 [**檔案名**] 方塊中，輸入 `SampleImportScript.sql`，記下儲存檔案的位置，然後選取 [**儲存**] 按鈕。

7. 在功能表列上 **，選取** 檔案  > **關閉方案**。

     接下來，建立資料庫專案，然後從您建立的腳本匯入架構。

## <a name="CreateProject"></a>建立資料庫專案並匯入架構

#### <a name="to-create-a-database-project"></a>建立資料庫專案

1. 在功能表列上，選取 [檔案] > [新增] > [專案]。

     [ **新增專案** ] 對話方塊隨即出現。

2. 在 [**已安裝**] 底下，展開 [**範本**] 節點，展開 [**其他語言**] 節點，選取 [ **SQL Server** ] 類別，然後選取 [ **SQL Server 資料庫] 專案**範本。

    > [!NOTE]
    > [**其他語言**] 節點不會出現在 Visual Studio 的所有安裝中。

3. 在 [**名稱**] 方塊中，輸入 `Small Database`。

4. 選取 [**為方案建立目錄**] 核取方塊（如果尚未選取）。

5. 清除 [**加入至原始檔控制**] 核取方塊（如果尚未清除），然後選取 [**確定]** 按鈕。

     資料庫專案隨即建立，並出現在**方案總管**中。

     接下來，從腳本匯入資料庫架構。

#### <a name="to-import-a-database-schema-from-a-script"></a>若要從腳本匯入資料庫架構

1. 在功能表列上，選取 [**專案**] [ >  匯**入** > **腳本**]。

2. 在 [**歡迎使用**] 頁面上，檢查文字，然後選取 [**下一步]** 按鈕。

3. 選取 [**單一**檔案] 選項按鈕，然後選取 [**流覽]** 按鈕。

     [匯**入 SQL 腳本**] 對話方塊隨即出現。

4. 開啟您儲存 SampleImportScript 的資料夾，選取該檔案，然後選取 [**開啟**] 按鈕。

5. 選取 [**完成]** 按鈕以關閉 [匯**入 SQL 腳本**] 對話方塊。

     系統會匯入腳本，並將腳本所定義的物件加入至您的資料庫專案。

6. 檢查 [摘要]，然後按一下 [**完成]** 按鈕以關閉 [匯**入 SQL 腳本**檔案] 對話方塊。

7. 在**方案總管**中，展開專案的 [銷售]、[腳本] 和 [安全性] 資料夾，並確認其中包含 .sql 檔案。

8. 在  **SQL Server 物件總管**中，確認資料庫出現在 **專案** 節點底下。

     此時，資料庫只會包含系統物件，例如資料表和預存程式。 在您部署資料庫之後，它會包含腳本所定義的使用者資料表和預存程式。

## <a name="DeployDatabase"></a>部署資料庫
 當您按**F5**鍵時，預設會將資料庫部署（或發行）至 LocalDB 資料庫。 您可以藉由開啟專案的 [屬性] 頁面，選取 [**調試**程式] 索引標籤，然後變更連接字串，將資料庫部署到不同的位置。
