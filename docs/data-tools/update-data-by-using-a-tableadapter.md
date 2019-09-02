---
title: 使用 TableAdapter 更新資料
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 61ebcd6c833b55f0769365b89274e35136c914f9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925355"
---
# <a name="update-data-by-using-a-tableadapter"></a>使用 TableAdapter 更新資料

修改和驗證資料集中的資料之後, 您可以藉由呼叫`Update` [TableAdapter](../data-tools/create-and-configure-tableadapters.md)的方法, 將更新的資料傳送回資料庫。 方法會更新單一資料表, 並根據<xref:System.Data.DataRow.RowState%2A>資料表中每個資料列的來執行正確的命令 (INSERT、UPDATE 或 DELETE)。 `Update` 當資料集具有相關資料表時, Visual Studio 會產生用來執行更新的 TableAdapterManager 類別。 TableAdapterManager 類別可確保根據資料庫中定義的外鍵條件約束, 以正確的順序來進行更新。 當您使用資料繫結控制項時, 資料系結架構會建立名為 tableAdapterManager 之 TableAdapterManager 類別的成員變數。

> [!NOTE]
> 當您嘗試使用資料集的內容來更新資料來源時, 您可能會收到錯誤。 為避免發生錯誤, 建議您將呼叫`Update`介面卡之方法的程式碼放在`catch`區塊`try` /內。

更新資料來源的確切程式可能會根據商務需求而有所不同, 但包括下列步驟:

1. 在區塊中`Update`呼叫介面卡的方法。/ `try` `catch`

2. 如果攔截到例外狀況, 請找出造成錯誤的資料列。

3. 協調資料列中的問題 (如果您可以, 以程式設計方式, 或將不正確資料列呈現給使用者進行修改), 然後再次嘗試更新<xref:System.Data.DataRow.HasErrors%2A>( <xref:System.Data.DataTable.GetErrors%2A>、)。

## <a name="save-data-to-a-database"></a>將資料儲存至資料庫

呼叫 TableAdapter 的方法。 `Update` 傳遞包含要寫入至資料庫之值的資料表名稱。

### <a name="to-update-a-database-by-using-a-tableadapter"></a>若要使用 TableAdapter 更新資料庫

- 將 TableAdapter 的`Update`方法/括`try`在區塊中。`catch` 下列範例顯示如何在`Customers` `try` `NorthwindDataSet` 區塊`catch`內/從更新中的資料表內容。

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)