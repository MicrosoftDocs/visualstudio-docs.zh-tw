---
title: DataContext 方法 （O-R 設計工具）
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3d8e3a39c79b5dee339c8835c78143277f3015f6
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756125"
---
# <a name="datacontext-methods-or-designer"></a>DataContext 方法 (O/R 設計工具)

<xref:System.Data.Linq.DataContext> 方法 (中的內容[LINQ to SQL 工具，在 Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) 方法的<xref:System.Data.Linq.DataContext>的資料庫中執行預存程序和函式的類別。

<xref:System.Data.Linq.DataContext> 類別是一個 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 類別，可以做為 SQL Server 資料庫與該資料庫對應之 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 實體類別之間的管道。 <xref:System.Data.Linq.DataContext>類別包含連接字串資訊和連線到資料庫及操作資料庫中的資料的方法。 根據預設，<xref:System.Data.Linq.DataContext>類別包含數種方法，您可以呼叫，例如<xref:System.Data.Linq.DataContext.SubmitChanges%2A>方法，會傳送更新的資料從[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]類別至資料庫。 您也可以建立其他<xref:System.Data.Linq.DataContext>對應至預存程序和函式的方法。 換句話說，呼叫這些自訂的方法執行預存程序或函式在資料庫中的<xref:System.Data.Linq.DataContext>方法對應。 您可以將新的方法加入至 <xref:System.Data.Linq.DataContext> 類別，方式就和加入方法以擴充任何類別一樣。 不過，在討論<xref:System.Data.Linq.DataContext>的內容中的方法**O/R Designer**，它是<xref:System.Data.Linq.DataContext>對應至預存程序和函式是在討論的方法。

## <a name="methods-pane"></a>方法窗格

<xref:System.Data.Linq.DataContext> 對應至預存程序和函式的方法會顯示在**方法**窗格**O/R Designer**。 **方法** 窗格是相鄰的窗格**實體**窗格 （主設計介面）。 **方法**窗格會列出所有<xref:System.Data.Linq.DataContext>方法，使用您建立**O/R Designer**。 根據預設，**方法** 窗格是空的將預存程序或函式從**伺服器總管**或**資料庫總管**拖曳至**O/R 設計工具**來建立<xref:System.Data.Linq.DataContext>方法並填入**方法**窗格。 如需詳細資訊，請參閱 <<c0> [ 如何： 對應至預存程序和函式 （O/R 設計工具） 建立 DataContext 方法](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)。

> [!NOTE]
> 開啟和關閉方法窗格，以滑鼠右鍵按一下**O/R Designer** ，然後按一下**隱藏方法窗格**或是**顯示方法窗格**，或使用鍵盤快速鍵**CTRL**+**1**。

## <a name="two-types-of-datacontext-methods"></a>兩種類型的 DataContext 方法

DataContext 方法是指在資料庫中對應至預存程序和函式的方法。 您可以建立和加入 DataContext 方法上**方法**窗格**O/R Designer**。 有兩種不同類型<xref:System.Data.Linq.DataContext>方法，傳回一或多個結果集，以及不這麼做：

-   傳回一個或多個結果集的 <xref:System.Data.Linq.DataContext> 方法：

     如果您的應用程式只需要執行資料庫中的預存程序和函式並傳回結果，請建立這種 <xref:System.Data.Linq.DataContext> 方法。 如需詳細資訊，請參閱 <<c0> [ 如何： 對應至預存程序和函式 （O/R 設計工具） 建立 DataContext 方法](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)，System.Data.Linq.ISingleResult\<T >，並<xref:System.Data.Linq.IMultipleResults>。

-   不會傳回結果集的 <xref:System.Data.Linq.DataContext> 方法：例如特定實體類別的插入、更新和刪除作業。

     建立這種<xref:System.Data.Linq.DataContext>方法時您的應用程式必須執行預存程序，而不是使用預設[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]行為儲存修改的實體類別與資料庫之間的資料。 如需詳細資訊，請參閱 <<c0> [ 如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。

## <a name="return-types-of-datacontext-methods"></a>DataContext 方法的傳回型別

當您將預存程序和函式從**伺服器總管**或**資料庫總管**拖曳至**O/R 設計工具**，所產生的傳回類型<xref:System.Data.Linq.DataContext>方法會依據您卸除項目而有所不同。 卸除現有的實體類別的直接放入的項目會建立<xref:System.Data.Linq.DataContext>傳回的型別實體類別的方法，卸除項目拖曳到空白區域**O/R Designer** （在其中一個窗格中） 會建立<xref:System.Data.Linq.DataContext>方法傳回自動產生的型別。 自動產生的型別具有名稱符合預存程序或函式名稱和屬性，對應至預存程序或函式所傳回的欄位。

> [!NOTE]
> 您可以在將 <xref:System.Data.Linq.DataContext> 方法加入至方法窗格後，變更方法的傳回型別。 若要檢查或變更的傳回型別<xref:System.Data.Linq.DataContext>方法中，選取它，並檢查**傳回型別**中的屬性**屬性**視窗。 如需詳細資訊，請參閱 <<c0> [ 如何： 變更 DataContext 方法 （O/R 設計工具） 的傳回型別](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。

您從資料庫拖曳至 O/R 設計工具介面上拖曳的物件會自動命名，根據資料庫中物件的名稱。 如果您多次拖曳相同的物件，會新增一個號碼，以便區別這些名稱的新名稱的結尾。 當資料庫物件名稱包含空格或是 Visual Basic 或 C# 中不支援的字元時，系統就會使用底線來取代空格或無效字元。

## <a name="see-also"></a>另請參閱

- [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [預存程序](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [如何： 建立對應至預存程序和函式 （O/R 設計工具） 的 DataContext 方法](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [逐步解說：自訂實體類別的插入、更新和刪除行為](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [逐步解說： 建立 LINQ to SQL 類別 （O-R 設計工具）](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)