---
title: "將資料從物件儲存至資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 1c7e99ce49df969fae439afac5d65369fae9c37a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="save-data-from-an-object-to-a-database"></a>將資料從物件儲存至資料庫
您也可以從物件的值傳遞至 TableAdapter 的 DBDirect 方法的其中一個資料庫物件中儲存資料 (例如， `TableAdapter.Insert`)。 如需詳細資訊，請參閱[TableAdapter](../data-tools/create-and-configure-tableadapters.md)。  
  
 若要將資料從物件的集合儲存，迴圈的集合物件 （例如下, 一步的迴圈），並使用其中一種 TableAdapter 的 DBDirect 方法傳送至資料庫的每個物件的值。  
  
 根據預設，會建立 DBDirect 方法，可以直接對資料庫執行 TableAdapter 上。 這些方法可以直接呼叫，且不需要<xref:System.Data.DataSet>或<xref:System.Data.DataTable>協調變更，才能將更新傳送至資料庫的物件。  
  
> [!NOTE]
>  當您設定 TableAdapter 時，主要的查詢必須提供足以 DBDirect 方法，以建立資訊。 例如，如果沒有定義主索引鍵資料行的資料表，TableAdapter 設定為查詢資料，它不會產生 DBDirect 方法。  
  
|TableAdapter DBDirect 方法|說明|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|將新記錄新增至資料庫，並讓您在個別資料行值做為方法參數中傳遞。|  
|`TableAdapter.Update`|更新現有的資料庫中的記錄。 `Update`方法會採用原始和新的資料行值做為方法參數。 用來尋找原始記錄中，原始值和新值來更新該記錄。<br /><br /> `TableAdapter.Update`方法也用來協調回資料庫的變更集中的資料，採取<xref:System.Data.DataSet>， <xref:System.Data.DataTable>， <xref:System.Data.DataRow>，或一組<xref:System.Data.DataRow>做為方法參數。|  
|`TableAdapter.Delete`|刪除現有記錄為方法參數傳入的原始資料行值為基礎的資料庫。|  
  
### <a name="to-save-new-records-from-an-object-to-a-database"></a>將新的記錄從物件儲存至資料庫  
  
-   藉由傳遞的值來建立記錄`TableAdapter.Insert`方法。  
  
     下列範例會建立新的客戶記錄中`Customers`資料表中的值傳遞`currentCustomer`物件`TableAdapter.Insert`方法。  
  
     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]  
  
### <a name="to-update-existing-records-from-an-object-to-a-database"></a>若要更新現有的資料錄從物件到資料庫  
  
-   藉由呼叫修改記錄`TableAdapter.Update`方法中，傳入新值來更新記錄，然後在原始的值，以找出記錄中傳遞。  
  
    > [!NOTE]
    >  您的物件需要維護原始值，才能將其傳遞給`Update`方法。 這個範例會使用具有屬性`orig`來儲存原始值的前置詞。  
  
     下列範例會更新中的現有記錄`Customers`資料表中的新增和原始值傳遞`Customer`物件`TableAdapter.Update`方法。  
  
     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]  
  
### <a name="to-delete-existing-records-from-a-database"></a>若要從資料庫刪除現有的記錄  
  
-   刪除記錄，藉由呼叫`TableAdapter.Delete`方法並傳入要尋找記錄的原始值。  
  
    > [!NOTE]
    >  您的物件需要維護原始值，才能將其傳遞給`Delete`方法。 這個範例會使用具有屬性`orig`來儲存原始值的前置詞。  
  
     下列範例會刪除記錄，以從`Customers`藉由傳遞中的原始值的資料表`Customer`物件`TableAdapter.Delete`方法。  
  
     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 您必須擁有權限來執行選取的 INSERT、 UPDATE 或 DELETE 上的資料庫中的資料表。  
  
## <a name="see-also"></a>另請參閱  
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)