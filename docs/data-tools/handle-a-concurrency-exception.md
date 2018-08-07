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
ms.openlocfilehash: 6aca4815672d700fbea9d489f6316b8b0337f8df
ms.sourcegitcommit: 3a11feebad45a0dd4ac45efcbfdf172fce46e1de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39582329"
---
# <a name="handle-a-concurrency-exception"></a>處理並行例外狀況

並行存取例外狀況 (<xref:System.Data.DBConcurrencyException?displayProperty=fullName>) 兩位使用者嘗試同時變更資料庫中相同的資料時，會引發。 在本逐步解說中，您建立的 Windows 應用程式，說明如何攔截<xref:System.Data.DBConcurrencyException>，找出造成錯誤之資料列，並了解如何處理它的策略。

本逐步解說會引導您完成下列程序：

1. 建立新的 [Windows Forms 應用程式] 專案。

2. 建立新的資料集，根據 Northwind Customers 資料表。

3. 建立表單<xref:System.Windows.Forms.DataGridView>來顯示資料。

4. 在資料集中填入來自 Northwind 資料庫中的 [客戶] 資料表的資料。

5. 使用**顯示資料表資料**功能**伺服器總管**存取客戶資料表的資料和變更記錄。

6. 變更同一筆記錄到不同的值，更新資料集，並嘗試將變更寫入資料庫中，會導致引發並行處理錯誤。

7. 攔截到錯誤，然後顯示該記錄，讓使用者決定是否要繼續，並更新資料庫，不同版本，或取消更新。

## <a name="prerequisites"></a>必要條件

本逐步解說會使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1. 如果您沒有 SQL Server Express LocalDB，請將它安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)，或透過**Visual Studio 安裝程式**。 在  **Visual Studio 安裝程式**，您可以安裝 SQL Server Express LocalDB 做為一部分**資料儲存和處理**工作負載，或作為個別的元件。

2. 安裝 Northwind 範例資料庫執行下列步驟：

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (SQL Server 物件總管 中已安裝的一部分**資料儲存和處理**Visual Studio 安裝程式中的工作負載。)依序展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢**。

       查詢編輯器視窗隨即開啟。

    2. 複製[Northwind 的 TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。

    3. 將 T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。

       短時間之後，查詢完成執行，並建立 Northwind 資料庫。

> [!NOTE]
> 對話方塊和功能表命令，您會看到，可能會有所不同說明中所述取決於您使用的設定或您使用的版本不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="create-a-new-project"></a>建立新專案

開始建立新的 Windows Forms 應用程式：

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增** > **專案**。

2. 展開  **Visual C#** 或是**Visual Basic**的左側窗格中，然後選取**Windows Desktop**。

3. 在中間窗格中，選取**Windows Forms 應用程式**專案類型。

4. 將專案命名為**ConcurrencyWalkthrough**，然後選擇**確定**。

     **ConcurrencyWalkthrough**建立專案並將其加入至**方案總管 中**，以及新的表單隨即在設計工具中開啟。

## <a name="create-the-northwind-dataset"></a>建立 Northwind 資料集

接下來，建立名為資料集**NorthwindDataSet**:

1. 在 **資料**功能表上，選擇**加入新的資料來源**。

   資料來源組態精靈 隨即開啟。

2. 在 **選擇資料來源類型**畫面上，選取**資料庫**。

   ![在 Visual Studio 中的資料來源組態精靈](media/data-source-configuration-wizard.png)

3. 選取 Northwind 範例資料庫的連線，從清單中可用的連線。 如果連接不在清單中的連線，請選取**新的連接**。

    > [!NOTE]
    > 如果您要連線至本機資料庫檔案，請選取**No**當系統詢問您是否要將檔案加入您的專案。

4. 在 [**將連接字串儲存到應用程式組態檔**畫面上，選取**下一步]**。

5. 依序展開**資料表**節點，然後選取**客戶**資料表。 資料集的預設名稱應該是**NorthwindDataSet**。

6. 選取 **完成**將資料集加入至專案。

## <a name="create-a-data-bound-datagridview-control"></a>建立資料繫結 DataGridView 控制項

在本節中，您會建立<xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType>藉由拖曳**客戶**項目從**Zdroje dat**視窗拖曳至您的 Windows Form。

1. 在上**資料**功能表上，選擇**顯示資料來源**以開啟**資料來源視窗**。

2. 在 [**資料來源**] 視窗中，展開**NorthwindDataSet**節點，然後再選取**客戶**資料表。

3. 選取 [資料表] 節點的向下箭頭，然後選取**DataGridView**下拉式清單中。

4. 將資料表拖曳至表單的空白區域。

     A<xref:System.Windows.Forms.DataGridView>控制項，名為**CustomersDataGridView**，以及<xref:System.Windows.Forms.BindingNavigator>名為**CustomersBindingNavigator**，加入至表單繫結至<xref:System.Windows.Forms.BindingSource>。 這反而是，繫結至 NorthwindDataSet 中的 Customers 資料表。

## <a name="test-the-form"></a>測試表單

您現在可以測試表單，以確定它的行為如預期般截至目前為止：

1. 選取  **F5**執行應用程式。

     表單會顯示<xref:System.Windows.Forms.DataGridView>它填滿 Customers 資料表中資料的控制項。

2. 在 **偵錯**功能表上，選取**停止偵錯**。

## <a name="handle-concurrency-errors"></a>處理並行存取錯誤

處理錯誤的方式取決於特定的商務規則管理您的應用程式。 此逐步解說中，我們可以使用下列策略做為如何處理並行錯誤的範例。

應用程式會對使用者顯示記錄的三個版本：

- 在資料庫中目前的記錄

- 原始記錄載入至資料集

- 中的資料集的建議的變更

使用者就能夠以建議的版本中，會覆寫資料庫，或取消更新，並重新整理資料庫中的新值的資料集。

### <a name="to-enable-the-handling-of-concurrency-errors"></a>若要啟用的並行錯誤處理

1. 建立自訂的錯誤處理常式。

2. 向使用者顯示的選項。

3. 處理使用者的回應。

4. 重新傳送更新，或重設資料集內。

### <a name="add-code-to-handle-the-concurrency-exception"></a>新增程式碼來處理並行例外狀況

當您嘗試執行更新，並引發例外狀況時，您通常會想要運用所引發的例外狀況所提供的資訊。 在本節中，您可以加入嘗試更新資料庫的程式碼。 您也會處理任何<xref:System.Data.DBConcurrencyException>，可能會引發，以及任何其他例外狀況。

> [!NOTE]
> `CreateMessage`和`ProcessDialogResults`方法加入稍後在本逐步解說。

1. 新增下列程式碼下方`Form1_Load`方法：

     [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2. 取代`CustomersBindingNavigatorSaveItem_Click`方法來呼叫`UpdateDatabase`方法，讓它看起來如下所示：

     [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>向使用者顯示的選項

您剛才的程式碼撰寫呼叫`CreateMessage`程序來向使用者顯示錯誤資訊。 此逐步解說中中,，您可以使用訊息方塊來向使用者顯示的資料錄的不同版本。 這可讓使用者選擇是否要覆寫以變更的記錄，或取消編輯。 一旦使用者在訊息方塊上，選取 （按下按鈕） 的選項，回應會傳遞至`ProcessDialogResult`方法。

藉由新增下列程式碼，以建立訊息**程式碼編輯器**。 輸入下列程式碼下方`UpdateDatabase`方法：

     [!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>處理使用者的回應

您也需要程式碼來處理使用者的回應訊息方塊。 有兩個選項所提議的變更，以覆寫在資料庫中目前的記錄或放棄本機變更並重新整理目前資料庫中的記錄資料表。 如果使用者選擇 **[是]**，則<xref:System.Data.DataTable.Merge%2A>方法呼叫*preserveChanges*引數設定為**true**。 這會導致更新嘗試會成功，因為資料錄的原始版本現在會符合資料庫中的記錄。

下列程式碼下方新增上一節中所加入的程式碼：

     [!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>測試表單

您現在可以測試表單，以確定它如預期般運作。 若要模擬並行存取違規，您可以變更資料庫中的資料填 NorthwindDataSet 後。

1. 選取  **F5**執行應用程式。

2. 表單出現後，讓它保持執行，並切換至 Visual Studio IDE。

3. 在 **檢視**功能表上，選擇**伺服器總管**。

4. 在**伺服器總管**，展開 的連線您的應用程式是使用，並依**資料表**節點。

5. 以滑鼠右鍵按一下**客戶**資料表，然後再選取**顯示資料表資料**。

6. 在第一筆記錄 (**ALFKI**)，變更**ContactName**來**Maria Anders2**。

    > [!NOTE]
    > 瀏覽至不同的資料列，以認可變更。

7. 切換至 ConcurrencyWalkthrough 正在執行的表單。

8. 在表單上的第一筆記錄 (**ALFKI**)，變更**ContactName**來**Maria Anders1**。

9. 選取 [**儲存**] 按鈕。

     引發了並行錯誤，並出現訊息方塊。

   選取**No**取消更新，並使用目前資料庫中的值來更新資料集。 選取**是**寫入資料庫中的建議的值。

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)