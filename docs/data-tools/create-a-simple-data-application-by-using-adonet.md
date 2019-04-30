---
title: 使用 ADO.NET 建立簡單的資料應用程式
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4e7f99f646d2a93878ec0a78f75cdc6ae1fb0d1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62570049"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>使用 ADO.NET 建立簡單的資料應用程式

建立應用程式來管理資料庫中的資料時，您會執行基本工作，例如定義連接字串、插入資料及執行預存程序。 遵循本主題，您可以探索如何使用 Visual C# 或 Visual Basic 和 ADO.NET 與簡單的 Windows Forms 「 資料表單 」 應用程式內的資料庫互動。  所有的.NET 資料技術，包括資料集，LINQ to SQL 和 Entity Framework，最後執行非常類似於本文中所示的步驟。

這篇文章示範簡單的方式，以快速的方式取得資料庫中的資料。 如果您的應用程式需要非一般的方式修改資料，並更新資料庫，您應該考慮使用 Entity Framework，並使用資料繫結至自動同步處理使用者介面控制項的基礎資料中的變更。

> [!IMPORTANT]
> 為了簡化程式碼，它不會包含已準備好投入生產環境的例外狀況處理。

## <a name="prerequisites"></a>必要條件

若要建立應用程式，您需要：

- Visual Studio。

- SQL Server Express LocalDB。 如果您沒有 SQL Server Express LocalDB，您可以安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)。

本主題假設您已熟悉使用 Visual Studio IDE 的基本功能和可以建立在 Windows Forms 應用程式，將表單加入專案中，將按鈕和其他控制項在表單上的設定屬性的控制項，以及編碼簡單事件。 如果您不熟悉這些工作，我們建議您先完成[開始使用 Visual C# 和 Visual Basic](../ide/quickstart-visual-basic-console.md)主題，然後再開始本逐步解說。

## <a name="set-up-the-sample-database"></a>設定範例資料庫

建立範例資料庫執行下列步驟：

1. 在 Visual Studio 中開啟**伺服器總管**視窗。

2. 以滑鼠右鍵按一下**資料連接**，然後選擇**建立新的 SQL Server 資料庫**。

3. 在 **伺服器名稱**文字方塊中，輸入 **(localdb) \mssqllocaldb**。

4. 在 **新的資料庫名稱**文字方塊中，輸入**銷售**，然後選擇 **確定**。

     空**銷售**建立資料庫並將其加入至伺服器總管 中的資料連接節點。

5. 以滑鼠右鍵按一下**銷售額**資料連接，然後選取**新的查詢**。

     查詢編輯器視窗隨即開啟。

6. 複製[銷售的 TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql)到剪貼簿。

7. 將 T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。

     短時間之後，查詢完成執行，並建立資料庫物件。 資料庫包含兩個資料表：客戶和訂單。 這些資料表一開始，包含任何資料，但當您執行的應用程式，您將建立時，您可以加入資料。 資料庫也會包含四個簡單的預存程序。

## <a name="create-the-forms-and-add-controls"></a>建立表單並加入控制項

1. 建立 Windows Forms 應用程式的專案，然後將其命名為 **SimpleDataApp**。

    Visual Studio 會建立專案和數個檔案，包括名為 **Form1** 的空白 Windows 表單。

2. 將兩個 Windows 表單新增至專案，使其具有三種形式，然後提供下列名稱：

   - **巡覽**

   - **NewCustomer**

   - **FillOrCancel**

3. 為每個表單加入下圖中顯示的文字方塊、按鈕和其他控制項。 對每個控制項設定資料表描述的屬性。

   > [!NOTE]
   > 加入群組方塊和標籤控制項會更清楚，但是不在程式碼中使用。

   **巡覽表單**

   ![[巡覽] 對話方塊](../data-tools/media/simpleappnav.png)

|瀏覽表單的控制項|屬性|
| - |----------------|
|按鈕|Name = btnGoToAdd|
|按鈕|Name = btnGoToFillOrCancel|
|按鈕|Name = btnExit|

 **NewCustomer 表單**

 ![新增客戶以及下訂單](../data-tools/media/simpleappnewcust.png)

|NewCustomer 表單的控制項|屬性|
| - |----------------|
|TextBox|Name = txtCustomerName|
|TextBox|Name = txtCustomerID<br /><br /> Readonly = True|
|按鈕|Name = btnCreateAccount|
|NumericUpdown|DecimalPlaces = 0<br /><br /> Maximum = 5000<br /><br /> Name = numOrderAmount|
|DateTimePicker|Format = Short<br /><br /> Name = dtpOrderDate|
|按鈕|Name = btnPlaceOrder|
|按鈕|Name = btnAddAnotherAccount|
|按鈕|Name = btnAddFinish|

 **FillOrCancel 表單**

 ![填寫或取消訂單](../data-tools/media/simpleappcancelfill.png)

|FillOrCancel 表單的控制項|屬性|
| - |----------------|
|TextBox|Name = txtOrderID|
|按鈕|Name = btnFindByOrderID|
|DateTimePicker|Format = Short<br /><br /> Name = dtpFillDate|
|DataGridView|Name = dgvCustomerOrders<br /><br /> Readonly = True<br /><br /> RowHeadersVisible = False|
|按鈕|Name = btnCancelOrder|
|按鈕|Name = btnFillOrder|
|按鈕|Name = btnFinishUpdates|

## <a name="store-the-connection-string"></a>儲存連接字串
 當您的應用程式嘗試開啟資料庫的連接時，應用程式必須存取連接字串。 若要避免手動輸入字串，每個表單上，將字串儲存在*App.config*檔案在您的專案，並建立從您的應用程式中的任何表單呼叫方法時，會傳回字串的方法。

 您可以找到連接字串上按一下滑鼠右鍵**銷售額**中的資料連線**伺服器總管**，然後選擇**屬性**。 找出**ConnectionString**屬性，然後使用**Ctrl**+**A**， **Ctrl**+**C**選取，並將字串複製到剪貼簿。

1. 如果您使用 C# 中，在**方案總管**，展開**屬性**節點下專案，然後開啟**Settings.settings**檔案。
    如果您使用 Visual Basic 中，在**方案總管**，按一下**顯示所有檔案**，展開**我的專案**節點，然後再開啟**Settings.settings**檔案。

2. 在 **名稱**資料行中，輸入`connString`。

3. 在 **型別**清單中，選取 **（連接字串）**。

4. 在 **領域**清單中，選取**應用程式**。

5. 在 [**值**] 欄中，輸入您的連接字串 （不含任何外部引號括住），然後儲存變更。

> [!NOTE]
> 在實際的應用程式中，您應該在連接字串安全地儲存中, 所述[連接字串和組態檔](/dotnet/framework/data/adonet/connection-strings-and-configuration-files)。

## <a name="write-the-code-for-the-forms"></a>撰寫表單的程式碼

本章節包含每個表單用途的簡短概觀。 它也提供按一下表單上的按鈕時，定義基礎邏輯的程式碼。

### <a name="navigation-form"></a>導覽表單

當您執行應用程式時，瀏覽表單隨即開啟。 [新增帳戶] 按鈕會開啟 NewCustomer 表單。 [填寫或取消訂單] 按鈕會開啟 FillOrCancel 表單。 [結束] 按鈕會關閉應用程式。

#### <a name="make-the-navigation-form-the-startup-form"></a>讓瀏覽表單成為啟動表單

如果您使用 C#，在 [方案總管] 中開啟 **Program.cs**，然後將 `Application.Run` 這一行變更如下：`Application.Run(new Navigation());`

如果您使用 Visual Basic 中，在**方案總管**，開啟**屬性**視窗中，選取**應用程式**索引標籤，然後再選取  **SimpleDataApp.Navigation**中**啟動表單**清單。

#### <a name="create-auto-generated-event-handlers"></a>建立自動產生的事件處理常式

按兩下上瀏覽表單，以建立空的事件處理常式方法的三個按鈕。 按兩下按鈕也新增可讓按鈕點選，來引發事件的設計工具程式碼檔案中自動產生的程式碼。

#### <a name="add-code-for-the-navigation-form-logic"></a>加入導覽表單邏輯的程式碼

在 瀏覽表單的字碼頁，完成方法主體的三個按鈕 click 事件處理常式中的下列程式碼所示。

[!code-csharp[Navigation#1](../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs#1)]
[!code-vb[Navigation#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb#1)]

### <a name="newcustomer-form"></a>NewCustomer 表單

當您輸入客戶名稱，然後選取**建立帳戶**按鈕時，NewCustomer 表單建立客戶帳戶，並且與 SQL Server 會傳回 IDENTITY 值做為新的客戶識別碼。 您可以再訂購新的帳戶指定數量和訂單日期，然後選取**訂購** 按鈕。

#### <a name="create-auto-generated-event-handlers"></a>建立自動產生的事件處理常式

建立空白 Click 事件處理常式之每四個按鈕上按兩下 NewCustomer 表單上的每個按鈕。 按兩下按鈕也新增可讓按鈕點選，來引發事件的設計工具程式碼檔案中自動產生的程式碼。

#### <a name="add-code-for-the-newcustomer-form-logic"></a>加入 NewCustomer 表單邏輯的程式碼

若要完成 NewCustomer 表單邏輯，請遵循下列步驟。

1. 將`System.Data.SqlClient`進入範圍內的命名空間，讓您不必完整限定其成員的名稱。

     ```csharp
     using System.Data.SqlClient;
     ```

     ```vb
     Imports System.Data.SqlClient
     ```

2. 加入下列程式碼所示的類別的一些變數和協助程式方法。

     [!code-csharp[NewCustomer#1](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#1)]
     [!code-vb[NewCustomer#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#1)]

3. 下列程式碼所示完成方法主體，四個按鈕的 click 事件處理常式。

     [!code-csharp[NewCustomer#2](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#2)]
     [!code-vb[NewCustomer#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#2)]

### <a name="fillorcancel-form"></a>FillOrCancel 表單

FillOrCancel 表單會執行查詢來傳回訂單，當您輸入訂單 ID，然後按一下**尋找訂單** 按鈕。 傳回的資料列會顯示在唯讀的資料格。 如果您選取，您可以將標記為已取消 (X) 的順序**取消訂單** 按鈕，或者您可以將訂單標示為已填寫 (F) 如果您選取**填寫訂單** 按鈕。 如果您選取**尋找訂單**同樣地，按鈕會顯示更新的資料列。

#### <a name="create-auto-generated-event-handlers"></a>建立自動產生的事件處理常式

建立空白按一下 FillOrCancel 表單上的四個按鈕的事件處理常式，按兩下按鈕。 按兩下按鈕也新增可讓按鈕點選，來引發事件的設計工具程式碼檔案中自動產生的程式碼。

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>加入 FillOrCancel 表單邏輯的程式碼

若要完成 FillOrCancel 表單邏輯，請遵循下列步驟。

1. 將下列兩個命名空間帶到範圍，讓您不必完整限定其成員的名稱。

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```

     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. 將變數和協助程式方法加入類別，如下列程式碼所示。

     [!code-csharp[FillOrCancel#1](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#1)]
     [!code-vb[FillOrCancel#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#1)]

3. 下列程式碼所示完成方法主體，四個按鈕的 click 事件處理常式。

     [!code-csharp[FillOrCancel#2](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#2)]
     [!code-vb[FillOrCancel#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#2)]

## <a name="test-your-application"></a>測試您的應用程式

在您編碼每一個 Click 事件處理常式，然後完成撰寫程式碼之後，選取 **F5** 鍵來建置及測試您的應用程式。

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
