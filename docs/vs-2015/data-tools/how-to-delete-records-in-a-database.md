---
title: 如何： 刪除資料庫中的記錄 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- records, deleting
- TableAdapter.Delete method
- databases, deleting records
- deleting data
- TableAdapter.Update method
- saving data
ms.assetid: d74d2130-9732-4648-abea-241059c4a372
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 87ab5ccde2c1100fbd0efc5f4272efe27803b717
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938613"
---
# <a name="how-to-delete-records-in-a-database"></a>如何：刪除資料庫中的資料錄
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要從資料庫刪除記錄，請使用`TableAdapter.Update`方法或`TableAdapter.Delete`方法。 或者，如果您的應用程式不會使用 TableAdapters，您可以使用命令物件可從資料庫刪除記錄 (例如<xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>)。  
  
 `TableAdapter.Update`方法通常用您的應用程式會使用資料集來儲存資料，而當`TableAdapter.Delete`應用程式用來儲存資料的物件時，通常會使用方法。  
  
 如果沒有您 TableAdapter`Delete`方法，表示可能是 TableAdapter 會設定為使用預存程序，或其`GenerateDBDirectMethods`屬性設定為`false`。 嘗試設定 TableAdapter`GenerateDBDirectMethods`屬性，以`true`內在[Dataset 設計工具](../data-tools/creating-and-editing-typed-datasets.md)，然後將儲存的資料集，以重新產生的 TableAdapter。 如果 TableAdapter 仍沒有`Delete`方法，則資料表可能無法提供足夠的結構描述資訊來區分個別資料列 （例如，資料表上設定沒有主索引鍵）。  
  
## <a name="delete-records-using-tableadapters"></a>使用 Tableadapter 刪除記錄  
 Tableadapter 會提供不同的方式，來刪除記錄，從資料庫，以根據您的應用程式的需求。  
  
 如果您的應用程式用來儲存資料的資料集只可以從想要刪除記錄<xref:System.Data.DataTable>中<xref:System.Data.DataSet>，然後呼叫`TableAdapter.Update`方法。 `TableAdapter.Update`方法需要的任何變更資料表中的資料，並將這些變更傳送至資料庫 （包括插入、 更新和刪除記錄）。  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterupdate-method"></a>若要使用 TableAdapter.Update 方法，從資料庫刪除記錄  
  
- 從所要刪除資料錄<xref:System.Data.DataTable>藉由刪除<xref:System.Data.DataRow>資料表中的物件。 如需詳細資訊，請參閱 <<c0> [ 如何： 刪除 DataTable 中的資料列](http://msdn.microsoft.com/library/add481e5-08c7-4923-9276-f036ae29d31e)。 從刪除資料列之後<xref:System.Data.DataTable>，呼叫`TableAdapter.Update`方法。 您可以控制要藉由傳入整個更新的資料量<xref:System.Data.DataSet>，則<xref:System.Data.DataTable>，陣列<xref:System.Data.DataRow>或單一<xref:System.Data.DataRow>。 下列程式碼示範如何刪除的記錄<xref:System.Data.DataTable>，然後呼叫`TableAdapter.Update`通訊變更，並從資料庫刪除資料列的方法。 (此範例使用 Northwind 資料庫的`Region`資料表。)  
  
   [!code-csharp[VbRaddataSaving#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#20)]
   [!code-vb[VbRaddataSaving#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#20)]  
  
  如果您的應用程式會使用物件來將資料儲存在您的應用程式，您可以使用 TableAdapter 的 DBDirect 方法，可直接從資料庫刪除資料。 呼叫`Delete`方法會從根據傳入的參數值的資料庫移除記錄。  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterdelete-method"></a>若要使用 TableAdapter.Delete 方法，從資料庫刪除記錄  
  
-   呼叫 TableAdapter`Delete`方法，傳遞每個資料行做為參數的值`Delete`方法。 (此範例使用 Northwind 資料庫的`Region`資料表。)  
  
    > [!NOTE]
    >  如果您沒有可用的執行個體，具現化您想要使用的 TableAdapter。  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="delete-records-using-command-objects"></a>使用命令物件來刪除記錄  
 下列範例會刪除記錄，直接從資料庫，使用命令物件。 如需有關如何使用命令物件來執行命令和預存程序的詳細資訊，請參閱 <<c0> [ 將資料提取到您的應用程式](../data-tools/fetching-data-into-your-application.md)。  
  
#### <a name="to-delete-records-from-a-database-using-command-objects"></a>若要使用命令物件，從資料庫刪除記錄  
  
-   建立新的命令物件、 設定其`Connection`， `CommandType`，和`CommandText`屬性。 (此範例使用 Northwind 資料庫的`Region`資料表。)  
  
     [!code-csharp[VbRaddataSaving#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#22)]
     [!code-vb[VbRaddataSaving#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#22)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 您必須存取您嘗試連接的資料庫，以及從所需的資料表刪除記錄的權限。  
  
## <a name="see-also"></a>另請參閱  
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [將新記錄插入資料庫](../data-tools/insert-new-records-into-a-database.md)   
 [如何： 更新資料庫中的記錄](../data-tools/how-to-update-records-in-a-database.md)   
 [將資料儲存至資料庫物件](../data-tools/save-data-from-an-object-to-a-database.md)   
 [在 Visual Studio 中的資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接到 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [將資料擷取至您的應用程式](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [儲存資料](../data-tools/saving-data.md)