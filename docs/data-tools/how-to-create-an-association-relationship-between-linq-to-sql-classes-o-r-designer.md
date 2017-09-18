---
title: "HOW TO：在 LINQ to SQL 類別之間建立關聯 (關聯性) (O/R 設計工具) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HOW TO：在 LINQ to SQL 類別之間建立關聯 (關聯性) (O/R 設計工具)
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 中實體類別 \(Class\) 之間的關聯，與資料庫中資料表之間的關聯性 \(Relationship\) 類似。您可以使用 \[**關聯編輯器**\] 對話方塊建立實體類別之間的關聯。  
  
 使用 \[**關聯編輯器**\] 對話方塊建立關聯時，必須選取父類別和子類別。父類別是包含主索引鍵的實體類別，而子類別是包含外部索引鍵的實體類別。例如，如果要建立與 Northwind 的 Customers 和 Orders 資料表對應的實體類別，則 Customer 類別會是父類別，而 Order 類別會是子類別。  
  
> [!NOTE]
>  將資料表從 \[**伺服器總管**\]\/\[**資料庫總管**\] 拖曳至[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) 時，會自動根據資料庫中的現有外部索引鍵關聯性建立關聯。  
  
 建立關聯之後，當您在 O\/R Designer 中選取該關聯時，\[**屬性**\] 視窗中會出現一些可設定的屬性 \(關聯就是相關類別之間的線條\)。下表提供關聯屬性的說明。  
  
|屬性|描述|  
|--------|--------|  
|**基數**|控制關聯是一對多還是一對一。|  
|**子屬性**|指定是否要在父代 \(Parent\) 上建立屬性，這個屬性是位於關聯的外部索引鍵端上之子記錄的集合或參考。例如，在 Customer 與 Order 之間的關聯中，如果 \[**子屬性**\] 設定為 \[**True**\]，則父類別上會建立名為 Orders 的屬性。|  
|**父屬性**|子類別上參考相關父類別的屬性。例如，在 Customer 與 Order 之間的關聯中，Order 類別上會建立名為 Customer 的屬性，以參考與訂單關聯的客戶。|  
|**參與屬性**|顯示關聯屬性，並提供省略按鈕 \(**...**\) 來重新開啟 \[**關聯編輯器**\] 對話方塊。|  
|**唯一**|指定外部目標資料行是否具有唯一性條件約束 \(Constraint\)。|  
  
### 若要在實體類別之間建立關聯  
  
1.  以滑鼠右鍵按一下代表關聯中之父類別的實體類別，並指向 \[**加入**\]，然後按一下 \[**關聯**\]。  
  
2.  確認 \[**關聯編輯器**\] 對話方塊中選取的是正確的 \[**父類別**\]。  
  
3.  選取下拉式方塊中的 \[**子類別**\]。  
  
4.  選取使類別互相關聯的 \[**關聯屬性**\]。通常，這會對應至資料庫中定義的外部索引鍵關聯性。例如，在 Customers 與 Orders 的關聯中，\[**關聯屬性**\] 是這兩個類別的 CustomerID。  
  
5.  按一下 \[**確定**\] 建立關聯。  
  
## 請參閱  
 [O\/R 設計工具概觀](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [逐步解說：建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext 方法 \(O\/R 設計工具\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [HOW TO：表示主索引鍵](../Topic/How%20to:%20Represent%20Primary%20Keys.md)