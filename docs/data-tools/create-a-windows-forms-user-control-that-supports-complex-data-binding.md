---
title: Create a Windows Forms user control with data binding | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
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
ms.sourcegitcommit: 33a857c2d8585e2e8da9bcd9158190366a3b6830
ms.openlocfilehash: 16d30bcbb397cdbafb74a6785e2ac109bfc2aa1e
ms.contentlocale: zh-tw
ms.lasthandoff: 09/07/2017

---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Create a Windows Forms user control that supports complex data binding
When displaying data on forms in Windows applications, you can choose existing controls from the **Toolbox**, or you can author custom controls if your application requires functionality that is not available in the standard controls. This walkthrough shows how to create a control that implements the <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Controls that implement the <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contain a `DataSource` and `DataMember` property that can be bound to data. Such controls are similar to a <xref:System.Windows.Forms.DataGridView> or <xref:System.Windows.Forms.ListBox>.  
  
 For more information on control authoring, see [Developing Windows Forms Controls at Design Time](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).  
  
 When authoring controls for use in data-binding scenarios you need to implement one of the following data-binding attributes:  
  
|Data-binding attribute usage|  
|-----------------------------------|  
|Implement the <xref:System.ComponentModel.DefaultBindingPropertyAttribute> on simple controls, like a <xref:System.Windows.Forms.TextBox>, that display a single column (or property) of data. For more information, see [Create a Windows Forms user control that supports simple data binding](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implement the <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> on controls, like a <xref:System.Windows.Forms.DataGridView>, that display lists (or tables) of data. (This process is described in this walkthrough page.)|  
|Implement the <xref:System.ComponentModel.LookupBindingPropertiesAttribute> on controls, like a <xref:System.Windows.Forms.ComboBox>, that display lists (or tables) of data but also need to present a single column or property. For more information, see [Create a Windows Forms user control that supports lookup data binding](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 This walkthrough creates a complex control that displays rows of data from a table. This example uses the `Customers` table from the Northwind sample database. The complex user control will display the customers table in a <xref:System.Windows.Forms.DataGridView> in the custom control.  
  
 During this walkthrough, you will learn how to:  
  
-   Create a new **Windows Application**.  
  
-   Add a new **User Control** to your project.  
  
-   Visually design the user control.  
  
-   Implement the `ComplexBindingProperty` attribute.  
  
-   Create a dataset with the [Data Source Configuration Wizard](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Set the **Customers** table in the [Data Sources Window](add-new-data-sources.md) to use the new complex control.  
  
-   Add the new control by dragging it from the **Data Sources Window** onto **Form1**.  
  
## <a name="prerequisites"></a>Prerequisites  
 In order to complete this walkthrough, you will need:  
  
-   Access to the Northwind sample database. For more information, see [How to: Install Sample Databases](../data-tools/installing-database-systems-tools-and-samples.md).  
  
## <a name="create-a-windows-application"></a>Create a Windows Application  
 The first step is to create a **Windows Application**.  
  
#### <a name="to-create-the-new-windows-project"></a>To create the new Windows project  
  
1.  In Visual Studio, from the **File** menu, create a new **Project**.  
  
2.  Name the project **ComplexControlWalkthrough**.  
  
3.  Select **Windows Application**, and click **OK**. For more information, see [Client Applications](/dotnet/framework/develop-client-apps).  
  
     The **ComplexControlWalkthrough** project is created, and added to **Solution Explorer**.  
  
## <a name="add-a-user-control-to-the-project"></a>Add a user control to the project  
 Because this walkthrough creates a complex data-bindable control from a **User Control**, you must add a **User Control** item to the project.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>To add a user control to the project  
  
1.  From the **Project** menu, choose **Add User Control**.  
  
2.  Type **ComplexDataGridView** in the **Name** area, and then click **Add**.  
  
     The **ComplexDataGridView** control is added to **Solution Explorer**, and opens in the designer.  
  
## <a name="design-the-complexdatagridview-control"></a>Design the ComplexDataGridView control  
 This step adds a <xref:System.Windows.Forms.DataGridView> to the user control.  
  
#### <a name="to-design-the-complexdatagridview-control"></a>To design the ComplexDataGridView control  
  
-   Drag a <xref:System.Windows.Forms.DataGridView> from the **Toolbox** onto the user control's design surface.  
  
## <a name="add-the-required-data-binding-attribute"></a>Add the required data-binding attribute  
 For complex controls that support data binding, you can implement the <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-complexbindingproperties-attribute"></a>To implement the ComplexBindingProperties attribute  
  
1.  Switch the **ComplexDataGridView** control to code view. (On the **View** menu, select **Code**.)  
  
2.  Replace the code in the `ComplexDataGridView` with the following:  
  
     [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]  [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]  
  
3.  From the **Build** menu, choose **Build Solution**.  
  
## <a name="creating-a-data-source-from-your-database"></a>Creating a data source from your database  
 This step uses the **Data Source Configuration** wizard to create a data source based on the `Customers` table in the Northwind sample database. You must have access to the Northwind sample database to create the connection. For information on setting up the Northwind sample database, see [Install SQL Server sample databases](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>To create the data source  
  
1.  On the **Data** menu, click **Show Data Sources**.  
  
2.  In the **Data Sources** window, select **Add New Data Source** to start the **Data Source Configuration** wizard.  
  
3.  Select **Database** on the **Choose a Data Source Type** page, and then click **Next**.  
  
4.  On the **Choose your Data Connection** page do one of the following:  
  
    -   If a data connection to the Northwind sample database is available in the drop-down list, select it.  
  
    -   Select **New Connection** to launch the **Add/Modify Connection** dialog box.  
  
5.  If your database requires a password, select the option to include sensitive data, and then click **Next**.  
  
6.  On the **Save connection string to the Application Configuration file** page, click **Next**.  
  
7.  On the **Choose your Database Objects** page, expand the **Tables** node.  
  
8.  Select the `Customers` table, and then click **Finish**.  
  
     The **NorthwindDataSet** is added to your project, and the `Customers` table appears in the **Data Sources** window.  
  
## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Set the Customers table to use the ComplexDataGridView control  
 Within the **Data Sources** window, you can set the control to be created prior to dragging items onto your form.  
  
#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>To set the Customers table to bind to the ComplexDataGridView control  
  
1.  Open **Form1** in the designer.  
  
2.  Expand the **Customers** node in the **Data Sources** window.  
  
3.  Click the drop-down arrow on the **Customers** node, and choose **Customize**.  
  
4.  Select the **ComplexDataGridView** from the list of **Associated Controls** in the **Data UI Customization Options** dialog box.  
  
5.  Click the drop-down arrow on the `Customers` table, and choose **ComplexDataGridView** from the control list.  
  
## <a name="add-controls-to-the-form"></a>Add controls to the form  
 You can create the data-bound controls by dragging items from the **Data Sources** window onto your form.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>To create data-bound controls on the form  
  
-   Drag the main **Customers** node from the **Data Sources** window onto the form.Verify that the **ComplexDataGridView** control is used to display the table's data.  
  
## <a name="running-the-application"></a>Running the application  
  
#### <a name="to-run-the-application"></a>To run the application  
  
-   Press F5 to run the application.  
  
## <a name="next-steps"></a>Next Steps  
 Depending on your application requirements, there are several steps you may want to perform after creating a control that supports databinding. Some typical next steps include:  
  
-   Placing your custom controls in a control library so you can reuse them in other applications.  
  
-   Creating controls that support lookup scenarios. For more information, see [Create a Windows Forms user control that supports lookup data binding](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>See Also  
 [Bind Windows Forms controls to data in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Set the control to be created when dragging from the Data Sources window](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Windows Forms Controls](/dotnet/framework/winforms/controls/index)

