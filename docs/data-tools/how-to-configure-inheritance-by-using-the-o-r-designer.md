---
title: 如何：使用 O-R 設計工具設定繼承
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e31e5e78d5c72167f9d1c1eaab974155a4c369f3
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282237"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>如何：使用 O/R 設計工具設定繼承
**物件關聯式設計工具**（**O/R 設計**工具）支援單一資料表繼承的概念，因為它通常是在關聯式系統中執行。 在單一資料表繼承 (Inheritance) 中，單一資料庫資料表的欄位會同時包含父代資訊和子系資料。 使用關聯式資料時，鑑別子資料行所含的值會決定任何記錄所屬的類別 (Class)。

例如，假設有一個 `Persons` 資料表包含公司所採用的每個人。 有些人是員工，而有些人是經理。 `Persons`資料表包含名為的資料行 `EmployeeType` ，管理員的值為1，而員工的值為 2; 這是鑒別子資料行。 在這個案例中，您可以建立員工子類別 (Subclass)，並且只將 `EmployeeType` 值為 2 的記錄填入 (Populate) 這個類別。 您也可以從每個類別中移除不適用的資料行。

建立使用繼承的物件模型 (並對應至關聯式資料) 在過程上較為複雜。 下列程序將會說明使用 **O/R 設計工具**設定繼承的必要步驟。 在不參考現有資料表和資料行的情況下，遵循一般步驟可能會很棘手，因此會提供使用資料的逐步解說。 針對使用設定繼承的詳細逐步指示**O/R Designer**，請參閱[逐步解說： 建立 LINQ to SQL 類別使用單一資料表繼承 （O/R 設計工具）](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)。

## <a name="to-create-inherited-data-classes"></a>若要建立繼承的資料類別

1. 藉由將**LINQ to SQL 類別**專案新增至現有的 Visual Basic 或 c # 專案，來開啟**O/R 設計**工具。

2. 將您想要用來做為基類的資料表拖曳至**O/R 設計**工具。

3. 將資料表的第二個複本拖曳至**O/R 設計**工具，並將它重新命名。 這就是衍生類別 (Derived Class) 或子類別。

4. 在 [工具箱]**** 的 [物件關聯式設計工具]**** 索引標籤中按一下 [繼承]****，然後按一下子類別 (重新命名的資料表)，將其連線至基底類別。

    > [!NOTE]
    > 按一下 [工具箱]**** 中的 [繼承]**** 項目，然後放開滑鼠按鍵，按一下在步驟 3 中建立的第二個類別複本，再按一下在步驟 2 中建立的第一個類別。 繼承線上的箭號指向第一個類別。

5. 在每個類別中，刪除任何不想要顯示而且沒有用於關聯的物件屬性。 如果您嘗試刪除用於關聯的物件屬性，就會收到錯誤： [ \<property name> 無法刪除屬性，因為它正在參與關聯 \<association name> ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md)。

    > [!NOTE]
    > 因為衍生類別會繼承其基底類別中定義的屬性，所以這兩個類別中不可以定義相同的資料行  （資料行會實作為屬性）。您可以在基類中的屬性上設定繼承修飾詞，藉以啟用衍生類別中的資料行建立。 如需詳細資訊，請參閱[繼承基本概念（Visual Basic）](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)。

6. 在**O/R 設計**工具中選取 [繼承線]。

7. 在 [**屬性**] 視窗中，將 [**鑒別子屬性**] 設定為區分類別中記錄的資料行名稱。

8. 將 [衍生類別鑑別子值]**** 屬性設定為資料庫中將記錄指定為繼承類型的值。 （這是儲存在鑒別子資料行中的值，用來指定繼承的類別）。

9. 將 [基底類別鑑別子值]**** 屬性設定為將記錄指定為基底類型的值。 （這是儲存在鑒別子資料行中的值，用來指定基類）。

10. 您也可以選擇設定 [繼承預設]**** 屬性，以指定當載入的資料列不符合任何既定的繼承程式碼時，要依繼承階層使用的類型。 換句話說，如果記錄的鑒別子資料行中的值不符合 [**衍生類別鑒別子值**] 或 [**基類鑒別子值**] 屬性中的值，則記錄會載入至指定為**繼承預設**值的類型。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [逐步解說：建立 LINQ to SQL 類別 (O-R 設計工具)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [逐步解說：使用單一資料表繼承建立 LINQ to SQL 類別（O/R 設計工具）](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [繼承基本概念（Visual Basic）](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [繼承](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
