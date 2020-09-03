---
title: 將物件的資料儲存至資料庫 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72607462"
---
# <a name="save-data-from-an-object-to-a-database"></a>從物件中將資料儲存至資料庫
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以將物件中的值傳遞給其中一個 TableAdapter 的 DBDirect (方法，將物件中的資料儲存至資料庫，例如 `TableAdapter.Insert`) 。

 若要從物件的集合儲存資料，請在物件集合中迴圈 (例如，) 的下一個迴圈，然後使用其中一個 TableAdapter 的 DBDirect 方法，將每個物件的值傳送至資料庫。

 根據預設，DBDirect 方法會在可直接對資料庫執行的 TableAdapter 上建立。 您可以直接呼叫這些方法，而不需要 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 物件來協調變更，以便將更新傳送至資料庫。

> [!NOTE]
> 當您設定 TableAdapter 時，主要查詢必須提供足夠的資訊，才能建立 DBDirect 方法。 例如，如果將 TableAdapter 設定為從未定義主鍵資料行的資料表中查詢資料，則不會產生 DBDirect 方法。

|TableAdapter DBDirect 方法|說明|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|將新的記錄加入至資料庫，並讓您以方法參數的形式傳入個別的資料行值。|
|`TableAdapter.Update`|更新資料庫中的現有記錄。 `Update`方法會採用原始和新的資料行值做為方法參數。 原始值會用來尋找原始記錄，而新的值會用來更新該記錄。<br /><br /> `TableAdapter.Update`方法也可用來將 <xref:System.Data.DataSet> 、 <xref:System.Data.DataTable> 、 <xref:System.Data.DataRow> 或的陣列當做方法參數，以將資料集的變更重新協調回資料庫 <xref:System.Data.DataRow> 。|
|`TableAdapter.Delete`|根據傳入做為方法參數的原始資料行值，從資料庫中刪除現有的記錄。|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>將新記錄從物件儲存至資料庫

- 藉由將值傳遞給方法來建立記錄 `TableAdapter.Insert` 。

     下列範例會將 `Customers` 物件中的值傳遞 `currentCustomer` 給方法，以在資料表中建立新的客戶記錄 `TableAdapter.Insert` 。

     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>將現有記錄從物件更新到資料庫

- 藉由呼叫方法來修改記錄 `TableAdapter.Update` ，並傳入新值來更新記錄，並傳入原始值以找出記錄。

    > [!NOTE]
    > 您的物件必須維護原始值，才能將它們傳遞給 `Update` 方法。 這個範例會使用具有前置詞的屬性 `orig` 來儲存原始值。

     下列範例會將 `Customers` 物件中的新和原始值傳遞給方法，以更新資料表中的現有記錄 `Customer` `TableAdapter.Update` 。

     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]

### <a name="to-delete-existing-records-from-a-database"></a>若要從資料庫刪除現有的記錄

- 藉由呼叫 `TableAdapter.Delete` 方法並傳入原始值以找出記錄，來刪除記錄。

    > [!NOTE]
    > 您的物件必須維護原始值，才能將它們傳遞給 `Delete` 方法。 這個範例會使用具有前置詞的屬性 `orig` 來儲存原始值。

     下列範例會藉 `Customers` 由將物件中的原始值傳遞 `Customer` 給方法，來刪除資料表中的記錄 `TableAdapter.Delete` 。

     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]

## <a name="net-framework-security"></a>.NET Framework 安全性
 您必須擁有在資料庫的資料表上執行所選插入、更新或刪除的許可權。

## <a name="see-also"></a>另請參閱
 [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)
