---
title: "HOW TO：使用 O/R 設計工具設定繼承 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 4
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HOW TO：使用 O/R 設計工具設定繼承
[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) 通常是在關聯式系統中實作，因此支援單一資料表繼承概念。在單一資料表繼承中，單一資料庫資料表的欄位會同時包含父代資訊和子系資訊。使用關聯式資料時，鑑別子資料行所含的值會決定任何記錄所屬的類別 \(Class\)。  
  
 例如，假設有個 Persons 資料表包含某家公司雇用的所有人員。有些人是員工，而有些人是經理。這個 Persons 資料表包含一個名為 `EmployeeType` 的資料行 \(其中值 1 代表經理，值 2 代表員工\)，這就是鑑別子資料行。在這個案例中，您可以建立員工子類別 \(Subclass\)，並且只將 `EmployeeType` 值為 2 的記錄填入 \(Populate\) 這個類別。您也可以從每個類別中移除不適用的資料行。  
  
 建立使用繼承的物件模型 \(並對應至關聯式資料\) 在過程上較為複雜。下列程序將會說明使用 O\/R 設計工具設定繼承的必要步驟。因為在不參考現有資料表和資料行的情況下遵循這些泛型步驟，將是一件困難的事，所以提供了使用資料的逐步解說。如需使用 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]設定繼承的詳細逐步指示，請參閱[逐步解說：使用單一資料表繼承建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)。  
  
### 若要建立繼承的資料類別  
  
1.  將 \[**LINQ to SQL 類別**\] 項目加入至現有 Visual Basic 或 C\# 專案，以開啟 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。  
  
2.  將想要當成基底類別 \(Base Class\) 的資料表拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。  
  
3.  將這個資料表複製一份複本並拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，然後將它重新命名。這就是衍生類別 \(Derived Class\) 或子類別。  
  
4.  在 \[**工具箱**\] 的 \[**物件關聯式設計工具**\] 索引標籤中按一下 \[**繼承**\]，然後按一下子類別 \(重新命名的資料表\)，將它連接至基底類別。  
  
    > [!NOTE]
    >  按一下 \[**工具箱**\] 中的 \[**繼承**\] 項目，然後放開滑鼠按鍵、按一下在步驟 3 中建立的第二個類別複本，再按一下在步驟 2 中建立的第一個類別。繼承線的箭號會指向第一個類別。  
  
5.  在每個類別中，刪除任何不想要顯示而且沒有用於關聯的物件屬性。如果您嘗試刪除用於關聯的物件屬性，就會收到錯誤：[無法刪除屬性 \<屬性名稱\>，因為它正參與關聯 \<關聯名稱\>](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md)。  
  
    > [!NOTE]
    >  因為衍生類別會繼承其基底類別中定義的屬性，所以這兩個類別中不可以定義相同的資料行 \(資料行是以屬性形式實作\)。在基底類別的屬性上設定 \[繼承修飾詞\]，就可以啟用衍生類別中的資料行建立作業。如需詳細資訊，請參閱[NOT IN BUILD: Overriding Properties and Methods](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)。  
  
6.  選取 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中的繼承線。  
  
7.  在 \[**屬性**\] 視窗中，將 \[**鑑別子屬性**\] 設定為類別中用於辨別記錄的資料行名稱。  
  
8.  將 \[**衍生類別鑑別子值**\] 屬性設定為資料庫中將記錄指定為繼承型別的值 \(這是儲存在鑑別子資料行中，用於指定繼承類別的值\)。  
  
9. 將 \[**基底類別鑑別子值**\] 屬性設定為將記錄指定為基底類型的值 \(這是儲存在鑑別子資料行中，用於指定基底類別的值\)。  
  
10. 您也可以選擇設定 \[**繼承預設值**\] 屬性，以指定當載入的資料列不符合任何既定的繼承程式碼時，要依繼承階層架構 \(Inheritance Hierarchy\) 使用的型別。換句話說，如果記錄的鑑別子資料行值不符合 \[**衍生類別鑑別子值**\] 或 \[**基底類別鑑別子值**\] 屬性值，就會以指定為 \[**繼承預設值**\] 的型別載入記錄。  
  
## 請參閱  
 [O\/R 設計工具概觀](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [逐步解說：建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [PAVE What's New for Data Application Development in Visual Studio 2012](http://msdn.microsoft.com/zh-tw/3d50d68f-5f44-4915-842f-6d42fce793f1)   
 [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [逐步解說：使用單一資料表繼承建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [NOT IN BUILD: Inheritance in Visual Basic](http://msdn.microsoft.com/zh-tw/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [繼承](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)