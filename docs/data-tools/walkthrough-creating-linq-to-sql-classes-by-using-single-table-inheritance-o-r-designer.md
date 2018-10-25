---
title: 逐步解說： 建立 LINQ to SQL 類別使用單一資料表繼承 （O-R 設計工具）
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 943b75c9c5f9c0c32ab02b5e73c07282728e0beb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864723"
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

## <a name="create-a-table-to-inherit-from"></a>建立資料表，以繼承自
 若要查看繼承的運作方式，您會建立一個小型`Person`資料表中，使用它做為基底類別，並接著建立`Employee`繼承自它的物件。

### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>若要建立用來示範繼承的基底資料表

1.  在 **伺服器總管**或**資料庫總管**，以滑鼠右鍵按一下**資料表**節點，然後按一下**加入新的資料表**。

    > [!NOTE]
    >  您可以使用 Northwind 資料庫，或其他可以在其中加入資料表的任何資料庫。

2.  在 **資料表設計工具**，將下列資料行加入至資料表：

    |資料行名稱|資料類型|允許 Null|
    |-----------------|---------------|-----------------|
    |**ID**|**int**|**False**|
    |**Type**|**int**|**True**|
    |**FirstName**|**nvarchar(200)**|**False**|
    |**lastName**|**nvarchar(200)**|**False**|
    |**Manager**|**int**|**True**|

3.  將 ID 資料行設定為主索引鍵。

4.  儲存資料表並將它命名**人員**。

## <a name="add-data-to-the-table"></a>將資料加入至資料表
 為了能夠確認繼承的設定是否正確，單一資料表繼承中的每個類別都需要在資料表中有一些資料。

### <a name="to-add-data-to-the-table"></a>若要加入資料至資料表

1.  在資料檢視中開啟資料表  (以滑鼠右鍵按一下**Person**資料表中**伺服器總管**或**資料庫總管**然後按一下**顯示資料表資料**。)

2.  將下列資料複製至資料表  (您可以將它複製並貼到資料表選取整個資料列中的**結果**窗格中。)

    ||||||
    |-|-|-|-|-|
    |**ID**|**Type**|**FirstName**|**lastName**|**Manager**|
    |**1**|**1**|**Anne**|**勒**|**NULL**|
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

2. 展開  **Visual C#** 或是**Visual Basic**的左側窗格中，然後選取**Windows Desktop**。

3. 在中間窗格中，選取**Windows Forms 應用程式**專案類型。

4. 將專案命名為**InheritanceWalkthrough**，然後選擇**確定**。

     **InheritanceWalkthrough**專案時建立，並加入至**方案總管 中**。

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>加入 LINQ to SQL 類別檔案加入專案

### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>若要加入 LINQ to SQL 檔案加入專案

1.  在 [專案]  功能表中，按一下 [加入新項目] 。

2.  按一下  **LINQ to SQL 類別**範本，然後按一下 **新增**。

     *.Dbml*檔案加入至專案並**O/R Designer**隨即開啟。

## <a name="create-the-inheritance-by-using-the-or-designer"></a>使用 O/R 設計工具建立繼承
 設定繼承拖曳**繼承**物件**工具箱**拖曳至設計介面。

### <a name="to-create-the-inheritance"></a>若要建立繼承

1.  在 **伺服器總管**或**資料庫總管**，瀏覽至**人員**您稍早建立的資料表。

2.  拖曳**Person**資料表拖曳至**O/R Designer**設計介面。

3.  拖曳第二個**Person**資料表拖曳至**O/R Designer**其名稱變更為**員工**。

4.  刪除**經理**屬性從**人員**物件。

5.  刪除**型別**，**識別碼**， **FirstName**，以及**LastName**屬性**員工**物件。 (換句話說，刪除所有的屬性，除了**Manager**。)

6.  從**物件關聯式設計工具**索引標籤**工具箱**，建立**繼承**之間**人員**和**員工**物件。 若要這樣做，請按一下**繼承**中的項目**工具箱**放開滑鼠按鈕。 接下來，按一下**員工**物件，然後**人員**物件**O/R Designer**。 繼承線的箭號則指向**人員**物件。

7.  按一下 **繼承**列在設計介面上的。

8.  設定**鑑別子屬性**屬性設**型別**。

9. 設定**衍生類別鑑別子值**屬性設**2**。

10. 設定**基底類別鑑別子值**屬性設**1**。

11. 設定**繼承預設值**屬性設**人員**。

12. 建置專案。

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>查詢繼承的類別，並在表單上顯示資料
 您現在會新增至表單，以查詢特定類別的物件模型中的一些程式碼。

### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>若要建立 LINQ 查詢並將結果顯示在表單上

1.  拖曳**ListBox**拖曳至**Form1**。

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
 執行應用程式，並確認清單方塊中顯示的記錄都是員工 (具有值為 2 中的記錄及其**型別**資料行)。

### <a name="to-test-the-application"></a>若要測試應用程式

1.  請按 **F5**。

2.  驗證，只會記錄具有值為 2，在其**型別**會顯示資料行。

3.  關閉表單  (在**偵錯**功能表上，按一下**停止偵錯**。)

## <a name="see-also"></a>另請參閱

- [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [逐步解說： 建立 LINQ to SQL 類別 （O-R 設計工具）](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [如何： 在 Visual Basic 或 C# 中產生物件模型](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)