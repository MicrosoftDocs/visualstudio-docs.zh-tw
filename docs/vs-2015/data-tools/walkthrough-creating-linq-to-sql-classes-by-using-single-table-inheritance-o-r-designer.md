---
title: 逐步解說：使用單一資料表繼承來建立 LINQ to SQL 類別 (O-R 設計工具) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9cf95bd2095d9713d498ddccf68fd1e81e1b1e64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535703"
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>逐步解說：使用單表繼承建立 LINQ to SQL 類別 (O/R 設計工具)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)支援單一資料表繼承，因為它通常是在關聯式系統中執行。 本逐步解說會根據「 [如何：使用 O/R 設計工具設定繼承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) 」主題中提供的一般步驟，並提供一些實際資料來示範在中使用繼承的一般步驟 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 。

 在這個逐步解說中，您將執行下列工作：

- 建立資料庫資料表，並在其中加入資料。

- 建立 Windows Forms 應用程式。

- 將 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 檔案加入至專案。

- 建立新的實體類別。

- 設定實體類別以使用繼承。

- 查詢繼承的類別。

- 將資料顯示在 Windows Form 上。

## <a name="create-a-table-to-inherit-from"></a>建立要繼承的來源資料表
 若要查看繼承的運作方式，請建立小型 Person 資料表、將它當成基底類別 (Base Class)，然後建立繼承自它的 Employee 物件。

#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>若要建立用來示範繼承的基底資料表

1. 在**伺服器總管** / **資料庫總管**中，以滑鼠右鍵按一下 [**資料表]** 節點，然後按一下 [**加入新的資料表**]。

    > [!NOTE]
    > 您可以使用 Northwind 資料庫，或其他可以在其中加入資料表的任何資料庫。

2. 在 [資料表設計工具] 中，將下列資料行加入至資料表：

    |資料行名稱|資料類型|允許 Null|
    |-----------------|---------------|-----------------|
    |**識別碼**|**int**|**False**|
    |**型別**|**int**|**True**|
    |**名字**|**nvarchar(200)**|**False**|
    |**姓氏**|**nvarchar(200)**|**False**|
    |**管理員**|**int**|**True**|

3. 將 ID 資料行設定為主索引鍵。

4. 儲存資料表，並將它命名為 **Person**。

## <a name="add-data-to-the-table"></a>將資料加入至資料表
 為了能夠確認繼承的設定是否正確，單一資料表繼承中的每個類別都需要在資料表中有一些資料。

#### <a name="to-add-data-to-the-table"></a>若要加入資料至資料表

1. 在資料檢視中開啟資料表   (以滑鼠右鍵按一下**伺服器總管**資料庫總管中的**Person**資料表 / **Database Explorer** ，然後按一下 [**顯示資料表資料**] ) 

2. 將下列資料複製至資料表   (您可以複製它，然後在 [結果] 窗格中選取整個資料列，將它貼到資料表中。 ) 

    |**識別碼**|**類型**|**名字**|**姓氏**|**管理員**|
    |-|-|-|-|-|
    |**1**|**1**|**Anne**|**Wallace**|**NULL**|
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|
    |**3**|**1**|**Yael**|**Peled**|**NULL**|
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|
    |**5**|**2**|**Andreas**|**Hauser**|**1**|
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|
    |**9**|**2**|**Tai**|**Yee**|**2**|
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|
    |**11**|**2**|**Mindy**|**Martin**|**3**|
    |**12**|**2**|**Ken**|**Kwok**|**3**|

## <a name="create-a-new-project"></a>建立新的專案
 現在您已建立好資料表，請建立新的專案來示範如何設定繼承。

#### <a name="to-create-the-new-windows-application"></a>若要建立新的 Windows 應用程式

1. **在 [檔案**] 功能表中，建立新專案。

2. 將專案命名為 **InheritanceWalkthrough**。

    > [!NOTE]
    > Visual Basic 和 C# 專案都支援 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]。 請使用下列其中一種語言，來建立新的專案。

3. 按一下 [ **Windows Forms 應用程式** ] 範本，然後按一下 **[確定]**。 如需詳細資訊，請參閱 [用戶端應用程式](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)。

4. 會建立 InheritanceWalkthrough 專案，並將其新增至 **方案總管**。

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>將 LINQ to SQL 類別檔案加入至專案

#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>若要將 LINQ to SQL 檔案加入至專案

1. 在 [專案]**** 功能表上，按一下 [加入新項目]****。

2. 按一下 [LINQ to SQL 類別]**** 範本，然後按一下 [新增]****。

     .dbml 檔案隨即加入至專案，並開啟 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]。

## <a name="create-the-inheritance-by-using-the-or-designer"></a>使用 O/R 設計工具建立繼承
 設定繼承的方法是將**繼承**物件從**工具箱**拖曳至設計介面。

#### <a name="to-create-the-inheritance"></a>若要建立繼承

1. 在**伺服器總管** / **資料庫總管**中，流覽至您稍早建立的**Person**資料表。

2. 將 **Person** 資料表拖曳至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 設計介面。

3. 將第二個 **Person** 資料表拖曳至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ，並將其名稱變更為 **Employee**。

4. 從 **Person** 物件中刪除 **Manager** 屬性。

5. 從 **Employee** 物件中刪除 **Type**、**ID**、**FirstName** 和 **LastName** 屬性。 (亦即刪除 **Manager** 以外的所有屬性。)

6. 從**工具箱**的 [物件關連式設計工具]**** 索引標籤中，在 **Person** 與 **Employee** 物件之間建立**繼承**。 若要這麼做，請按一下 [工具箱]**** 中的 [繼承]**** 項目，然後放開滑鼠按鍵。 接下來，在中按一下 [ **Employee** ] 物件，然後按一下 [ **Person** ] 物件 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 。 繼承線上的箭號會指向 **Person** 物件。

7. 按一下設計介面上的 [繼承]**** 線。

8. 將 [鑑別子屬性]**** 屬性設定為 **Type**。

9. 將 [衍生類別鑑別子值]**** 屬性設定為 **2**。

10. 將 [基底類別鑑別子值]**** 屬性設定為 **1**。

11. 將**繼承預設值**屬性設定為 **Person**。

12. 建置專案。

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>查詢繼承的類別並將資料顯示在表單上
 您現在要將一些程式碼加入至表單，以查詢物件模型中的特定類別。

#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>若要建立 LINQ 查詢並將結果顯示在表單上

1. 將 **ListBox** 拖曳至 Form1。

2. 按兩下表單，以建立 `Form1_Load` 事件處理常式。

3. 將下列程式碼加入至 `Form1_Load` 事件處理常式：

    ```vb
    Dim dc As New DataClasses1DataContext
    Dim results = From emp In dc.Persons _
        Where TypeOf emp Is Employee _
        Select emp

    For Each Emp As Employee In results
        ListBox1.Items.Add(Emp.LastName)
    Next
    ```

    ```csharp
    NorthwindDataContext dc = new DataClasses1DataContext();
    var results = from emp in dc.Persons
                  where emp is Employee
                  select emp;

    foreach(Employee Emp in results)
    {
        listBox1.Items.Add(Emp.LastName)
    }
    ```

## <a name="test-the-application"></a>測試應用程式
 執行應用程式，並確認清單方塊中顯示的記錄都是員工 (Type 資料行值為 2 的記錄)。

#### <a name="to-test-the-application"></a>若要測試應用程式

1. 按下 F5。

2. 確認只顯示 Type 資料行值為 2 的記錄。

3. 關閉表單   (在 [ **調試** ] 功能表上，按一下 [ **停止調試**]。 ) 

## <a name="see-also"></a>另請參閱
 [LINQ to SQL 中的工具 Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [如何：將 LINQ to SQL 類別加入至專案 (O-r 設計工具) ](https://msdn.microsoft.com/library/7bb184ab-ec54-4cda-b706-604b2b4a3ed6)逐步解說 [：建立 LINQ to SQL 類別 (o-r 設計工具) ](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [如何：指派預存程式來執行更新、插入和刪除 (o/r 設計 ](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)工具) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [如何：以 Visual Basic 或 c # 產生物件模型](https://msdn.microsoft.com/library/a0c73b33-5650-420c-b9dc-f49310c201ee)
