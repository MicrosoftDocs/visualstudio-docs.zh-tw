---
title: "無法刪除屬性 &lt;屬性名稱&gt;，因為它正參與關聯 &lt;關聯名稱&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 無法刪除屬性 &lt;屬性名稱&gt;，因為它正參與關聯 &lt;關聯名稱&gt;
選取的屬性已設定為在錯誤訊息指出的類別 \(Class\) 之間進行關聯時，所需的 \[**關聯屬性**\]。如果屬性已參與資料類別之間的關聯，就無法刪除屬性。  
  
 將 \[**關聯屬性**\] 設定為資料類別的不同屬性，就可以成功刪除要刪的屬性。  
  
### 若要更正這個錯誤  
  
1.  在 O\/R Designer 上，選取在錯誤訊息指出的資料類別之間連接的關聯線。  
  
2.  按兩下這條線以開啟 \[**關聯編輯器**\] 對話方塊。  
  
3.  從 \[**關聯屬性**\] 中移除屬性。  
  
4.  試著再次刪除屬性。  
  
## 請參閱  
 [O\/R 設計工具概觀](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [HOW TO：在 LINQ to SQL 類別之間建立關聯 \(關聯性\) \(O\/R 設計工具\)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [逐步解說：建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)