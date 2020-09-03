---
title: 處理並行例外狀況 |Microsoft Docs
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
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b3f9bdaf5107f805100b938212128d42c0263dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670030"
---
# <a name="handle-a-concurrency-exception"></a>處理並行例外狀況
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Data.DBConcurrencyException>當兩位使用者嘗試同時變更資料庫中的相同資料時，會引發並行例外狀況 () 。 在這個逐步解說中，您會建立 Windows 應用程式來說明如何捕捉 <xref:System.Data.DBConcurrencyException> 、找出造成錯誤的資料列，以及瞭解如何處理它的策略。

 本逐步解說會引導您完成下列程式：

1. 建立新的 **Windows 應用程式** 專案。

2. 根據 Northwind 資料表建立新的資料集 `Customers` 。

3. 使用來建立表單， <xref:System.Windows.Forms.DataGridView> 以顯示資料。

4. 使用 Northwind 資料庫中資料表的資料來填滿資料集 `Customers` 。

5. 使用 Visual Studio 中的 [Visual Database Tools](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) ，直接存取 `Customers` 資料表並變更記錄。

6. 將相同的記錄變更為不同的值、更新資料集，並嘗試將變更寫入資料庫，這會導致引發並行處理錯誤。

7. 攔截錯誤，然後顯示記錄的不同版本，讓使用者判斷是否要繼續並更新資料庫，或取消更新。

## <a name="prerequisites"></a>必要條件
 若要完成這個逐步解說，您需要：

- 具有執行更新許可權的 Northwind 範例資料庫的存取權。

> [!NOTE]
> 您所看到的對話方塊和功能表命令可能會與 [說明] 中描述的不同，視您使用的作用中設定或版本而定。 若要變更您的設定，請在 [工具]**** 功能表上選擇 [匯入和匯出設定]****。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。

## <a name="create-a-new-project"></a>建立新專案
 您可以藉由建立新的 Windows 應用程式來開始逐步解說。

#### <a name="to-create-a-new-windows-application-project"></a>建立新的 Windows 應用程式專案

1. **在 [檔案**] 功能表上，建立新專案。

2. 在 [ **專案類型** ] 窗格中，選取程式設計語言。

3. 在 [範本] 窗格中，選取 [Windows 應用程式]。

4. 為專案命名 `ConcurrencyWalkthrough` ，然後選取 **[確定]**。

     Visual Studio 將專案新增至 **方案總管** ，並在設計工具中顯示新表單。

## <a name="create-the-northwind-dataset"></a>建立 Northwind 資料集
 在本節中，您會建立名為的資料集 `NorthwindDataSet` 。

#### <a name="to-create-the-northwinddataset"></a>若要建立 NorthwindDataSet

1. 在 [ **資料** ] 功能表上，選擇 [ **加入新資料來源**]。

     [ [資料來源設定]](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) 設定會開啟。

2. 在 [ **選擇資料來源類型**] 畫面上，選取 [ **資料庫**]。

3. 從可用的連接清單中，選取 Northwind 範例資料庫的連接。如果連接清單中未提供連線，請選取 [**新增**連線]。

    > [!NOTE]
    > 如果您要連接至本機資料庫檔案，則當系統詢問您是否要將檔案新增至專案時，請選取 [ **否** ]。

4. 在 [ **將連接字串儲存到應用程式佈建檔**] 畫面上，選取 [ **下一步]**。

5. 展開 [ **資料表]** 節點，然後選取 `Customers` 資料表。 資料集的預設名稱應該是 `NorthwindDataSet` 。

6. 選取 **[完成]** 將資料集加入至專案。

## <a name="create-a-data-bound-datagridview-control"></a>建立資料系結 DataGridView 控制項
 在本節中，您會 <xref:System.Windows.Forms.DataGridView> 從 [**資料來源**] 視窗將 [ **Customers** ] 專案拖曳至 Windows Form，藉以建立。

#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>若要建立系結至 Customers 資料表的 DataGridView 控制項

1. 在 [ **資料** ] 功能表上，選擇 [ **顯示資料來源** ] 以開啟 [ **資料來源] 視窗**。

2. 在 [ **資料來源** ] 視窗中，展開 [ **NorthwindDataSet** ] 節點，然後選取 [ **Customers** ] 資料表。

3. 選取 [資料表] 節點上的向下箭號，然後在下拉式清單中選取 [ **DataGridView** ]。

4. 將資料表拖曳至表單的空白區域。

     <xref:System.Windows.Forms.DataGridView>名為 `CustomersDataGridView` 和的控制項 <xref:System.Windows.Forms.BindingNavigator> `CustomersBindingNavigator` 會加入至系結至的表單 <xref:System.Windows.Forms.BindingSource> 。在中，它會變成系結至 `Customers` 中的資料表 `NorthwindDataSet` 。

## <a name="test-the-form"></a>測試表單
 您現在可以測試表單，以確定其在此時間點的行為如預期般運作。

#### <a name="to-test-the-form"></a>測試表單

1. 選取 **F5** 以執行應用程式

     表單隨即出現，並顯示 <xref:System.Windows.Forms.DataGridView> 其上的控制項，並填入資料表中的資料 `Customers` 。

2. 在 [ **調試** ] 功能表上，選取 [**停止調試**]。

## <a name="handleconcurrency-errors"></a>Handleconcurrency 錯誤
 處理錯誤的方式取決於管理您應用程式的特定商務規則。 在這個逐步解說中，我們會使用下列策略作為 tohandle 並行處理錯誤的範例。

 Applicationpresents 具有三個記錄版本的使用者：

- 資料庫中的目前記錄

- 載入至資料集的原始記錄

- 資料集中建議的變更

  使用者接著可以使用建議的版本來覆寫資料庫，或取消更新，並使用資料庫中的新值重新整理資料集。

#### <a name="to-enable-the-handling-of-concurrency-errors"></a>若要啟用並行錯誤的處理

1. 建立自訂錯誤處理常式。

2. 顯示使用者的選項。

3. 處理使用者的回應。

4. 重新傳送更新，或重設資料集中的資料。

### <a name="addcode-to-handle-the-concurrency-exception"></a>Addcode 以處理並行例外狀況
 當您嘗試執行更新並引發例外狀況時，您通常會想要使用引發之例外狀況所提供的資訊來執行某些動作。

 在本節中，您會加入嘗試更新資料庫的程式碼。您也可以處理 <xref:System.Data.DBConcurrencyException> 可能引發的任何例外狀況，以及任何其他例外狀況。

> [!NOTE]
> `CreateMessage` `ProcessDialogResults` 稍後將在本逐步解說中加入和方法。

##### <a name="to-add-error-handling-for-the-concurrency-error"></a>若要加入並行錯誤的錯誤處理

1. 在方法下方新增下列程式碼 `Form1_Load` ：

     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]

2. 取代 `CustomersBindingNavigatorSaveItem_Click` 方法以呼叫 `UpdateDatabase` 方法，使其看起來如下所示：

     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]

### <a name="displaychoices-to-the-user"></a>Displaychoices 給使用者
 您剛剛撰寫的程式碼會呼叫程式， `CreateMessage` 向使用者顯示錯誤資訊。 在這個逐步解說中，您可以使用訊息方塊來顯示使用者的不同記錄版本。這可讓使用者選擇是否要使用變更來覆寫記錄，或取消編輯。 當使用者選取選項 (按一下訊息方塊中的按鈕) ，回應就會傳遞給 `ProcessDialogResult` 方法。

##### <a name="to-create-the-message-to-display-to-the-user"></a>若要建立要對使用者顯示的訊息

- 在程式 **代碼編輯器**中加入下列程式碼，以建立訊息。 在方法下方輸入此程式碼 `UpdateDatabase` 。

     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]

### <a name="process-the-users-response"></a>處理使用者的回應
 您也需要程式碼來處理使用者對訊息方塊的回應。 選項是使用建議的變更來覆寫資料庫中目前的記錄，或放棄本機變更，並使用目前在資料庫中的記錄來重新整理資料表。 如果使用者選擇 [是]，則 <xref:System.Data.DataTable.Merge%2A> 會呼叫方法，並將 *preserveChanges* 引數設定為 `true` 。 這會導致更新嘗試成功，因為原始版本的記錄現在會符合資料庫中的記錄。

##### <a name="to-process-the-user-input-from-the-message-box"></a>從訊息方塊處理使用者輸入

- 在上一節中新增的程式碼下方新增下列程式碼。

     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]

## <a name="test-the-form"></a>測試表單
 您現在可以測試表單，以確保其行為如預期般運作。 若要模擬平行存取違規，您必須在填妥 NorthwindDataSet 之後變更資料庫中的資料。

#### <a name="to-test-the-form"></a>測試表單

1. 選取 **F5** 以執行應用程式。

2. 表單出現後，請讓它保持執行並切換至 Visual Studio IDE。

3. 在 [檢視]**** 功能表上，選擇 [伺服器總管]****。

4. 在 **伺服器總管**中，展開您的應用程式所使用的連接，然後展開 [ **資料表]** 節點。

5. 以滑鼠右鍵按一下 [ **Customers** ] 資料表，然後選取 [ **顯示資料表資料**]。

6. 在第一個記錄中 (`ALFKI`) 變更 `ContactName` 為 `Maria Anders2` 。

    > [!NOTE]
    > 流覽至不同的資料列來認可變更。

7. 切換至執行中的 `ConcurrencyWalkthrough` 表單。

8. 在表單 () 的第一筆記錄中 `ALFKI` ，變更 `ContactName` 為 `Maria Anders1` 。

9. 選取 [儲存] 按鈕。

     並行錯誤會引發，並顯示訊息方塊。

10. 選取 [ **否** ] 會取消更新，並使用目前在資料庫中的值來更新資料集。 選取 [ **是]** 會將建議的值寫入資料庫。

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)