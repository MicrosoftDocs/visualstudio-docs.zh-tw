---
title: 如何： 建立對應至預存程序和函式 （O R 設計工具） 的 DataContext 方法
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6d086157761bbade92e7b79973876d18bc52f2fd
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>如何： 建立對應至預存程序和函式 （O/R 設計工具） 的 DataContext 方法
預存程序和函式可以加入至[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]為<xref:System.Data.Linq.DataContext>方法。 呼叫這個方法並傳入必要的參數，在資料庫上執行的預存程序或函式，並將資料傳回的傳回型別中<xref:System.Data.Linq.DataContext>方法。 如需詳細資訊<xref:System.Data.Linq.DataContext>方法，請參閱[DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)。

> [!NOTE]
>  預存程序也可以用來覆寫當儲存實體類別 (Class) 的變更至資料庫時，用於執行插入、更新和刪除作業的預設 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 執行階段行為。 如需詳細資訊，請參閱[如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。

## <a name="creating-datacontext-methods"></a>建立 DataContext 方法
 您可以建立<xref:System.Data.Linq.DataContext>方法拖曳預存程序或函數從**伺服器總管/資料庫總管**到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。

> [!NOTE]
>  所產生 <xref:System.Data.Linq.DataContext> 方法的傳回型別，會根據預存程序或函式在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]上的置放位置而不同。 如果將項目直接放入現有的實體類別，則建立的 <xref:System.Data.Linq.DataContext> 方法會具有該實體類別的傳回型別。 如果將項目放入 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的空白區域，則建立的 <xref:System.Data.Linq.DataContext> 方法會傳回自動產生的型別。 您可以變更的傳回型別<xref:System.Data.Linq.DataContext>之後將它加入至方法窗格的方法。 若要檢查或變更的傳回型別<xref:System.Data.Linq.DataContext>方法中，選取它，然後檢查**傳回型別**屬性**屬性**視窗。 如需詳細資訊，請參閱[如何： 變更 DataContext 方法 （O/R 設計工具） 的傳回型別](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>若要建立可傳回自動產生型別的 DataContext 方法

1.  在**伺服器總管**/**資料庫總管**，依序展開**預存程序**您正在使用資料庫的節點。

2.  尋找所要的預存程序，並將它拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的空白區域。

     <xref:System.Data.Linq.DataContext>方法會透過自動產生的傳回型別，並出現在**方法**窗格。

#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>若要建立具有實體類別之傳回型別的 DataContext 方法

1.  在**伺服器總管**/**資料庫總管**，依序展開**預存程序**您正在使用資料庫的節點。

2.  尋找所要的預存程序，並將它拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的現有實體類別。

     <xref:System.Data.Linq.DataContext>方法會透過選取的實體類別的傳回型別，並出現在**方法**窗格。

> [!NOTE]
>  如需變更現有的傳回型別資訊<xref:System.Data.Linq.DataContext>方法，請參閱[如何： 變更 DataContext 方法 （O/R 設計工具） 的傳回型別](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。

## <a name="see-also"></a>另請參閱

- [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Visual Studio 中的 LINQ to SQL 工具)
- [DataContext 方法 （O/R 設計工具）](../data-tools/datacontext-methods-o-r-designer.md)
- [逐步解說： 建立 LINQ to SQL 類別](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Basic 中的 LINQ 簡介](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [C# 中的 LINQ](/dotnet/csharp/linq/linq-in-csharp)