---
title: 在表單之間傳遞資料 |Microsoft Docs
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
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 27d4b1ec935444009be1f85f4c1ad95f9da91f68
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425503"
---
# <a name="pass-data-between-forms"></a>在表單之間傳遞資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此逐步解說提供將資料從某個表單傳遞至另一個表單的指示。 使用客戶和訂單資料表，從 Northwind，一種格式可讓使用者選取客戶，和第二個表單會顯示所選取的客戶的訂單。 本逐步解說示範如何從第一個表單接收資料的第二個表單上建立方法。  
  
> [!NOTE]
> 此逐步解說只示範一種在表單之間傳遞資料的方法。 還有其他選項，將資料傳遞至表單，包括建立第二個建構函式來接收資料，或建立的公用屬性，可以使用設定資料從第一種形式。  
  
 這個逐步解說中所述的工作包括：  
  
- 建立新**Windows 應用程式**專案。  
  
- 建立和設定與資料集[資料來源組態精靈](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)。  
  
- 選取從 [資料來源] 視窗拖曳項目時，要在表單上建立的控制項。 如需詳細資訊，請參閱 <<c0> [ 設定要從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
- 從 [資料來源] 視窗將項目拖曳至表單，以建立資料繫結控制項。  
  
- 使用資料格建立第二個表單以顯示資料。  
  
- 建立 TableAdapter 查詢以擷取特定客戶的訂單。  
  
- 在表單之間傳遞資料。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您需要：  
  
- Northwind 範例資料庫的存取權。
  
## <a name="create-the-windows-application"></a>建立 Windows 應用程式  
  
#### <a name="to-create-the-new-windows-project"></a>建立新的 Windows 專案  
  
1. 從**檔案** 功能表中，建立新的專案。  
  
2. 將專案命名為 `PassingDataBetweenForms`。  
  
3. 選取  **Windows Forms 應用程式**，然後按一下**確定**。 如需詳細資訊，請參閱 <<c0> [ 用戶端應用程式](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)。  
  
     隨即建立 **PassingDataBetweenForms** 專案，並將其新增至 [方案總管]。  
  
## <a name="create-the-data-source"></a>建立資料來源  
  
#### <a name="to-create-the-data-source"></a>若要建立資料來源  
  
1. 按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。  
  
2. 在 [資料來源] 視窗中，選取 [新增新資料來源]，以啟動 [資料來源組態精靈]。  
  
3. 請選取 [ **選擇資料來源類型** ] 頁面上的 [ **資料庫** ]，再按 [ **下一步**]。  
  
4. 在 [選擇資料庫模型] 頁面中，確認已指定 [資料集]，然後按一下 [下一步]。  
  
5. 在 [選擇您的資料連線] 頁面上，執行下列其中一項：  
  
    - 如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
    - 選取 [新增連線] 啟動 [新增/修改連線] 對話方塊。  
  
6. 若您的資料庫需要密碼，且可以使用包含敏感性資料的選項，則請選取此選項，然後按一下 [下一步]。  
  
7. 在 [**將連接字串儲存到應用程式組態檔**頁面上，按一下**下一步]**。  
  
8. 展開 [選擇您的資料庫物件] 頁面上的 [資料表] 節點。  
  
9. 選取 [客戶] 和 [訂單] 資料表，然後按一下 [完成]。  
  
     **NorthwindDataSet** 即會新增至專案，且 [客戶] 和 [訂單] 資料表會出現在 [資料來源] 視窗中。  
  
## <a name="create-the-first-form-form1"></a>建立第一個表單 (Form1)  
 您可以從 [資料來源] 視窗拖曳 [客戶] 節點以建立資料繫結資料格 (<xref:System.Windows.Forms.DataGridView> 控制項)。  
  
#### <a name="to-create-a-data-bound-grid-on-the-form"></a>在表單上建立資料繫結資料格  
  
- 從 [資料來源] 視窗，將 [客戶] 主節點拖曳至 **Form1**。  
  
     <xref:System.Windows.Forms.DataGridView> 以及巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 會出現在 **Form1** 上。 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、CustomersTableAdapter、<xref:System.Windows.Forms.BindingSource> 及 <xref:System.Windows.Forms.BindingNavigator> 會顯示在元件匣中。  
  
## <a name="create-the-second-form-form2"></a>建立第二個表單 (Form2)  
  
#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>建立要將資料傳遞至其中的第二個表單  
  
1. 在 [專案] 功能表中，選擇 [新增 Windows Form]。  
  
2. 保留 **Form2** 預設名稱，然後按一下 [新增]。  
  
3. 從 [資料來源] 視窗，將 [訂單] 主節點拖曳至 **Form2**。  
  
     <xref:System.Windows.Forms.DataGridView> 以及巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 會出現在 **Form2** 上。 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、CustomersTableAdapter、<xref:System.Windows.Forms.BindingSource> 及 <xref:System.Windows.Forms.BindingNavigator> 會顯示在元件匣中。  
  
4. 從元件匣刪除 **OrdersBindingNavigator**。  
  
     **OrdersBindingNavigator** 會從 **Form2** 中消失。  
  
## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>將 TableAdapter 查詢加入 Form2 以載入 Form1 上所選客戶的訂單  
  
#### <a name="to-create-a-tableadapter-query"></a>若要建立 TableAdapter 查詢  
  
1. 在 [方案總管] 中按兩下 **NorthwindDataSet.xsd** 檔案。  
  
2. 以滑鼠右鍵按一下 **OrdersTableAdapter**，並選取 [新增查詢]。  
  
3. 保留 [使用 SQL 陳述式] 預設選項，然後按一下 [下一步]。  
  
4. 保留 [傳回資料列的 SELECT] 預設選項，然後按一下 [下一步]。  
  
5. 將 WHERE 子句新增至查詢，以根據 `CustomerID` 傳回 `Orders`。 查詢應與下列類似：  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    > 針對資料庫確認參數語法是否正確。 例如，在 Microsoft Access 中，WHERE 子句應看起來類似：`WHERE CustomerID = ?`。  
  
6. 按 [ **下一步**]。  
  
7. 針對**填滿 DataTableMethod 名稱**，輸入`FillByCustomerID`。  
  
8. 清除 [傳回 DataTable] 選項，然後按一下 [下一步]。  
  
9. 按一下 [ **完成**]。  
  
## <a name="create-a-method-on-form2-to-pass-data-to"></a>若要將資料傳遞至 Form2 上建立方法  
  
#### <a name="to-create-a-method-to-pass-data-to"></a>建立方法以將資料傳遞給它  
  
1. 以滑鼠右鍵按一下 **Form2**，並選取 [檢視程式碼]，以在 [程式碼編輯器] 中開啟 **Form2**。  
  
2. 在 `Form2_Load` 方法之後，將下列程式碼新增至 **Form2**：  
  
     [!code-csharp[VbRaddataDisplaying#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs#1)]
     [!code-vb[VbRaddataDisplaying#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb#1)]  
  
## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>將資料傳遞，並顯示 Form2 的 Form1 上建立方法  
  
#### <a name="to-create-a-method-to-pass-data-to-form2"></a>建立方法以將資料傳遞給 Form2  
  
1. 在 **Form1** 中，以滑鼠右鍵按一下 [客戶] 資料格，然後按一下 [屬性]。  
  
2. 在 [屬性] 視窗中按一下 [事件]。  
  
3. 按兩下 **CellDoubleClick** 事件。  
  
     程式碼編輯器隨即開啟。  
  
4. 更新方法定義以符合下列範例：  
  
     [!code-csharp[VbRaddataDisplaying#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#2)]
     [!code-vb[VbRaddataDisplaying#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#2)]  
  
## <a name="run-the-application"></a>執行應用程式  
  
#### <a name="to-run-the-application"></a>若要執行應用程式  
  
- 按 F5 執行應用程式。  
  
- 按兩下 **Form1** 中的客戶記錄，以該客戶的訂單開啟 **Form2**。  
  
## <a name="next-steps"></a>後續步驟  
 視應用程式的需求而定，在表單之間傳遞資料之後，您可能會有幾個想要執行的步驟。 一些您可以加強這個逐步解說的部分包括：  
  
- 編輯資料集，以加入或移除資料庫物件。 如需詳細資訊，請參閱[建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。  
  
- 加入將資料存回資料庫的功能。 如需詳細資訊，請參閱 <<c0> [ 將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)。  
  
## <a name="see-also"></a>另請參閱  
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
