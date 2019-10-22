---
title: 在資料庫中插入新的記錄
ms.date: 11/04/2016
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: aaca23e6aa81fab958fc813fa5e2331f8906a562
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648321"
---
# <a name="insert-new-records-into-a-database"></a>在資料庫中插入新的記錄

若要將新記錄插入資料庫，您可以使用 `TableAdapter.Update` 方法或其中一個 TableAdapter 的 DBDirect 方法（特別是 `TableAdapter.Insert` 方法）。 如需詳細資訊，請參閱[TableAdapter](../data-tools/create-and-configure-tableadapters.md)。

如果您的應用程式不使用 Tableadapter，您可以使用命令物件（例如 <xref:System.Data.SqlClient.SqlCommand>），在您的資料庫中插入新的記錄。

如果您的應用程式使用資料集來儲存資料，請使用 `TableAdapter.Update` 方法。 @No__t_0 方法會將所有變更（更新、插入和刪除）傳送到資料庫。

如果您的應用程式使用物件來儲存資料，或如果您想要更精確地控制在資料庫中建立新的記錄，請使用 `TableAdapter.Insert` 方法。

如果您的 TableAdapter 沒有 `Insert` 方法，則表示 TableAdapter 已設定為使用預存程式，或其 `GenerateDBDirectMethods` 屬性設為 `false`。 嘗試將 TableAdapter 的 `GenerateDBDirectMethods` 屬性設定為從**DataSet 設計工具**內 `true`，然後儲存資料集。 這會重新產生 TableAdapter。 如果 TableAdapter 仍然沒有 `Insert` 方法，資料表可能無法提供足夠的架構資訊來區別個別的資料列（例如，資料表上可能沒有設定主鍵）。

## <a name="insert-new-records-by-using-tableadapters"></a>使用 Tableadapter 插入新記錄

Tableadapter 提供不同的方式，將新記錄插入資料庫中，視您應用程式的需求而定。

如果您的應用程式使用資料集來儲存資料，您可以直接將新記錄加入至資料集內所需的 <xref:System.Data.DataTable>，然後再呼叫 `TableAdapter.Update` 方法。 @No__t_0 方法會將 <xref:System.Data.DataTable> 中的任何變更傳送至資料庫（包括已修改和已刪除的記錄）。

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>若要使用 TableAdapter. Update 方法將新記錄插入至資料庫

1. 藉由建立新的 <xref:System.Data.DataRow>，並將其加入至 <xref:System.Data.DataTable.Rows%2A> 集合，將新記錄新增至所需的 <xref:System.Data.DataTable>。

2. 將新的資料列加入至 <xref:System.Data.DataTable> 之後，請呼叫 `TableAdapter.Update` 方法。 您可以控制要更新的資料量，方法是傳入整個 <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow>s 陣列或單一 <xref:System.Data.DataRow>。

   下列程式碼會示範如何將新記錄加入至 <xref:System.Data.DataTable>，然後呼叫 `TableAdapter.Update` 方法，將新的資料列儲存至資料庫。 （此範例會使用 Northwind 資料庫中的 `Region` 資料表）。

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>使用 TableAdapter. Insert 方法將新記錄插入至資料庫

如果您的應用程式使用物件來儲存資料，您可以使用 `TableAdapter.Insert` 方法，直接在資料庫中建立新的資料列。 @No__t_0 方法會接受每個資料行的個別值做為參數。 呼叫方法會使用傳入的參數值，將新記錄插入資料庫中。

- 呼叫 TableAdapter 的 `Insert` 方法，傳入每個資料行的值做為參數。

下列程式將示範如何使用 `TableAdapter.Insert` 方法來插入資料列。 這個範例會將資料插入 Northwind 資料庫中的 `Region` 資料表。

> [!NOTE]
> 如果您沒有可用的實例，請將您想要使用的 TableAdapter 具現化。

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>使用命令物件插入新記錄

您可以使用命令物件，將新記錄直接插入資料庫中。

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>若要使用命令物件將新記錄插入至資料庫

- 建立新的命令物件，然後設定其 `Connection`、`CommandType` 和 `CommandText` 屬性。

下列範例示範如何使用 command 物件將記錄插入至資料庫。 它會將資料插入 Northwind 資料庫中的 `Region` 資料表。

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-security"></a>.NET 安全性

您必須能夠存取您嘗試連接的資料庫，以及執行插入所需資料表的許可權。

## <a name="see-also"></a>請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)