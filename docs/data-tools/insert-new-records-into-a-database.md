---
title: 在資料庫中插入新的記錄
description: 使用 TableAdapter. Update 方法、其中一個 TableAdapter 的 DBDirect 方法或命令物件，將新的記錄插入資料庫中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 6e1046dfd114e4cad69445b8f4e1432c03aac0e5
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216458"
---
# <a name="insert-new-records-into-a-database"></a>在資料庫中插入新的記錄

若要在資料庫中插入新的記錄，您可以使用 `TableAdapter.Update` 方法，或使用其中一個 TableAdapter 的 DBDirect 方法 (明確地 `TableAdapter.Insert`) 方法。 如需詳細資訊，請參閱 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)。

如果您的應用程式不使用 Tableadapter，您可以使用命令物件 (例如，  <xref:System.Data.SqlClient.SqlCommand>) 在您的資料庫中插入新的記錄。

如果您的應用程式使用資料集來儲存資料，請使用 `TableAdapter.Update` 方法。 `Update`方法會將所有變更傳送至資料庫)  (更新、插入和刪除。

如果您的應用程式使用物件來儲存資料，或如果您想要更精確地控制在資料庫中建立新記錄，請使用 `TableAdapter.Insert` 方法。

如果您的 TableAdapter 沒有 `Insert` 方法，則表示 tableadapter 已設定為使用預存程式或其 `GenerateDBDirectMethods` 屬性設定為 `false` 。 嘗試 `GenerateDBDirectMethods` 從 DataSet 設計工具中將 TableAdapter 的屬性設定為 `true` ，然後儲存資料集。  這會重新產生 TableAdapter。 如果 TableAdapter 仍沒有 `Insert` 方法，資料表可能無法提供足夠的架構資訊來區別個別的資料列 (例如，資料表) 上可能沒有設定主鍵。

## <a name="insert-new-records-by-using-tableadapters"></a>使用 Tableadapter 插入新的記錄

Tableadapter 會根據您的應用程式需求提供不同的方式，將新的記錄插入資料庫中。

如果您的應用程式使用資料集來儲存資料，您可以直接將新的記錄加入至資料集所需的 <xref:System.Data.DataTable> ，然後呼叫 `TableAdapter.Update` 方法。 `TableAdapter.Update`方法會將中的任何變更傳送 <xref:System.Data.DataTable> 至資料庫 (包括) 修改和刪除的記錄。

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>使用 TableAdapter. Update 方法將新的記錄插入資料庫

1. <xref:System.Data.DataTable>建立新的記錄 <xref:System.Data.DataRow> ，並將其新增至集合，以將新的記錄新增至所需的記錄 <xref:System.Data.DataTable.Rows%2A> 。

2. 將新資料列加入至之後 <xref:System.Data.DataTable> ，請呼叫 `TableAdapter.Update` 方法。 您可以控制要更新的資料量，方法是傳入整個 <xref:System.Data.DataSet> 、 <xref:System.Data.DataTable> 、或的陣列 <xref:System.Data.DataRow> 或單一 <xref:System.Data.DataRow> 。

   下列程式碼示範如何將新記錄加入至 <xref:System.Data.DataTable> ，然後呼叫 `TableAdapter.Update` 方法將新的資料列儲存至資料庫。  (此範例使用 `Region` Northwind 資料庫中的資料表。 ) 

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb" id="Snippet14":::
   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs" id="Snippet14":::

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>使用 TableAdapter. Insert 方法將新的記錄插入資料庫

如果您的應用程式使用物件來儲存資料，您可以使用 `TableAdapter.Insert` 方法，直接在資料庫中建立新的資料列。 `Insert`方法會接受每個資料行的個別值做為參數。 呼叫方法會將新的記錄插入資料庫，並傳入參數值。

- 呼叫 TableAdapter 的 `Insert` 方法，將每個資料行的值傳入做為參數。

下列程式示範 `TableAdapter.Insert` 如何使用方法來插入資料列。 此範例會將資料插入 `Region` Northwind 資料庫中的資料表。

> [!NOTE]
> 如果您沒有可用的實例，請將您想要使用的 TableAdapter 具現化。

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet15":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet15":::

## <a name="insert-new-records-by-using-command-objects"></a>使用命令物件插入新的記錄

您可以使用命令物件，直接將新的記錄插入資料庫中。

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>使用命令物件將新的記錄插入資料庫

- 建立新的命令物件，然後設定其 `Connection` 、 `CommandType` 和 `CommandText` 屬性。

下列範例示範如何使用 command 物件將記錄插入資料庫中。 它會將資料插入 `Region` Northwind 資料庫中的資料表。

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet16":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet16":::

## <a name="net-security"></a>.NET 安全性

您必須能夠存取您嘗試連接的資料庫，以及在所需的資料表中執行插入的許可權。

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
