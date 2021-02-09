---
title: 使用 O/R 設計工具設定繼承
description: 瞭解如何使用物件關聯式設計工具的 (O/R 設計工具) 支援單一資料表繼承，以設定繼承。 建立繼承的資料類別。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: fee2c42e6ec84280f4090a8ae1dfea83a81ee369
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866823"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>如何：使用 O/R 設計工具設定繼承
**物件關聯式設計工具** (**O/R 設計** 工具) 支援單一資料表繼承的概念，因為它通常是在關聯式系統中執行。 在單一資料表繼承 (Inheritance) 中，單一資料庫資料表的欄位會同時包含父代資訊和子系資料。 使用關聯式資料時，鑑別子資料行所含的值會決定任何記錄所屬的類別 (Class)。

例如，假設有一個 `Persons` 資料表包含公司所採用的每個人。 有些人是員工，而有些人是經理。 `Persons`資料表包含名為的資料行 `EmployeeType` ，其值為1代表經理，值為2代表員工。這是鑒別子資料行。 在這個案例中，您可以建立員工子類別 (Subclass)，並且只將 `EmployeeType` 值為 2 的記錄填入 (Populate) 這個類別。 您也可以從每個類別中移除不適用的資料行。

建立使用繼承的物件模型 (並對應至關聯式資料) 在過程上較為複雜。 下列程序將會說明使用 **O/R 設計工具** 設定繼承的必要步驟。 在不參考現有資料表和資料行的情況下執行一般步驟可能很困難，因此會提供使用資料的逐步解說。 針對使用設定繼承的詳細逐步指示 **O/R Designer**，請參閱 [逐步解說： 建立 LINQ to SQL 類別使用單一資料表繼承 （O/R 設計工具）](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)。

## <a name="to-create-inherited-data-classes"></a>若要建立繼承的資料類別

1. 將 **LINQ to SQL 類別** 專案加入至現有的 Visual Basic 或 c # 專案，以開啟 **O/R 設計** 工具。

2. 將您想要作為基類的資料表拖曳到 **O/R 設計** 工具上。

3. 將資料表的第二個複本拖曳到 **O/R 設計** 工具上，然後將它重新命名。 這就是衍生類別 (Derived Class) 或子類別。

4. 在 [工具箱] 的 [物件關聯式設計工具] 索引標籤中按一下 [繼承]，然後按一下子類別 (重新命名的資料表)，將其連線至基底類別。

    > [!NOTE]
    > 按一下 [工具箱] 中的 [繼承] 項目，然後放開滑鼠按鍵，按一下在步驟 3 中建立的第二個類別複本，再按一下在步驟 2 中建立的第一個類別。 繼承線上的箭號會指向第一個類別。

5. 在每個類別中，刪除任何不想要顯示而且沒有用於關聯的物件屬性。 如果您嘗試刪除用於關聯的物件屬性，就會收到錯誤： [ \<property name> 無法刪除屬性，因為它正在參與關聯 \<association name> ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md)。

    > [!NOTE]
    > 因為衍生類別會繼承其基底類別中定義的屬性，所以這兩個類別中不可以定義相同的資料行   (的資料行會實作為屬性。 ) 您可以在基類的屬性上設定繼承修飾詞，藉以在衍生類別中建立資料行。 如需詳細資訊，請參閱 [ (Visual Basic) 的繼承基本概念 ](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)。

6. 選取 [ **O/R 設計** 工具] 中的 [繼承] 行。

7. 在 [ **屬性** ] 視窗中，將 [ **鑒別子屬性** ] 設定為數據行名稱，以區分您類別中的記錄。

8. 將 [衍生類別鑑別子值] 屬性設定為資料庫中將記錄指定為繼承類型的值。  (這是儲存在鑒別子資料行中的值，用來指定繼承的類別。 ) 

9. 將 [基底類別鑑別子值] 屬性設定為將記錄指定為基底類型的值。  (這是儲存在鑒別子資料行中的值，用來指定基類。 ) 

10. 您也可以選擇設定 [繼承預設] 屬性，以指定當載入的資料列不符合任何既定的繼承程式碼時，要依繼承階層使用的類型。 換句話說，如果記錄的鑒別子資料行值不符合 [ **衍生類別鑒別子值** ] 或 [ **基類鑒別子值** ] 屬性中的值，則會將記錄載入至指定為 **繼承預設** 值的型別。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [逐步解說：建立 LINQ to SQL 類別 (O-R 設計工具)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [逐步解說：使用單一資料表繼承來建立 LINQ to SQL 類別 (O/R 設計工具) ](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [繼承基本概念 (Visual Basic) ](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [繼承](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
