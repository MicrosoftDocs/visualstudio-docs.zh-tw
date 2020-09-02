---
title: DataCoNtext 方法 (O-R 設計工具) |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657396"
---
# <a name="datacontext-methods-or-designer"></a>DataContext 方法 (O/R 設計工具)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataCoNtext] (assetId:///T:System.Data.Linq.DataCoNtext?qualifyHint=False&autoUpgrade = True) 方法 (在 LINQ to SQL 中的 [Visual Studio 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md) 的內容中，是在資料庫中 <xref:System.Data.Linq.DataContext> 執行預存程式和函數之類別的方法。

 <xref:System.Data.Linq.DataContext> 類別是一個 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 類別，可以做為 SQL Server 資料庫與該資料庫對應之 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 實體類別之間的管道。 <xref:System.Data.Linq.DataContext>類別包含連接字串資訊，以及連接到資料庫並運算元據庫中資料的方法。 根據預設， <xref:System.Data.Linq.DataContext> 類別包含數個您可以呼叫的方法，例如將 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 更新的資料從 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 類別傳送至資料庫的方法。 您也可以建立其他對應至預存程序和函式的 <xref:System.Data.Linq.DataContext> 方法。 換句話說，呼叫這些自訂方法會執行 <xref:System.Data.Linq.DataContext> 方法在資料庫中對應的預存程序或函式。 您可以將新的方法加入至 <xref:System.Data.Linq.DataContext> 類別，方式就和加入方法以擴充任何類別一樣。 不過，在的 <xref:System.Data.Linq.DataContext> 內容中，有關方法的討論 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 是 <xref:System.Data.Linq.DataContext> 對應至所討論之預存程式和函式的方法。

## <a name="methods-pane"></a>方法窗格
 <xref:System.Data.Linq.DataContext> 對應至預存程式和函數的方法會顯示在的 [方法] 窗格中 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 。 [方法] 窗格是 [ **實體** ] 窗格旁邊的窗格， (主要設計介面) 。 [方法] 窗格會列出 <xref:System.Data.Linq.DataContext> 您使用建立的所有方法 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 。 依預設，[方法] 窗格是空的;將預存程式或函式從**伺服器總管** / **資料庫總管**拖曳至， [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 以建立 <xref:System.Data.Linq.DataContext> 方法並填入方法窗格。 如需詳細資訊，請參閱 [如何：建立對應至預存程式和函式的 DataCoNtext 方法 (O/R 設計工具) ](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)。

> [!NOTE]
> 開啟並關閉方法窗格，方法是以滑鼠右鍵按一下 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ，然後按一下 [ **隱藏方法** 窗格] 或 [ **顯示方法窗格]**，或使用鍵盤快速鍵 CTRL + 1。

## <a name="two-types-of-datacontext-methods"></a>兩種 DataContext 方法
 DataContext 方法是指在資料庫中對應至預存程序和函式的方法。 您可以在 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]的方法窗格上，建立和加入 DataContext 方法。 <xref:System.Data.Linq.DataContext> 方法有兩種不同的類型：傳回一個或多個結果集的方法，以及不會傳回結果集的方法：

- 傳回一個或多個結果集的 <xref:System.Data.Linq.DataContext> 方法：

     如果您的應用程式只需要執行資料庫中的預存程序和函式並傳回結果，請建立這種 <xref:System.Data.Linq.DataContext> 方法。 如需詳細資訊，請參閱 [如何：建立對應至預存程式和函式的 DataCoNtext 方法 (O/R 設計工具) ](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)、ISingleResult \<T> 和 <xref:System.Data.Linq.IMultipleResults> 。

- 不會傳回結果集的 <xref:System.Data.Linq.DataContext> 方法：例如特定實體類別的插入、更新和刪除作業。

     如果您的應用程式必須執行預存程序 (而不是使用預設 <xref:System.Data.Linq.DataContext> 行為) 在實體類別與資料庫之間儲存修改過的資料，請建立這種 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 方法。 如需詳細資訊，請參閱 [如何：指派預存程式來執行更新、插入和刪除 (O/R 設計工具) ](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。

## <a name="return-types-of-datacontext-methods"></a>DataContext 方法的傳回型別
 當您將預存程式和函式從**伺服器總管** / **資料庫總管**拖曳至時 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ，所產生方法的傳回型別會 <xref:System.Data.Linq.DataContext> 根據您放置專案的位置而有所不同。 直接將專案放入現有的實體類別時，會建立 <xref:System.Data.Linq.DataContext> 具有實體類別之傳回類型的方法; 將專案放到 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 任一個窗格中的 (空白區域，) <xref:System.Data.Linq.DataContext> 會建立傳回自動產生之類型的方法。 這個自動產生的型別，不僅名稱上會符合預存程序或函式名稱，其屬性也會對應至預存程序或函式傳回的欄位。

> [!NOTE]
> 您可以在將 <xref:System.Data.Linq.DataContext> 方法加入至方法窗格後，變更方法的傳回型別。 若要檢查或變更 <xref:System.Data.Linq.DataContext> 方法的傳回型別，請選取該方法，然後檢查 [屬性]**** 視窗中的 [傳回型別]**** 屬性。 如需詳細資訊，請參閱 [如何：變更 DataCoNtext 方法的傳回類型 (O/R 設計工具) ](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。

 您從資料庫拖曳至 O/R 設計工具介面的物件將會根據資料庫中的物件名稱自動命名。 如果您多次拖曳相同的物件，系統就會在新名稱的結尾附加一個數字，以便區別這些名稱。 當資料庫物件名稱包含空格或是 Visual Basic 或 C# 中不支援的字元時，系統就會使用底線來取代空格或無效字元。

## <a name="see-also"></a>另請參閱
 Visual Studio [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [預存程式](https://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc)[中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)[如何：建立對應至預存程式和函式的 DataCoNtext 方法 (o/r 設計工具) ](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) [如何：指派預存程式來執行更新、插入和刪除 (O/r 設計](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)工具) [逐步解說：自訂實體類別的插入、更新和刪除行為](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)逐步解說[：建立 LINQ to SQL 類別 (O-R 設計工具) ](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
