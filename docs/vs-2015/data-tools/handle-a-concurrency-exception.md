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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c18b34cd3a38f41279885658a8d354ff6f9e8fe7
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59650170"
---
# <a name="handle-a-concurrency-exception"></a>處理並行例外狀況
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

並行存取例外狀況 (<xref:System.Data.DBConcurrencyException>) 兩位使用者嘗試同時變更資料庫中相同的資料時，會引發。 在本逐步解說中，您建立的 Windows 應用程式，說明如何攔截<xref:System.Data.DBConcurrencyException>，找出造成錯誤之資料列，並了解如何處理它的策略。  
  
 本逐步解說會引導您完成下列程序：  
  
1.  建立新**Windows 應用程式**專案。  
  
2.  建立新的資料集，根據 Northwind`Customers`資料表。  
  
3.  建立表單<xref:System.Windows.Forms.DataGridView>來顯示資料。  
  
4.  中的資料填入資料集`Customers`Northwind 資料庫中的資料表。  
  
5.  使用[Visual Database Tools](http://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1)在 Visual Studio 中直接存取`Customers`資料資料表和變更記錄。  
  
6.  變更同一筆記錄到不同的值，更新資料集，並嘗試將變更寫入資料庫中，會導致引發並行處理錯誤。  
  
7.  攔截到錯誤，然後顯示該記錄，讓使用者決定是否要繼續，並更新資料庫，或取消更新的不同版本。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您需要：  
  
-   Northwind 範例資料庫，以執行更新的權限的存取。
  
> [!NOTE]
>  對話方塊和功能表命令，您會看到，可能會有所不同說明中所述取決於您使用的設定或您使用的版本不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="create-a-new-project"></a>建立新專案  
 您可以建立新的 Windows 應用程式，以開始您逐步解說。  
  
#### <a name="to-create-a-new-windows-application-project"></a>若要建立新的 Windows 應用程式專案  
  
1.  在 [**檔案**] 功能表中，建立新的專案。  
  
2.  在 [**專案類型**] 窗格中，選取程式設計語言。  
  
3.  在 **範本**窗格中，選取**Windows 應用程式**。  
  
4.  將專案命名為`ConcurrencyWalkthrough`，然後選取 **[確定]**。  
  
     Visual Studio 將專案加入**方案總管 中**並顯示新的表單設計工具中。  
  
## <a name="create-the-northwind-dataset"></a>建立 Northwind 資料集  
 在本節中，您會建立名為資料集`NorthwindDataSet`。  
  
#### <a name="to-create-the-northwinddataset"></a>若要建立 NorthwindDataSet  
  
1.  在 **資料**功能表上，選擇**加入新的資料來源**。  
  
     [資料來源組態精靈][](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) 隨即開啟。  
  
2.  在 **選擇資料來源類型**畫面上，選取**資料庫**。  
  
3.  選取 Northwind 範例資料庫的連線，從清單中可用的連線。如果連接不在清單中的連線，請選取**新連線**  
  
    > [!NOTE]
    >  如果您要連接到本機資料庫檔案，請選取**No**當系統詢問您是否要將檔案加入您的專案。  
  
4.  在 [**將連接字串儲存到應用程式組態檔**畫面上，選取**下一步]**。  
  
5.  依序展開**資料表**節點，然後選取`Customers`資料表。 資料集的預設名稱應該是`NorthwindDataSet`。  
  
6.  選取 **完成**將資料集加入至專案。  
  
## <a name="create-a-data-bound-datagridview-control"></a>建立資料繫結 DataGridView 控制項  
 在本節中，您會建立<xref:System.Windows.Forms.DataGridView>藉由拖曳**客戶**項目從**Zdroje dat**視窗拖曳至您的 Windows Form。  
  
#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>若要建立繫結至 Customers 資料表的 DataGridView 控制項  
  
1.  在上**資料**功能表上，選擇**顯示資料來源**以開啟**資料來源視窗**。  
  
2.  在 [**資料來源**] 視窗中，展開**NorthwindDataSet**節點，然後再選取**客戶**資料表。  
  
3.  選取 [資料表] 節點的向下箭頭，然後選取**DataGridView**下拉式清單中。  
  
4.  將資料表拖曳至表單的空白區域。  
  
     A<xref:System.Windows.Forms.DataGridView>控制項，名為`CustomersDataGridView`並<xref:System.Windows.Forms.BindingNavigator>名為`CustomersBindingNavigator`新增至表單繫結至<xref:System.Windows.Forms.BindingSource>。這是在中，開啟繫結至`Customers`資料表中`NorthwindDataSet`。  
  
## <a name="test-the-form"></a>測試表單  
 您現在可以測試表單，以確定它的行為如預期般運作為止。  
  
#### <a name="to-test-the-form"></a>若要測試表單  
  
1.  選取  **F5**執行應用程式  
  
     表單會顯示<xref:System.Windows.Forms.DataGridView>填滿資料的控制項在其上`Customers`資料表。  
  
2.  在 **偵錯**功能表上，選取**停止偵錯**。  
  
## <a name="handleconcurrency-errors"></a>Handleconcurrency 錯誤  
 處理錯誤的方式是管理您的應用程式的特定商務規則而定。 此逐步解說中，我們使用下列策略做為範例如何 tohandle 並行錯誤。  
  
 Applicationpresents 記錄的三個版本的使用者：  
  
- 在資料庫中目前的記錄  
  
- 原始記錄載入至資料集  
  
- 中的資料集的建議的變更  
  
  使用者就能夠以建議的版本中，會覆寫資料庫，或取消更新，並重新整理資料庫中的新值的資料集。  
  
#### <a name="to-enable-the-handling-of-concurrency-errors"></a>若要啟用的並行錯誤處理  
  
1.  建立自訂的錯誤處理常式。  
  
2.  向使用者顯示的選項。  
  
3.  處理使用者的回應。  
  
4.  重新傳送更新，或重設資料集內。  
  
### <a name="addcode-to-handle-the-concurrency-exception"></a>Addcode 處理並行例外狀況  
 當您嘗試執行更新，並取得在引發例外狀況時，您通常會想要運用所引發的例外狀況所提供的資訊。  
  
 在本節中，您可以加入嘗試更新資料庫的程式碼。您也會處理任何<xref:System.Data.DBConcurrencyException>，可能會引發，以及任何其他例外狀況。  
  
> [!NOTE]
>  `CreateMessage`和`ProcessDialogResults`方法將會新增稍後在本逐步解說。  
  
##### <a name="to-add-error-handling-for-the-concurrency-error"></a>若要加入並行錯誤的錯誤處理  
  
1.  新增下列程式碼下方`Form1_Load`方法：  
  
     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]  
  
2.  取代`CustomersBindingNavigatorSaveItem_Click`方法來呼叫`UpdateDatabase`方法，讓它看起來如下所示：  
  
     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]  
  
### <a name="displaychoices-to-the-user"></a>Displaychoices 給使用者  
 您剛才的程式碼撰寫呼叫`CreateMessage`程序來向使用者顯示錯誤資訊。 此逐步解說中中,，您可以使用訊息方塊來向使用者顯示的資料錄的不同版本。這可讓使用者選擇是否要覆寫以變更的記錄，或取消編輯。 一旦使用者在訊息方塊上，選取 （按下按鈕） 的選項，回應會傳遞至`ProcessDialogResult`方法。  
  
##### <a name="to-create-the-message-to-display-to-the-user"></a>若要建立要向使用者顯示的訊息  
  
-   藉由新增下列程式碼，以建立訊息**程式碼編輯器**。 輸入下列程式碼下方`UpdateDatabase`方法。  
  
     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]  
  
### <a name="process-the-users-response"></a>處理使用者的回應  
 您也需要程式碼來處理使用者的回應訊息方塊。 有兩個選項所提議的變更，以覆寫在資料庫中目前的記錄或放棄本機變更並重新整理目前資料庫中的記錄資料表。 如果使用者選擇 [是]<xref:System.Data.DataTable.Merge%2A>方法呼叫*preserveChanges*引數設定為`true`。 這會導致更新嘗試會成功，因為資料錄的原始版本現在會符合資料庫中的記錄。  
  
##### <a name="to-process-the-user-input-from-the-message-box"></a>若要處理使用者輸入從訊息方塊  
  
-   下列程式碼下方新增上一節中所加入的程式碼。  
  
     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>測試表單  
 您現在可以測試表單，以確定它如預期般運作。 若要模擬並行存取違規，您必須填 NorthwindDataSet 後變更資料庫中的資料。  
  
#### <a name="to-test-the-form"></a>若要測試表單  
  
1.  選取  **F5**執行應用程式。  
  
2.  表單出現後，讓它保持執行，並切換至 Visual Studio IDE。  
  
3.  在 **檢視**功能表上，選擇**伺服器總管**。  
  
4.  在**伺服器總管**，展開 的連線您的應用程式是使用，並依**資料表**節點。  
  
5.  以滑鼠右鍵按一下**客戶**資料表，然後再選取**顯示資料表資料**。  
  
6.  在第一筆記錄 (`ALFKI`) 變更`ContactName`至`Maria Anders2`。  
  
    > [!NOTE]
    >  瀏覽至不同的資料列，以認可變更。  
  
7.  切換至`ConcurrencyWalkthrough`執行表單。  
  
8.  在表單上的第一筆記錄 (`ALFKI`)，變更`ContactName`至`Maria Anders1`。  
  
9. 選取 [儲存] 按鈕。  
  
     引發了並行錯誤，並出現訊息方塊。  
  
10. 選取**No**取消更新，並使用目前資料庫中的值來更新資料集。 選取**是**寫入資料庫中的建議的值。
  
## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)