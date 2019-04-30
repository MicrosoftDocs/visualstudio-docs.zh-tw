---
title: 將資料儲存至資料庫物件 |Microsoft Docs
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
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c079d3f85dbab87e30edb059c76202dd727f715c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425053"
---
# <a name="save-data-from-an-object-to-a-database"></a>從物件中將資料儲存至資料庫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您也可以將值從您的物件傳遞至 TableAdapter 的 DBDirect 方法的其中一個資料庫物件中儲存資料 (例如`TableAdapter.Insert`)。
  
 若要用於儲存的資料物件的集合，物件 （例如，針對下一步迴圈） 的集合執行迴圈，並使用其中一種 TableAdapter 的 DBDirect 方法傳送至資料庫的每個物件的值。  
  
 根據預設，會產生上可以直接對資料庫執行 TableAdapter DBDirect 方法。 這些方法可以直接呼叫，而且不需要<xref:System.Data.DataSet>或<xref:System.Data.DataTable>協調變更，以便將更新傳送至資料庫的物件。  
  
> [!NOTE]
> 當您設定 TableAdapter 時，主查詢必須提供足夠的資訊，如需建立 DBDirect 方法。 例如，如果沒有定義主索引鍵資料行的資料表，TableAdapter 已設定來查詢資料，它不會產生 DBDirect 方法。  
  
|TableAdapter DBDirect 方法|描述|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|將新記錄新增至資料庫，並可讓您在個別的資料行值做為方法參數中傳遞。|  
|`TableAdapter.Update`|更新現有的資料庫中的記錄。 `Update`方法會採用原始及新的資料行做為方法參數的值。 原始的值用來找出原始記錄中，與新的值來更新該記錄。<br /><br /> `TableAdapter.Update`方法也會用來協調回到資料庫的資料集內的變更，藉由採取<xref:System.Data.DataSet>， <xref:System.Data.DataTable>， <xref:System.Data.DataRow>，或陣列<xref:System.Data.DataRow>做為方法參數。|  
|`TableAdapter.Delete`|刪除現有記錄從資料庫根據原始的資料行值傳遞為方法參數。|  
  
### <a name="to-save-new-records-from-an-object-to-a-database"></a>若要從物件的新記錄儲存至資料庫  
  
- 建立記錄值傳遞至`TableAdapter.Insert`方法。  
  
     下列範例會建立新的客戶記錄，在`Customers`資料表中的值傳遞`currentCustomer`物件到`TableAdapter.Insert`方法。  
  
     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]  
  
### <a name="to-update-existing-records-from-an-object-to-a-database"></a>若要更新現有的資料錄從物件到資料庫  
  
- 修改記錄，藉由呼叫`TableAdapter.Update`方法，傳遞新的值來更新記錄，並傳入要找出資料錄的原始值。  
  
    > [!NOTE]
    > 您的物件需要維護的原始值，才能將其傳遞給`Update`方法。 這個範例會使用具有屬性`orig`儲存原始值的前置詞。  
  
     下列範例會更新中的現有記錄`Customers`藉由傳遞中的全新及原始值的表格`Customer`物件到`TableAdapter.Update`方法。  
  
     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]  
  
### <a name="to-delete-existing-records-from-a-database"></a>若要從資料庫刪除現有的記錄  
  
- 刪除記錄，藉由呼叫`TableAdapter.Delete`方法並傳入要找出資料錄的原始值。  
  
    > [!NOTE]
    > 您的物件需要維護的原始值，才能將其傳遞給`Delete`方法。 這個範例會使用具有屬性`orig`儲存原始值的前置詞。  
  
     下列範例會刪除從資料錄`Customers`藉由傳遞中的原始值的資料表`Customer`物件到`TableAdapter.Delete`方法。  
  
     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 您必須擁有權限可以執行選取的 INSERT、 UPDATE 或 DELETE 上的資料庫中的資料表。  
  
## <a name="see-also"></a>另請參閱  
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
