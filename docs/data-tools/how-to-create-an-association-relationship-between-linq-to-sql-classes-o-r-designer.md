---
title: 如何建立 LINQ to SQL 類別使用 O/R 設計工具之間的關聯性
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9eb6237af696dc1f56ae82bd99a1ddfc54851484
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>如何： 建立 LINQ to SQL 類別 （O/R 設計工具） 之間的關聯
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 中實體類別 (Class) 之間的關聯，與資料庫中資料表之間的關聯性 (Relationship) 類似。 您可以建立使用的實體類別之間的關聯**關聯編輯器** 對話方塊。

您使用時必須選取父類別和子類別**關聯編輯器**對話方塊來建立關聯。 父類別是包含主索引鍵的實體類別，而子類別是包含外部索引鍵的實體類別。 例如，如果要建立與 Northwind 的 Customers 和 Orders 資料表對應的實體類別，則 Customer 類別會是父類別，而 Order 類別會是子類別。

> [!NOTE]
>  當您將資料表從**伺服器總管**/**資料庫總管**到[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)])，會自動建立根據現有的關聯在資料庫中的外部索引鍵關聯性。

## <a name="association-properties"></a>關聯屬性
當您在 O/R 設計工具中選取該關聯時，建立關聯之後，有一些可設定的屬性中**屬性**視窗。 (關聯就是相關類別之間的線條)。下表提供關聯屬性的說明。

|屬性|描述|
|--------------|-----------------|
|**基數**|控制關聯是一對多還是一對一。|
|**子屬性**|指定是否要在父代 (Parent) 上建立屬性，這個屬性是位於關聯的外部索引鍵端上之子記錄的集合或參考。 例如，在 Customer 與 Order，之間的關聯如果**子屬性**設**True**，父類別上會建立名為 Orders 的屬性。|
|**父屬性**|子類別上參考相關父類別的屬性。 例如，在 Customer 與 Order 之間的關聯中，Order 類別上會建立名為 Customer 的屬性，以參考與訂單關聯的客戶。|
|**參與屬性**|顯示關聯屬性，並提供**省略**按鈕 （…） 來重新開啟**關聯編輯器** 對話方塊。|
|**唯一**|指定外部目標資料行是否具有唯一性條件約束 (Constraint)。|

## <a name="to-create-an-association-between-entity-classes"></a>若要在實體類別之間建立關聯

1.  以滑鼠右鍵按一下代表關聯中的之父類別的實體類別，並指向**新增**，然後按一下 **關聯**。

2.  確認正確**父類別**中選取**關聯編輯器** 對話方塊。

3.  選取**子類別**下拉式方塊中。

4.  選取**關聯屬性**相關的類別。 通常，這會對應至資料庫中定義的外部索引鍵關聯性。 例如，在 Customers 與 Orders 的關聯，**關聯屬性**會針對每個類別的 CustomerID。

5.  按一下**確定**建立關聯。

## <a name="see-also"></a>另請參閱

- [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Visual Studio 中的 LINQ to SQL 工具)
- [逐步解說： 建立 LINQ to SQL 類別](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)
- [如何：表示主索引鍵](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)