---
title: 如何：擴充 O-R 設計工具產生的程式碼
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6ff7dfc9a83028b866f7601b9b41c685262356ac
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55909596"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>如何：擴充 O/R 設計工具產生的程式碼
所產生的程式碼**O/R Designer**實體類別和設計工具介面上的其他物件進行變更時重新產生。 因為有這項重新產生作業，所以當設計工具重新產生程式碼時，您之前加入至所產生程式碼的程式碼，通常都會遭覆寫。 **O/R Designer**提供產生部分類別檔案，您可以在其中新增的功能不會覆寫的程式碼。 將您自己的程式碼加入至產生的程式碼的其中一個範例**O/R Designer**是資料將驗證新增至 LINQ to SQL (entity) 類別。 如需詳細資訊，請參閱 <<c0> [ 如何： 將驗證新增至實體類別](../data-tools/how-to-add-validation-to-entity-classes.md)。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>將程式碼新增至實體類別

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>若要建立部分類別並將程式碼加入至實體類別

1.  開啟或建立新的 LINQ to SQL 類別檔案 (**.dbml**檔案) 中**O/R Designer**。 (按兩下 **.dbml**中的檔案**方案總管**或是**資料庫總管**。)

2.  在 **O/R 設計工具**中，以滑鼠右鍵按一下要新增驗證的類別，然後按一下 [檢視程式碼]。

     [程式碼編輯器] 會以所選取實體類別的部分類別開啟。

3.  在實體類別的部分類別宣告中，加入程式碼。

## <a name="add-code-to-a-datacontext"></a>將程式碼加入至 DataContext

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>若要建立部分類別並將程式碼加入至 DataContext

1.  開啟或建立新的 LINQ to SQL 類別檔案 (**.dbml**檔案) 中**O/R Designer**。 (按兩下 **.dbml**中的檔案**方案總管**或是**資料庫總管**。)

2.  在  **O/R Designer**，以滑鼠右鍵按一下設計工具上的空白區域，然後按一下**檢視程式碼**。

     [程式碼編輯器] 會以 DataContext 的部分類別開啟。

3.  在 DataContext 的部分類別宣告中，加入程式碼。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [逐步解說：建立 LINQ to SQL 類別 (O-R 設計工具)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)