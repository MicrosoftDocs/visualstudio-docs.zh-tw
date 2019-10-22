---
title: 從物件中將資料儲存至資料庫
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5208b7764949f6ba6d3e862c7a2102608afb7e24
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648206"
---
# <a name="save-data-from-an-object-to-a-database"></a>從物件中將資料儲存至資料庫

您可以藉由將物件中的值傳遞給其中一個 TableAdapter 的 DBDirect 方法（例如 `TableAdapter.Insert`），將物件中的資料儲存至資料庫。 如需詳細資訊，請參閱[TableAdapter](../data-tools/create-and-configure-tableadapters.md)。

若要儲存物件集合的資料，請在物件集合中執行迴圈（例如，針對下一個迴圈），然後使用其中一個 TableAdapter 的 `DBDirect` 方法，將每個物件的值傳送至資料庫。

根據預設，會在可以直接針對資料庫執行的 TableAdapter 上建立 `DBDirect` 方法。 您可以直接呼叫這些方法，而不需要 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 物件來協調變更，以便將更新傳送至資料庫。

> [!NOTE]
> 當您要設定 TableAdapter 時，主要查詢必須提供足夠的資訊，以供建立 `DBDirect` 方法。 例如，如果將 TableAdapter 設定為從未定義主鍵資料行的資料表查詢資料，則不會產生 `DBDirect` 方法。

|TableAdapter DBDirect 方法|描述|
| - |-----------------|
|`TableAdapter.Insert`|將新記錄加入至資料庫，並可讓您傳入個別的資料行值做為方法參數。|
|`TableAdapter.Update`|更新資料庫中的現有記錄。 @No__t_0 方法會採用原始和新的資料行值做為方法參數。 原始的值是用來尋找原始記錄，而新值則是用來更新該記錄。<br /><br /> @No__t_0 方法也可用來將資料集的變更重新協調回資料庫，方法是將 <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow> 或 <xref:System.Data.DataRow>s 陣列當做方法參數。|
|`TableAdapter.Delete`|根據當做方法參數傳入的原始資料行值，從資料庫中刪除現有的記錄。|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>若要將新記錄從物件儲存至資料庫

- 藉由將值傳遞給 `TableAdapter.Insert` 方法來建立記錄。

     下列範例會將 `currentCustomer` 物件中的值傳遞給 `TableAdapter.Insert` 方法，以在 `Customers` 資料表中建立新的客戶記錄。

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>若要將現有的記錄從物件更新至資料庫

- 藉由呼叫 `TableAdapter.Update` 方法來修改記錄，傳入新的值以更新記錄，然後傳入原始值以尋找記錄。

    > [!NOTE]
    > 您的物件必須維護原始值，才能將它們傳遞給 `Update` 方法。 這個範例會使用具有 `orig` 前置詞的屬性來儲存原始值。

     下列範例會藉由將 `Customer` 物件中的新和原始值傳遞至 `TableAdapter.Update` 方法，來更新 `Customers` 資料表中的現有記錄。

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>若要從資料庫中刪除現有的記錄

- 藉由呼叫 `TableAdapter.Delete` 方法並傳入原始值以尋找記錄，來刪除記錄。

    > [!NOTE]
    > 您的物件必須維護原始值，才能將它們傳遞給 `Delete` 方法。 這個範例會使用具有 `orig` 前置詞的屬性來儲存原始值。

     下列範例會藉由將 `Customer` 物件中的原始值傳遞至 `TableAdapter.Delete` 方法，來刪除 `Customers` 資料表中的記錄。

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-security"></a>.NET 安全性

您必須擁有在資料庫的資料表上執行選取的 `INSERT`、`UPDATE` 或 `DELETE` 的許可權。

## <a name="see-also"></a>請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)