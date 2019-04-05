---
title: 使用設計工具建立 SQL database |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- SQL Server Express
- local data
- LocalDB
- SQLEXPRESS
- data [Visual Studio], Local data
- SQL Express
- data [Visual Studio], walkthroughs
- databases, creating
- database files, creating
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
caps.latest.revision: 54
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 24aae7066d3fb14a298c780e5cd9f7e91901821e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940419"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>使用設計工具建立 SQL database
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
您可以查看基本工作，例如加入資料表和資料行，以定義可以使用 Visual Studio 來建立和更新 SQL Server Express LocalDB 中的本機資料庫檔案。 當您完成本逐步解說之後，您可以使用本機資料庫做為其他逐步解說的起點，探索更多進階的功能。  
  
 您也可以使用 SQL Server Management Studio （個別下載） 或 TRANSACT-SQL 陳述式中的建立資料庫**SQL Server 物件總管**Visual Studio 中的工具視窗。  
  
 在這個逐步解說中，您將探索下列工作：  
  
-   [建立專案和本機資料庫檔案](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)  
  
-   [建立資料表、 資料行、 主索引鍵和外部索引鍵](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)  
  
-   [填入資料表的資料](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)  
  
## <a name="prerequisites"></a>必要條件  
 若要完成本逐步解說，請確定您已安裝的 SQL Server Data Tools。 在 [**檢視**] 功能表中，您應該會看到**SQL Server 物件總管**。 如果找不到，請移至**新增或移除程式**，按一下**Visual Studio 2015**，選取**變更**，然後選取方塊旁**SQL Server Data Tools**.  
  
##  <a name="BKMK_CreateNewSQLDB"></a> 建立專案和本機資料庫檔案  
  
#### <a name="to-create-a-project-and-a-database-file"></a>若要建立專案和資料庫檔案  
  
1. 建立 Windows Forms 專案，稱為`SampleDatabaseWalkthrough`。  
  
2. 在功能表列上選取**專案** > **加入新項目**。  
  
3. 在項目範本清單中，向下捲動並選取**服務架構資料庫**。  
  
    ![項目範本 對話方塊](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")  
  
4. 為資料庫命名**命名為 SampleDatabase**，然後選取**新增** 按鈕。  
  
5. 如果**資料來源** 視窗未開啟，請開啟它，選取 Shift + Alt + D 鍵，或在功能表列，選取**檢視** > **其他 Windows**  >  **Zdroje dat**。  
  
6. 在 **資料來源**視窗中，選取**加入新的資料來源**連結。  
  
7. 在 **資料來源組態精靈**，選取**下一步**按鈕四次接受預設設定，然後按**完成** 按鈕。  
  
   藉由開啟資料庫的屬性視窗，就可以檢視其連接字串和主要 .mdf 檔案的位置。 您會看到資料庫檔案位於專案資料夾。  
  
-   在 Visual Studio 中，選取**檢視** > **SQL Server 物件總管**如果視窗尚未開啟。 開啟 [屬性] 視窗，展開**資料連接**節點、 開啟 SampleDatabase.mdf，捷徑功能表，然後選取**屬性**。  
  
-   或者，您可以選取**檢視** > **伺服器總管**，如果視窗尚未開啟。 開啟 [屬性] 視窗，展開**資料連接**節點。 針對 SampleDatabase.mdf，開啟捷徑功能表，然後選取**屬性**。  
  
##  <a name="BKMK_CreateNewTbls"></a> 建立資料表、 資料行、 主索引鍵和外部索引鍵  
 在本節中，您將建立幾個資料表、每個資料表中的主索引鍵以及一些範例資料列。 在下一個逐步解說中，您將會了解該資訊可能會以哪種方式出現在應用程式中的概念。 您也會建立外部索引鍵，以指定資料表中的記錄如何與另一個資料表中的記錄對應。  
  
#### <a name="to-create-the-customers-table"></a>若要建立 Customers 資料表  
  
1.  中**伺服器總管**或**SQL Server 物件總管**，展開**資料連接** 節點，然後展開**SampleDatabase.mdf**節點。  
  
2.  開啟捷徑功能表**資料表**，然後選取**加入新的資料表**。  
  
     [資料表設計工具] 隨即開啟並顯示含有一個預設列的格線，這表示您要建立的資料表中的單一資料行。 藉由在格線中加入資料列，您就是在資料表中加入資料行。  
  
3.  在格線中，為下列每一個項目加入一個資料列：  
  
    |資料行名稱|資料類型|允許 Null|  
    |-----------------|---------------|-----------------|  
    |`CustomerID`|`nchar(5)`|False (已清除)|  
    |`CompanyName`|`nvarchar(50)`|False (已清除)|  
    |`ContactName`|`nvarchar (50)`|True (已選取)|  
    |`Phone`|`nvarchar (24)`|True (已選取)|  
  
4.  開啟捷徑功能表`CustomerID`資料列，然後按**設定主索引鍵**。  
  
5.  開啟預設資料列的捷徑功能表，然後選取**刪除**。  
  
6.  透過更新指令碼窗格中的第一行來命名 Customers 資料表，以符合下面範例：  
  
    ```  
    CREATE TABLE [dbo].[Customers]  
    ```  
  
     您應該會看到類似下面的內容：  
  
     ![資料表設計工具](../data-tools/media/raddata-table-designer.png "raddata 資料表設計工具")  
  
7.  在左上角**資料表設計工具**，選取**更新** 按鈕。  
  
8.  在 [**預覽資料庫更新**對話方塊中，選取**更新資料庫**] 按鈕。  
  
     您所做的變更會儲存到本機資料庫檔案中。  
  
#### <a name="to-create-the-orders-table"></a>若要建立 Orders 資料表  
  
1.  加入另一個資料表，然後為下表中的每個項目加入一個資料列：  
  
    |資料行名稱|資料類型|允許 Null|  
    |-----------------|---------------|-----------------|  
    |`OrderID`|`int`|False (已清除)|  
    |`CustomerID`|`nchar(5)`|False (已清除)|  
    |`OrderDate`|`datetime`|True (已選取)|  
    |`OrderQuantity`|`int`|True (已選取)|  
  
2.  設定**OrderID**作為主索引鍵，然後刪除預設資料列。  
  
3.  透過更新指令碼窗格中的第一行來命名 Orders 資料表，以符合下面範例：  
  
    ```  
    CREATE TABLE [dbo].[Orders]  
    ```  
  
4.  在左上角**資料表設計工具**，選取**更新** 按鈕。  
  
5.  在 [**預覽資料庫更新**對話方塊中，選取**更新資料庫**] 按鈕。  
  
     您所做的變更會儲存到本機資料庫檔案中。  
  
#### <a name="to-create-a-foreign-key"></a>若要建立外部索引鍵  
  
1.  在方格右側的 [內容] 窗格，開啟捷徑功能表**外部索引鍵**，然後選取**加入新的外部索引鍵**，如下圖所示。  
  
     ![在 資料表設計工具中加入外部索引鍵](../data-tools/media/foreignkey.png "ForeignKey")  
  
2.  在出現的文字方塊中，將**ToTable**使用`Customers`。  
  
3.  在 [T-SQL] 窗格中，更新最後一行以符合下面範例：  
  
    ```  
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])  
    ```  
  
4.  在左上角**資料表設計工具**，選取**更新** 按鈕。  
  
5.  在 [**預覽資料庫更新**對話方塊中，選取**更新資料庫**] 按鈕。  
  
     您所做的變更會儲存到本機資料庫檔案中。  
  
##  <a name="BKMK_Populating"></a> 填入資料表的資料  
  
#### <a name="to-populate-the-tables-with-data"></a>若要將資料填入資料表  
  
1.  在 **伺服器總管**或**SQL Server 物件總管**，展開範例資料庫的節點。  
  
2.  開啟捷徑功能表**資料表**節點中，選取**重新整理**，然後展開**資料表**節點。  
  
3.  開啟 [客戶] 資料表的捷徑功能表，然後選取**顯示資料表資料**。  
  
4.  針對至少三個客戶，加入任何想要的資料。  
  
     您可以指定要做為客戶 ID 的五個任意字元，不過，請至少選擇一個可記住且之後可在此程序中使用的字元。  
  
5.  開啟 「 訂單 」 資料表的捷徑功能表，然後選取**顯示資料表資料**。  
  
6.  加入至少三筆訂單的資料。  
  
    > [!IMPORTANT]
    >  確定所有訂單 ID 和訂單數量都是整數，而且每個客戶 ID 都符合您在 Customers 資料表的 CustomerID 資料行中指定的值。  
  
7.  在功能表列上選取**檔案** > **全部儲存**。  
  
8.  在功能表列上選取**檔案** > **關閉方案**。  
  
    > [!NOTE]
    >  最佳做法是，複製資料庫檔案，然後將複本貼到其他位置或為複本指定不同的名稱，以此方式備份剛建立的資料庫檔案。  
  
## <a name="next-steps"></a>後續步驟  
 有一些範例資料的本機資料庫檔案之後，您可以完成任何示範資料庫工作的逐步解說。
