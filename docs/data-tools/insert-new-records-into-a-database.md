---
title: 將新記錄插入至資料庫
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c0b85c0f373f9536da2d2ad621e5898b4365c456
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="insert-new-records-into-a-database"></a>將新記錄插入至資料庫
若要將新記錄插入資料庫中，您可以使用`TableAdapter.Update`方法，或其中一個 TableAdapter 的 DBDirect 方法 (特別是`TableAdapter.Insert`方法)。 如需詳細資訊，請參閱[TableAdapter](../data-tools/create-and-configure-tableadapters.md)。

 如果您的應用程式不會使用 Tableadapter，您可以使用命令物件 (例如， <xref:System.Data.SqlClient.SqlCommand>) 來將新記錄插入資料庫中。

 如果您的應用程式會使用資料集來儲存資料，請`TableAdapter.Update`方法。 `Update`方法傳送至資料庫的所有變更 （更新、 插入和刪除）。

 如果您的應用程式會使用物件來儲存資料，或如果您想在資料庫中，建立新資料錄的更細微地控制使用`TableAdapter.Insert`方法。

 如果您的 TableAdapter 沒有`Insert`方法，表示可能是 TableAdapter 已設定為使用預存程序或其`GenerateDBDirectMethods`屬性設定為`false`。 嘗試設定 TableAdapter 的`GenerateDBDirectMethods`屬性`true`從**Dataset 設計工具**，然後將儲存的資料集。 這會重新產生的 TableAdapter。 如果 TableAdapter 仍然沒有`Insert`方法，則資料表可能無法提供足夠的結構描述資訊來區分各個資料列 （例如，有可能在資料表上的沒有主要金鑰組）。

## <a name="insert-new-records-by-using-tableadapters"></a>使用 Tableadapter 中插入新的記錄
 Tableadapter 會提供不同的方式，將新記錄插入資料庫中，根據您的應用程式的需求。

 如果您的應用程式會使用資料集來儲存資料，則您可以只是加入新的記錄所需<xref:System.Data.DataTable>中資料集，然後再呼叫`TableAdapter.Update`方法。 `TableAdapter.Update`方法以傳送的任何變更<xref:System.Data.DataTable>資料庫 （包括修改和刪除記錄）。

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>將新記錄插入資料庫，使用 TableAdapter.Update 方法

1.  將新記錄新增至所需<xref:System.Data.DataTable>藉由建立新<xref:System.Data.DataRow>並將它加入至<xref:System.Data.DataTable.Rows%2A>集合。

2.  新的資料列會加入之後<xref:System.Data.DataTable>，呼叫`TableAdapter.Update`方法。 您可以控制要由傳入整個更新的資料量<xref:System.Data.DataSet>、 <xref:System.Data.DataTable>，陣列<xref:System.Data.DataRow>或單一<xref:System.Data.DataRow>。

 下列程式碼示範如何將加入新的記錄，到<xref:System.Data.DataTable>，然後呼叫`TableAdapter.Update`方法，將新的資料列儲存到資料庫。 (這個範例會使用`Region`Northwind 資料庫中的資料表。)

 [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
 [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>將新記錄插入資料庫，使用 TableAdapter.Insert 方法
如果您的應用程式使用物件來儲存資料，您可以使用`TableAdapter.Insert`方法直接在資料庫中建立新的資料列。 `Insert`方法會接受每個資料行做為參數的個別值。 呼叫方法將新記錄插入資料庫中所傳遞的參數值。

- 呼叫 TableAdapter 的`Insert`方法，做為參數傳遞的值每個資料行。

 下列程序示範如何使用`TableAdapter.Insert`方法來插入資料列。 這個範例會將資料插入`Region`Northwind 資料庫中的資料表。

 > [!NOTE]
 >  如果您沒有可用的執行個體，具現化您想要使用的 TableAdapter。

 [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
 [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>使用命令物件中插入新的記錄
新的記錄直接插入資料庫，使用命令物件。

#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>若要使用命令物件將新記錄插入資料庫

-   建立新的命令物件，並將其`Connection`， `CommandType`，和`CommandText`屬性。

 下列範例會示範記錄插入至資料庫，使用命令物件。 它會插入資料至`Region`Northwind 資料庫中的資料表。

 [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
 [!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-framework-security"></a>.NET Framework 安全性
 您必須存取您嘗試連接的資料庫，以及所需的資料表執行插入的權限。

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)