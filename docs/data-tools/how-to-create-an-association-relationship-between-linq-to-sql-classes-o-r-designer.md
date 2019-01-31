---
title: 如何建立 LINQ to SQL 類別使用 O/R 設計工具之間的關聯性
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: ab66f41a6510eb8cf2376cb7bb4d6fa21e7b1159
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001326"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>HOW TO：建立 LINQ to SQL 類別 （O/R 設計工具） 之間的關聯
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 中實體類別 (Class) 之間的關聯，與資料庫中資料表之間的關聯性 (Relationship) 類似。 您可以使用 [關聯編輯器] 對話方塊建立實體類別之間的關聯。

使用 [關聯編輯器] 對話方塊建立關聯時，必須選取父類別和子類別。 父類別是包含主索引鍵的實體類別，而子類別是包含外部索引鍵的實體類別。 比方說，如果已建立實體類別對應至`Northwind Customers`並`Orders`資料表`Customer`類別會是父類別和`Order`類別會是子類別。

> [!NOTE]
>  當您將資料表從**伺服器總管**或是**資料庫總管**拖曳至**物件關聯式設計工具**(**O/R 設計工具**)，關聯會自動建立根據資料庫中的現有外部索引鍵關聯性。

## <a name="association-properties"></a>關聯屬性
建立關聯之後，當您在 [O/R 設計工具] 中選取該關聯時，[屬性] 視窗中會出現一些可設定的屬性。 (關聯就是相關類別之間的線條)。下表提供關聯屬性的說明。

|屬性|說明|
|--------------|-----------------|
|**基數**|控制關聯是一對多還是一對一。|
|**子屬性**|指定是否要在父代 (Parent) 上建立屬性，這個屬性是位於關聯的外部索引鍵端上之子記錄的集合或參考。 例如，在之間的關聯`Customer`並`Order`，如果**子屬性**設為 **，則為 True**，名為的屬性`Orders`父類別上會建立。|
|**父屬性**|子類別上參考相關父類別的屬性。 例如，在之間的關聯`Customer`和`Order`，一個名為屬性`Customer`參考相關聯的客戶訂單會建立在`Order`類別。|
|**參與屬性**|顯示關聯屬性，並提供**省略符號**按鈕 (...) 來重新開啟 [關聯編輯器] 對話方塊。|
|**唯一**|指定外部目標資料行是否具有唯一性條件約束 (Constraint)。|

## <a name="to-create-an-association-between-entity-classes"></a>若要在實體類別之間建立關聯

1.  以滑鼠右鍵按一下代表關聯中父類別的實體類別，指向 [新增]，然後按一下 [關聯]。

2.  確認 [關聯編輯器] 對話方塊中選取的是正確的 [父類別]。

3.  選取下拉式方塊中的 [子類別]。

4.  選取使類別互相關聯的 [關聯屬性]。 通常，這會對應至資料庫中定義的外部索引鍵關聯性。 例如，在`Customers`和`Orders`關聯**關聯屬性**是`CustomerID`針對每個類別。

5.  按一下 [確定] 建立關聯。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [逐步解說：建立 LINQ to SQL 類別](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext 方法 (O/R 設計工具)](../data-tools/datacontext-methods-o-r-designer.md)
- [如何：表示主索引鍵](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)