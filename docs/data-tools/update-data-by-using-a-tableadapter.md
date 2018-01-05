---
title: "使用 TableAdapter 更新資料 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 4968eab5e1d355543a8658e72540bc66fa2543b9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="update-data-by-using-a-tableadapter"></a>使用 TableAdapter 更新資料
修改資料集的資料並驗證之後，您可以藉由呼叫回資料庫傳送更新的資料`Update`方法[TableAdapter](../data-tools/create-and-configure-tableadapters.md)。 `Update`方法更新單一資料表，並執行正確的命令 （INSERT、 UPDATE 或 DELETE） 根據<xref:System.Data.DataRow.RowState%2A>的資料表中每個資料列。 當資料集有連結的資料表時，Visual Studio 會產生 TableAdapterManager 類別用來進行更新。 TableAdapterManager 類別可確保以正確的順序，根據資料庫所定義的外部索引鍵條件約束會進行更新。 當您使用資料繫結控制項時，資料繫結架構會建立稱為 tableAdapterManager TableAdapterManager 類別的成員變數。 
  
> [!NOTE]
>  當您嘗試更新資料來源的資料集的內容時，您可能會收到錯誤。若要避免發生錯誤，我們建議您將程式碼呼叫配接器的`Update`方法內`try` / `catch`區塊。  
  
 確切的程序，以更新資料來源的商務需求，而有所不同，但包含下列步驟：  
  
1.  呼叫配接器的`Update`方法中的`try` / `catch`區塊。  
  
2.  如果會攔截到例外狀況，找出造成錯誤的資料列。 
  
3.  調解問題的資料列 （以程式設計方式如果可以或修改的使用者提供無效的資料列），並再試一次更新 (<xref:System.Data.DataRow.HasErrors%2A>， <xref:System.Data.DataTable.GetErrors%2A>)。  
  
## <a name="save-data-to-a-database"></a>將資料儲存至資料庫  
 呼叫`Update`的 TableAdapter 方法。 傳遞的名稱資料表，其中包含要寫入資料庫的值。  
  
#### <a name="to-update-a-database-by-using-a-tableadapter"></a>使用 TableAdapter 更新資料庫  
  
-   括住的 TableAdapter`Update`方法中的`try` / `catch`區塊。 下列範例示範如何更新的內容`Customers`資料表中`NorthwindDataSet`從`try` / `catch`區塊。  
  
     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]  
  
## <a name="see-also"></a>請參閱  
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)