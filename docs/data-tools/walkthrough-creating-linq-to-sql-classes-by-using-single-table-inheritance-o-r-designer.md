---
title: 逐步解說：使用單一資料表繼承建立 LINQ to SQL 類別 (O-R 設計工具)
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 20f4c2b4a876c35868b08378bda4daaf6d13c2e3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945842"
---
# <a name="walkthrough-create-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>逐步解說： 建立 LINQ to SQL 類別使用單一資料表繼承 （O/R 設計工具）
[在 Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)支援單一資料表繼承，因為它通常實作在關聯式系統中。 這個逐步解說以中提供的泛型步驟為基礎[如何： 使用 O/R 設計工具設定繼承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)主題，並提供一些實際資料來示範如何使用中的繼承[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。

 在此逐步解說中，您可以執行下列工作：

- 建立資料庫資料表，並在其中加入資料。

- 建立 Windows Form 應用程式。

- 將 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 檔案加入至專案。

- 建立新的實體類別。

- 設定實體類別以使用繼承。

- 查詢繼承的類別。

- 將資料顯示在 Windows Form 上。

## <a name="create-a-table-to-inherit-from"></a>建立要繼承的來源資料表
 若要查看繼承的運作方式，您會建立一個小型`Person`資料表中，使用它做為基底類別，並接著建立`Employee`繼承自它的物件。

### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>若要建立用來示範繼承的基底資料表

1.  在 **伺服器總管**或**資料庫總管**，以滑鼠右鍵按一下**資料表**節點，然後按一下**加入新的資料表**。

    > [!NOTE]
    >  您可以使用 Northwind 資料庫，或其他可以在其中加入資料表的任何資料庫。

2.  在**資料表設計工具**中，將下列資料行新增至資料表：

    |資料行名稱|資料類型|允許 Null|
    |-----------------|---------------|-----------------|
    |**ID**|**int**|**False**|
    |**Type**|**int**|**True**|
    |**FirstName**|**nvarchar(200)**|**False**|
    |**LastName**|**nvarchar(200)**|**False**|
    |**Manager**|**int**|**True**|

3.  將 ID 資料行設定為主索引鍵。

4.  儲存資料表，並將它命名為 **Person**。

## <a name="add-data-to-the-table"></a>將資料新增至資料表
 為了能夠確認繼承的設定是否正確，單一資料表繼承中的每個類別都需要在資料表中有一些資料。

### <a name="to-add-data-to-the-table"></a>若要加入資料至資料表

1.  在資料檢視中開啟資料表  (以滑鼠右鍵按一下**Person**資料表中**伺服器總管**或**資料庫總管**然後按一下**顯示資料表資料**。)

2.  將下列資料複製至資料表  (您可以將它複製並貼到資料表選取整個資料列中的**結果**窗格中。)

    ||||||
    |-|-|-|-|-|
    |**ID**|**Type**|**FirstName**|**LastName**|**Manager**|
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

## <a name="create-a-new-project"></a>建立新專案
 現在您已建立好資料表，請建立新的專案來示範如何設定繼承。

### <a name="to-create-the-new-windows-forms-application"></a>若要建立新的 Windows Forms 應用程式

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增** > **專案**。

2. 展開  **Visual C#** 或是**Visual Basic**左窗格中，然後選取**Windows Desktop**。

3. 在中間窗格中，選取**Windows Forms 應用程式**專案類型。

4. 將專案命名為**InheritanceWalkthrough**，然後選擇**確定**。

     **InheritanceWalkthrough** 專案已建立並新增至**方案總管**中。

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>將 LINQ to SQL 類別檔案新增至專案

### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>若要將 LINQ to SQL 檔案新增至專案

1.  在 [專案]  功能表中，按一下 [加入新項目] 。

2.  按一下 [LINQ to SQL 類別] 範本，然後按一下 [新增]。

     *.Dbml*檔案加入至專案並**O/R Designer**隨即開啟。

## <a name="create-the-inheritance-by-using-the-or-designer"></a>使用 O/R 設計工具建立繼承
 設定繼承的方法是將**繼承**物件從**工具箱**拖曳至設計介面。

### <a name="to-create-the-inheritance"></a>若要建立繼承

1.  在 **伺服器總管**或**資料庫總管**，瀏覽至**人員**您稍早建立的資料表。

2.  拖曳**Person**資料表拖曳至**O/R Designer**設計介面。

3.  拖曳第二個**Person**資料表拖曳至**O/R Designer**其名稱變更為**員工**。

4.  從 **Person** 物件中刪除 **Manager** 屬性。

5.  從 **Employee** 物件中刪除 **Type**、**ID**、**FirstName** 和 **LastName** 屬性。 (亦即刪除 **Manager** 以外的所有屬性。)

6.  從**工具箱**的 [物件關連式設計工具] 索引標籤中，在 **Person** 與 **Employee** 物件之間建立**繼承**。 若要這麼做，請按一下 [工具箱] 中的 [繼承] 項目，然後放開滑鼠按鍵。 接下來，按一下**員工**物件，然後**人員**物件**O/R Designer**。 繼承線的箭號則指向**人員**物件。

7.  按一下設計介面上的 [繼承] 線。

8.  將 [鑑別子屬性] 屬性設定為 **Type**。

9. 將 [衍生類別鑑別子值] 屬性設定為 **2**。

10. 將 [基底類別鑑別子值] 屬性設定為 **1**。

11. 將**繼承預設值**屬性設定為 **Person**。

12. 建置專案。

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>查詢繼承的類別並將資料顯示在表單上
 您現在會新增至表單，以查詢特定類別的物件模型中的一些程式碼。

### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>若要建立 LINQ 查詢並將結果顯示在表單上

1.  將 **ListBox** 拖曳至 **Form1**。

2.  按兩下表單，以建立 `Form1_Load` 事件處理常式。

3.  將下列程式碼加入至 `Form1_Load` 事件處理常式：

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
 執行應用程式，並確認清單方塊中顯示的記錄都是員工 (**Type** 資料行值為 2 的記錄)。

### <a name="to-test-the-application"></a>若要測試應用程式

1.  請按 **F5**。

2.  確認只顯示 **Type** 資料行值為 2 的記錄。

3.  關閉表單  (按一下 [偵錯] 功能表上的 [停止偵錯]。)

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [逐步解說：建立 LINQ to SQL 類別 (O-R 設計工具)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [如何：在 Visual Basic 或 C# 中產生物件模型](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)