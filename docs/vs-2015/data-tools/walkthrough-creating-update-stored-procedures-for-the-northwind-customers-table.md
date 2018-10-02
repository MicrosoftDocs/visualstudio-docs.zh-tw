---
title: 逐步解說： 建立更新 Northwind Customers 資料表的項目預存程序 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
helpviewer_keywords:
- Northwind sample database
- stored procedures [Visual Studio]
- O/R Designer, stored procedures
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: bbcd68b7604f7a80546168406146f326e1bac224
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485102"
---
# <a name="walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table"></a>逐步解說：建立 Northwind Customers 資料表的更新預存程序
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在某些 [說明] 主題[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]文件還需要額外的預存程序，在 Northwind 範例資料庫中 Customers 資料表中執行的資料的更新 （插入、 更新和刪除）。  
  
 此逐步解說提供在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的 Northwind 範例資料庫中建立這些額外預存程序的指引。  
  
 本主題稍後的＜後續步驟＞一節會提供主題的連結，示範如何使用這些額外預存程序。  
  
 在此逐步解說中，您會學到如何執行下列工作：  
  
-   建立 Northwind 範例資料庫的資料連接。  
  
-   建立預存程序。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您需要：  
  
-   SQL Server 版本的 Northwind 範例資料庫的存取權。 如需詳細資訊，請參閱 <<c0> [ 如何： 安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## <a name="connecting-to-the-northwind-database"></a>連接 Northwind 資料庫  
 此逐步解說需要連接 SQL Server 版本的 Northwind 資料庫。 下列程序提供建立資料連接的指引。  
  
> [!NOTE]
>  若您已經有 Northwind 資料庫的資料連接，可以直接到下一節＜建立預存程序＞。  
  
#### <a name="to-create-a-data-connection-to-the-northwind-sql-server-database"></a>建立 Northwind SQL Server 資料庫的資料連接  
  
1.  在 [**檢視**] 功能表中，按一下**伺服器總管**/**資料庫總管**。  
  
2.  以滑鼠右鍵按一下**資料連接**然後按一下**加入連接**。  
  
3.  在 [**選擇資料來源**] 對話方塊中，按一下**Microsoft SQL Server**，然後按一下 **[確定]**。  
  
     如果**加入連接** 對話方塊隨即開啟，而**資料來源**不**Microsoft SQL Server (SqlClient)**，按一下 **變更**開啟**選擇/變更資料來源** 對話方塊中，按一下**Microsoft SQL Server**，然後按一下**確定**。  
  
4.  按一下 **伺服器名稱**在下拉式清單，或輸入 Northwind 資料庫所在的伺服器的名稱。  
  
5.  根據資料庫或應用程式的需求，請按一下**使用 Windows 驗證**，或使用特定的使用者名稱和密碼來登入執行 SQL Server 的電腦 (**的SQLServer驗證**).  
  
6.  按一下 Northwind 資料庫中的**選取或輸入資料庫名稱**清單。  
  
7.  按一下 [確定 **Deploying Office Solutions**]。  
  
     資料連線 」 新增至**伺服器總管**/**資料庫總管**。  
  
## <a name="creating-the-stored-procedures"></a>建立預存程序  
 藉由使用提供的 SQL 指令碼執行針對 Northwind 資料庫中建立預存程序[Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1)中可用**伺服器總管**/ **資料庫總管**。  
  
#### <a name="to-create-the-stored-procedures-by-using-a-sql-script"></a>使用 SQL 指令碼建立預存程序  
  
1.  展開 Northwind 資料庫中的**伺服器總管**/**資料庫總管**。  
  
2.  以滑鼠右鍵按一下**預存程序**節點，然後按一下**加入新的預存程序**。  
  
3.  將下列程式碼貼入程式碼編輯器中，取代 `CREATE PROCEDURE` 範本：  
  
    ```  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'SelectCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.[SelectCustomers]  
    GO  
  
    CREATE PROCEDURE dbo.[SelectCustomers]  
    AS  
        SET NOCOUNT ON;  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM dbo.Customers  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'InsertCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.InsertCustomers  
    GO  
  
    CREATE PROCEDURE dbo.InsertCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24)  
    )  
    AS  
        SET NOCOUNT OFF;  
    INSERT INTO [dbo].[Customers] ([CustomerID], [CompanyName], [ContactName], [ContactTitle], [Address], [City], [Region], [PostalCode], [Country], [Phone], [Fax]) VALUES (@CustomerID, @CompanyName, @ContactName, @ContactTitle, @Address, @City, @Region, @PostalCode, @Country, @Phone, @Fax);  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'UpdateCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.UpdateCustomers  
    GO  
  
    CREATE PROCEDURE dbo.UpdateCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24),  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    UPDATE [dbo].[Customers] SET [CustomerID] = @CustomerID, [CompanyName] = @CompanyName, [ContactName] = @ContactName, [ContactTitle] = @ContactTitle, [Address] = @Address, [City] = @City, [Region] = @Region, [PostalCode] = @PostalCode, [Country] = @Country, [Phone] = @Phone, [Fax] = @Fax WHERE (([CustomerID] = @Original_CustomerID));  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'DeleteCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.DeleteCustomers  
    GO  
  
    CREATE PROCEDURE dbo.DeleteCustomers  
    (  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    DELETE FROM [dbo].[Customers] WHERE (([CustomerID] = @Original_CustomerID))  
    GO  
    ```  
  
4.  選取所有文字在程式碼編輯器，以滑鼠右鍵按一下選取的文字，然後按一下**執行選取範圍**。  
  
     隨即會建立 Northwind 資料庫的 SelectCustomers、InsertCustomers、UpdateCustomers 及 DeleteCustomers 預存程序。  
  
## <a name="next-steps"></a>後續步驟  
 現在您已建立預存程序，您可以嘗試進行下列示範如何使用它們的逐步說明：  
  
 [如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [逐步解說： 建立 LINQ to SQL 類別 （O-R 設計工具）](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)  
  
 [逐步解說：自訂實體類別的插入、更新和刪除行為](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)