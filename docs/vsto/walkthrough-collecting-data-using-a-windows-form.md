---
title: 'Walkthrough: Collecting Data Using a Windows Form | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.prod: visual-studio-dev14
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], Windows Forms
- Windows Forms [Office development in Visual Studio], collecting data
- forms [Office development in Visual Studio], walkthroughs
- worksheets [Office development in Visual Studio], collecting data
ms.assetid: 40e87f7f-cfbb-4761-bf1b-d042f45f4f09
caps.latest.revision: 54
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: d69e91088401857391c935f768e171153a50faeb
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="walkthrough-collecting-data-using-a-windows-form"></a>Walkthrough: Collecting Data Using a Windows Form
  This walkthrough demonstrates how to open a Windows Form from a document-level customization for Microsoft Office Excel, collect information from the user, and write that information into a worksheet cell.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Although this walkthrough uses a document-level project for Excel specifically, the concepts demonstrated by the walkthrough are applicable to other Office projects.  
  
## <a name="prerequisites"></a>Prerequisites  
 You need the following components to complete this walkthrough:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] or [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
> [!NOTE]  
>  Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions. The Visual Studio edition that you have and the settings that you use determine these elements. For more information, see [Personalize the Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-a-new-project"></a>Creating a New Project  
 The first step is to create an Excel Workbook project.  
  
#### <a name="to-create-a-new-project"></a>To create a new project  
  
1.  Create an Excel Workbook project with the name **WinFormInput**, and select **Create a new document** in the wizard. For more information, see [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio opens the new Excel workbook in the designer and adds the **WinFormInput** project to **Solution Explorer**.  
  
## <a name="adding-a-namedrange-control-to-the-worksheet"></a>Adding a NamedRange Control to the Worksheet  
  
#### <a name="to-add-a-named-range-to-sheet1"></a>To add a named range to Sheet1  
  
1.  Select cell **A1** on `Sheet1`.  
  
2.  In the **Name** box, type **formInput**.  
  
     The **Name** box is located to the left of the formula bar, just above column **A** of the worksheet.  
  
3.  Press ENTER.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> control is added to cell **A1**. There is no visible indication on the worksheet, but **formInput** appears in the **Name** box (just above the worksheet on the left side) and in the **Properties** window when cell **A1** is selected.  
  
## <a name="adding-a-windows-form-to-the-project"></a>Adding a Windows Form to the Project  
 Create a Windows Form to prompt the user for information.  
  
#### <a name="to-add-a-windows-form"></a>To add a Windows Form  
  
1.  Select the project **WinFormInput** in **Solution Explorer**.  
  
2.  On the **Project** menu, click **Add Windows Form**.  
  
3.  Name the form **GetInputString.vb** or **GetInputString.cs**, and then click **Add**.  
  
     The new form opens in the designer.  
  
4.  Add a <xref:System.Windows.Forms.TextBox> and a <xref:System.Windows.Forms.Button> to the form.  
  
5.  Select the button, find the property **Text** in the **Properties** window, and change the text to **OK**.  
  
 Next, add code to `ThisWorkbook.vb` or `ThisWorkbook.cs` to collect the user's information.  
  
## <a name="displaying-the-windows-form-and-collecting-information"></a>Displaying the Windows Form and Collecting Information  
 Create an instance of the `GetInputString` Windows Form and display it, and then write the user's information into a cell in the worksheet.  
  
#### <a name="to-display-the-form-and-collect-information"></a>To display the form and collect information  
  
1.  Right-click **ThisWorkbook.vb** or **ThisWorkbook.cs** in **Solution Explorer**, and then click **View Code**.  
  
2.  In the <xref:Microsoft.Office.Tools.Excel.Workbook.Open> event handler of `ThisWorkbook`, add the following code to declare a variable for the form `GetInputString` and then show the form.  
  
    > [!NOTE]  
    >  In C#, you must add an event handler as shown in the <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> event below. For information about creating event handlers, see [How to: Create Event Handlers in Office Projects](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#1)]  [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#1)]  
  
3.  Create a method called `WriteStringToCell` that writes text to a named range. This method is called from the form, and the user's input is passed to the <xref:Microsoft.Office.Tools.Excel.NamedRange> control, `formInput`, on cell **A1**.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#2)]  [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#2)]  
  
 Next, add code to the form to handle the button's click event.  
  
## <a name="sending-information-to-the-worksheet"></a>Sending Information to the Worksheet  
  
#### <a name="to-send-information-to-the-worksheet"></a>To send information to the worksheet  
  
1.  Right-click **GetInputString** in **Solution Explorer**, and then click **View Designer**.  
  
2.  Double-click the button to open the code file with the button's <xref:System.Windows.Forms.Control.Click> event handler added.  
  
3.  Add code to the event handler to take the input from the text box, send it to the function `WriteStringToCell`, and then close the form.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs#3)]  [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb#3)]  
  
## <a name="testing"></a>Testing  
 You can now run the project. The Windows Form appears, and your input appears in the worksheet.  
  
#### <a name="to-test-your-workbook"></a>To test your workbook  
  
1.  Press F5 to run your project.  
  
2.  Confirm that the Windows Form appears.  
  
3.  Type **Hello World** in the text box, and then click **OK**.  
  
4.  Confirm that **Hello World** appears in cell **A1** of the worksheet.  
  
## <a name="next-steps"></a>Next Steps  
 This walkthrough shows the basics of showing a Windows Form and passing data to a worksheet. Other tasks you may want to perform include:  
  
-   Use Windows Forms controls on an Excel workbook or a Word document. For more information, see [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Modify the user interface of a Microsoft Office application from a document-level customization or an VSTO Add-in. For more information, see [Office UI Customization](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>See Also  
 [Developing Office Solutions](../vsto/developing-office-solutions.md)   
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)   
 [Walkthroughs Using Word](../vsto/walkthroughs-using-word.md)   
 [Walkthroughs Using Excel](../vsto/walkthroughs-using-excel.md)  
  
  
