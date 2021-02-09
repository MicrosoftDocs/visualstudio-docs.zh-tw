---
title: 將 DataCoNtext 方法對應至 sprocs 和函數
description: 瞭解如何使用物件關聯式設計工具 (O/R 設計工具) ，建立對應至預存程式的 DataCoNtext 方法 (sprocs) 和函式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 2f9b003deb7bc4c564be62d8e7ca486c88cee8a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858731"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>如何：建立對應至預存程序和函式的 DataContext 方法 (O/R 設計工具)

您可以將預存程式和函式加入至 **O/R 設計** 工具中做為 <xref:System.Data.Linq.DataContext> 方法。 只要呼叫這個方法並傳入必要參數，就會在資料庫上執行預存程序或函式，並以 <xref:System.Data.Linq.DataContext> 方法的傳回型別傳回資料。 如需方法的詳細資訊 <xref:System.Data.Linq.DataContext> ，請參閱 [DataCoNtext 方法 (O/R 設計工具) ](../data-tools/datacontext-methods-o-r-designer.md)。

> [!NOTE]
> 您也可以使用預存程式來覆寫 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 從實體類別將變更儲存至資料庫時，執行插入、更新和刪除的預設執行時間行為。 如需詳細資訊，請參閱 [如何：指派預存程式來執行更新、插入和刪除 (O/R 設計工具) ](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。

## <a name="create-datacontext-methods"></a>建立 DataCoNtext 方法

您可以將 <xref:System.Data.Linq.DataContext> 預存程式或函式從 <strong>伺服器總管或 * * 資料庫總管</strong> 拖曳至 **O/R 設計** 工具，以建立方法。

> [!NOTE]
> 產生之方法的傳回型別 <xref:System.Data.Linq.DataContext> 會根據您在 **O/R 設計** 工具上放置預存程式或函數的位置而有所不同。 如果將項目直接置放入現有的實體類別，則建立的 <xref:System.Data.Linq.DataContext> 方法會具有該實體類別的傳回型別。 將專案放到 **O/R 設計** 工具的空白區域 <xref:System.Data.Linq.DataContext> ，會建立一個方法來傳回自動產生的型別。 您可以在將 <xref:System.Data.Linq.DataContext> 方法新增至 [方法] 窗格後，變更此方法的傳回型別。 若要檢查或變更 <xref:System.Data.Linq.DataContext> 方法的傳回型別，請選取該方法，然後檢查 [屬性] 視窗中的 [傳回型別] 屬性。 如需詳細資訊，請參閱 [如何：變更 DataCoNtext 方法的傳回類型 (O/R 設計工具) ](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>若要建立可傳回自動產生型別的 DataContext 方法

1. 在 **伺服器總管** 或 **資料庫總管** 中，展開您要使用之資料庫的 [ **預存程式** ] 節點。

2. 找出所需的預存程式，並將它拖曳到 **O/R 設計** 工具的空白區域。

     <xref:System.Data.Linq.DataContext> 方法會以自動產生的傳回型別建立，並出現在 [方法] 窗格中。

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>若要建立具有實體類別之傳回型別的 DataContext 方法

1. 在 **伺服器總管** 或 **資料庫總管** 中，展開您要使用之資料庫的 [ **預存程式** ] 節點。

2. 找出所需的預存程式，並將它拖曳到 **O/R 設計** 工具中的現有實體類別。

     <xref:System.Data.Linq.DataContext> 方法會以所選取實體類別的傳回型別建立，並出現在 [方法] 窗格中。

> [!NOTE]
> 如需變更現有方法之傳回類型的詳細資訊 <xref:System.Data.Linq.DataContext> ，請參閱 [如何：變更 DataCoNtext 方法的傳回類型 (O/R 設計工具) ](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataCoNtext 方法 (O/R 設計工具) ](../data-tools/datacontext-methods-o-r-designer.md)
- [逐步解說：建立 LINQ to SQL 類別](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Basic 中的 LINQ 簡介](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [C# 中的 LINQ](/dotnet/csharp/linq/linq-in-csharp)
