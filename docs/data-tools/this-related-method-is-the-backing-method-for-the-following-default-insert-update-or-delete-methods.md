---
title: "此關聯方法是下列預設插入、更新或刪除方法的支援方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 此關聯方法是下列預設插入、更新或刪除方法的支援方法
此關聯方法是下列預設插入、更新或刪除方法的備份方法。如果刪除它，這些方法也會被刪除。是否要繼續?  
  
 選取的 `DataContext` 方法目前是當成 O\/R 設計工具上某個實體類別 \(Class\) 的插入、更新或刪除方法。刪除選取的方法會將使用這個方法的實體類別，還原成在更新期間執行插入、更新或刪除作業的預設執行階段行為。  
  
### 若要刪除選取的方法以讓實體類別使用執行階段更新  
  
-   按一下 \[**是**\]。  
  
     會刪除選取的方法，而且任何使用這個方法覆寫更新行為的類別都會還原成使用預設 LINQ to SQL 執行階段行為。  
  
### 若要關閉訊息方塊並保留選取的方法  
  
-   按一下 \[**否**\]。  
  
     會關閉訊息方塊，不進行任何變更。  
  
## 請參閱  
 [DataContext 方法 \(O\/R 設計工具\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [HOW TO：指派預存程序來執行更新、插入和刪除 \(O\/R 設計工具\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [O\/R 設計工具概觀](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)