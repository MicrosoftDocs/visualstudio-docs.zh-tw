---
title: 直接存取 TableAdapter 的資料庫
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
ms.openlocfilehash: 9985d9e072163bab722edde403ee1ec8aa801a69
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>直接存取 TableAdapter 的資料庫
除了`InsertCommand`， `UpdateCommand`，和`DeleteCommand`，可以直接對資料庫執行的方法以建立 TableAdapters。 這些方法 (`TableAdapter.Insert`， `TableAdapter.Update`，和`TableAdapter.Delete`) 可以呼叫來操作直接在資料庫中的資料。

 如果您不想要建立這些直接的方法，設定 TableAdapter 的`GenerateDbDirectMethods`屬性`false`中**屬性**視窗。 如果除了 TableAdapter 的主要查詢的 TableAdapter 加入任何查詢，都不會產生這些 DbDirect 方法的獨立查詢。

## <a name="send-commands-directly-to-a-database"></a>命令直接傳送到資料庫
 呼叫 TableAdapter 的 DbDirect 方法要完成之工作。

#### <a name="to-insert-new-records-directly-into-a-database"></a>若要直接將新記錄插入資料庫

-   呼叫 TableAdapter 的`Insert`方法，做為參數傳遞的值每個資料行。 下列程序使用`Region`做為範例 Northwind 資料庫中的資料表。

    > [!NOTE]
    >  如果您沒有可用的執行個體，具現化您想要使用的 TableAdapter。

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

#### <a name="to-update-records-directly-in-a-database"></a>若要更新直接在資料庫中的記錄

-   呼叫 TableAdapter 的`Update`方法，做為參數傳遞新的和原始值中每個資料行。

    > [!NOTE]
    >  如果您沒有可用的執行個體，具現化您想要使用的 TableAdapter。

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

#### <a name="to-delete-records-directly-from-a-database"></a>若要直接從資料庫刪除記錄

-   呼叫 TableAdapter 的`Delete`方法，傳入值的每個資料行做為參數的`Delete`方法。 下列程序使用`Region`做為範例 Northwind 資料庫中的資料表。

    > [!NOTE]
    >  如果您沒有可用的執行個體，具現化您想要使用的 TableAdapter。

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>另請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)