---
title: 將資料儲存在交易中 |Microsoft Docs
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
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b30f51da001c62166a97c954b1416e35fd8b540f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671094"
---
# <a name="save-data-in-a-transaction"></a>儲存異動中的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說示範如何使用命名空間來儲存交易中的資料 <xref:System.Transactions> 。 此範例使用 Northwind 範例資料庫的 `Customers` 和 `Orders` 資料表。

## <a name="prerequisites"></a>必要條件
 此逐步解說需要 Northwind 範例資料庫的存取權。

## <a name="create-a-windows-application"></a>建立 Windows 應用程式
 第一個步驟是建立 **Windows 應用程式**。

#### <a name="to-create-the-new-windows-project"></a>建立新的 Windows 專案

1. 在 Visual Studio **的 [檔案** ] 功能表上，建立新 **專案**。

2. 將專案命名為 **SavingDataInATransactionWalkthrough**。

3. 選取 [ **Windows 應用程式**]，然後選取 **[確定]**。 如需詳細資訊，請參閱 [用戶端應用程式](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)。

     隨即建立 **SavingDataInATransactionWalkthrough** 專案，並將其新增至 [方案總管]****。

## <a name="create-a-database-data-source"></a>建立資料庫資料來源
 此步驟會使用 [ [資料來源設定向導]](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) ，根據 `Customers` `Orders` Northwind 範例資料庫中的和資料表建立資料來源。

#### <a name="to-create-the-data-source"></a>若要建立資料來源

1. 在 [ **資料** ] 功能表上，選取 [**顯示資料來源**]。

2. 在 [資料來源]**** 視窗中，選取 [新增新資料來源]****，以啟動 [資料來源組態精靈]****。

3. 在 [ **選擇資料來源類型**] 畫面上，選取 [ **資料庫**]，然後選取 **[下一步]**。

4. 在 [ **選擇您的資料連線**] 畫面上，執行下列其中一項：

    - 如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。

         -或-

    - 選取 [新增連線]**** 以啟動 [新增/修改連線]**** 對話方塊，並建立 Northwind 資料庫的連線。

5. 如果您的資料庫需要密碼，請選取包含機密資料的選項，然後選取 **[下一步]**。

6. 在 [ **將連接字串儲存到應用程式佈建檔** ] 畫面上，選取 [ **下一步]**。

7. 在 [ **選擇您的資料庫物件** ] 畫面上，展開 [ **資料表]** 節點。

8. 選取 `Customers` 和 `Orders` 資料表，然後選取 **[完成]**。

     **NorthwindDataSet** 會新增至您的專案中，且 `Customers` 和 `Orders` 資料表會出現在 [資料來源]**** 視窗中。

## <a name="addcontrols-to-the-form"></a>Addcontrols 至表單
 您可以從 [ **資料來源** ] 視窗將專案拖曳至表單，以建立資料繫結控制項。

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>在 Windows form 上建立資料繫結控制項

- 在 [ **資料來源** ] 視窗中，展開 [ **Customers** ] 節點。

- 從 [資料來源]**** 視窗，將 [客戶]**** 主節點拖曳至 **Form1**。

     <xref:System.Windows.Forms.DataGridView> 控制項以及巡覽記錄的工具區域 (<xref:System.Windows.Forms.BindingNavigator>) 會出現在表單上。 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、CustomersTableAdapter、<xref:System.Windows.Forms.BindingSource> 及 <xref:System.Windows.Forms.BindingNavigator> 會顯示在元件匣中。

- 拖曳 [相關 **Orders** ] 節點 (不是 [主要 **orders** ] 節點，但 [ **Fax** ] 資料行下方的相關子資料工作表節點) 至 **CustomersDataGridView**底下的表單。

     <xref:System.Windows.Forms.DataGridView> 隨即出現在表單上。 OrdersTableAdapter 並 <xref:System.Windows.Forms.BindingSource> 出現在元件匣中。

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>將參考加入至 System.object 元件
 交易會使用 <xref:System.Transactions> 命名空間。 預設不會新增對 system.string 元件的專案參考，所以您需要手動加入。

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>加入 System.Transactions DLL 檔案的參考

1. 選取 [ **專案** ] 功能表上的 [**加入參考**]。

2. 選取 [ **.net** ] 索引標籤上的 [ (的**交易**]) ，然後選取 **[確定]**。

     隨即會將 **System.Transactions** 的參考新增至專案。

## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>BindingNavigator 的 [SaveItem] 按鈕中的 Modifythe 程式碼
 若為放入表單的第一個資料表，則預設會將程式碼新增至的 [ `click` 儲存] 按鈕的事件 <xref:System.Windows.Forms.BindingNavigator> 。 您必須手動加入程式碼以更新所有其他資料表。 在這個逐步解說中，我們會從 [儲存] 按鈕的 click 事件處理常式中重構現有的儲存程式碼。我們也會建立一些方法，根據是否需要新增或刪除資料列，提供特定的更新功能。

#### <a name="to-modify-the-auto-generated-save-code"></a>修改自動產生的儲存程式碼

1. 在**CustomersBindingNavigator**上選取 [**儲存**] 按鈕， (具有磁碟片圖示的按鈕) 。

2. 以下列程式碼取代 `CustomersBindingNavigatorSaveItem_Click` 方法：

    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]

   對關聯資料變更的協調順序如下：

- 刪除子記錄。  (在這種情況下，請從資料表中刪除記錄 `Orders` 。 ) 

- 刪除父記錄。  (在這種情況下，請從資料表中刪除記錄 `Customers` 。 ) 

- 插入父記錄。 (在此案例中，請在資料表中插入記錄 `Customers` 。 ) 

- 插入子記錄。  (在這種情況下，請在資料表中插入記錄 `Orders` 。 ) 

#### <a name="to-delete-existing-orders"></a>刪除現有訂單

- 將下列 `DeleteOrders` 方法新增至 **Form1**：

     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]

#### <a name="to-delete-existing-customers"></a>刪除現有客戶

- 將下列 `DeleteCustomers` 方法新增至 **Form1**：

     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]

#### <a name="to-add-new-customers"></a>加入新客戶

- 將下列 `AddNewCustomers` 方法新增至 **Form1**：

     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]

#### <a name="to-add-new-orders"></a>加入新訂單

- 將下列 `AddNewOrders` 方法新增至 **Form1**：

     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]

## <a name="run-the-application"></a>執行應用程式

#### <a name="to-run-the-application"></a>若要執行應用程式

- 選取 **F5** 以執行應用程式。

## <a name="see-also"></a>另請參閱
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
