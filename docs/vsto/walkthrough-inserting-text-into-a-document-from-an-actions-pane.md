---
title: 'Walkthrough: Inserting Text into a Document from an Actions Pane | Microsoft Docs'
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
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
ms.assetid: fd14c896-5737-4a20-94f7-6064b67112c5
caps.latest.revision: 70
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: f4952081dea98ae372ff1df9d87cd4146b6e6da6
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="walkthrough-inserting-text-into-a-document-from-an-actions-pane"></a>Walkthrough: Inserting Text into a Document from an Actions Pane
  This walkthrough demonstrates how to create an actions pane in a Microsoft Office Word document. The actions pane contains two controls that collect input and then send the text to the document.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 This walkthrough illustrates the following tasks:  
  
-   Designing an interface by using Windows Forms controls on an actions pane control.  
  
-   Displaying the actions pane when the application opens.  
  
> [!NOTE]  
>  Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions. The Visual Studio edition that you have and the settings that you use determine these elements. For more information, see [Personalize the Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisites  
 You need the following components to complete this walkthrough:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] or [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Creating the Project  
 The first step is to create a Word Document project.  
  
#### <a name="to-create-a-new-project"></a>To create a new project  
  
1.  Create a Word Document project with the name **My Basic Actions Pane**. In the wizard, select **Create a new document**. For more information, see [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio opens the new Word document in the designer and adds the **My Basic Actions Pane** project to **Solution Explorer**.  
  
## <a name="adding-text-and-bookmarks-to-the-document"></a>Adding Text and Bookmarks to the Document  
 The actions pane will send text to bookmarks in the document. To design the document, type some text to create a basic form.  
  
#### <a name="to-add-text-to-your-document"></a>To add text to your document  
  
1.  Type the following text into your Word document:  
  
     **March 21, 2008**  
  
     **Name**  
  
     **Address**  
  
     **This is an example of a basic actions pane in Word.**  
  
 You can add a <xref:Microsoft.Office.Tools.Word.Bookmark> control to your document by dragging it from the **Toolbox** in Visual Studio or by using the **Bookmark** dialog box in Word.  
  
#### <a name="to-add-a-bookmark-control-to-your-document"></a>To add a Bookmark control to your document  
  
1.  From the **Word Controls** tab of the **Toolbox**, drag a <xref:Microsoft.Office.Tools.Word.Bookmark> control to your document.  
  
     The **Add Bookmark Control** dialog box appears.  
  
2.  Select the word **Name**, without selecting the paragraph mark, and click **OK**.  
  
    > [!NOTE]  
    >  The paragraph mark should be outside of the bookmark. If paragraph marks are not visible in the document, click the **Tools** menu, point to **Microsoft Office Word Tools** and then click **Options**. Click the **View** tab, and select the **Paragraph marks** check box in the **Formatting marks** section of the **Options** dialog box.  
  
3.  In the **Properties** window, change the **Name** property of **Bookmark1** to **showName**.  
  
4.  Select the word **Address**, without selecting the paragraph mark.  
  
5.  On the **Insert** tab of the Ribbon, in the **Links** group, click **Bookmark**.  
  
6.  In the **Bookmark** dialog box, type **showAddress** in the **Bookmark Name** box and click **Add**.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Adding Controls to the Actions Pane  
 To design the actions pane interface, add an actions pane control to the project and then add Windows Forms controls to the actions pane control.  
  
#### <a name="to-add-an-actions-pane-control"></a>To add an actions pane control  
  
1.  Select the **My Basic Actions Pane** project in **Solution Explorer**.  
  
2.  On the **Project** menu, click **Add New Item**.  
  
3.  In the **Add New Item** dialog box, click **Actions Pane Control**, name the control **InsertTextControl,** and click **Add**.  
  
#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>To add Windows Form controls to the actions pane control  
  
1.  If the actions pane control is not visible in the designer, double-click **InsertTextControl**.  
  
2.  From the **Common Controls** tab of the **Toolbox**, drag a **Label** control to the actions pane control.  
  
3.  Change the **Text** property of the Label control to **Name**.  
  
4.  Add a **Textbox** control to the actions pane control, and change the following properties.  
  
    |Property|Value|  
    |--------------|-----------|  
    |**Name**|**getName**|  
    |**Size**|**130, 20**|  
  
5.  Add a second **Label** control to the actions pane control, and change the **Text** property to **Address**.  
  
6.  Add a second **Textbox** control to the actions pane control, and change the following properties.  
  
    |Property|Value|  
    |--------------|-----------|  
    |**Name**|**getAddress**|  
    |**Accepts Return**|**True**|  
    |**Multiline**|**True**|  
    |**Size**|**130, 40**|  
  
7.  Add a **Button** control to the actions pane control, and change the following properties.  
  
    |Property|Value|  
    |--------------|-----------|  
    |**Name**|**addText**|  
    |**Text**|**Insert**|  
  
## <a name="adding-code-to-insert-text-into-the-document"></a>Adding Code to Insert Text into the Document  
 In the actions pane, write code that inserts the text from the text boxes into the appropriate <xref:Microsoft.Office.Tools.Word.Bookmark> controls in the document. You can use the `Globals` class to access controls on the document from the controls on the actions pane. For more information, see [Global Access to Objects in Office Projects](../vsto/global-access-to-objects-in-office-projects.md).  
  
#### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>To insert text from the actions pane in a bookmark in the document  
  
1.  Add the following code to the <xref:System.Windows.Forms.Control.Click> event handler of the **addText** button.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]  [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]  
  
2.  In C#, you must add an event handler for the button click. You can place this code in the `InsertTextControl` constructor after the call to `IntializeComponent`. For information about creating event handlers, see [How to: Create Event Handlers in Office Projects](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]  
  
## <a name="adding-code-to-show-the-actions-pane"></a>Adding Code to Show the Actions Pane  
 To show the actions pane, add the control you created to the control collection.  
  
#### <a name="to-show-the-actions-pane"></a>To show the actions pane  
  
1.  Create a new instance of the actions pane control in the `ThisDocument` class.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]  [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]  
  
2.  Add the following code to the <xref:Microsoft.Office.Tools.Word.Document.Startup> event handler of `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]  [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]  
  
## <a name="testing-the-application"></a>Testing the Application  
 Test your document to verify that the actions pane opens when the document is opened and that text typed into the text boxes is inserted into the bookmarks when the button is clicked.  
  
#### <a name="to-test-your-document"></a>To test your document  
  
1.  Press F5 to run your project.  
  
2.  Confirm that the actions pane is visible.  
  
3.  Type your name and address into the text boxes on the actions pane and click **Insert**.  
  
## <a name="next-steps"></a>Next Steps  
 Here are some tasks that might come next:  
  
-   Creating an actions pane in Excel. For more information, see [How to: Add an Actions Pane to Excel Workbooks](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872).  
  
-   Binding data to controls on an actions pane. For more information, see [Walkthrough: Binding Data to Controls on a Word Actions Pane](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
## <a name="see-also"></a>See Also  
 [Actions Pane Overview](../vsto/actions-pane-overview.md)   
 [How to: Add an Actions Pane to Word Documents or Excel Workbooks](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [How to: Add an Actions Pane to Excel Workbooks](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [How to: Manage Control Layout on Actions Panes](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Bookmark Control](../vsto/bookmark-control.md)  
  
  
