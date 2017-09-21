---
title: "逐步解說：使用單一資料表繼承建立 LINQ to SQL 類別 (O/R 設計工具) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 4
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：使用單一資料表繼承建立 LINQ to SQL 類別 (O/R 設計工具)
[物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) 通常是在關聯式系統中實作，因此支援單一資料表繼承。這個逐步解說以 [HOW TO：使用 O\/R 設計工具設定繼承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) 主題中提供的泛型步驟為基礎，提供一些實際資料來示範 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中的繼承用法。  
  
 在這個逐步解說中，您將執行下列工作：  
  
-   建立資料庫資料表，並在其中加入資料。  
  
-   建立 Windows Form 應用程式。  
  
-   將 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 檔案加入至專案。  
  
-   建立新的實體類別。  
  
-   設定實體類別以使用繼承。  
  
-   查詢繼承的類別。  
  
-   將資料顯示在 Windows Form 上。  
  
## 建立要繼承的來源資料表  
 若要查看繼承的運作方式，請建立小型 Person 資料表、將它當成基底類別 \(Base Class\)，然後建立繼承自它的 Employee 物件。  
  
#### 若要建立用來示範繼承的基底資料表  
  
1.  在 \[**伺服器總管**\/**資料庫總管**\] 中，以滑鼠右鍵按一下 \[**資料表**\] 節點，然後按一下 \[**加入新的資料表**\]。  
  
    > [!NOTE]
    >  您可以使用 Northwind 資料庫，或其他可以在其中加入資料表的任何資料庫。  
  
2.  在 \[資料表設計工具\] 中，將下列資料行加入至資料表：  
  
    |資料行名稱|資料型別|允許 Null|  
    |-----------|----------|-------------|  
    |ID|int|False|  
    |型別|int|True|  
    |FirstName|nvarchar\(200\)|False|  
    |LastName|nvarchar\(200\)|False|  
    |Manager|int|True|  
  
3.  將 ID 資料行設定為主索引鍵。  
  
4.  儲存資料表，並將它命名為 Person。  
  
## 將資料加入至資料表  
 為了能夠確認繼承的設定是否正確，單一資料表繼承中的每個類別都需要在資料表中有一些資料。  
  
#### 若要加入資料至資料表  
  
1.  在資料檢視中開啟資料表 \(以滑鼠右鍵按一下 \[**伺服器總管**\]\/\[**資料庫總管**\] 中的 \[**Person**\] 資料表，然後按一下 \[**顯示資料表資料**\]\)。  
  
2.  將下列資料複製至資料表 \(您可以在[Results Pane](http://msdn.microsoft.com/zh-tw/3c712f20-7c9f-4021-b1ac-fdc6f534c95a)中選取整個資料列，然後將它複製並貼上至資料表中\)。  
  
    ||||||  
    |-|-|-|-|-|  
    |ID|型別|FirstName|LastName|Manager|  
    |1|1|Anne|Wallace|NULL|  
    |2|1|Carlos|Grilo|NULL|  
    |3|1|Yael|Peled|NULL|  
    |4|2|Gatis|Ozolins|1|  
    |5|2|Andreas|Hauser|1|  
    |6|2|Tiffany|Phuvasate|1|  
    |7|2|Alexey|Orekhov|2|  
    |8|2|Michał|Poliszkiewicz|2|  
    |9|2|Tai|Yee|2|  
    |10|2|Fabricio|Noriega|3|  
    |11|2|Mindy|Martin|3|  
    |12|2|Ken|Kwok|3|  
  
## 建立新專案  
 現在您已建立好資料表，請建立新的專案來示範如何設定繼承。  
  
#### 若要建立新的 Windows 應用程式  
  
1.  從 \[**檔案**\] 功能表中，建立新專案。  
  
2.  將專案命名為 InheritanceWalkthrough。  
  
    > [!NOTE]
    >  Visual Basic 和 C\# 專案都支援 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。請以其中一種語言建立新的專案。  
  
3.  按一下 \[**Windows Form 應用程式**\] 範本，然後按一下 \[**確定**\]。如需詳細資訊，請參閱[用戶端應用程式](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
4.  InheritanceWalkthrough 專案已建立並加入至 \[**方案總管**\] 中。  
  
## 將 LINQ to SQL 類別檔案加入至專案  
  
#### 若要將 LINQ to SQL 檔案加入至專案  
  
1.  按一下 \[**專案**\] 功能表上的 \[**加入新項目**\]。  
  
2.  按一下 \[**LINQ to SQL 類別**\] 範本，然後按一下 \[**加入**\]。  
  
     .dbml 檔案隨即加入至專案，並開啟 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。  
  
## 使用 O\/R 設計工具建立繼承  
 設定繼承的方法是將 \[**繼承**\] 物件從 \[**工具箱**\] 拖曳至設計介面。  
  
#### 若要建立繼承  
  
1.  在 \[**伺服器總管**\]\/\[**資料庫總管**\] 中，巡覽至先前所建立的 \[**Person**\] 資料表。  
  
2.  將 \[**Person**\] 資料表拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]設計介面。  
  
3.  將第二個 \[**Person**\] 資料表拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，並將它的名稱變更為 Employee。  
  
4.  從 \[**Person**\] 物件中刪除 \[**Manager**\] 屬性。  
  
5.  從 \[**Employee**\] 物件中刪除 \[**Type**\]、\[**ID**\]、\[**FirstName**\] 和 \[**LastName**\] 屬性 \(換句話說，請刪除 \[**Manager**\] 以外的所有屬性\)。  
  
6.  從 \[**工具箱**\] 的 \[**物件關連式設計工具**\] 索引標籤中，在 \[**Person**\] 與 \[**Employee**\] 物件之間建立 \[**繼承**\]。若要這麼做，請按一下 \[**工具箱**\] 中的 \[**繼承**\] 項目，然後放開滑鼠按鍵。接著按一下 \[**Employee**\] 物件，然後按一下 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中的 \[**Person**\] 物件。繼承關聯線的箭號會指向 \[**Person**\] 物件。  
  
7.  按一下設計介面上的 \[**繼承**\] 關聯線。  
  
8.  將 \[**鑑別子屬性**\] 屬性設定為 **Type**。  
  
9. 將 \[**衍生類別鑑別子值**\] 屬性設定為 **2**。  
  
10. 將 \[**基底類別鑑別子值**\] 屬性設定為 **1**。  
  
11. 將 \[**繼承預設值**\] 屬性設定為 **Person**。  
  
12. 建置專案。  
  
## 查詢繼承的類別並將資料顯示在表單上  
 您現在要將一些程式碼加入至表單，以查詢物件模型中的特定類別。  
  
#### 若要建立 LINQ 查詢並將結果顯示在表單上  
  
1.  將 \[**ListBox**\] 拖曳至 Form1。  
  
2.  按兩下表單，以建立 `Form1_Load` 事件處理常式。  
  
3.  將下列程式碼加入至 `Form1_Load` 事件處理常式：  
  
    ```vb#  
    Dim dc As New DataClasses1DataContext  
    Dim results = From emp In dc.Persons _  
        Where TypeOf emp Is Employee _  
        Select emp  
  
    For Each Emp As Employee In results  
        ListBox1.Items.Add(Emp.LastName)  
    Next  
    ```  
  
    ```c#  
    NorthwindDataContext dc = new DataClasses1DataContext();  
    var results = from emp in dc.Persons  
                  where emp is Employee  
                  select emp;  
  
    foreach(Employee Emp in results)  
    {  
        listBox1.Items.Add(Emp.LastName)  
    }  
    ```  
  
## 測試應用程式  
 執行應用程式，並確認清單方塊中顯示的記錄都是員工 \(Type 資料行值為 2 的記錄\)。  
  
#### 若要測試應用程式  
  
1.  按下 F5 鍵。  
  
2.  確認只顯示 Type 資料行值為 2 的記錄。  
  
3.  關閉表單 \(按一下 \[**偵錯**\] 功能表上的 \[**停止偵錯**\]\)。  
  
## 請參閱  
 [O\/R 設計工具概觀](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [HOW TO：將 LINQ to SQL 類別加入至專案 \(O\/R 設計工具\)](../Topic/How%20to:%20Add%20LINQ%20to%20SQL%20Classes%20to%20a%20Project%20\(O-R%20Designer\).md)   
 [逐步解說：建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [HOW TO：指派預存程序來執行更新、插入和刪除 \(O\/R 設計工具\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [HOW TO：在 Visual Basic 或 C\# 中產生物件模型](../Topic/How%20to:%20Generate%20the%20Object%20Model%20in%20Visual%20Basic%20or%20C%23.md)