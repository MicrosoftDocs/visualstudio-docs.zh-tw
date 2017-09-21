---
title: "HOW TO：變更 DataContext 方法的傳回型別 (O/R 設計工具) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HOW TO：變更 DataContext 方法的傳回型別 (O/R 設計工具)
<xref:System.Data.Linq.DataContext> 方法 \(根據預存程序 \(Stored Procedure\) 或函式所建立\) 的傳回型別，會隨預存程序或函式在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中的置放位置而不同。如果將項目直接放入現有的實體類別，且預存程序或函式所傳回資料的結構描述符合實體類別的型態，則建立的 <xref:System.Data.Linq.DataContext> 方法會具有該實體類別的傳回型別。如果您將項目放入 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的空白區域，則建立的 <xref:System.Data.Linq.DataContext> 方法會傳回自動產生的型別。您可以在將 <xref:System.Data.Linq.DataContext> 方法加入至方法窗格後，變更方法的傳回型別。若要檢查或變更 <xref:System.Data.Linq.DataContext> 方法的傳回型別，請選取該方法，然後按一下 \[**屬性**\] 視窗中的 \[**傳回型別**\] 屬性。  
  
> [!NOTE]
>  您不可以使用 \[**屬性**\] 視窗，將傳回型別設定為實體類別的 <xref:System.Data.Linq.DataContext> 方法還原成傳回自動產生的型別。若要將 <xref:System.Data.Linq.DataContext> 方法還原成傳回自動產生的型別，則必須再次將原始資料庫物件拖曳至 O\/R 設計工具。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### 若要將 DataContext 方法的傳回型別從自動產生的型別變更為實體類別  
  
1.  選取方法窗格中的 <xref:System.Data.Linq.DataContext> 方法。  
  
2.  選取 \[**屬性**\] 視窗中的 \[**傳回型別**\]，然後在 \[**傳回型別**\] 清單中選取可用的實體類別。如果所要的實體類別不在清單中，請在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中加入或建立它，以將它加入至清單。  
  
3.  儲存 .dbml 檔案。  
  
### 若要將 DataContext 方法的傳回型別從實體類別變更為自動產生的型別  
  
1.  選取並刪除方法窗格中的 <xref:System.Data.Linq.DataContext> 方法。  
  
2.  將資料庫物件從 \[**伺服器總管**\]\/\[**資料庫總管**\] 拖曳至 O\/R 設計工具的空白區域。  
  
3.  儲存 .dbml 檔案。  
  
## 請參閱  
 [物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext 方法 \(O\/R 設計工具\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [HOW TO：建立對應到預存程序和函式的 DataContext 方法 \(O\/R 設計工具\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)