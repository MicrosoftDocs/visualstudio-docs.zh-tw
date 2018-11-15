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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 22a2580809394ba1b41e7923f4f2df458d995a93
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750958"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>以 TableAdapter 直接存取資料庫

除了`InsertCommand`， `UpdateCommand`，和`DeleteCommand`，可以直接對資料庫執行的方法以建立 TableAdapters。 您可以呼叫這些方法 (`TableAdapter.Insert`， `TableAdapter.Update`，和`TableAdapter.Delete`) 來操作直接在資料庫中的資料。

如果您不想要建立這些直接方法，設定 TableAdapter`GenerateDbDirectMethods`屬性，以`false`中**屬性**視窗。 如果除了 TableAdapter 的主要查詢的 TableAdapter 加入任何查詢，它們是獨立的查詢，不會產生這些`DbDirect`方法。

## <a name="send-commands-directly-to-a-database"></a>命令直接傳送到資料庫

呼叫 TableAdapter`DbDirect`執行工作的方法您嘗試完成的工作。

### <a name="to-insert-new-records-directly-into-a-database"></a>若要直接將新記錄插入資料庫

-   呼叫 TableAdapter 的`Insert`方法，傳遞每個資料行做為參數的值。 下列程序使用`Region`做為範例 Northwind 資料庫中的資料表。

    > [!NOTE]
    > 如果您沒有可用的執行個體，具現化您想要使用的 TableAdapter。

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>若要更新直接在資料庫中的記錄

-   呼叫 TableAdapter 的`Update`方法並傳入新值和原始值的每個資料行做為參數。

    > [!NOTE]
    > 如果您沒有可用的執行個體，具現化您想要使用的 TableAdapter。

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>若要直接從資料庫刪除記錄

-   呼叫 TableAdapter`Delete`方法，傳遞每個資料行做為參數的值`Delete`方法。 下列程序使用`Region`做為範例 Northwind 資料庫中的資料表。

    > [!NOTE]
    > 如果您沒有可用的執行個體，具現化您想要使用的 TableAdapter。

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>另請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)