---
title: 'Walkthrough: Creating LINQ to SQL Classes by Using Single-Table Inheritance (O-R Designer) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 4
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 61dcd114c13b8ea6d996650e5b475f383ca34c72
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Walkthrough: Creating LINQ to SQL Classes by Using Single-Table Inheritance (O/R Designer)
The [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) supports single-table inheritance as it is typically implemented in relational systems. This walkthrough expands upon the generic steps provided in the [How to: Configure inheritance by using the O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) topic and provides some real data to demonstrate the use of inheritance in the [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 During this walkthrough, you will perform the following tasks:  
  
-   Create a database table and add data to it.  
  
-   Create a Windows Forms application.  
  
-   Add a [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] file to a project.  
  
-   Create new entity classes.  
  
-   Configure the entity classes to use inheritance.  
  
-   Query the inherited class.  
  
-   Display the data on a Windows Form.  
  
## <a name="create-a-table-to-inherit-from"></a>Create a Table to Inherit From  
 To see how inheritance works, you will create a small Person table, use it as a base class, and then create an Employee object that inherits from it.  
  
#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>To create a base table to demonstrate inheritance  
  
1.  In **Server Explorer**/**Database Explorer**, right-click the **Tables** node and click **Add New Table**.  
  
    > [!NOTE]
    >  You can use the Northwind database or any other database that you can add a table to.  
  
2.  In the Table Designer, add the following columns to the table:  
  
    |Column Name|Data Type|Allow Nulls|  
    |-----------------|---------------|-----------------|  
    |**ID**|**int**|**False**|  
    |**Type**|**int**|**True**|  
    |**FirstName**|**nvarchar(200)**|**False**|  
    |**LastName**|**nvarchar(200)**|**False**|  
    |**Manager**|**int**|**True**|  
  
3.  Set the ID column as the primary key.  
  
4.  Save the table and name it **Person**.  
  
## <a name="add-data-to-the-table"></a>Add Data to the Table  
 So that you can verify that inheritance is configured correctly, the table needs some data for each class in the single-table inheritance.  
  
#### <a name="to-add-data-to-the-table"></a>To add data to the table  
  
1.  Open the table in data view. (Right-click the **Person** table in **Server Explorer**/**Database Explorer** and click **Show Table Data**.)  
  
2.  Copy the following data into the table. (You can copy it and then paste it into the table by selecting the whole row in the Results Pane.)  
  
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
  
## <a name="create-a-new-project"></a>Create a New Project  
 Now that you have created the table, create a new project to demonstrate configuring inheritance.  
  
#### <a name="to-create-the-new-windows-application"></a>To create the new Windows Application  
  
1.  From the **File** menu, create a new project.  
  
2.  Name the project **InheritanceWalkthrough**.  
  
    > [!NOTE]
    >  The [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] is supported in Visual Basic and C# projects. Create the new project in one of these languages.  
  
3.  Click the **Windows Forms Application** template and then click **OK**. For more information, see [Client Applications](/dotnet/framework/develop-client-apps).  
  
4.  The InheritanceWalkthrough project is created and added to **Solution Explorer**.  
  
## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Add a LINQ to SQL Classes File to the Project  
  
#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>To add a LINQ to SQL File to the project  
  
1.  On the **Project** menu, click **Add New Item**.  
  
2.  Click the **LINQ to SQL Classes** template and then click **Add**.  
  
     The .dbml file is added to the project and the [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] opens.  
  
## <a name="create-the-inheritance-by-using-the-or-designer"></a>Create the Inheritance by Using the O/R Designer  
 Configure the inheritance by dragging an **Inheritance** object from the **Toolbox** onto the design surface.  
  
#### <a name="to-create-the-inheritance"></a>To create the inheritance  
  
1.  In **Server Explorer**/**Database Explorer**, navigate to the **Person** table that you created earlier.  
  
2.  Drag the **Person** table onto the [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] design surface.  
  
3.  Drag a second **Person** table onto the [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] and change its name to **Employee**.  
  
4.  Delete the **Manager** property from the **Person** object.  
  
5.  Delete the **Type**, **ID**, **FirstName**, and **LastName** properties from the **Employee** object. (In other words, delete all properties except for **Manager**.)  
  
6.  From the **Object Relational Designer** tab of the **Toolbox**, create an **Inheritance** between the **Person** and **Employee** objects. To do this, click the **Inheritance** item in the **Toolbox** and release the mouse button. Next, click the **Employee** object and then the **Person** object in the [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. The arrow on the inheritance line will point to the **Person** object.  
  
7.  Click the **Inheritance** line on the design surface.  
  
8.  Set the **Discriminator Property** property to **Type**.  
  
9. Set the **Derived Class Discriminator Value** property to **2**.  
  
10. Set the **Base Class Discriminator Value** property to **1**.  
  
11. Set the **Inheritance Default** property to **Person**.  
  
12. Build the project.  
  
## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Query the Inherited Class and Display the Data on the Form  
 You will now add some code to the form that queries for a specific class in the object model.  
  
#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>To create a LINQ query and display the results on the form  
  
1.  Drag a **ListBox** onto Form1.  
  
2.  Double-click the form to create a `Form1_Load` event handler.  
  
3.  Add the following code to the `Form1_Load` event handler:  
  
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
  
## <a name="test-the-application"></a>Test the Application  
 Run the application and verify that the records displayed in the list box are all employees (records that have a value of 2 in their Type column).  
  
#### <a name="to-test-the-application"></a>To test the application  
  
1.  Press F5.  
  
2.  Verify that only records that have a value of 2 in their Type column are displayed.  
  
3.  Close the form. (On the **Debug** menu, click **Stop Debugging**.)  
  
## <a name="see-also"></a>See Also  
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Walkthrough: Creating LINQ to SQL Classes (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [How to: Generate the Object Model in Visual Basic or C#](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)
