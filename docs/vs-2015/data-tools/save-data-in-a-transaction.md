---
title: 儲存異動中的資料 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bade19778c64b6338c29db1eef8eb09a0d95fa3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874640"
---
# <a name="save-data-in-a-transaction"></a>儲存異動中的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
本逐步解說示範如何將資料儲存在交易中，使用<xref:System.Transactions>命名空間。 此範例使用 Northwind 範例資料庫中的 `Customers` 和 `Orders` 資料表。  
  
## <a name="prerequisites"></a>必要條件  
 此逐步解說需要 Northwind 範例資料庫的存取權。 如需設定 Northwind 範例資料庫的詳細資訊，請參閱[如何： 安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## <a name="create-a-windows-application"></a>建立 Windows 應用程式  
 第一個步驟是建立**Windows 應用程式**。  
  
#### <a name="to-create-the-new-windows-project"></a>建立新的 Windows 專案  
  
1.  在 Visual Studio 中，在**檔案** 功能表中，建立新**專案**。  
  
2.  將專案命名為**SavingDataInATransactionWalkthrough**。  
  
3.  選取  **Windows 應用程式**，然後選取**確定**。 如需詳細資訊，請參閱 <<c0> [ 用戶端應用程式](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)。  
  
     **SavingDataInATransactionWalkthrough**建立專案並將其加入至**方案總管 中**。  
  
## <a name="create-a-database-data-source"></a>建立資料庫資料來源  
 此步驟中使用[資料來源組態精靈](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)來建立資料來源，根據`Customers`和`Orders`Northwind 範例資料庫中的資料表。  
  
#### <a name="to-create-the-data-source"></a>若要建立資料來源  
  
1.  在 **資料**功能表上，選取**顯示資料來源**。  
  
2.  在 **資料來源**視窗中，選取**加入新的資料來源**來啟動**資料來源組態精靈**。  
  
3.  在 [**選擇資料來源類型**畫面上，選取**資料庫**，然後選取**下一步]**。  
  
4.  在 **選擇您的資料連接**畫面執行下列其中一項：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
         -或-  
  
    -   選取**新的連線**來啟動**加入/修改連接**對話方塊並且建立與 Northwind 資料庫的連接。  
  
5.  如果您的資料庫需要密碼，請選取選項來加入敏感性資料，然後選取**下一步**。  
  
6.  在 [**將連接字串儲存到應用程式組態檔**畫面上，選取**下一步]**。  
  
7.  在 **選擇您的資料庫物件**畫面上，展開**資料表**節點。  
  
8.  選取 `Customers`並`Orders`資料表，然後選取**完成**。  
  
     **NorthwindDataSet**新增至您的專案和`Customers`並`Orders`資料表會出現在**Zdroje dat**視窗。  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols 至表單  
 您可以建立資料繫結控制項項目從**Zdroje dat**視窗拖曳至表單。  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>若要建立資料繫結 Windows form 上的控制項  
  
-   在 [**資料來源**] 視窗中，展開**客戶**節點。  
  
-   主**客戶**從節點**Zdroje dat**  視窗拖曳到**Form1**。  
  
     <xref:System.Windows.Forms.DataGridView> 控制項以及用於巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 會出現在表單上。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)， [CustomersTableAdapter](../data-tools/tableadapter-overview.md)，<xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>會出現在元件匣。  
  
-   將相關**訂單**節點 (不是主**訂單**節點，但是相關的子資料表節點下方**傳真**資料行) 至下面的表單**CustomersDataGridView**。  
  
     <xref:System.Windows.Forms.DataGridView> 隨即出現在表單上。 [OrdersTableAdapter](../data-tools/tableadapter-overview.md)和<xref:System.Windows.Forms.BindingSource>會出現在元件匣。  
  
## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>加入 System.Transactions 組件的參考  
 異動會使用 <xref:System.Transactions> 命名空間。 預設不會加入 system.transactions 組件的專案參考，所以您必須手動加入。  
  
#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>加入 System.Transactions DLL 檔案的參考  
  
1.  在 **專案**功能表上，選取**加入參考**。  
  
2.  選取 [ **System.Transactions**(在 **.NET** ] 索引標籤)，然後選取**確定**。  
  
     參考**System.Transactions**加入至專案。  
  
## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Modifythe BindingNavigator 的 SaveItem 按鈕中的程式碼  
 預設為第一個資料表拖曳至表單，加入程式碼`click`事件的儲存按鈕<xref:System.Windows.Forms.BindingNavigator>。 您必須手動加入程式碼以更新所有其他資料表。 此逐步解說中，我們重構現有儲存程式碼，從儲存按鈕的 click 事件處理常式。我們也會建立幾個方法，以提供特定的更新功能，根據是否需要新增或刪除資料列。  
  
#### <a name="to-modify-the-auto-generated-save-code"></a>修改自動產生的儲存程式碼  
  
1. 選取 **儲存**按鈕**CustomersBindingNavigator** （磁碟片圖示的按鈕）。  
  
2. 以下列程式碼取代 `CustomersBindingNavigatorSaveItem_Click` 方法：  
  
    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]  
  
   對關聯資料變更的協調順序如下：  
  
-   刪除子記錄。 (在此情況下，刪除資料錄`Orders`資料表。)  
  
-   刪除父記錄。 (在此情況下，刪除資料錄`Customers`資料表。)  
  
-   插入父記錄。(在此情況下，將記錄插入`Customers`資料表。)  
  
-   插入子記錄。 (在此情況下，將記錄插入`Orders`資料表。)  
  
#### <a name="to-delete-existing-orders"></a>刪除現有訂單  
  
-   新增下列`DeleteOrders`方法，以**Form1**:  
  
     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]  
  
#### <a name="to-delete-existing-customers"></a>刪除現有客戶  
  
-   新增下列`DeleteCustomers`方法，以**Form1**:  
  
     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]  
  
#### <a name="to-add-new-customers"></a>加入新客戶  
  
-   新增下列`AddNewCustomers`方法，以**Form1**:  
  
     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]  
  
#### <a name="to-add-new-orders"></a>加入新訂單  
  
-   新增下列`AddNewOrders`方法，以**Form1**:  
  
     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]  
  
## <a name="run-the-application"></a>執行應用程式  
  
#### <a name="to-run-the-application"></a>若要執行應用程式  
  
-   選取 **F5**執行應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)

