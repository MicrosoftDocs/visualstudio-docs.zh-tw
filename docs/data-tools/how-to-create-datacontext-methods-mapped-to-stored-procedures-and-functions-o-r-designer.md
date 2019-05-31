---
title: DataContext 方法對應至 sprocs 和函式 （O-R 設計工具）
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3051820be7972af93419833cc62617f6d7e524da
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260489"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>作法：建立對應至預存程序和函式的 DataContext 方法 (O/R 設計工具)

您可以加入預存程序和函式**O/R Designer**做為<xref:System.Data.Linq.DataContext>方法。 只要呼叫這個方法並傳入必要參數，就會在資料庫上執行預存程序或函式，並以 <xref:System.Data.Linq.DataContext> 方法的傳回型別傳回資料。 如需詳細資訊<xref:System.Data.Linq.DataContext>方法，請參閱[DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。

> [!NOTE]
> 您也可以使用預存程序覆寫預設[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]執行插入、 更新和刪除時的變更儲存至資料庫的實體類別的執行階段行為。 如需詳細資訊，請參閱[如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。

## <a name="create-datacontext-methods"></a>建立 DataContext 方法

您可以建立<xref:System.Data.Linq.DataContext>方法，藉由拖曳預存程序或函數從<strong>伺服器總管或 * * 資料庫總管</strong>拖曳至**O/R Designer**。

> [!NOTE]
> 產生的傳回型別<xref:System.Data.Linq.DataContext>方法而有所不同卸除預存程序或函式的地方**O/R Designer**。 如果將項目直接置放入現有的實體類別，則建立的 <xref:System.Data.Linq.DataContext> 方法會具有該實體類別的傳回型別。 項目放入的空白區域**O/R Designer**建立<xref:System.Data.Linq.DataContext>方法會傳回自動產生的型別。 您可以在將 <xref:System.Data.Linq.DataContext> 方法新增至 [方法]  窗格後，變更此方法的傳回型別。 若要檢查或變更 <xref:System.Data.Linq.DataContext> 方法的傳回型別，請選取該方法，然後檢查 [屬性]  視窗中的 [傳回型別]  屬性。 如需詳細資訊，請參閱[如何：變更 DataContext 方法的傳回型別 (O/R 設計工具)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>若要建立可傳回自動產生型別的 DataContext 方法

1. 在 **伺服器總管**或**資料庫總管**，展開**預存程序**您所使用的資料庫節點。

2. 找出所需的預存程序，並將它拖曳至空白的地方**O/R Designer**。

     <xref:System.Data.Linq.DataContext> 方法會以自動產生的傳回型別建立，並出現在 [方法]  窗格中。

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>若要建立具有實體類別之傳回型別的 DataContext 方法

1. 在 **伺服器總管**或**資料庫總管**，展開**預存程序**您所使用的資料庫節點。

2. 找出所需的預存程序，並將它拖曳至現有的實體類別中**O/R Designer**。

     <xref:System.Data.Linq.DataContext> 方法會以所選取實體類別的傳回型別建立，並出現在 [方法]  窗格中。

> [!NOTE]
> 如需變更現有的傳回型別資訊<xref:System.Data.Linq.DataContext>方法，請參閱[How to:變更 DataContext 方法的傳回型別 (O/R 設計工具)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext 方法 (O/R 設計工具)](../data-tools/datacontext-methods-o-r-designer.md)
- [逐步解說：建立 LINQ to SQL 類別](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Basic 中的 LINQ 簡介](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [C# 中的 LINQ](/dotnet/csharp/linq/linq-in-csharp)
