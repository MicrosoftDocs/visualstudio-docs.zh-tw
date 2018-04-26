---
title: 處理並行例外狀況
ms.date: 09/11/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 24338b2a6bc49a9a1a2a77e6395f60013c4465b7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="handle-a-concurrency-exception"></a>處理並行例外狀況
並行存取例外狀況 (<xref:System.Data.DBConcurrencyException>) 兩位使用者試圖同時變更資料庫中相同的資料時，會引發。 在本逐步解說中，您可以建立 Windows 應用程式示範如何攔截<xref:System.Data.DBConcurrencyException>，找出造成錯誤之資料列，並了解如何處理它的策略。

 本逐步解說會引導您完成下列程序：

1.  建立新的 [Windows Forms 應用程式] 專案。

2.  建立新的資料集，根據 Northwind`Customers`資料表。

3.  建立的表單具有<xref:System.Windows.Forms.DataGridView>來顯示資料。

4.  資料集填入來自資料`Customers`Northwind 資料庫中的資料表。

5.  使用**顯示資料表資料**功能**伺服器總管**存取`Customers`資料表的資料，以及變更記錄。

6.  將相同的記錄變更為不同的值，更新資料集，並嘗試將變更寫入至資料庫時，會導致引發並行錯誤。

7.  攔截到錯誤，然後顯示不同版本的記錄，讓使用者決定是否要繼續，並更新資料庫，或是取消更新。

## <a name="prerequisites"></a>必要條件
本逐步解說會使用 SQL Server Express LocalDB 與 Northwind 範例資料庫。

1.  如果您沒有 SQL Server Express LocalDB，將其安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)，或透過**Visual Studio 安裝程式**。 在 Visual Studio 安裝程式，可以安裝 SQL Server Express LocalDB 的一部份**資料儲存和處理**工作負載，或做為個別的元件。

2.  安裝 Northwind 範例資料庫執行下列步驟：

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (SQL Server 物件總管 中安裝的一部份**資料儲存和處理**在 Visual Studio 安裝程式工作負載。)展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢...**.

       查詢編輯器視窗隨即開啟。

    2. 複製[Northwind TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。

    3. T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。

       在一段時間之後, 查詢完成執行，並建立 Northwind 資料庫。

> [!NOTE]
>  對話方塊與功能表命令，您會看到可能與根據您目前使用的設定或版本，您所使用的 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="create-a-new-project"></a>建立新專案
 您開始您逐步解說中建立新的 Windows Form 應用程式。

#### <a name="to-create-a-new-windows-forms-application-project"></a>若要建立新的 Windows Forms 應用程式專案

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增**，**專案...**.

2. 展開  **Visual C#** 或**Visual Basic**左窗格中，然後選取**的傳統 Windows 桌面**。

3. 在中間窗格中，選取**Windows Form 應用程式**專案類型。

4. 將專案命名**ConcurrencyWalkthrough**，然後選擇 **確定**。

     **ConcurrencyWalkthrough**建立專案並將其加入**方案總管 中**，並在設計工具中開啟新表單。

## <a name="create-the-northwind-dataset"></a>建立 Northwind 資料集
 在本節中，您會建立名為資料集`NorthwindDataSet`。

#### <a name="to-create-the-northwinddataset"></a>若要建立 NorthwindDataSet

1.  在**資料**功能表上，選擇**加入新的資料來源**。

     [資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)隨即開啟。

2.  在**選擇資料來源類型**畫面上，選取**資料庫**。

3.  從選取連接至 Northwind 範例資料庫的可用連線清單。 如果連接無法使用的連接清單中，選取**新連線**

    > [!NOTE]
    >  如果您要連接到本機資料庫檔案中，選取**否**當系統詢問您是否要將檔案加入您的專案。

4.  在**將連接字串儲存到應用程式組態檔**畫面上，選取**下一步**。

5.  展開**資料表**節點，然後選取`Customers`資料表。 資料集的預設名稱應該是`NorthwindDataSet`。

6.  選取**完成**將資料集加入至專案。

## <a name="create-a-data-bound-datagridview-control"></a>建立資料繫結 DataGridView 控制項
 在本節中，您會建立<xref:System.Windows.Forms.DataGridView>拖曳**客戶**項目從**資料來源**視窗拖曳至 Windows 表單。

#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>若要建立繫結至 Customers 資料表的 DataGridView 控制項

1.  在**資料**功能表上，選擇**顯示資料來源**開啟**資料來源視窗**。

2.  在**資料來源**視窗中，展開  **NorthwindDataSet**節點，然後再選取**客戶**資料表。

3.  選取的資料表節點上，向下箭號，然後選取**DataGridView**下拉式清單中。

4.  將資料表拖曳至表單的空白區域。

     A<xref:System.Windows.Forms.DataGridView>控制項，名為`CustomersDataGridView`和<xref:System.Windows.Forms.BindingNavigator>名為`CustomersBindingNavigator`加入至表單繫結至<xref:System.Windows.Forms.BindingSource>。這是在中，開啟繫結至`Customers`資料表中`NorthwindDataSet`。

## <a name="test-the-form"></a>測試表單
 您現在可以測試表單，請確定它的行為如預期般為止。

#### <a name="to-test-the-form"></a>若要測試表單

1.  選取**F5**執行應用程式

     表單隨即出現，並<xref:System.Windows.Forms.DataGridView>控制項在其上的填滿資料`Customers`資料表。

2.  在**偵錯**功能表上，選取**停止偵錯**。

## <a name="handle-concurrency-errors"></a>處理並行存取錯誤
 處理錯誤的方式取決於特定的商務規則，以管理您的應用程式。 這個逐步解說中，我們可以使用下列策略做為並行錯誤的處理方式的範例。

 應用程式會對使用者顯示三個版本的記錄：

-   在資料庫中目前的記錄

-   原始記錄中載入資料集

-   在資料集中所提出之變更

然後，使用者將能夠覆寫資料庫，以建議的版本，或取消更新並重新整理資料集與資料庫中的新值。

#### <a name="to-enable-the-handling-of-concurrency-errors"></a>若要啟用的並行錯誤處理

1.  建立自訂錯誤處理常式。

2.  選擇顯示給使用者。

3.  處理使用者的回應。

4.  重新傳送更新，或重設資料集內。

### <a name="add-code-to-handle-the-concurrency-exception"></a>加入程式碼來處理並行例外狀況
 當您嘗試執行更新，並引發例外狀況時，您通常會想要運用提供所引發的例外狀況的資訊。

 在本節中，您可以加入嘗試更新資料庫的程式碼。 您也處理任何<xref:System.Data.DBConcurrencyException>，可能會取得會引發，以及任何其他例外狀況。

> [!NOTE]
>  `CreateMessage`和`ProcessDialogResults`方法將會加入稍後在本逐步解說。

##### <a name="to-add-error-handling-for-the-concurrency-error"></a>若要加入的並行錯誤錯誤處理

1.  加入下列程式碼下方`Form1_Load`方法：

     [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2.  取代`CustomersBindingNavigatorSaveItem_Click`方法呼叫`UpdateDatabase`方法，使它看起來如下：

     [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>選擇顯示給使用者
 您剛才的程式碼撰寫呼叫`CreateMessage`程序，以向使用者顯示資訊時發生錯誤。 這個逐步解說中，您可以使用訊息方塊向使用者顯示不同的版本記錄。 這可讓使用者選擇是否要覆寫記錄，以變更或取消編輯。 一旦使用者訊息方塊上，選取 （按下按鈕） 的選項，回應會傳遞至`ProcessDialogResult`方法。

##### <a name="to-create-the-message-to-display-to-the-user"></a>若要建立要向使用者顯示的訊息

-   加入下列程式碼來建立的訊息**程式碼編輯器**。 輸入以下這個程式碼`UpdateDatabase`方法。

     [!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>處理使用者的回應
 您也需要處理使用者的回應訊息方塊的程式碼。 有兩個選項提議的變更，以覆寫在資料庫中目前的記錄或放棄本機變更並重新整理與目前資料庫中的記錄資料表。 如果使用者選擇 [是]，<xref:System.Data.DataTable.Merge%2A>方法呼叫*preserveChanges*引數設定為`true`。 這會導致更新嘗試會成功，因為該記錄的原始版本現在符合資料庫中的記錄。

##### <a name="to-process-the-user-input-from-the-message-box"></a>若要處理使用者輸入的訊息方塊

-   加入下列程式碼是在上一節中新增的程式碼底下。

     [!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>測試表單
 您現在可以測試表單，以確定其如預期般運作。 若要模擬並行存取違規，您需要變更資料庫中的資料之後填入 NorthwindDataSet。

#### <a name="to-test-the-form"></a>若要測試表單

1.  選取**F5**執行應用程式。

2.  顯示表單後，讓它繼續執行，並切換至 Visual Studio IDE。

3.  在**檢視**功能表上，選擇**伺服器總管**。

4.  在**伺服器總管**，依序展開 的連線您的應用程式是使用，然後展開**資料表**節點。

5.  以滑鼠右鍵按一下**客戶**資料表，，然後選取**顯示資料表資料**。

6.  在第一筆記錄 (`ALFKI`) 變更`ContactName`至`Maria Anders2`。

    > [!NOTE]
    >  瀏覽至不同的資料列，以認可變更。

7.  切換至`ConcurrencyWalkthrough`執行表單。

8.  在表單上的第一個資料錄 (`ALFKI`)，變更`ContactName`至`Maria Anders1`。

9. 選取**儲存** 按鈕。

     並行引發錯誤，而且會出現訊息方塊。

10. 選取**否**取消更新並更新資料集是目前資料庫中的值。 選取**是**寫入資料庫中的建議的值。

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)