---
title: 建立資料庫檔案並使用資料表設計工具
description: 本教學課程說明如何使用 Visual Studio 中的資料表設計工具，將資料表和外鍵加入至資料庫。 它也會示範如何透過圖形化介面來新增資料。
ms.date: 09/19/2019
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 595b8ea35799effd36e4a8599c61b3ab42efb940
ms.sourcegitcommit: a1e899248adaf104697fa7dea32a36e69e9cc119
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "71159973"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>建立資料庫並在 Visual Studio 中新增資料表

您可以使用 Visual Studio，在 SQL Server Express LocalDB 中建立及更新本機資料庫檔案。 您也可以在 Visual Studio 的 [ **SQL Server 物件總管**工具] 視窗中執行 transact-sql 語句來建立資料庫。 在本主題中，我們將建立 *.mdf*檔案，並使用資料表設計工具來新增資料表和索引鍵。

## <a name="prerequisites"></a>必要條件

若要完成此逐步解說，您將需要安裝在 Visual Studio 中的 **.net 桌面開發**和**資料儲存和處理**工作負載。 若要安裝它們，請開啟**Visual Studio 安裝程式**，然後選擇您想要修改之 Visual Studio 版本旁邊的 [**修改**（或**更多** > **修改**）]。

## <a name="create-a-project-and-a-local-database-file"></a>建立專案和本機資料庫檔案

1. 建立新的**Windows Forms 應用程式**專案，並將其命名為**SampleDatabaseWalkthrough**。

2. 在功能表列上，選取 [**專案** > ] [**加入新專案**]。

3. 在專案範本清單中，向下選取 [以**服務為基礎的資料庫**]。

   ![項目範本對話方塊](../data-tools/media/raddata-vsitemtemplates.png)

4. 將資料庫命名為**sampledatabase.mdf**，然後按一下 [**新增**]。

### <a name="add-a-data-source"></a>新增資料來源

1. 如果 [**資料來源**] 視窗未開啟，請按下**Shift** + **Alt** + **D** ，或選取 [**查看** > **其他 Windows**  > **資料來源**]，將它開啟。功能表列。

1. 在 [**資料來源**] 視窗中，選取 [**加入新的資料來源**]。

   ![在 Visual Studio 中加入新的資料來源](media/add-new-data-source.png)

   [資料來源組態精靈] 隨即開啟。

1. 在 [**選擇資料來源類型**] 頁面上，選擇 [**資料庫**]，然後選擇 **[下一步]** 。

1. 在 [**選擇資料庫模型**] 頁面上，選擇 [**下一步]** 以接受預設值（資料集）。

1. 在 [**選擇您的資料連線**] 頁面上，選取下拉式清單中的 [ **sampledatabase.mdf** ]，然後選擇 [**下一步]** 。

1. 在 [將**連接字串儲存到應用程式佈建檔**] 頁面上，選擇 [**下一步]** 。

1. 在 [**選擇您的資料庫物件**] 頁面上，您會看到一則訊息，指出資料庫未包含任何物件。 選擇 [完成]。

### <a name="view-properties-of-the-data-connection"></a>資料連線的視圖屬性

您可以藉由開啟資料連線的屬性視窗，來查看*sampledatabase.mdf*的連接字串：

- 選取 [ **View**  >  **SQL Server 物件總管**] 以開啟 [ **SQL Server 物件總管**] 視窗。 展開 **（localdb） [\MSSQLLocalDB**  > **資料庫**]，然後以滑鼠右鍵按一下 [ *sampledatabase.mdf* ]，然後選取 [**屬性**]。

- 或者，如果該視窗尚未開啟，您可以選取 [ **View**  > **伺服器總管**]。 展開 [**資料連線**] 節點，以滑鼠右鍵按一下 [ *sampledatabase.mdf*]，然後選取 [**屬性**]，以開啟 [屬性視窗]。

## <a name="create-tables-and-keys-by-using-table-designer"></a>使用資料表設計工具建立資料表和索引鍵

在本節中，您將建立兩個數據表、每個資料表中的主鍵，以及幾個範例資料列。 您也會建立外鍵，以指定單一資料表中的記錄如何對應至另一個資料表中的記錄。

### <a name="create-the-customers-table"></a>建立 Customers 資料表

1. 在**伺服器總管**中，展開 [**資料連線**] 節點，然後展開 [ **sampledatabase.mdf** ] 節點。

2. 以滑鼠右鍵按一下 [**資料表]** ，然後選取 [**加入新的資料表**]。

   資料表設計工具會開啟並顯示含有一個預設資料列的方格，這表示您要建立之資料表中的單一資料行。 藉由在格線中加入資料列，您就是在資料表中加入資料行。

3. 在格線中，為下列每一個項目加入一個資料列：

   |資料行名稱|資料類型|允許 Null|
   |-----------------|---------------|-----------------|
   |`CustomerID`|`nchar(5)`|False (已清除)|
   |`CompanyName`|`nvarchar(50)`|False (已清除)|
   |`ContactName`|`nvarchar (50)`|True (已選取)|
   |`Phone`|`nvarchar (24)`|True (已選取)|

4. 以滑鼠右鍵按一下資料`CustomerID`列，然後選取 [**設定主鍵**]。

5. 以滑鼠右鍵按一下預設資料列（`Id`），然後選取 [**刪除**]。

6. 透過更新指令碼窗格中的第一行來命名 Customers 資料表，以符合下面範例：

   ```sql
   CREATE TABLE [dbo].[Customers]
   ```

   您應該會看到類似下面的內容：

   ![資料表設計工具](../data-tools/media/table-designer.png)

7. 在**資料表設計工具**的左上角，選取 [**更新**]。

8. 在 [**預覽資料庫更新**] 對話方塊中，選取 [**更新資料庫**]。

   [Customers] 資料表會建立在本機資料庫檔案中。

### <a name="create-the-orders-table"></a>建立 Orders 資料表

1. 加入另一個資料表，然後為下表中的每個項目加入一個資料列：

   |資料行名稱|資料類型|允許 Null|
   |-----------------|---------------|-----------------|
   |`OrderID`|`int`|False (已清除)|
   |`CustomerID`|`nchar(5)`|False (已清除)|
   |`OrderDate`|`datetime`|True (已選取)|
   |`OrderQuantity`|`int`|True (已選取)|

2. 將 [**訂單**] 設定為主鍵，然後刪除預設資料列。

3. 透過更新指令碼窗格中的第一行來命名 Orders 資料表，以符合下面範例：

   ```sql
   CREATE TABLE [dbo].[Orders]
   ```

4. 在**資料表設計工具**的左上角，選取 [**更新**]。

5. 在 [**預覽資料庫更新**] 對話方塊中，選取 [**更新資料庫**]。

   Orders 資料表會建立在本機資料庫檔案中。 如果您展開伺服器總管中的 [**資料表]** 節點，您會看到兩個數據表：

   ![伺服器總管中展開的 [資料表] 節點](media/server-explorer-tables-node.png)

### <a name="create-a-foreign-key"></a>建立外鍵

1. 在 [訂單] 資料表之資料表設計工具方格右側的內容窗格中，以滑鼠右鍵按一下 [**外鍵**]，然後選取 [**加入新的外鍵**]。

   ![在資料表設計工具的 Visual Studio 中新增外鍵](../data-tools/media/add-foreign-key.png)

2. 在出現的文字方塊中，將**ToTable**的文字取代為**Customers**。

3. 在 [T-sql] 窗格中，更新最後一行以符合下列範例：

   ```sql
   CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
   ```

4. 在**資料表設計工具**的左上角，選取 [**更新**]。

5. 在 [**預覽資料庫更新**] 對話方塊中，選取 [**更新資料庫**]。

   建立外鍵。

## <a name="populate-the-tables-with-data"></a>將資料填入資料表

1. 在**伺服器總管**或**SQL Server 物件總管**中，展開範例資料庫的節點。

2. 開啟 [**資料表]** 節點的快捷方式功能表，**選取 [** 重新整理]，然後展開 [**資料表]** 節點。

3. 開啟 [Customers] 資料表的快捷方式功能表，然後選取 [**顯示資料表資料**]。

4. 為某些客戶新增您想要的任何資料。

    您可以指定要做為客戶 ID 的五個任意字元，不過，請至少選擇一個可記住且之後可在此程序中使用的字元。

5. 開啟 Orders 資料表的快捷方式功能表，然後選取 [**顯示資料表資料**]。

6. 新增部分訂單的資料。

    > [!IMPORTANT]
    > 確定所有訂單識別碼和訂單數量都是整數，而且每個客戶識別碼都符合您在 Customers 資料表的 **CustomerID** 資料行中指定的值。

7. 在功能表列上 **，選取** > [檔案] [**全部儲存**]。

## <a name="see-also"></a>另請參閱

- [存取 Visual Studio 中的資料](accessing-data-in-visual-studio.md)
