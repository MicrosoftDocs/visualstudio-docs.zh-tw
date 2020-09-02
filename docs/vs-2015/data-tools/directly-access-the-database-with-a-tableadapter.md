---
title: 使用 TableAdapter 直接存取資料庫 |Microsoft Docs
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
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 58500e59a624dac55824033b8b9667754a9040c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657367"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>以 TableAdapter 直接存取資料庫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

除了 `InsertCommand` 、和以外，也會 `UpdateCommand` `DeleteCommand` 使用可直接對資料庫執行的方法來建立 tableadapter。 您可以呼叫這些方法 (`TableAdapter.Insert` 、 `TableAdapter.Update` 和 `TableAdapter.Delete`) ，以便直接在資料庫中運算元據。

 如果您不想要建立這些直接方法，請 `GenerateDbDirectMethods` `false` 在 [ **屬性** ] 視窗中將 TableAdapter 的屬性設定為。 如果除了 TableAdapter 的主要查詢以外，還將任何查詢加入至 TableAdapter，它們是不會產生這些 DbDirect 方法的獨立查詢。

## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirectly 至資料庫
 呼叫 TableAdapter DbDirect 方法，此方法會執行您要嘗試完成的工作。

#### <a name="to-insert-new-records-directly-into-a-database"></a>將新記錄直接插入至資料庫

- 呼叫 TableAdapter 的 `Insert` 方法，將每個資料行的值傳入做為參數。 下列 `Region` 程式使用 Northwind 中的表格 databaseas 範例。

    > [!NOTE]
    > 如果您沒有可用的實例，請將您要使用的 TableAdapter 具現化。

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

#### <a name="to-update-records-directly-in-a-database"></a>若要直接在資料庫中更新記錄

- 呼叫 TableAdapter 的 `Update` 方法，將每個資料行的新值和原始值傳入做為參數。

    > [!NOTE]
    > 如果您沒有可用的實例，請將您要使用的 TableAdapter 具現化。

     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]

#### <a name="to-delete-records-directly-from-a-database"></a>若要直接從資料庫刪除記錄

- 呼叫 TableAdapter 的 `Delete` 方法，將每個資料行的值傳入做為方法的參數 `Delete` 。 下列 `Region` 程式使用 Northwind 中的表格 databaseas 範例。

    > [!NOTE]
    > 如果您沒有可用的實例，請將您要使用的 TableAdapter 具現化。

     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]

## <a name="see-also"></a>另請參閱
 [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)
