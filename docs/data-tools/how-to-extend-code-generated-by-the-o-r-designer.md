---
title: 如何：擴充 O-R 設計工具產生的程式碼
description: 請參閱如何延伸物件關聯式設計工具 (O/R 設計工具) 產生的程式碼。 將程式碼加入至實體類別。 將程式碼加入至 DataCoNtext。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 2404fd48aade91c623efb12e89f4a97da01ec66b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858705"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>如何：擴充 O/R 設計工具產生的程式碼
當對設計工具介面上的實體類別和其他物件進行變更時，會重新產生 **O/R 設計** 工具所產生的程式碼。 因為有這項重新產生作業，所以當設計工具重新產生程式碼時，您之前加入至所產生程式碼的程式碼，通常都會遭覆寫。 **O/R 設計** 工具提供產生部分類別檔案的功能，您可以在其中加入不會覆寫的程式碼。 將您自己的程式碼加入至 **O/R 設計** 工具所產生之程式碼的其中一個範例，就是將資料驗證加入至 LINQ to SQL (實體) 類別中。 如需詳細資訊，請參閱 [如何：將驗證加入至實體類別](../data-tools/how-to-add-validation-to-entity-classes.md)。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>將程式碼加入至實體類別

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>若要建立部分類別並將程式碼加入至實體類別

1. 在 **O/R 設計** 工具中，開啟或建立 (**.dbml** 檔) 的新 LINQ to SQL 類別檔案。  (在 **方案總管** 或 **資料庫總管** 中按兩下 **.dbml** 檔。 ) 

2. 在 **O/R 設計工具** 中，以滑鼠右鍵按一下要新增驗證的類別，然後按一下 [檢視程式碼]。

     [程式碼編輯器] 會以所選取實體類別的部分類別開啟。

3. 在實體類別的部分類別宣告中，加入程式碼。

## <a name="add-code-to-a-datacontext"></a>將程式碼加入至 DataCoNtext

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>若要建立部分類別並將程式碼加入至 DataContext

1. 在 **O/R 設計** 工具中，開啟或建立 (**.dbml** 檔) 的新 LINQ to SQL 類別檔案。  (在 **方案總管** 或 **資料庫總管** 中按兩下 **.dbml** 檔。 ) 

2. 在 **O/R 設計** 工具中，以滑鼠右鍵按一下設計工具上的空白區域，然後按一下 [ **視圖程式碼**]。

     [程式碼編輯器] 會以 DataContext 的部分類別開啟。

3. 在 DataContext 的部分類別宣告中，加入程式碼。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [逐步解說：建立 LINQ to SQL 類別 (O-R 設計工具)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
