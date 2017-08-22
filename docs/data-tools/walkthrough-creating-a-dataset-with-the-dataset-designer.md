---
title: 'Walkthrough: Creating a Dataset with the Dataset Designer | Microsoft Docs'
ms.custom: 
ms.date: 11/02/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
robots: noindex,nofollow
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
ms.sourcegitcommit: 9e6c28d42bec272c6fd6107b4baf0109ff29197e
ms.openlocfilehash: 5f944d0611d9e0ce54730bb3583822c959f3a962
ms.contentlocale: zh-tw
ms.lasthandoff: 08/22/2017

---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>Walkthrough: Creating a Dataset with the Dataset Designer
In this walkthrough you will create a dataset using the **Dataset Designer**. It will take you through the process of creating a new project and adding a new **DataSet** item to it. You will learn how to create tables based on tables in a database without using a wizard.  
  
 Tasks illustrated in this walkthrough include:  
  
-   Creating a new **Windows Application** project.  
  
-   Adding an empty **DataSet** item to the project.  
  
-   Creating and configuring a data source in your application by building a dataset with the **Dataset Designer**.  
  
-   Creating a connection to the Northwind database in **Server Explorer**.  
  
-   Creating tables with TableAdapters in the dataset based on tables in the database.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Prerequisites  
 In order to complete this walkthrough, you need:  
  
-   Access to the Northwind sample database (SQL Server or Access version). For more information, see [How to: Install Sample Databases](../data-tools/installing-database-systems-tools-and-samples.md).  
  
## <a name="creating-a-new-windows-application-project"></a>Creating a New Windows Application Project  
  
#### <a name="to-create-a-new-windows-application-project"></a>To create a new Windows Application project  
  
1.  From the **File** menu, create a new project.  
  
2.  Choose a programming language in the **Project Types** pane.  
  
3.  Click **Windows Application** in the **Templates** pane.  
  
4.  Name the project `DatasetDesignerWalkthrough`, and then click **OK**.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] will add the project to **Solution Explorer** and display a new form in the designer.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Adding a New Dataset to the Application  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>To add a new dataset item to the project  
  
1.  On the **Project** menu, click **Add New Item**.  
  
     The **Add New Item** dialog box appears.  
  
2.  In the **Templates** box of the **Add New Item** dialog box, click **DataSet**.  
  
3.  Name the Dataset `NorthwindDataset`, and then click **Add**.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] will add a file called **NorthwindDataset.xsd** to the project and open it in the **Dataset Designer**.  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>Creating a Data Connection in Server Explorer  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>To create a connection to the Northwind database  
  
1.  On the **View** menu, click **Server Explorer**.  
  
2.  In **Server Explorer**, click the **Connect to Database** button.  
  
3.  Create a connection to the Northwind sample database.  
  
    > [!NOTE]
    >  You can connect to the SQL Server or Access version of Northwind for this walkthrough.  
  
## <a name="creating-the-tables-in-the-dataset"></a>Creating the Tables in the Dataset  
 This section will explain how to add tables to the dataset.  
  
#### <a name="to-create-the-customers-table"></a>To create the Customers table  
  
1.  Expand the data connection you created in **Server Explorer**, and then expand the **Tables** node.  
  
2.  Drag the **Customers** table from **Server Explorer** onto the **Dataset Designer**.  
  
     A **Customers** data table and **CustomersTableAdapter** are added to the dataset.  
  
#### <a name="to-create-the-orders-table"></a>To create the Orders table  
  
-   Drag the **Orders** table from **Server Explorer** onto the **Dataset Designer**.  
  
     An **Orders** data table, **OrdersTableAdapter**, and data relation between the **Customers** and **Orders** tables are added to the dataset.  
  
#### <a name="to-create-the-orderdetails-table"></a>To create the OrderDetails table  
  
-   Drag the **Order Details** table from **Server Explorer** onto the **Dataset Designer**.  
  
     An **Order Details** data table, **OrderDetailsTableAdapter**, and a data relation between the **Orders** and **OrderDetails** tables are added to the dataset.  
  
## <a name="next-steps"></a>Next Steps  
  
### <a name="to-add-functionality-to-your-application"></a>To add functionality to your application  
  
-   Save the dataset.  
  
-   Select items in the **Data Sources** window and drag them onto a form. For more information, see [Bind Windows Forms controls to data in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Add more queries to the TableAdapters. 
  
-   Add validation logic to the <xref:System.Data.DataTable.ColumnChanging> or <xref:System.Data.DataTable.RowChanging> events of the data tables in the dataset. For more information, see [Validate data in datasets](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>See Also  
 [Bind Windows Forms controls to data in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Bind controls to data in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Validating Data](validate-data-in-datasets.md)   
 [Saving Data](../data-tools/saving-data.md)
