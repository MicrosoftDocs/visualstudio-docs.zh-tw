---
title: 如何： 將資料集變更儲存至資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DbDataAdapter.Update
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- databases, updating
- updating datasets, writing changes to data source
ms.assetid: c9970150-b71b-4c9d-a355-5efb6b510dca
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 60bb855202cfb333820fe2292fedc0b31608c5c6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949015"
---
# <a name="how-to-save-dataset-changes-to-a-database"></a>如何：將資料集變更儲存至資料庫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在資料集中的資料已修改且驗證之後，您可能會想要將更新的資料傳送回資料庫。 若要將已修改的資料傳送至資料庫中，您呼叫`Update`方法[TableAdapter](../data-tools/tableadapter-overview.md)或資料配接器。 配接器的`Update`方法會更新單一資料表，並執行正確的命令 （INSERT、 UPDATE 或 DELETE） 根據<xref:System.Data.DataRow.RowState%2A>的資料表中每個資料列。  
  
 在相關資料表中儲存資料時，Visual Studio 會提供 TableAdapterManager 元件，可協助執行儲存在適當的順序，根據資料庫中定義的外部索引鍵條件約束。 如需詳細資訊，請參閱 <<c0> [ 階層式更新概觀](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)。  
  
> [!NOTE]
>  因為嘗試更新資料來源的資料集的內容，可能會導致錯誤，您應該將程式碼呼叫的介面卡`Update`方法內`try` / `catch`區塊。  
  
 確切的程序來更新資料來源而異您的業務需求，但您的應用程式應該包含下列步驟：  
  
1.  執行程式碼嘗試將更新傳送至資料庫內`try` / `catch`區塊。  
  
2.  如果攔截到例外狀況時，找出造成錯誤的資料列。 如需詳細資訊，請參閱 <<c0> [ 如何： 尋找資料列在有錯誤](http://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c)。  
  
3.  調解這個問題，資料中的資料列 （如果可能的話，就以程式設計方式或無效的資料列呈現給使用者進行修改），並再重新嘗試更新 (<xref:System.Data.DataRow.HasErrors%2A>屬性，<xref:System.Data.DataTable.GetErrors%2A>方法)。  
  
## <a name="saving-data-to-a-database"></a>將資料儲存至資料庫  
 呼叫`Update`TableAdapter 或資料配接器方法，並傳遞資料表名稱，包含要寫入資料庫的值。 如需有關如何將資料從單一資料表儲存回資料庫的詳細資訊，請參閱 <<c0> [ 逐步解說： 將資料儲存至資料庫 （單一資料表）](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d)。  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-tableadapter"></a>若要更新資料庫中使用 TableAdapter 的資料集  
  
-   括住`TableAdapter.Update`方法內`try` / `catch`區塊。 下列範例示範如何嘗試進行更新的內容`Customers`資料表中`NorthwindDataSet`。  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-data-adapter"></a>若要更新資料庫中使用資料配接器的資料集  
  
-   括住`DataAdapter.Update`方法內`try` / `catch`區塊。 下列範例示範如何嘗試更新資料來源的內容`Table1`在`DataSet1`。  
  
     [!code-csharp[VbRaddataSaving#26](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#26)]
     [!code-vb[VbRaddataSaving#26](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#26)]  
  
## <a name="updating-two-related-tables-in-a-dataset"></a>更新資料集內的兩個相關的資料表  
 在更新資料集中的相關的資料表時，務必依照正確順序排列，以減少發生違反參考完整性條件約束的更新。 命令執行的順序也會遵循索引<xref:System.Data.DataRowCollection>資料集內。 若要避免資料完整性錯誤所引發，最佳做法是依下列順序將資料庫更新：  
  
1. 子資料表： 刪除記錄。  
  
2. 父資料表： 插入、 更新和刪除記錄。  
  
3. 子資料表： 插入和更新記錄。  
  
   如需儲存多個資料表中資料的詳細資訊，請參閱[將資料儲存至資料庫 （多個資料表）](../data-tools/save-data-to-a-database-multiple-tables.md)。  
  
   如果您要更新兩個或多個相關的資料表，您就應該包含在交易內的所有更新邏輯。 異動是可以在認可所有變更之前，確保對資料庫的所有相關變更都能成功的流程。 如需詳細資訊，請參閱[異動和並行存取](http://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b)。  
  
#### <a name="to-update-two-related-tables-using-a-tableadapter"></a>若要更新使用 TableAdapter 的兩個相關的資料表  
  
1.  建立三個暫存<xref:System.Data.DataTable>以保存不同的記錄。  
  
2.  呼叫`Update`方法內的資料列的每個子集`try` / `catch`區塊。 如果發生更新錯誤，建議的採取是動作的分支，並加以解決。  
  
3.  從資料集的變更認可到資料庫中。  
  
4.  處置暫存資料表，來釋放資源。  
  
     [!code-csharp[VbRaddataSaving#27](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#27)]
     [!code-vb[VbRaddataSaving#27](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#27)]  
  
#### <a name="to-update-two-related-tables-using-a-data-adapter"></a>若要更新使用資料配接器的兩個相關的資料表  
  
-   呼叫`Update`的每個資料配接器的方法。  
  
     下列範例示範如何使用包含相關的資料表的資料集更新資料來源。 若要遵循上述序列，也就是三個暫存<xref:System.Data.DataTable>s 將建立來保存不同的記錄。 然後`Update`會針對每個部分的資料列呼叫方法，從`try` / `catch`區塊。 如果發生更新錯誤，建議的採取是動作的分支，並加以解決。 然後將資料集認可的變更。 最後，處置暫存資料表，來釋放資源。  
  
     [!code-csharp[VbRaddataSaving#28](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#28)]
     [!code-vb[VbRaddataSaving#28](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>另請參閱  
 [資料逐步解說](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [連接到 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [將資料擷取至您的應用程式](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [儲存資料](../data-tools/saving-data.md)