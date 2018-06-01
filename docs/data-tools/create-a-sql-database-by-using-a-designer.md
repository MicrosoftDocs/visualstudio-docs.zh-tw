---
title: 建立資料庫檔案，並在 Visual Studio 中使用資料表設計工具
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 433a8bc7cae982b5ec8106966ec8c6ca0af45076
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34690922"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>建立資料庫，並在 Visual Studio 中加入資料表
您可以使用 Visual Studio 建立及更新 SQL Server Express LocalDB 中的本機資料庫檔案。 您也可以藉由執行 TRANSACT-SQL 陳述式中的建立資料庫**SQL Server 物件總管**Visual Studio 中的工具視窗。 本主題中，我們將建立的.mdf 檔案，並使用資料表設計工具中加入資料表和索引鍵。

## <a name="prerequisites"></a>必要條件
若要完成此逐步解說，您必須具有選擇性**資料儲存和處理**安裝 Visual Studio 中的工作負載。 若要安裝，請開啟**Visual Studio 安裝程式**選擇**工作負載** 索引標籤。在下**Web 和雲端**，選擇**資料儲存和處理**。 選擇**修改**按鈕以加入 Visual Studio 中的工作負載。

## <a name="create-a-project-and-a-local-database-file"></a>建立專案和本機資料庫檔案

### <a name="to-create-a-project-and-a-database-file"></a>若要建立專案和資料庫檔案
1.  建立名為 Windows Form 專案`SampleDatabaseWalkthrough`。

2.  在功能表列上，選取**專案**，**加入新項目**。

3.  在項目範本清單中，向下捲動並選取**服務架構資料庫**。

     ![項目範本對話方塊](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")

4.  為資料庫命名**命名為 SampleDatabase**，然後選取**新增** 按鈕。

### <a name="to-add-a-data-source"></a>加入資料來源
5.  如果**資料來源**] 視窗未開啟，請選取 [開啟**Shift + Alt + D**索引鍵或在功能表列，選取**檢視**，**其他視窗**，**資料來源**。

6.  在**資料來源**視窗中，選取**加入新資料來源**連結。

    **資料來源組態精靈**隨即開啟。

7. 在**選擇資料來源類型**頁面上，選擇**資料庫**，然後選擇 **下一步**。

8. 在**選擇資料庫模型**頁面上，選擇**下一步**接受預設值 （資料集）。

9. 在**選擇資料連接**頁面上，選取**SampleDatabase.mdf**在下拉式清單中，檔案，然後選擇 **下一步**。

10. 在**連接字串儲存到應用程式組態檔**頁面上，選擇**下一步**。

11. 一個**選擇您的資料庫物件** 頁面上，您會看到訊息指出資料庫不包含任何物件。 選擇 [完成]。

### <a name="to-view-properties-of-the-data-connection"></a>若要檢視的資料連線屬性
您可以開啟資料連接屬性 視窗來檢視 SampleDatabase.mdf 檔案的連接字串：

-   在 Visual Studio 中，選取**檢視**， **SQL Server 物件總管**如果視窗尚未開啟。 開啟 [屬性] 視窗，方法是展開**資料連接**節點、 開啟 sampledatabase.mdf，捷徑功能表，然後選取**屬性**。

-   或者，您可以選取**檢視**，**伺服器總管**，如果視窗尚未開啟。 開啟 [屬性] 視窗，方法是展開**資料連接**節點。 Sampledatabase.mdf，開啟捷徑功能表，然後選取**屬性**。

## <a name="create-tables-and-keys-by-using-table-designer"></a>使用資料表設計工具中建立資料表和索引鍵
在本節中，您將建立兩個資料表，每個資料表及少數資料列的範例資料中的主索引鍵。 您也會建立以指定一個資料表中的記錄如何與其他資料表中的記錄對應的外部索引鍵。

### <a name="to-create-the-customers-table"></a>若要建立 Customers 資料表
1.  在**伺服器總管**或**SQL Server 物件總管**，依序展開**資料連接** 節點，然後展開**SampleDatabase.mdf**節點。

2.  開啟快顯功能表**資料表**，然後選取**加入新的資料表**。

     **資料表設計工具**隨即開啟並顯示具有一個預設資料列，代表您要建立的資料表中的單一資料行的方格。 藉由在格線中加入資料列，您就是在資料表中加入資料行。

3.  在格線中，為下列每一個項目加入一個資料列：

    |資料行名稱|資料類型|允許 Null|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|False (已清除)|
    |`CompanyName`|`nvarchar(50)`|False (已清除)|
    |`ContactName`|`nvarchar (50)`|True (已選取)|
    |`Phone`|`nvarchar (24)`|True (已選取)|

4.  開啟快顯功能表`CustomerID`資料列，然後再選取**設定主索引鍵**。

5.  開啟預設資料列的捷徑功能表，然後選取**刪除**。

6.  透過更新指令碼窗格中的第一行來命名 Customers 資料表，以符合下面範例：

    ```sql
    CREATE TABLE [dbo].[Customers]
    ```

    您應該會看到類似下面的內容：

    ![資料表設計工具](../data-tools/media/raddata-table-designer.png "raddata 資料表設計工具")

7.  在左上角的**資料表設計工具**，選取**更新** 按鈕。

8.  在**預覽資料庫更新**對話方塊中，選取**更新資料庫** 按鈕。

    您所做的變更會儲存到本機資料庫檔案中。

### <a name="to-create-the-orders-table"></a>若要建立 Orders 資料表
1.  加入另一個資料表，然後為下表中的每個項目加入一個資料列：

    |資料行名稱|資料類型|允許 Null|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|False (已清除)|
    |`CustomerID`|`nchar(5)`|False (已清除)|
    |`OrderDate`|`datetime`|True (已選取)|
    |`OrderQuantity`|`int`|True (已選取)|

2.  設定**OrderID**作為主索引鍵，然後刪除預設資料列。

3.  透過更新指令碼窗格中的第一行來命名 Orders 資料表，以符合下面範例：

    ```sql
    CREATE TABLE [dbo].[Orders]
    ```

4.  在左上角的**資料表設計工具**，選取**更新** 按鈕。

5.  在**預覽資料庫更新**對話方塊中，選取**更新資料庫** 按鈕。

    您所做的變更會儲存到本機資料庫檔案中。

### <a name="to-create-a-foreign-key"></a>若要建立外部索引鍵
1.  在方格右側內容窗格中，開啟捷徑功能表**外部索引鍵**，然後選取**加入新的外部索引鍵**，如下圖所示。

     ![在資料表設計工具中加入外部索引鍵](../data-tools/media/foreignkey.png "ForeignKey")

2.  在文字方塊中取代**Customers**與`Customers`。

3.  在 [T-SQL] 窗格中，更新最後一行以符合下面範例：

    ```sql
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4.  在左上角的**資料表設計工具**，選取**更新** 按鈕。

5.  在**預覽資料庫更新**對話方塊中，選取**更新資料庫** 按鈕。

    您所做的變更會儲存到本機資料庫檔案中。

## <a name="populate-the-tables-with-data"></a>填入資料表的資料

### <a name="to-populate-the-tables-with-data"></a>若要將資料填入資料表

1.  在**伺服器總管**或**SQL Server 物件總管**，展開範例資料庫的節點。

2.  開啟快顯功能表**資料表**節點中，選取**重新整理**，然後展開**資料表**節點。

3.  開啟 [客戶] 資料表的捷徑功能表，然後選取**顯示資料表資料**。

4.  新增任何您想要對某些客戶的資料。

    您可以指定要做為客戶 ID 的五個任意字元，不過，請至少選擇一個可記住且之後可在此程序中使用的字元。

5.  開啟 [訂單] 資料表的捷徑功能表，然後選取**顯示資料表資料**。

6.  新增一些訂單的資料。

    > [!IMPORTANT]
    > 請確定所有訂單 Id 和訂單數量都是整數，而且每個客戶 ID 符合您在 Customers 資料表的 CustomerID 資料行中指定的值。

7.  在功能表列上，選取**檔案**，**全部儲存**。

## <a name="see-also"></a>另請參閱

- [存取 Visual Studio 中的資料](accessing-data-in-visual-studio.md)