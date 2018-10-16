---
title: 使用指令碼中建立 SQL database |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 13816c499002f8eaf81067aba8d1854d06a41445
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266587"
---
# <a name="create-a-sql-database-by-using-a-script"></a>使用指令碼中建立 SQL database
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
在本逐步解說中，您可以使用 Visual Studio 建立一個小型資料庫，其中包含的範例程式碼[使用 ADO.NET 建立簡單資料應用程式](../data-tools/create-a-simple-data-application-by-using-adonet.md)。  
  
 **本主題內容**  
  
-   [建立包含資料庫結構描述的指令碼](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
-   [建立資料庫專案並匯入結構描述](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
-   [將資料庫部署](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## <a name="prerequisites"></a>必要條件  
 若要完成此逐步解說中，您必須有 SQL Server Express LocalDB 或另一個 SQL database，安裝。  
  
##  <a name="CreateScript"></a> 建立包含資料庫結構描述的指令碼  
  
#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>若要建立指令碼，您可以從中匯入結構描述  
  
1.  在  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，在功能表列中，選取**檔案** > **新增** > **檔案**。  
  
     **新的檔案** 對話方塊隨即出現。  
  
2.  在 **分類**清單中，選取**一般**。  
  
3.  在 [**範本**清單中，選取**Sql 檔案**，然後選取**開啟**] 按鈕。  
  
     TRANSACT-SQL 編輯器隨即開啟。  
  
4.  下列 TRANSACT-SQL 程式碼中，複製並貼到 TRANSACT-SQL 編輯器。  
  
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
  
5.  在功能表列上選取**檔案** > **另存 SqlQuery_1.sql 為**。  
  
     **另存新檔** 對話方塊隨即出現。  
  
6.  在 [**檔名**方塊中，輸入`SampleImportScript.sql`，記下的位置中，您將在其中儲存檔案，然後按**儲存**] 按鈕。  
  
7.  在功能表列上選取**檔案** > **關閉方案**。  
  
     接下來，建立資料庫專案，並從您已建立的指令碼，然後匯入結構描述。  
  
##  <a name="CreateProject"></a> 建立資料庫專案並匯入結構描述  
  
#### <a name="to-create-a-database-project"></a>建立資料庫專案  
  
1.  在功能表列上，選取 [檔案] > [新增] > [專案]。  
  
     [ **新增專案** ] 對話方塊隨即出現。  
  
2.  底下**已安裝**，展開**範本**節點，展開**其他語言**節點中，選取**SQL Server**類別目錄，然後選取  **SQL Server 資料庫專案**範本。  
  
    > [!NOTE]
    >  **其他語言**節點不會出現在 Visual Studio 的所有安裝。  
  
3.  在 **名稱**方塊中，輸入`Small Database`。  
  
4.  選取 **為方案建立目錄**如果尚未選取的核取方塊。  
  
5.  清除**加入原始檔控制**核取方塊，如果還沒有已清除，然後再選取**確定** 按鈕。  
  
     資料庫專案建立時，會出現在**方案總管 中**。  
  
     從指令碼，接下來，匯入資料庫結構描述。  
  
#### <a name="to-import-a-database-schema-from-a-script"></a>若要從指令碼匯入資料庫結構描述  
  
1.  在功能表列上選取**專案** > **匯入** > **指令碼**。  
  
2.  在 **歡迎**頁面上，檢閱文字，然後選取**下一步**  按鈕。  
  
3.  選取 [**單一檔案**選項按鈕，然後按**瀏覽**] 按鈕。  
  
     **匯入 SQL 指令碼** 對話方塊隨即出現。  
  
4.  開啟您儲存 SampleImportScript.sql 檔案的資料夾、 選取檔案，然後按**開啟** 按鈕。  
  
5.  選取 [**完成**按鈕以關閉**匯入 SQL 指令碼**] 對話方塊。  
  
     匯入指令碼時，並將指令碼會定義物件加入至資料庫專案。  
  
6.  檢閱 摘要，然後按**完成**按鈕以關閉**匯入 SQL 指令碼檔** 對話方塊。  
  
7.  在**方案總管 中**，銷售額、 指令碼，以及安全性，依序展開您的專案的資料夾，並確認皆包含.sql 檔案。  
  
8.  在  **SQL Server 物件總管**，確認資料庫出現在**專案**節點。  
  
     到目前為止，資料庫只包含系統物件，例如資料表和預存程序。 部署資料庫之後，它會包含使用者資料表和預存程序指令碼定義。  
  
##  <a name="DeployDatabase"></a> 將資料庫部署  
 當您按下**F5**金鑰，您將部署 （或發行） 至 LocalDB 資料庫的預設資料庫。 您可以將資料庫部署到不同的位置開啟專案的 [屬性] 頁面選取**偵錯**索引標籤，然後再變更連接字串。

