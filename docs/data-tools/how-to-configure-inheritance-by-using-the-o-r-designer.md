---
title: HOW TO：使用 O/R 設計工具設定繼承
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 2a68101b6090a20526088309a441956a68e875e9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55014662"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>HOW TO：使用 O/R 設計工具設定繼承
**物件關聯式設計工具**(**O/R Designer**) 支援的單一資料表繼承概念，通常是在關聯式系統中實作。 在單一資料表繼承 (Inheritance) 中，單一資料庫資料表的欄位會同時包含父代資訊和子系資料。 使用關聯式資料時，鑑別子資料行所含的值會決定任何記錄所屬的類別 (Class)。

例如，假設`Persons`包含某家公司雇用的所有人的資料表。 有些人是員工，而有些人是經理。 `Persons`資料表包含資料行名為`EmployeeType`經理和 2 的值具有值為 1 的員工，這是鑑別子資料行。 在這個案例中，您可以建立員工子類別 (Subclass)，並且只將 `EmployeeType` 值為 2 的記錄填入 (Populate) 這個類別。 您也可以從每個類別中移除不適用的資料行。

建立使用繼承的物件模型 (並對應至關聯式資料) 在過程上較為複雜。 下列程序將會說明使用 **O/R 設計工具**設定繼承的必要步驟。 遵循這些泛型步驟而不會參考現有的資料表和資料行可能很困難，因此提供逐步解說中使用資料。 針對使用設定繼承的詳細逐步指示**O/R Designer**，請參閱[逐步解說：使用單一資料表繼承建立 LINQ to SQL 類別 (O/R 設計工具)

## <a name="to-create-inherited-data-classes"></a>若要建立繼承的資料類別

1.  開啟**O/R Designer**加上**LINQ to SQL 類別**到現有的 Visual Basic 的項目或C#專案。

2.  拖曳您想要使用的基底類別拖曳至的資料表**O/R Designer**。

3.  拖曳資料表拖曳至第二個副本**O/R Designer**並將它重新命名。 這就是衍生類別 (Derived Class) 或子類別。

4.  在 [工具箱] 的 [物件關聯式設計工具] 索引標籤中按一下 [繼承]，然後按一下子類別 (重新命名的資料表)，將其連線至基底類別。

    > [!NOTE]
    >  按一下 [工具箱] 中的 [繼承] 項目，然後放開滑鼠按鍵，按一下在步驟 3 中建立的第二個類別複本，再按一下在步驟 2 中建立的第一個類別。 繼承線的箭號會指向第一個類別。

5.  在每個類別中，刪除任何不想要顯示而且沒有用於關聯的物件屬性。 如果您嘗試刪除用於關聯的物件屬性，您會收到錯誤：[無法刪除屬性 \<屬性名稱>，因為它正參與關聯 \<關聯名稱>](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md)

    > [!NOTE]
    >  因為衍生類別會繼承其基底類別中定義的屬性，所以這兩個類別中不可以定義相同的資料行  (資料行是以屬性形式實作)。在基底類別的屬性上設定繼承修飾詞，就可以啟用衍生類別中的資料行建立作業。 如需詳細資訊，請參閱 <<c0> [ 繼承的基本概念 (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)。

6.  選取中的繼承線**O/R Designer**。

7.  在 **屬性**視窗中，將**鑑別子屬性**區分您的類別中的資料錄的資料行名稱。

8.  將 [衍生類別鑑別子值] 屬性設定為資料庫中將記錄指定為繼承類型的值。 （這是儲存在鑑別子資料行，用來指定繼承的類別的值）。

9. 將 [基底類別鑑別子值] 屬性設定為將記錄指定為基底類型的值。 （這是儲存在鑑別子資料行，用來將指定的基底類別的值）。

10. 您也可以選擇設定 [繼承預設] 屬性，以指定當載入的資料列不符合任何既定的繼承程式碼時，要依繼承階層使用的類型。 換句話說，如果記錄的鑑別子資料行中的值不符合中的值**衍生類別鑑別子值**或是**基底類別鑑別子值**屬性，記錄載入為指定的型別**繼承預設值**。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [逐步解說：建立 LINQ to SQL 類別 （O-R 設計工具）](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [逐步解說：使用單一資料表繼承建立 LINQ to SQL 類別 (O/R 設計工具)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [繼承基本概念 (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [繼承](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)