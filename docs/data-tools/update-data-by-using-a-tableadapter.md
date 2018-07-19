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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 88d4da868174396bfed148fc6088e5675e1198b2
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37116889"
---
# <a name="update-data-by-using-a-tableadapter"></a>使用 TableAdapter 更新資料

在資料集中的資料已修改且驗證之後，您可以藉由呼叫傳回至資料庫傳送更新的資料`Update`方法[TableAdapter](../data-tools/create-and-configure-tableadapters.md)。 `Update`方法會更新單一資料表，並執行正確的命令 （INSERT、 UPDATE 或 DELETE） 根據<xref:System.Data.DataRow.RowState%2A>的資料表中每個資料列。 當資料集有相關的資料表時，則 Visual Studio 會產生 TableAdapterManager 類別，您用來進行更新。 TableAdapterManager 類別可確保以正確的順序，根據資料庫所定義的外部索引鍵條件約束會進行更新。 當您使用資料繫結控制項時，資料繫結架構會建立呼叫 tableAdapterManager TableAdapterManager 類別成員變數。

> [!NOTE]
> 當您嘗試更新資料來源的資料集的內容時，您可能會收到錯誤。 為了避免錯誤，我們建議您將程式碼呼叫的介面卡`Update`方法內`try` / `catch`區塊。

 更新資料來源的確切程序會根據商務需求而有所不同，但包含下列步驟：

1.  呼叫的介面卡`Update`方法中的`try` / `catch`區塊。

2.  如果攔截到例外狀況時，找出造成錯誤的資料列。

3.  調解這個問題，資料中的資料列 （如果可以，以程式設計方式或出示無效的資料列已修改的使用者），並再試一次更新 (<xref:System.Data.DataRow.HasErrors%2A>， <xref:System.Data.DataTable.GetErrors%2A>)。

## <a name="save-data-to-a-database"></a>將資料儲存至資料庫

呼叫`Update`TableAdapter 的方法。 傳遞包含要寫入至資料庫值的資料表的名稱。

### <a name="to-update-a-database-by-using-a-tableadapter"></a>使用 TableAdapter 更新資料庫

-   括住的 TableAdapter`Update`方法中的`try` / `catch`區塊。 下列範例示範如何更新的內容`Customers`資料表中`NorthwindDataSet`內在`try` / `catch`區塊。

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)