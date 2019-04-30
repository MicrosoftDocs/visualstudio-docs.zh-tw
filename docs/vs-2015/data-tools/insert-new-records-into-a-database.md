---
title: 將新記錄插入資料庫 |Microsoft Docs
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
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd5074af8f0a9ca172d04b4cd5bb1d9057ad4bb5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63384082"
---
# <a name="insert-new-records-into-a-database"></a>在資料庫中插入新的記錄
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要將新記錄插入資料庫，您可以使用`TableAdapter.Update`方法，或其中一個 TableAdapter 的 DBDirect 方法 (特別是`TableAdapter.Insert`方法)。
  
 如果您的應用程式未使用 TableAdapters，您可以使用命令物件 (例如<xref:System.Data.SqlClient.SqlCommand>) 資料庫中插入新記錄。  
  
 如果您的應用程式會使用資料集來儲存資料，使用`TableAdapter.Update`方法。 `Update`方法傳送至資料庫的所有變更 （更新、 插入和刪除）。  
  
 如果您的應用程式會使用物件來儲存資料，或如果您想要在資料庫中，建立新資料錄的更細微地控制使用`TableAdapter.Insert`方法。  
  
 如果沒有您 TableAdapter`Insert`方法，表示可能是 TableAdapter 已設定為使用預存程序或其`GenerateDBDirectMethods`屬性設定為`false`。 嘗試設定 TableAdapter`GenerateDBDirectMethods`屬性設`true`從 Dataset 設計工具中，然後再儲存資料集。 這會重新產生的 TableAdapter。 TableAdapter 仍未獲`Insert`方法，則資料表可能無法提供足夠的結構描述資訊來區分個別資料列 （例如，有可能在資料表上的沒有主要索引鍵集）。  
  
## <a name="insert-new-records-by-using-tableadapters"></a>使用 Tableadapter 中插入新的記錄  
 Tableadapter 會提供不同的方式，將新記錄插入資料庫中，根據您的應用程式的需求。  
  
 如果您的應用程式使用資料集來儲存資料，則您只可以將新資料錄加入所需<xref:System.Data.DataTable>中的資料集，然後呼叫`TableAdapter.Update`方法。 `TableAdapter.Update`方法傳送的任何變更<xref:System.Data.DataTable>資料庫 （包括已修改和刪除記錄）。  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>將新記錄插入資料庫，使用 TableAdapter.Update 方法  
  
1. 將新記錄新增至所需<xref:System.Data.DataTable>藉由建立新<xref:System.Data.DataRow>並將它新增至<xref:System.Data.DataTable.Rows%2A>集合。 如需詳細資訊，請參閱[如何：將資料列加入至 DataTable](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf)。  
  
2. 新的資料列新增至後<xref:System.Data.DataTable>，呼叫`TableAdapter.Update`方法。 您可以控制要藉由傳入整個更新的資料量<xref:System.Data.DataSet>，則<xref:System.Data.DataTable>，陣列<xref:System.Data.DataRow>或單一<xref:System.Data.DataRow>。  
  
    下列程式碼示範如何新增新的記錄，以<xref:System.Data.DataTable>，然後呼叫`TableAdapter.Update`方法，將新的資料列儲存到資料庫。 (這個範例會使用`Region`Northwind 資料庫中的資料表。)  
  
    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]  
  
   如果您的應用程式會使用物件來儲存資料，您可以使用`TableAdapter.Insert`直接在資料庫中建立新的資料列的方法。 `Insert`方法會接受每個資料行的個別值做為參數。 呼叫此方法將新記錄插入資料庫中所傳遞的參數值。  
  
   下列程序使用`Region`做為範例 Northwind 資料庫中的資料表。  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>將新記錄插入資料庫，使用 TableAdapter.Insert 方法  
  
- 呼叫 TableAdapter 的`Insert`方法，傳遞每個資料行做為參數的值。  
  
    > [!NOTE]
    > 如果您沒有可用的執行個體，具現化您想要使用的 TableAdapter。  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
## <a name="insert-new-records-by-using-command-objects"></a>使用命令物件中插入新的記錄  
 下列範例會將新記錄，直接插入資料庫，使用命令物件。
  
 下列程序使用`Region`做為範例 Northwind 資料庫中的資料表。  
  
#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>將新記錄插入資料庫，使用命令物件  
  
- 建立新的命令物件，並將其`Connection`， `CommandType`，和`CommandText`屬性。  
  
     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 您必須存取您嘗試連接的資料庫，以及所需的資料表執行插入的權限。  
  
## <a name="see-also"></a>另請參閱  
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
