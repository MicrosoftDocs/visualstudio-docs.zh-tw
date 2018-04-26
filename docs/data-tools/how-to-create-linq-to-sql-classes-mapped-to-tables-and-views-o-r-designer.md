---
title: 如何： 建立 LINQ to SQL 類別對應至資料表和檢視 （O R 設計工具）
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b81d67d6897826ab2f6de1e3b48663b18bffdb1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>如何： 建立 LINQ to SQL 類別對應至資料表和檢視 （O/R 設計工具）
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 會對應至資料庫資料表和檢視表的類別稱為*實體類別*。 實體類別對應至記錄，而實體類別的個別屬性會對應至組成記錄的個別資料行。 建立實體類別，根據資料庫資料表或檢視表拖曳資料表或檢視表**伺服器總管**/**資料庫總管**到[LINQ to SQL 中的工具Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]產生類別，並套用特定[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]屬性，可讓[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]功能 (資料通訊和編輯功能<xref:System.Data.Linq.DataContext>)。 如需詳細資訊[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]類別，請參閱[LINQ to SQL 物件模型](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)。

> [!NOTE]
>  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]是簡單的物件關聯式對應工具 」，因為它支援僅 1:1 對應關係。 換句話說，實體類別與資料庫資料表或檢視之間只可以有一對一對應關聯性。 目前不支援複雜對應 (例如，將實體類別對應至多個資料表)。 不過，您可以將一個實體類別對應至一個將多個相關資料表聯結 (Join) 在一起的檢視。

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>建立會對應至資料庫資料表或檢視的 LINQ to SQL 類別
 將資料表或檢視從**伺服器總管**/**資料庫總管**到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]建立實體類別，除了<xref:System.Data.Linq.DataContext>所使用的方法執行更新。

 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 執行階段預設會建立邏輯，以將可更新之實體類別中的變更儲存回資料庫。 這個邏輯是根據資料表的結構描述 (資料行定義和主索引鍵資訊)。 如果不想要有這個行為，則可以將實體類別設定成使用預存程序來執行插入、更新和刪除，而不是使用預設的 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 執行階段行為。 如需詳細資訊，請參閱[如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>若要建立會對應至資料庫資料表或檢視的 LINQ to SQL 類別

1.  在**伺服器**/**資料庫總管**，依序展開**資料表**或**檢視**並找出資料庫資料表或檢視您想要在您的應用程式中使用。

2.  將資料表或檢視拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。

     實體類別隨即建立並出現在設計介面上。 這個實體類別的屬性會對應至所選取資料表或檢視中的資料行。

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>建立物件資料來源並將資料顯示在表單上
 使用建立實體類別之後[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，您可以建立物件資料來源，並填入[資料來源視窗](add-new-data-sources.md)與實體類別。

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>若要根據 LINQ to SQL 實體類別來建立物件資料來源

1.  在**建置**功能表上，按一下 **建置方案**建置專案。

2.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。

3.  在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。

4.  按一下**物件**上**選擇資料來源類型**頁面，然後按一下**下一步**。

5.  展開節點，並尋找和選取類別。

    > [!NOTE]
    >  如果**客戶**類別不提供，取消精靈、 建置專案時，並再次執行精靈。

6.  按一下**完成**建立資料來源並將新增**客戶**實體類別，以**資料來源**視窗。

7.  將項目從**資料來源**視窗拖曳至表單。

## <a name="see-also"></a>另請參閱

- [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Visual Studio 中的 LINQ to SQL 工具)
- [逐步解說： 建立 LINQ to SQL 類別 （O R 設計工具）](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)
- [如何： 建立對應至預存程序和函式 （O/R 設計工具） 的 DataContext 方法](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL 物件模型](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [逐步解說：自訂實體類別的插入、更新和刪除行為](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [如何： 建立 LINQ to SQL 類別 （O/R 設計工具） 之間的關聯 （關聯性）](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)