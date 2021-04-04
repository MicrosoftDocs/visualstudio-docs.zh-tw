---
title: 以 TableAdapter 直接存取資料庫
description: 使用 Insert、Update 和 Delete 等方法直接存取資料庫中的資料，直接存取具有 TableAdapter 的資料庫。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 30248632eacde07cfcc94213aeeb75ecac8dcf70
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215912"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>以 TableAdapter 直接存取資料庫

除了 `InsertCommand` 、和以外，也會 `UpdateCommand` `DeleteCommand` 使用可直接對資料庫執行的方法來建立 tableadapter。 您可以呼叫這些方法 (`TableAdapter.Insert` 、 `TableAdapter.Update` 和 `TableAdapter.Delete`) ，直接在資料庫中運算元據。

如果您不想要建立這些直接方法，請 `GenerateDbDirectMethods` `false` 在 [ **屬性** ] 視窗中將 TableAdapter 的屬性設定為。 如果除了 TableAdapter 的主要查詢以外，還將任何查詢加入至 TableAdapter，它們是不會產生這些方法的獨立查詢 `DbDirect` 。

## <a name="send-commands-directly-to-a-database"></a>直接將命令傳送至資料庫

呼叫 `DbDirect` 可執行您嘗試完成之工作的 TableAdapter 方法。

### <a name="to-insert-new-records-directly-into-a-database"></a>將新記錄直接插入至資料庫

- 呼叫 TableAdapter 的 `Insert` 方法，將每個資料行的值傳入做為參數。 下列程式會使用 `Region` Northwind 資料庫中的資料表做為範例。

    > [!NOTE]
    > 如果您沒有可用的實例，請將您要使用的 TableAdapter 具現化。

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet15":::

### <a name="to-update-records-directly-in-a-database"></a>若要直接在資料庫中更新記錄

- 呼叫 TableAdapter 的 `Update` 方法，將每個資料行的新值和原始值傳入做為參數。

    > [!NOTE]
    > 如果您沒有可用的實例，請將您要使用的 TableAdapter 具現化。

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet18":::

### <a name="to-delete-records-directly-from-a-database"></a>若要直接從資料庫刪除記錄

- 呼叫 TableAdapter 的 `Delete` 方法，將每個資料行的值傳入做為方法的參數 `Delete` 。 下列程式會使用 `Region` Northwind 資料庫中的資料表做為範例。

    > [!NOTE]
    > 如果您沒有可用的實例，請將您要使用的 TableAdapter 具現化。

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet21":::

## <a name="see-also"></a>另請參閱

- [使用 TableAdapter 填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)
