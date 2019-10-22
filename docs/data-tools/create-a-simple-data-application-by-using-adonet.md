---
title: 使用 ADO.NET 建立簡單的資料應用程式
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f895bd909ec9fda496d284c163bff4a5168bd057
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648736"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>使用 ADO.NET 建立簡單的資料應用程式

建立應用程式來管理資料庫中的資料時，您會執行基本工作，例如定義連接字串、插入資料及執行預存程序。 遵循本主題，您可以探索如何使用 Visual C#或 Visual Basic 和 ADO.NET，從簡單的 Windows Forms 「表單資料」應用程式內與資料庫互動。  所有 .NET 資料技術（包括資料集、LINQ to SQL 和 Entity Framework）最後都會執行與本文中所示類似的步驟。

本文示範以快速方式從資料庫中取得資料的簡單方式。 如果您的應用程式需要以不常用的方式修改資料並更新資料庫，您應該考慮使用 Entity Framework 並使用資料系結，將使用者介面控制項自動同步處理至基礎資料中的變更。

> [!IMPORTANT]
> 為了簡化程式碼，它不會包含已準備好投入生產環境的例外狀況處理。

## <a name="prerequisites"></a>Prerequisites

若要建立應用程式，您需要：

- Visual Studio。

- SQL Server Express LocalDB。 如果您沒有 SQL Server Express LocalDB，可以從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)進行安裝。

本主題假設您熟悉 Visual Studio IDE 的基本功能，而且可以建立 Windows Forms 應用程式、將表單加入專案、將按鈕和其他控制項放在表單上、設定控制項的屬性，以及撰寫程式碼的簡單事件。 如果您不熟悉這些工作，建議您先完成開始[使用視覺效果C#和 Visual Basic](../ide/quickstart-visual-basic-console.md)主題，再開始進行本逐步解說。

## <a name="set-up-the-sample-database"></a>設定範例資料庫

遵循下列步驟來建立範例資料庫：

1. 在 Visual Studio 中，開啟 [**伺服器總管**] 視窗。

2. 以滑鼠右鍵按一下 [**資料連線**]，然後選擇 [**建立新的 SQL Server 資料庫**]。

3. 在 [**伺服器名稱**] 文字方塊中，輸入 **（localdb） \mssqllocaldb**。

4. 在 [**新資料庫名稱**] 文字方塊中，輸入**Sales**，然後選擇 **[確定]** 。

     空的**Sales**資料庫隨即建立，並加入至伺服器總管中的 [資料連線] 節點。

5. 以滑鼠右鍵按一下**銷售**資料連線，然後選取 [追加**查詢**]。

     [查詢編輯器] 視窗隨即開啟。

6. 將[Sales transact-sql 腳本](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql)複製到剪貼簿。

7. 將 T-sql 腳本貼入查詢編輯器中，然後選擇 [**執行**] 按鈕。

     在短時間之後，查詢就會完成執行，並建立資料庫物件。 資料庫包含兩個數據表： Customer 和 Orders。 這些資料表一開始不包含任何資料，但您可以在執行您將建立的應用程式時加入資料。 資料庫也包含四個簡單的預存程式。

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

|瀏覽表單的控制項|內容|
| - |----------------|
|按鈕|Name = btnGoToAdd|
|按鈕|Name = btnGoToFillOrCancel|
|按鈕|Name = btnExit|

**NewCustomer 表單**

![新增客戶以及下訂單](../data-tools/media/simpleappnewcust.png)

|NewCustomer 表單的控制項|內容|
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

|FillOrCancel 表單的控制項|內容|
| - |----------------|
|TextBox|Name = txtOrderID|
|按鈕|Name = btnFindByOrderID|
|DateTimePicker|Format = Short<br /><br /> Name = dtpFillDate|
|DataGridView|Name = dgvCustomerOrders<br /><br /> Readonly = True<br /><br /> RowHeadersVisible = False|
|按鈕|Name = btnCancelOrder|
|按鈕|Name = btnFillOrder|
|按鈕|Name = btnFinishUpdates|

## <a name="store-the-connection-string"></a>儲存連接字串
當您的應用程式嘗試開啟資料庫的連接時，應用程式必須存取連接字串。 若要避免在每個表單上手動輸入字串，請將字串儲存在*專案的 app.config*檔案中，並建立方法，以便在從應用程式中的任何表單呼叫方法時，傳回字串。

以滑鼠右鍵按一下**伺服器總管**中的 [**銷售**資料] 連接，然後選擇 [**屬性**]，即可找到連接字串。 找出**ConnectionString**屬性，然後使用**ctrl** +**A**、 **ctrl** +**C**來選取字串，並將其複製到剪貼簿。

1. 如果C#您使用的是，請在**方案總管**中，展開專案底下的 [**屬性**] 節點，然後開啟 [**設定**] 檔案。
    如果您使用 Visual Basic，請在**方案總管**中按一下 [**顯示所有**檔案]，展開 [**我的專案**] 節點，然後開啟 [**配置**檔案]。

2. 在 [**名稱**] 資料行中，輸入 `connString`。

3. 在 [**類型**] 清單中，選取 **[（連接字串）** ]。

4. 在 [**範圍**] 清單中，選取 [**應用程式**]。

5. 在 [**值**] 資料行中，輸入您的連接字串（不含任何外引號），然後儲存您的變更。

> [!NOTE]
> 在實際的應用程式中，您應該安全地儲存連接字串，如[連接字串和設定檔](/dotnet/framework/data/adonet/connection-strings-and-configuration-files)中所述。

## <a name="write-the-code-for-the-forms"></a>撰寫表單的程式碼

本章節包含每個表單執行內容的簡要概述。 它也會提供程式碼，以在按一下表單上的按鈕時定義基礎邏輯。

### <a name="navigation-form"></a>導覽表單

當您執行應用程式時，瀏覽表單隨即開啟。 [新增帳戶] 按鈕會開啟 NewCustomer 表單。 [填寫或取消訂單] 按鈕會開啟 FillOrCancel 表單。 [結束] 按鈕會關閉應用程式。

#### <a name="make-the-navigation-form-the-startup-form"></a>讓瀏覽表單成為啟動表單

如果您使用 C#，在 [方案總管] 中開啟 **Program.cs**，然後將 `Application.Run` 這一行變更如下：`Application.Run(new Navigation());`

如果您使用 Visual Basic，請在**方案總管**中開啟 [**屬性**] 視窗，選取 [**應用程式**] 索引標籤，然後選取 [**啟動表單**] 清單中的 [**命名為 simpledataapp]。**

#### <a name="create-auto-generated-event-handlers"></a>建立自動產生的事件處理常式

按兩下導覽表單上的三個按鈕，以建立空的事件處理常式方法。 按兩下按鈕也會在設計工具程式碼檔案中加入自動產生的程式碼，讓按一下按鈕來引發事件。

#### <a name="add-code-for-the-navigation-form-logic"></a>新增導覽表單邏輯的程式碼

在流覽表單的字碼頁中，完成三個按鈕 click 事件處理常式的方法主體，如下列程式碼所示。

[!code-csharp[Navigation#1](../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs#1)]
[!code-vb[Navigation#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb#1)]

### <a name="newcustomer-form"></a>NewCustomer 表單

當您輸入客戶名稱，然後選取 [**建立帳戶**] 按鈕時，NewCustomer 表單會建立客戶帳戶，而 SQL Server 會傳回身分識別值做為新的客戶識別碼。 接著，您可以指定金額和訂單日期，然後選取 [訂購**單**] 按鈕，以放置新帳戶的訂單。

#### <a name="create-auto-generated-event-handlers"></a>建立自動產生的事件處理常式

按兩下四個按鈕，為 NewCustomer 表單上的每個按鈕建立空白 Click 事件處理常式。 按兩下按鈕也會在設計工具程式碼檔案中加入自動產生的程式碼，讓按一下按鈕來引發事件。

#### <a name="add-code-for-the-newcustomer-form-logic"></a>新增 NewCustomer 表單邏輯的程式碼

若要完成 NewCustomer 表單邏輯，請遵循下列步驟。

1. 將 `System.Data.SqlClient` 命名空間帶入範圍中，讓您不需要完整限定其成員的名稱。

     ```csharp
     using System.Data.SqlClient;
     ```

     ```vb
     Imports System.Data.SqlClient
     ```

2. 將一些變數和 helper 方法新增至類別，如下列程式碼所示。

     [!code-csharp[NewCustomer#1](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#1)]
     [!code-vb[NewCustomer#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#1)]

3. 完成四個按鈕 click 事件處理常式的方法主體，如下列程式碼所示。

     [!code-csharp[NewCustomer#2](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#2)]
     [!code-vb[NewCustomer#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#2)]

### <a name="fillorcancel-form"></a>FillOrCancel 表單

當您輸入訂單識別碼，然後按一下 [**尋找訂單**] 按鈕時，FillOrCancel 表單會執行查詢以傳回訂單。 傳回的資料列會顯示在唯讀的資料格。 如果您選取 [**取消訂單**] 按鈕，可以將訂單標示為 [已取消] （X），或者，如果您選取 [**填滿訂單**] 按鈕，則可以將訂單標示為已填滿（F）。 如果您再次選取 [**尋找訂單**] 按鈕，則會顯示更新的資料列。

#### <a name="create-auto-generated-event-handlers"></a>建立自動產生的事件處理常式

按兩下按鈕，為 FillOrCancel 表單上的四個按鈕建立空白的 Click 事件處理常式。 按兩下按鈕也會在設計工具程式碼檔案中加入自動產生的程式碼，讓按一下按鈕來引發事件。

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>新增 FillOrCancel 表單邏輯的程式碼

若要完成 FillOrCancel 表單邏輯，請遵循下列步驟。

1. 將下列兩個命名空間帶入範圍中，讓您不需要完整限定其成員的名稱。

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```

     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. 將變數和 helper 方法新增至類別，如下列程式碼所示。

     [!code-csharp[FillOrCancel#1](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#1)]
     [!code-vb[FillOrCancel#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#1)]

3. 完成四個按鈕 click 事件處理常式的方法主體，如下列程式碼所示。

     [!code-csharp[FillOrCancel#2](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#2)]
     [!code-vb[FillOrCancel#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#2)]

## <a name="test-your-application"></a>測試您的應用程式

在您編碼每一個 Click 事件處理常式，然後完成撰寫程式碼之後，選取 **F5** 鍵來建置及測試您的應用程式。

## <a name="see-also"></a>請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
