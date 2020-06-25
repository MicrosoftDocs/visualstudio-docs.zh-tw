---
title: LINQ to SQL 類別之間的關聯性（O/R 設計工具）
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b081e989932ea03a3aaf3203bdc7383f90b9b7ed
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282146"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>如何：建立 LINQ to SQL 類別之間的關聯（O/R 設計工具）
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 中實體類別 (Class) 之間的關聯，與資料庫中資料表之間的關聯性 (Relationship) 類似。 您可以使用 [關聯編輯器]**** 對話方塊建立實體類別之間的關聯。

使用 [關聯編輯器]**** 對話方塊建立關聯時，必須選取父類別和子類別。 父類別是包含主索引鍵的實體類別，而子類別是包含外部索引鍵的實體類別。 例如，如果建立對應到和資料表的實體類別 `Northwind Customers` `Orders` ，則 `Customer` 類別會是父類別，而 `Order` 類別會是子類別。

> [!NOTE]
> 當您將資料表從**伺服器總管**或**資料庫總管**拖曳至**物件關聯式設計工具**（**O/R 設計**工具）時，會根據資料庫中現有的外鍵關聯性，自動建立關聯。

## <a name="association-properties"></a>關聯屬性
建立關聯之後，當您在 [O/R 設計工具]**** 中選取該關聯時，[屬性]**** 視窗中會出現一些可設定的屬性。 （關聯是相關類別之間的線條）。下表提供關聯屬性的描述。

|屬性|說明|
|--------------|-----------------|
|**基數**|控制關聯是一對多還是一對一。|
|**子屬性**|指定是否要在父代 (Parent) 上建立屬性，這個屬性是位於關聯的外部索引鍵端上之子記錄的集合或參考。 例如，在和之間的關聯中， `Customer` `Order` 如果**子屬性**設定為**True**， `Orders` 則會在父類別上建立名為的屬性。|
|**Parent 屬性**|子類別上參考相關父類別的屬性。 例如，在和之間的關聯 `Customer` 中 `Order` ， `Customer` 會在類別上建立名為的屬性，其參考訂單的相關聯客戶 `Order` 。|
|**參與屬性**|顯示關聯屬性，並提供**省略符號**按鈕 (...) 來重新開啟 [關聯編輯器]**** 對話方塊。|
|**唯一**|指定外部目標資料行是否具有唯一性條件約束 (Constraint)。|

## <a name="to-create-an-association-between-entity-classes"></a>若要在實體類別之間建立關聯

1. 以滑鼠右鍵按一下代表關聯中父類別的實體類別，指向 [新增]****，然後按一下 [關聯]****。

2. 確認 [關聯編輯器]**** 對話方塊中選取的是正確的 [父類別]****。

3. 選取下拉式方塊中的 [子類別]****。

4. 選取使類別互相關聯的 [關聯屬性]****。 通常，這會對應至資料庫中定義的外部索引鍵關聯性。 例如，在 `Customers` 和關聯中 `Orders` ，**關聯屬性**為 `CustomerID` 每個類別的。

5. 按一下 [確定]**** 建立關聯。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [逐步解說：建立 LINQ to SQL 類別](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataCoNtext 方法（O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)
- [如何：表示主鍵](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)
