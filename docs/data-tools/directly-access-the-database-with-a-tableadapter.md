---
title: 以 TableAdapter 直接存取資料庫
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e8d5d8e3091b464084df065bb7b889db9fc2194f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648518"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>以 TableAdapter 直接存取資料庫

除了 `InsertCommand`、`UpdateCommand` 和 `DeleteCommand` 之外，也會使用可直接對資料庫執行的方法來建立 Tableadapter。 您可以呼叫這些方法（`TableAdapter.Insert`、`TableAdapter.Update` 和 `TableAdapter.Delete`）直接運算元據庫中的資料。

如果您不想要建立這些直接方法，請將 TableAdapter 的 `GenerateDbDirectMethods` 屬性設定為 [**屬性**] 視窗中的 [`false`]。 如果除了 TableAdapter 的主查詢之外，還有任何查詢新增至 TableAdapter，它們就是不會產生這些 `DbDirect` 方法的獨立查詢。

## <a name="send-commands-directly-to-a-database"></a>直接將命令傳送至資料庫

呼叫 TableAdapter `DbDirect` 方法，以執行您嘗試完成的工作。

### <a name="to-insert-new-records-directly-into-a-database"></a>將新記錄直接插入資料庫

- 呼叫 TableAdapter 的 `Insert` 方法，傳入每個資料行的值做為參數。 下列程式會使用 Northwind 資料庫中的 `Region` 資料表做為範例。

    > [!NOTE]
    > 如果您沒有可用的實例，請具現化您要使用的 TableAdapter。

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>直接在資料庫中更新記錄

- 呼叫 TableAdapter 的 `Update` 方法，傳入每個資料行的新和原始值做為參數。

    > [!NOTE]
    > 如果您沒有可用的實例，請具現化您要使用的 TableAdapter。

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>直接從資料庫刪除記錄

- 呼叫 TableAdapter 的 `Delete` 方法，傳入每個資料行的值做為 `Delete` 方法的參數。 下列程式會使用 Northwind 資料庫中的 `Region` 資料表做為範例。

    > [!NOTE]
    > 如果您沒有可用的實例，請具現化您要使用的 TableAdapter。

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)