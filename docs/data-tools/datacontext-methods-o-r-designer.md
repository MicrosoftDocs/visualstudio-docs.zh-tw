---
title: "DataContext 方法 (O/R 設計工具) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 5
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DataContext 方法 (O/R 設計工具)
<xref:System.Data.Linq.DataContext> 方法 \(在[物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) 的內容中\) 是 <xref:System.Data.Linq.DataContext> 類別 \(Class\) 的方法，可以執行資料庫中的預存程序 \(Stored Procedure\) 和函式。  
  
 <xref:System.Data.Linq.DataContext> 類別是一個 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 類別，可以做為 SQL Server 資料庫與該資料庫對應之 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 實體類別之間的管道。<xref:System.Data.Linq.DataContext> 類別包含連接字串資訊及連接至資料庫及處理資料庫中資料的方法。根據預設，<xref:System.Data.Linq.DataContext> 類別包含多種您可以呼叫的方法，例如 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 方法，該方法會傳送 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 類別的更新資料至資料庫。您也可以建立其他對應至預存程序和函式的 <xref:System.Data.Linq.DataContext> 方法。換句話說，呼叫這些自訂方法會執行 <xref:System.Data.Linq.DataContext> 方法在資料庫中對應的預存程序或函式。您可以將新的方法加入至 <xref:System.Data.Linq.DataContext> 類別，方式就和加入方法以擴充任何類別一樣。不過，在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的內容中討論 <xref:System.Data.Linq.DataContext> 方法時，主要是在討論對應至預存程序和函式的 <xref:System.Data.Linq.DataContext> 方法。  
  
> [!NOTE]
>  在 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 中，是以相同的方式來處理預存程序和函式，因此預存程序和函式都是使用相同的 <xref:System.Data.Linq.StoredProcedureAttribute> 對應至實體類別。在 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 的內容中，對應至預存程序與對應至函式的 <xref:System.Data.Linq.DataContext> 方法相同。  
  
## 方法窗格  
 對應至預存程序和函式的 <xref:System.Data.Linq.DataContext> 方法會顯示在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的方法窗格中。方法窗格是與 \[**實體**\] 窗格 \(主設計介面\) 相鄰的窗格。方法窗格會列出所有已使用 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]建立的 <xref:System.Data.Linq.DataContext> 方法。方法窗格預設是空的。將預存程序或函式從 \[**伺服器總管**\]\/\[**資料庫總管**\] 拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，就可以建立 <xref:System.Data.Linq.DataContext> 方法並將其填入 \(Populate\) 方法窗格中。如需詳細資訊，請參閱 [HOW TO：建立對應到預存程序和函式的 DataContext 方法 \(O\/R 設計工具\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)。  
  
> [!NOTE]
>  開啟和關閉方法窗格的方式有兩種：一種是以滑鼠右鍵按一下 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，然後按一下 \[**隱藏方法窗格**\] 或 \[**顯示方法窗格**\]，另一種是使用鍵盤快速鍵 CTRL\+1。  
  
## 兩種 DataContext 方法  
 DataContext 方法是指在資料庫中對應至預存程序和函式的方法。您可以在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的方法窗格上，建立和加入 DataContext 方法。<xref:System.Data.Linq.DataContext> 方法有兩種不同的類型：傳回一個或多個結果集的方法，以及不會傳回結果集的方法：  
  
-   傳回一個或多個結果集的 <xref:System.Data.Linq.DataContext> 方法：  
  
     如果您的應用程式只需要執行資料庫中的預存程序和函式並傳回結果，請建立這種 <xref:System.Data.Linq.DataContext> 方法。如需詳細資訊，請參閱 [HOW TO：建立對應到預存程序和函式的 DataContext 方法 \(O\/R 設計工具\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)、<xref:System.Data.Linq.ISingleResult%271> 和 <xref:System.Data.Linq.IMultipleResults>。  
  
-   不會傳回結果集的 <xref:System.Data.Linq.DataContext> 方法：例如特定實體類別的插入、更新和刪除作業。  
  
     如果您的應用程式必須執行預存程序 \(而不是使用預設 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 行為\) 在實體類別與資料庫之間儲存修改過的資料，請建立這種 <xref:System.Data.Linq.DataContext> 方法。如需詳細資訊，請參閱 [HOW TO：指派預存程序來執行更新、插入和刪除 \(O\/R 設計工具\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。  
  
## DataContext 方法的傳回型別  
 將預存程序和函式從 \[**伺服器總管**\]\/\[**資料庫總管**\] 拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]時，所產生 <xref:System.Data.Linq.DataContext> 方法的傳回型別會根據項目的置放位置而不同。如果直接將項目放入現有的實體類別，則建立的 <xref:System.Data.Linq.DataContext> 方法會具有該實體類別的傳回型別，如果將項目放入 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]任一窗格的空白區域中，則建立的 <xref:System.Data.Linq.DataContext> 方法會傳回自動產生的型別。這個自動產生的型別，不僅名稱上會符合預存程序或函式名稱，其屬性也會對應至預存程序或函式傳回的欄位。  
  
> [!NOTE]
>  您可以在將 <xref:System.Data.Linq.DataContext> 方法加入至方法窗格後，變更方法的傳回型別。若要檢查或變更 <xref:System.Data.Linq.DataContext> 方法的傳回型別，請選取該方法，然後檢查 \[**屬性**\] 視窗中的 \[**傳回型別**\] 屬性。如需詳細資訊，請參閱 [HOW TO：變更 DataContext 方法的傳回型別 \(O\/R 設計工具\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。  
  
 您從資料庫拖曳至 O\/R 設計工具介面的物件將會根據資料庫中的物件名稱自動命名。如果您多次拖曳相同的物件，系統就會在新名稱的結尾附加一個數字，以便區別這些名稱。當資料庫物件名稱包含空格或是 Visual Basic 或 C\# 中不支援的字元時，系統就會使用底線來取代空格或無效字元。  
  
## 請參閱  
 [物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [預存程序](../Topic/Stored%20Procedures.md)   
 [HOW TO：建立對應到預存程序和函式的 DataContext 方法 \(O\/R 設計工具\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [HOW TO：指派預存程序來執行更新、插入和刪除 \(O\/R 設計工具\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [逐步解說：自訂實體類別的插入、更新和刪除行為](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [逐步解說：建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)