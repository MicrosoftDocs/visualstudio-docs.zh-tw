---
title: 將資料從物件儲存到資料庫 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c1470c831177e74e7670d696b44fc2b0119a9a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607462"
---
# <a name="save-data-from-an-object-to-a-database"></a>從物件中將資料儲存至資料庫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以藉由將物件中的值傳遞給其中一個 TableAdapter 的 DBDirect 方法（例如 `TableAdapter.Insert`），將物件中的資料儲存至資料庫。

 若要儲存物件集合的資料，請在物件集合中執行迴圈（例如，針對下一個迴圈），然後使用其中一個 TableAdapter 的 DBDirect 方法將每個物件的值傳送至資料庫。

 根據預設，DBDirect 方法會建立在可以直接針對資料庫執行的 TableAdapter 上。 您可以直接呼叫這些方法，而不需要 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 物件來協調變更，以便將更新傳送至資料庫。

> [!NOTE]
> 當您要設定 TableAdapter 時，主要查詢必須提供足夠的資訊，以供建立 DBDirect 方法。 例如，如果將 TableAdapter 設定為從未定義主鍵資料行的資料表查詢資料，則不會產生 DBDirect 方法。

|TableAdapter DBDirect 方法|描述|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|將新記錄加入至資料庫，並可讓您傳入個別的資料行值做為方法參數。|
|`TableAdapter.Update`|更新資料庫中的現有記錄。 @No__t_0 方法會採用原始和新的資料行值做為方法參數。 原始的值是用來尋找原始記錄，而新值則是用來更新該記錄。<br /><br /> @No__t_0 方法也可用來將資料集的變更重新協調回資料庫，方法是將 <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow> 或 <xref:System.Data.DataRow>s 陣列當做方法參數。|
|`TableAdapter.Delete`|根據當做方法參數傳入的原始資料行值，從資料庫中刪除現有的記錄。|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>若要將新記錄從物件儲存至資料庫

- 藉由將值傳遞給 `TableAdapter.Insert` 方法來建立記錄。

     下列範例會將 `currentCustomer` 物件中的值傳遞給 `TableAdapter.Insert` 方法，以在 `Customers` 資料表中建立新的客戶記錄。

     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>若要將現有的記錄從物件更新至資料庫

- 藉由呼叫 `TableAdapter.Update` 方法來修改記錄，傳入新的值以更新記錄，然後傳入原始值以尋找記錄。

    > [!NOTE]
    > 您的物件必須維護原始值，才能將它們傳遞給 `Update` 方法。 這個範例會使用具有 `orig` 前置詞的屬性來儲存原始值。

     下列範例會藉由將 `Customer` 物件中的新和原始值傳遞至 `TableAdapter.Update` 方法，來更新 `Customers` 資料表中的現有記錄。

     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]

### <a name="to-delete-existing-records-from-a-database"></a>若要從資料庫中刪除現有的記錄

- 藉由呼叫 `TableAdapter.Delete` 方法並傳入原始值以尋找記錄，來刪除記錄。

    > [!NOTE]
    > 您的物件必須維護原始值，才能將它們傳遞給 `Delete` 方法。 這個範例會使用具有 `orig` 前置詞的屬性來儲存原始值。

     下列範例會藉由將 `Customer` 物件中的原始值傳遞至 `TableAdapter.Delete` 方法，來刪除 `Customers` 資料表中的記錄。

     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]

## <a name="net-framework-security"></a>.NET Framework 安全性
 您必須擁有在資料庫的資料表上執行選取的插入、更新或刪除的許可權。

## <a name="see-also"></a>請參閱
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
