---
title: DataCoNtext 方法（O-R 設計工具） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9d7e0eee35e0f1e62247865bd539aab8d21349d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657396"
---
# <a name="datacontext-methods-or-designer"></a>DataContext 方法 (O/R 設計工具)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataCoNtext] （assetId：///T： System.object？ qualifyHint = False & autoUpgrade = True）方法（在[Visual Studio 中 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)的內容）是在中執行預存程式和函式之 <xref:System.Data.Linq.DataContext> 類別的方法。資料.

 <xref:System.Data.Linq.DataContext> 類別是一個 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 類別，可以做為 SQL Server 資料庫與該資料庫對應之 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 實體類別之間的管道。 @No__t_0 類別包含連接字串資訊，以及用來連接到資料庫及運算元據庫中資料的方法。 根據預設，<xref:System.Data.Linq.DataContext> 類別包含數個您可以呼叫的方法，例如將更新的資料從 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 類別傳送到資料庫的 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 方法。 您也可以建立其他對應至預存程序和函式的 <xref:System.Data.Linq.DataContext> 方法。 換句話說，呼叫這些自訂方法會執行 <xref:System.Data.Linq.DataContext> 方法在資料庫中對應的預存程序或函式。 您可以將新的方法加入至 <xref:System.Data.Linq.DataContext> 類別，方式就和加入方法以擴充任何類別一樣。 不過，在討論 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 內容中的 <xref:System.Data.Linq.DataContext> 方法時，它是對應至所討論之預存程式和函式的 <xref:System.Data.Linq.DataContext> 方法。

## <a name="methods-pane"></a>方法窗格
 對應至預存程序和函式的 <xref:System.Data.Linq.DataContext> 方法會顯示在 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]的方法窗格中。 [方法] 窗格是沿著 [**實體**] 窗格（主要設計介面）側邊的窗格。 [方法] 窗格會列出您使用 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 建立的所有 <xref:System.Data.Linq.DataContext> 方法。 根據預設，[方法] 窗格是空的;將預存程式或函式從**伺服器總管**/**資料庫總管**拖曳至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 上，以建立 <xref:System.Data.Linq.DataContext> 方法並填入方法窗格。 如需詳細資訊，請參閱[如何：建立對應至預存程式和函式的 DataCoNtext 方法（O/R 設計工具）](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)。

> [!NOTE]
> 開啟並關閉 [方法] 窗格，方法是以滑鼠右鍵按一下 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]，然後按一下 [**隱藏方法窗格]** 或 [**顯示方法窗格]** ，或使用鍵盤快速鍵 CTRL + 1。

## <a name="two-types-of-datacontext-methods"></a>兩種 DataContext 方法
 DataContext 方法是指在資料庫中對應至預存程序和函式的方法。 您可以在 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]的方法窗格上，建立和加入 DataContext 方法。 <xref:System.Data.Linq.DataContext> 方法有兩種不同的類型：傳回一個或多個結果集的方法，以及不會傳回結果集的方法：

- 傳回一個或多個結果集的 <xref:System.Data.Linq.DataContext> 方法：

     如果您的應用程式只需要執行資料庫中的預存程序和函式並傳回結果，請建立這種 <xref:System.Data.Linq.DataContext> 方法。 如需詳細資訊，請參閱[如何：建立對應至預存程式和函式的 DataCoNtext 方法（O/R 設計工具）](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)、ISingleResult \<T > 和 <xref:System.Data.Linq.IMultipleResults>。

- 不會傳回結果集的 <xref:System.Data.Linq.DataContext> 方法：例如特定實體類別的插入、更新和刪除作業。

     如果您的應用程式必須執行預存程序 (而不是使用預設 <xref:System.Data.Linq.DataContext> 行為) 在實體類別與資料庫之間儲存修改過的資料，請建立這種 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 方法。 如需詳細資訊，請參閱[如何：指派預存程式來執行更新、插入和刪除（O/R 設計工具）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。

## <a name="return-types-of-datacontext-methods"></a>DataContext 方法的傳回型別
 當您將預存程式和函式從**伺服器總管**/**資料庫總管**拖曳至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 上時，所產生之 <xref:System.Data.Linq.DataContext> 方法的傳回型別會根據您放置專案的位置而有所不同。 將專案直接卸載到現有的實體類別，會使用實體類別的傳回型別來建立 <xref:System.Data.Linq.DataContext> 方法;將專案放在 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] （在任一窗格中）的空白區域，會建立傳回自動產生之類型的 <xref:System.Data.Linq.DataContext> 方法。 這個自動產生的型別，不僅名稱上會符合預存程序或函式名稱，其屬性也會對應至預存程序或函式傳回的欄位。

> [!NOTE]
> 您可以在將 <xref:System.Data.Linq.DataContext> 方法加入至方法窗格後，變更方法的傳回型別。 若要檢查或變更 <xref:System.Data.Linq.DataContext> 方法的傳回型別，請選取該方法，然後檢查 [屬性] 視窗中的 [傳回型別] 屬性。 如需詳細資訊，請參閱[如何：變更 DataCoNtext 方法的傳回型別（O/R 設計工具）](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。

 您從資料庫拖曳至 O/R 設計工具介面的物件將會根據資料庫中的物件名稱自動命名。 如果您多次拖曳相同的物件，系統就會在新名稱的結尾附加一個數字，以便區別這些名稱。 當資料庫物件名稱包含空格或是 Visual Basic 或 C# 中不支援的字元時，系統就會使用底線來取代空格或無效字元。

## <a name="see-also"></a>請參閱
 Visual Studio [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [預存程式](https://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc)[中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)[如何：建立對應至預存程式和函式的 DataCoNtext 方法（O/R 設計工具）](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) [如何：指派預存程式來執行更新、插入、和刪除（O/R 設計工具）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [逐步解說：自訂實體類別的插入、更新和刪除行為](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)[逐步解說：建立 LINQ to SQL 類別（O-R 設計工具）](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
