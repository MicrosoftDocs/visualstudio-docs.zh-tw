---
title: '將 LINQ to SQL 類別對應至資料表/views (O R 設計工具) '
description: 瞭解如何建立 (類別的 LINQ to SQL 實體類別，這些類別會對應至物件關聯式設計工具 (O/R 設計工具) 中) 的資料表和 views。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b440e8c47afdec6e0b04b5f48a35e15fe48e1875
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866797"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>如何：建立對應至資料表和檢視的 LINQ to SQL 類別 (O/R 設計工具)

[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 對應至資料庫資料表和視圖的類別稱為 *實體類別*。 Entity 類別會對應至記錄，而實體類別的個別屬性會對應至組成記錄的個別資料行。 從 **伺服器總管** 或 **資料庫總管** 將資料表或視圖拖曳至 [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)，以建立以資料庫資料表或視圖為基礎的實體類別。 **O/R 設計** 工具會產生類別並套用特定的 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 屬性，以啟用 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] () 資料通訊和編輯功能的功能 <xref:System.Data.Linq.DataContext> 。 如需類別的詳細資訊 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ，請參閱 [LINQ to SQL 物件模型](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)。

> [!NOTE]
> **O/R 設計** 工具是簡單的物件關聯式對應程式，因為它只支援1:1 對應關聯性。 換句話說，實體類別與資料庫資料表或檢視之間只可以有一對一對應關聯性。 目前不支援複雜對應 (例如，將實體類別對應至多個資料表)。 不過，您可以將一個實體類別對應至一個將多個相關資料表聯結 (Join) 在一起的檢視。

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>建立對應至資料庫資料表或檢視的 LINQ to SQL 類別

從 **伺服器總管** 或 **資料庫總管** 拖曳資料表或視圖至 **O/R 設計** 工具時，除了用來執行更新的方法之外，還會建立實體類別 <xref:System.Data.Linq.DataContext> 。

[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 執行階段預設會建立邏輯，以將可更新之實體類別中的變更儲存回資料庫。 這個邏輯是根據資料表的結構描述 (資料行定義和主索引鍵資訊)。 如果您不想要此行為，可以將實體類別設定為使用預存程式來執行插入、更新和刪除，而不是使用預設的 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 執行時間行為。 如需詳細資訊，請參閱 [如何：指派預存程式來執行更新、插入和刪除 (O/R 設計工具) ](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>若要建立會對應至資料庫資料表或檢視的 LINQ to SQL 類別

1. 在 [伺服器] 或 [資料庫總管] 中，展開 [資料表] 或 [檢視]，並尋找您希望在應用程式中使用的資料庫資料表或檢視。

2. 將資料表或視圖拖曳至 **O/R 設計** 工具。

     實體類別隨即建立並出現在設計介面上。 這個實體類別的屬性會對應至所選取資料表或檢視中的資料行。

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>建立物件資料來源並將資料顯示在表單上

使用 **O/R 設計** 工具建立實體類別之後，您可以建立物件資料來源，並在 [ [資料來源] 視窗](add-new-data-sources.md#data-sources-window) 中填入實體類別。

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>若要根據 LINQ to SQL 實體類別來建立物件資料來源

1. 按一下 [建置] 功能表上的 [建置方案] 來建置您的專案。

2. 若要開啟 [ **資料來源** ] 視窗，請按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。

3. 在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。

4. 按一下 [選擇資料來源類型] 頁面上的 [物件]，然後按一下 [下一步]。

5. 展開節點，並尋找和選取類別。

    > [!NOTE]
    > 如果 **客戶** 類別無法使用，請取消精靈、建置專案，然後再次執行精靈。

6. 按一下 [完成] 以建立資料來源，然後將 [客戶] 實體類別新增至 [資料來源] 視窗。

7. 將項目從 [資料來源] 視窗拖曳至表單。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [逐步解說：建立 LINQ to SQL 類別 (O-R 設計工具)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [DataCoNtext 方法 (O/R 設計工具) ](../data-tools/datacontext-methods-o-r-designer.md)
- [如何：建立對應至預存程序和函式的 DataContext 方法 (O/R 設計工具)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL 物件模型](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [逐步解說：自訂實體類別的插入、更新和刪除行為](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [如何：建立 LINQ to SQL 類別之間的關聯 (關聯性) (O/R 設計工具)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)
