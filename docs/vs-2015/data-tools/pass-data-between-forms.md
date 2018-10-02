---
title: 在表單之間傳遞資料 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: e046bdf38af09b5f7ea0e8beb296a2b3d32cff6d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491580"
---
# <a name="pass-data-between-forms"></a>在表單之間傳遞資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[表單之間傳遞資料](https://docs.microsoft.com/visualstudio/data-tools/pass-data-between-forms)。  
  
  
此逐步解說提供將資料從某個表單傳遞至另一個表單的指示。 使用客戶和訂單資料表，從 Northwind，一種格式可讓使用者選取客戶，和第二個表單會顯示所選取的客戶的訂單。 本逐步解說示範如何從第一個表單接收資料的第二個表單上建立方法。  
  
> [!NOTE]
>  此逐步解說只示範一種在表單之間傳遞資料的方法。 還有其他選項，將資料傳遞至表單，包括建立第二個建構函式來接收資料，或建立的公用屬性，可以使用設定資料從第一種形式。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立新**Windows 應用程式**專案。  
  
-   建立和設定與資料集[資料來源組態精靈](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)。  
  
-   選取要拖曳的項目時，表單上建立的控制項**Zdroje dat**視窗。 如需詳細資訊，請參閱 <<c0> [ 設定要從資料來源視窗拖曳時要建立的控制項](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
-   建立資料繫結控制項中的項目**Zdroje dat**視窗拖曳至表單。  
  
-   使用資料格建立第二個表單以顯示資料。  
  
-   建立 TableAdapter 查詢以擷取特定客戶的訂單。  
  
-   在表單之間傳遞資料。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您需要：  
  
-   Northwind 範例資料庫的存取權。 如需詳細資訊，請參閱 <<c0> [ 如何： 安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## <a name="create-the-windows-application"></a>建立 Windows 應用程式  
  
#### <a name="to-create-the-new-windows-project"></a>建立新的 Windows 專案  
  
1.  從**檔案** 功能表中，建立新的專案。  
  
2.  將專案命名為 `PassingDataBetweenForms`。  
  
3.  選取  **Windows Forms 應用程式**，然後按一下**確定**。 如需詳細資訊，請參閱 <<c0> [ 用戶端應用程式](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)。  
  
     **PassingDataBetweenForms**專案時建立，並加入至**方案總管 中**。  
  
## <a name="create-the-data-source"></a>建立資料來源  
  
#### <a name="to-create-the-data-source"></a>若要建立資料來源  
  
1.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。  
  
2.  在 **資料來源**視窗中，選取**加入新的資料來源**來啟動**資料來源組態**精靈。  
  
3.  請選取 [ **選擇資料來源類型** ] 頁面上的 [ **資料庫** ]，再按 [ **下一步**]。  
  
4.  在 [**選擇資料庫模型**頁面上，確認**資料集**未指定，然後**下一步]**。  
  
5.  在 **選擇您的資料連接**頁面上，執行下列其中之一：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
    -   選取 [**新的連線**來啟動**加入/修改連接**] 對話方塊。  
  
6.  如果您的資料庫需要密碼，而且會啟用此選項来包括敏感性資料，選取選項，然後按一下**下一步**。  
  
7.  在 [**將連接字串儲存到應用程式組態檔**頁面上，按一下**下一步]**。  
  
8.  在 **選擇您的資料庫物件**頁面上，展開**資料表**節點。  
  
9. 選取 **客戶**並**訂單**資料表，然後再按一下**完成**。  
  
     **NorthwindDataSet**新增至您的專案，而**客戶**並**訂單**資料表會出現在**資料來源**視窗。  
  
## <a name="create-the-first-form-form1"></a>建立第一個表單 (Form1)  
 您可以建立資料繫結方格 (<xref:System.Windows.Forms.DataGridView>控制項)，藉由拖曳**客戶**節點從**Zdroje dat**視窗拖曳至表單。  
  
#### <a name="to-create-a-data-bound-grid-on-the-form"></a>在表單上建立資料繫結資料格  
  
-   主**客戶**從節點**Zdroje dat**  視窗拖曳到**Form1**。  
  
     A<xref:System.Windows.Forms.DataGridView>和的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 的巡覽記錄會出現在**Form1**。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)， [CustomersTableAdapter](../data-tools/tableadapter-overview.md)， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>會出現在元件匣。  
  
## <a name="create-the-second-form-form2"></a>建立第二個表單 (Form2)  
  
#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>建立要將資料傳遞至其中的第二個表單  
  
1.  在 [專案] 功能表中，選擇 [新增 Windows Form]。  
  
2.  保留預設名稱**Form2**，然後按一下**新增**。  
  
3.  主**訂單**從節點**Zdroje dat**  視窗拖曳到**Form2**。  
  
     A<xref:System.Windows.Forms.DataGridView>和的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 的巡覽記錄會出現在**Form2**。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)， [CustomersTableAdapter](../data-tools/tableadapter-overview.md)， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>會出現在元件匣。  
  
4.  刪除**OrdersBindingNavigator**從元件匣。  
  
     **OrdersBindingNavigator**就會消失**Form2**。  
  
## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>將 TableAdapter 查詢加入 Form2 以載入 Form1 上所選客戶的訂單  
  
#### <a name="to-create-a-tableadapter-query"></a>若要建立 TableAdapter 查詢  
  
1.  按兩下**NorthwindDataSet.xsd**中的檔案**方案總管 中**。  
  
2.  以滑鼠右鍵按一下**OrdersTableAdapter**，然後選取**加入查詢**。  
  
3.  保留預設選項**使用 SQL 陳述式**，然後按一下**下一步**。  
  
4.  保留預設選項**會傳回資料列選取**，然後按一下**下一步**。  
  
5.  WHERE 子句加入查詢，傳回`Orders`根據`CustomerID`。 查詢應與下列類似：  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  針對資料庫確認參數語法是否正確。 例如，在 Microsoft Access 中，WHERE 子句應看起來類似：`WHERE CustomerID = ?`。  
  
6.  按 [ **下一步**]。  
  
7.  針對**填滿 DataTableMethod 名稱**，輸入`FillByCustomerID`。  
  
8.  清除**傳回 DataTable**選項，然後再按一下**下一步**。  
  
9. 按一下 [ **完成**]。  
  
## <a name="create-a-method-on-form2-to-pass-data-to"></a>若要將資料傳遞至 Form2 上建立方法  
  
#### <a name="to-create-a-method-to-pass-data-to"></a>建立方法以將資料傳遞給它  
  
1.  以滑鼠右鍵按一下**Form2**，然後選取**檢視程式碼**以開啟**Form2**中**程式碼編輯器**。  
  
2.  將下列程式碼加入**Form2**之後`Form2_Load`方法：  
  
     [!code-csharp[VbRaddataDisplaying#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs#1)]
     [!code-vb[VbRaddataDisplaying#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb#1)]  
  
## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>將資料傳遞，並顯示 Form2 的 Form1 上建立方法  
  
#### <a name="to-create-a-method-to-pass-data-to-form2"></a>建立方法以將資料傳遞給 Form2  
  
1.  在  **Form1**，在 Customer 資料格，以滑鼠右鍵按一下，然後按一下**屬性**。  
  
2.  在 [**屬性**] 視窗中，按一下**事件**。  
  
3.  按兩下**CellDoubleClick**事件。  
  
     程式碼編輯器隨即開啟。  
  
4.  更新方法定義以符合下列範例：  
  
     [!code-csharp[VbRaddataDisplaying#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#2)]
     [!code-vb[VbRaddataDisplaying#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#2)]  
  
## <a name="run-the-application"></a>執行應用程式  
  
#### <a name="to-run-the-application"></a>若要執行應用程式  
  
-   按 F5 執行應用程式。  
  
-   按兩下中的客戶記錄**Form1**來開啟**Form2**與該客戶的訂單。  
  
## <a name="next-steps"></a>後續步驟  
 視應用程式的需求而定，在表單之間傳遞資料之後，您可能會有幾個想要執行的步驟。 一些您可以加強這個逐步解說的部分包括：  
  
-   編輯資料集，以加入或移除資料庫物件。 如需詳細資訊，請參閱[建立和設定資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。  
  
-   加入將資料存回資料庫的功能。 如需詳細資訊，請參閱 <<c0> [ 將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)。  
  
## <a name="see-also"></a>另請參閱  
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

