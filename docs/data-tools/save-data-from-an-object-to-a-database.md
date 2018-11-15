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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c1203b3b129b42ca65b94cd7a4b9cebf108740f4
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750945"
---
# <a name="save-data-from-an-object-to-a-database"></a>從物件中將資料儲存至資料庫

您也可以將值從您的物件傳遞至 TableAdapter 的 DBDirect 方法的其中一個資料庫物件中儲存資料 (例如`TableAdapter.Insert`)。 如需詳細資訊，請參閱 < [TableAdapter](../data-tools/create-and-configure-tableadapters.md)。

若要用於儲存的資料物件的集合，物件 （例如，針對下一步迴圈） 的集合執行迴圈，並傳送至資料庫的每個物件的值，使用其中一種 TableAdapter 的`DBDirect`方法。

根據預設，`DBDirect`可以直接對資料庫執行的 TableAdapter 上所建立的方法。 這些方法可以直接呼叫，而且不需要<xref:System.Data.DataSet>或<xref:System.Data.DataTable>協調變更，以便將更新傳送至資料庫的物件。

> [!NOTE]
> 當您設定 TableAdapter 時，主要的查詢必須提供足夠的資訊`DBDirect`方法來建立。 例如，如果沒有定義主索引鍵資料行的資料表，TableAdapter 已設定來查詢資料，它不會產生`DBDirect`方法。

|TableAdapter DBDirect 方法|描述|
| - |-----------------|
|`TableAdapter.Insert`|將新記錄新增至資料庫，並可讓您在個別的資料行值做為方法參數中傳遞。|
|`TableAdapter.Update`|更新現有的資料庫中的記錄。 `Update`方法會採用原始及新的資料行做為方法參數的值。 原始的值用來找出原始記錄中，與新的值來更新該記錄。<br /><br /> `TableAdapter.Update`方法也會用來協調回到資料庫的資料集內的變更，藉由採取<xref:System.Data.DataSet>， <xref:System.Data.DataTable>， <xref:System.Data.DataRow>，或陣列<xref:System.Data.DataRow>做為方法參數。|
|`TableAdapter.Delete`|刪除現有記錄從資料庫根據原始的資料行值傳遞為方法參數。|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>若要從物件的新記錄儲存至資料庫

-   建立記錄值傳遞至`TableAdapter.Insert`方法。

     下列範例會建立新的客戶記錄，在`Customers`資料表中的值傳遞`currentCustomer`物件到`TableAdapter.Insert`方法。

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>若要更新現有的資料錄從物件到資料庫

-   修改記錄，藉由呼叫`TableAdapter.Update`方法，傳遞新的值來更新記錄，並傳入要找出資料錄的原始值。

    > [!NOTE]
    > 您的物件需要維護的原始值，才能將其傳遞給`Update`方法。 這個範例會使用具有屬性`orig`儲存原始值的前置詞。

     下列範例會更新中的現有記錄`Customers`藉由傳遞中的全新及原始值的表格`Customer`物件到`TableAdapter.Update`方法。

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>若要從資料庫刪除現有的記錄

-   刪除記錄，藉由呼叫`TableAdapter.Delete`方法並傳入要找出資料錄的原始值。

    > [!NOTE]
    > 您的物件需要維護的原始值，才能將其傳遞給`Delete`方法。 這個範例會使用具有屬性`orig`儲存原始值的前置詞。

     下列範例會刪除從資料錄`Customers`藉由傳遞中的原始值的資料表`Customer`物件到`TableAdapter.Delete`方法。

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-framework-security"></a>.NET Framework 安全性

您必須執行選取的權限`INSERT`， `UPDATE`，或`DELETE`上資料庫中的資料表。

## <a name="see-also"></a>另請參閱

- [將資料儲存回資料庫](../data-tools/save-data-back-to-the-database.md)