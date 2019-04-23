---
title: 使用 TableAdapter DBDirect 方法儲存的資料 |Microsoft Docs
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
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 096d15b82e256df2bc35bc443c248e8ca0662c19
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59661850"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>使用 TableAdapter DBDirect 方法儲存資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說提供使用 TableAdapter 的 DBDirect 方法，直接對資料庫執行 SQL 陳述式的詳細的指示。 TableAdapter 的 DBDirect 方法可讓您妥善控制您的資料庫更新。 您可以使用它們來執行特定 SQL 陳述式和預存程序的呼叫個別`Insert`， `Update`，並`Delete`方法，視您的應用程式 (而不是多載`Update`方法，以執行更新INSERT 和 DELETE 陳述式，全都在一個呼叫中的)。  
  
 在這個逐步解說期間，您將了解如何：  
  
-   建立新**Windows 應用程式**。  
  
-   建立並設定與資料集[資料來源組態精靈](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)。  
  
-   從 [資料來源] 視窗拖曳項目時，選取要在表單上建立的控制項。 如需詳細資訊，請參閱 <<c0> [ 設定要從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
-   從 [資料來源] 視窗將項目拖曳至表單，以建立資料繫結表單。  
  
-   加入方法以直接存取資料庫，並執行插入、 更新和刪除...  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您將需要：  
  
-   Northwind 範例資料庫的存取權。
  
## <a name="create-a-windows-application"></a>建立 Windows 應用程式  
 第一個步驟是建立**Windows 應用程式**。  
  
#### <a name="to-create-the-new-windows-project"></a>建立新的 Windows 專案  
  
1.  在 Visual Studio 中，在**檔案** 功能表中，建立新**專案**。  
  
2.  將專案命名為**TableAdapterDbDirectMethodsWalkthrough**。  
  
3.  選取  **Windows 應用程式**，然後選取**確定**。 如需詳細資訊，請參閱 <<c0> [ 用戶端應用程式](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)。  
  
     隨即建立 **TableAdapterDbDirectMethodsWalkthrough** 專案，並將其新增至 [方案總管]。  
  
## <a name="create-a-data-source-from-your-database"></a>從您的資料庫建立資料來源  
 此步驟使用 [資料來源組態精靈]，根據 Northwind 範例資料庫中的 `Region` 資料表建立資料來源。 您必須具有 Northwind 範例資料庫的存取權，才能建立連接。
  
#### <a name="to-create-the-data-source"></a>若要建立資料來源  
  
1.  在 **資料**功能表上，選取**顯示資料來源**。  
  
2.  在 [資料來源] 視窗中，選取 [新增新資料來源]，以啟動 [資料來源組態精靈]。  
  
3.  在 [**選擇資料來源類型**畫面上，選取**資料庫**，然後選取**下一步]**。  
  
4.  在 **選擇您的資料連接**畫面上，執行下列其中一項：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
         -或-  
  
    -   選取 [新增連線] 啟動 [新增/修改連線] 對話方塊。  
  
5.  如果您的資料庫需要密碼，請選取選項來加入敏感性資料，然後選取**下一步**。  
  
6.  在 [**將連接字串儲存到應用程式組態檔**畫面上，選取**下一步]**。  
  
7.  在 **選擇您的資料庫物件**畫面上，展開**資料表**節點。  
  
8.  選取 `Region`資料表，然後再選取**完成**。  
  
     **NorthwindDataSet** 隨即會新增至您的專案，且 `Region` 資料表會出現在 [資料來源] 視窗中。  
  
## <a name="addcontrols-to-the-form-to-display-the-data"></a>Addcontrols 表單來顯示資料  
 從 [資料來源] 視窗將項目拖曳至表單，以建立資料繫結控制項。  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>若要建立資料繫結 Windows form 上的控制項  
  
-   主**地區**從節點**Zdroje dat**視窗拖曳至表單。  
  
     <xref:System.Windows.Forms.DataGridView> 控制項以及巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 會出現在表單上。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)，RegionTableAdapter， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>會出現在元件匣。  
  
#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>加入會呼叫個別 TableAdapter DbDirect 方法的按鈕  
  
1.  從 [工具箱] 將三個 <xref:System.Windows.Forms.Button> 控制項拖曳至 **Form1** (位於 **RegionDataGridView** 下方)。  
  
2.  在每個按鈕上，設定下列 [名稱] 及 [文字] 屬性。  
  
    |名稱|文字|  
    |----------|----------|  
    |`InsertButton`|**插入**|  
    |`UpdateButton`|**更新**|  
    |`DeleteButton`|**刪除**|  
  
#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>加入程式碼以將新記錄插入至資料庫  
  
1.  選取  **InsertButton**建立 click 事件的事件處理常式，並在程式碼編輯器中開啟您的表單。  
  
2.  以下列程式碼取代 `InsertButton_Click` 事件處理常式：  
  
     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]  
  
#### <a name="to-add-code-to-update-records-in-the-database"></a>加入程式碼以更新資料庫中的記錄  
  
1.  按兩下 [UpdateButton] 建立 Click 事件的事件處理常式，並在程式碼編輯器中開啟表單。  
  
2.  以下列程式碼取代 `UpdateButton_Click` 事件處理常式：  
  
     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]  
  
#### <a name="to-add-code-to-delete-records-from-the-database"></a>加入程式碼以從資料庫刪除記錄  
  
1.  選取  **DeleteButton**建立 click 事件的事件處理常式，並在程式碼編輯器中開啟您的表單。  
  
2.  以下列程式碼取代 `DeleteButton_Click` 事件處理常式：  
  
     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]  
  
## <a name="run-the-application"></a>執行應用程式  
  
#### <a name="to-run-the-application"></a>若要執行應用程式  
  
-   選取  **F5**執行應用程式。  
  
-   選取 **插入**按鈕，並確認新的記錄會出現在方格中。  
  
-   選取 **更新**按鈕，並確認更新的記錄時，會在方格中。  
  
-   選取 **刪除**按鈕，並確認該記錄移除時的方格中。  
  
## <a name="next-steps"></a>後續步驟  
 根據您的應用程式的需求，有幾個步驟，您可能想要建立資料繫結表單之後執行。 一些您可以加強這個逐步解說的部分包括：  
  
-   將搜尋功能加入至表單。 如需詳細資訊，請參閱[如何：參數化的查詢的 Windows Form 應用程式中加入](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416)。  
  
-   在 [資料來源] 視窗中選取 [使用精靈設定資料集]，將其他資料表新增至資料集。 您可以藉由將關聯節點拖曳至表單，加入顯示關聯資料的控制項。 
  
## <a name="see-also"></a>另請參閱  
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
