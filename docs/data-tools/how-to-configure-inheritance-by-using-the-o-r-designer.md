---
title: 如何： 使用 O R 設計工具設定繼承
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 12874d7f2202225ba35c16f9e4d6fee7f9165206
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>如何： 使用 O/R 設計工具設定繼承
[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) 通常是在關聯式系統中實作，因此支援單一資料表繼承概念。 在單一資料表繼承 (Inheritance) 中，單一資料庫資料表的欄位會同時包含父代資訊和子系資料。 使用關聯式資料時，鑑別子資料行所含的值會決定任何記錄所屬的類別 (Class)。

例如，假設有個 Persons 資料表包含某家公司雇用的所有人員。 有些人是員工，而有些人是經理。 這個 Persons 資料表包含一個名為 `EmployeeType` 的資料行 (其中值 1 代表經理，值 2 代表員工)，這就是鑑別子資料行。 在這個案例中，您可以建立員工子類別 (Subclass)，並且只將 `EmployeeType` 值為 2 的記錄填入 (Populate) 這個類別。 您也可以從每個類別中移除不適用的資料行。

建立使用繼承的物件模型 (並對應至關聯式資料) 在過程上較為複雜。 下列程序將會說明使用 O/R 設計工具設定繼承的必要步驟。 因為在不參考現有資料表和資料行的情況下遵循這些泛型步驟，將是一件困難的事，所以提供了使用資料的逐步解說。 詳細逐步指示，說明如何藉由設定繼承[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，請參閱[逐步解說： 建立 LINQ to SQL 類別，以使用單一資料表繼承 （O/R 設計工具）](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)。

## <a name="to-create-inherited-data-classes"></a>若要建立繼承的資料類別

1.  開啟[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]加**LINQ to SQL 類別**項目加入現有的 Visual Basic 或 C# 專案。

2.  將想要當成基底類別 (Base Class) 的資料表拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。

3.  拖曳資料表拖曳至第二個副本[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]並將它重新命名。 這就是衍生類別 (Derived Class) 或子類別。

4.  按一下**繼承**中**物件關聯式設計工具**] 索引標籤**工具箱**，然後按一下 [子類別 （已重新命名的資料表），並將它連接到基底類別。

    > [!NOTE]
    >  按一下**繼承**中的項目**工具箱**並放開滑鼠按鈕，按一下您在步驟 3 中建立類別的第二個副本，然後按一下您在步驟 2 中建立的第一個類別。 繼承線的箭號會指向第一個類別。

5.  在每個類別中，刪除任何不想要顯示而且沒有用於關聯的物件屬性。 如果您嘗試刪除用於關聯的物件屬性，您會收到錯誤：[屬性\<屬性名稱 > 無法刪除，因為它正參與關聯\<關聯名稱 >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    >  因為衍生類別會繼承其基底類別中定義的屬性，所以這兩個類別中不可以定義相同的資料行  (資料行是以屬性形式實作)。在基底類別的屬性上設定 [繼承修飾詞]，就可以啟用衍生類別中的資料行建立作業。 如需詳細資訊，請參閱[繼承基本概念 (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)。

6.  選取 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中的繼承線。

7.  在**屬性**視窗中，將**鑑別子屬性**用來區別您類別中的資料錄的資料行名稱。

8.  設定**衍生類別鑑別子值**屬性設為將記錄指定為繼承類型的資料庫中的值。 (這是儲存在鑑別子資料行中，用於指定繼承類別的值)。

9. 設定**基底類別鑑別子值**屬性設為將記錄指定的基底類型的值。 (這是儲存在鑑別子資料行中，用於指定基底類別的值)。

10. （選擇性） 您也可以設定**繼承預設值**屬性來指定將載入的資料列不符合任何既定的繼承程式碼時，會使用的繼承階層架構中的型別。 換句話說，如果某筆記錄的鑑別子資料行有值，不符合值在**衍生類別鑑別子值**或**基底類別鑑別子值**屬性、 記錄會將載入的型別指定為**繼承預設值**。

## <a name="see-also"></a>另請參閱

- [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Visual Studio 中的 LINQ to SQL 工具)
- [逐步解說： 建立 LINQ to SQL 類別 （O R 設計工具）](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [逐步解說： 建立 LINQ to SQL 類別使用單一資料表繼承 （O/R 設計工具）](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [繼承基本概念 (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [繼承](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)