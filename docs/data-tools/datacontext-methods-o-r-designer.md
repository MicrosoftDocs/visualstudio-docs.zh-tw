---
title: "DataContext 方法 （O R 設計工具） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 5eb37bd3abbf88b04bed0d382e07abe4379eb661
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="datacontext-methods-or-designer"></a>DataContext 方法 (O/R 設計工具)
<xref:System.Data.Linq.DataContext>方法 (的內容中[LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) 是方法<xref:System.Data.Linq.DataContext>在資料庫中執行預存程序和函式的類別。  
  
 <xref:System.Data.Linq.DataContext> 類別是一個 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 類別，可以做為 SQL Server 資料庫與該資料庫對應之 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 實體類別之間的管道。 <xref:System.Data.Linq.DataContext>類別包含連接字串資訊和連線到資料庫及操作資料庫中的資料的方法。 根據預設，<xref:System.Data.Linq.DataContext>類別包含數種方法，您可以呼叫，例如<xref:System.Data.Linq.DataContext.SubmitChanges%2A>方法傳送更新的資料從[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]資料庫的類別。 您也可以建立其他<xref:System.Data.Linq.DataContext>方法對應至預存程序和函式。 換句話說，呼叫這些自訂方法會執行 <xref:System.Data.Linq.DataContext> 方法在資料庫中對應的預存程序或函式。 您可以將新的方法加入至 <xref:System.Data.Linq.DataContext> 類別，方式就和加入方法以擴充任何類別一樣。 不過，在討論<xref:System.Data.Linq.DataContext>方法的內容中[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，它是<xref:System.Data.Linq.DataContext>對應至預存程序和函式是在討論的方法。  
  
## <a name="methods-pane"></a>方法窗格  
 對應至預存程序和函式的 <xref:System.Data.Linq.DataContext> 方法會顯示在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的方法窗格中。 方法窗格是邊的窗格**實體**窗格 （主設計介面）。 方法窗格會列出所有<xref:System.Data.Linq.DataContext>方法建立使用[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。 根據預設，方法窗格是空的。拖曳預存程序或函式從**伺服器總管**/**資料庫總管**到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]建立<xref:System.Data.Linq.DataContext>方法，並填入方法窗格。 如需詳細資訊，請參閱[How to： 建立 DataContext 方法對應至預存程序和函式 （O/R 設計工具）](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)。  
  
> [!NOTE]
>  開啟和關閉方法窗格，以滑鼠右鍵按一下[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，然後按一下 **隱藏方法窗格**或**顯示方法窗格**，或使用鍵盤快速鍵 CTRL + 1。  
  
## <a name="two-types-of-datacontext-methods"></a>兩種 DataContext 方法  
 DataContext 方法是指在資料庫中對應至預存程序和函式的方法。 您可以在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的方法窗格上，建立和加入 DataContext 方法。 有兩種不同類型<xref:System.Data.Linq.DataContext>方法; 傳回一或多個結果集，以及不這麼做：  
  
-   傳回一個或多個結果集的 <xref:System.Data.Linq.DataContext> 方法：  
  
     如果您的應用程式只需要執行資料庫中的預存程序和函式並傳回結果，請建立這種 <xref:System.Data.Linq.DataContext> 方法。 如需詳細資訊，請參閱[How to： 建立 DataContext 方法對應至預存程序和函式 （O/R 設計工具）](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)，System.Data.Linq.ISingleResult\<T >，並<xref:System.Data.Linq.IMultipleResults>。  
  
-   不會傳回結果集的 <xref:System.Data.Linq.DataContext> 方法：例如特定實體類別的插入、更新和刪除作業。  
  
     建立這種<xref:System.Data.Linq.DataContext>方法，當您的應用程式都必須執行預存程序，而不是使用預設[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]行為儲存修改的實體類別與資料庫之間的資料。 如需詳細資訊，請參閱[如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。  
  
## <a name="return-types-of-datacontext-methods"></a>DataContext 方法的傳回型別  
 當您拖曳預存程序和函式從**伺服器總管**/**資料庫總管**拖曳至[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，產生的傳回型別<xref:System.Data.Linq.DataContext>方法視您卸除項目。 卸除的項目直接放入現有的實體類別建立<xref:System.Data.Linq.DataContext>方法的實體類別的傳回型別，則卸除項目拖曳到空白區域[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]（任一窗格） 中建立<xref:System.Data.Linq.DataContext>方法會傳回自動產生的型別。 這個自動產生的型別，不僅名稱上會符合預存程序或函式名稱，其屬性也會對應至預存程序或函式傳回的欄位。  
  
> [!NOTE]
>  您可以在將 <xref:System.Data.Linq.DataContext> 方法加入至方法窗格後，變更方法的傳回型別。 若要檢查或變更的傳回型別<xref:System.Data.Linq.DataContext>方法中，選取它，然後檢查**傳回型別**屬性**屬性**視窗。 如需詳細資訊，請參閱[如何： 變更 DataContext 方法 （O/R 設計工具） 的傳回型別](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。  
  
 您從資料庫拖曳至 O/R 設計工具介面的物件將會根據資料庫中的物件名稱自動命名。 如果您多次拖曳相同的物件，系統就會在新名稱的結尾附加一個數字，以便區別這些名稱。 當資料庫物件名稱包含空格或是 Visual Basic 或 C# 中不支援的字元時，系統就會使用底線來取代空格或無效字元。  
  
## <a name="see-also"></a>請參閱  
 [LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [預存程序](/dotnet/framework/data/adonet/sql/linq/stored-procedures)   
 [如何： 建立對應至預存程序和函式 （O/R 設計工具） 的 DataContext 方法](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [逐步解說： 自訂插入、 更新和刪除實體類別的行為](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [逐步解說： 建立 LINQ to SQL 類別 （O R 設計工具）](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)