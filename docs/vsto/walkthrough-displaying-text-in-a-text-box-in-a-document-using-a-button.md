---
title: "逐步解說： 使用按鈕在文件中的文字方塊中顯示文字 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: text boxes, displaying text in documents
ms.assetid: 04c54ed7-9f00-4068-aaec-1f3200110116
caps.latest.revision: "60"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 28d755d6123b2911bccd10e668212e1ea6a54484
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button"></a>逐步解說：使用按鈕在文件的文字方塊中顯示文字
  本逐步解說示範如何在 Microsoft Office Word 的文件層級自訂中使用按鈕和文字方塊。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   在設計階段，將控制項新增至文件層級專案中的 Word 文件。  
  
-   按一下按鈕時填入文字方塊。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立 Windows 文件專案。  
  
#### <a name="to-create-a-new-project"></a>建立新的專案  
  
1.  建立 Word 文件專案名稱**My Word Button**。 在精靈中，選取**建立新的文件**。  
  
     如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 設計工具中開啟新的 Word 文件，並將**My Word Button**專案加入**方案總管 中**。  
  
## <a name="adding-controls-to-the-word-document"></a>將控制項新增至 Word 文件  
 使用者介面控制項包含 Word 文件上的一個按鈕和一個文字方塊。  
  
#### <a name="to-add-a-button-and-a-text-box"></a>新增按鈕和文字方塊  
  
1.  請確認已在 Visual Studio 設計工具中開啟文件。  
  
2.  從**通用控制項** 索引標籤**工具箱**，拖曳<xref:Microsoft.Office.Tools.Word.Controls.TextBox>控制項加入文件。  
  
    > [!NOTE]  
    >  在 Word 中，控制項預設會內嵌於文字。 您可以修改方式控制項和圖案物件的預設值，進而插入**編輯** 索引標籤**選項**在 Word 中的對話方塊。  
  
3.  在 [ **檢視** ] 功能表中，按一下 [ **屬性視窗**]。  
  
4.  尋找**TextBox1**中**屬性**視窗下拉式方塊，並變更**名稱**文字方塊的屬性**displayText**。  
  
5.  拖曳**按鈕**控制項加入文件，並變更下列屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**insertText**|  
    |**Text**|**插入文字**|  
  
 現在，您可以撰寫在按一下按鈕時將執行的程式碼。  
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>在按一下按鈕時填入文字方塊  
 每次使用者按一下按鈕， **Hello World ！** 會加入到文字方塊中。  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>在按一下按鈕時寫入至文字方塊  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下**ThisDocument**，然後按一下 [**檢視程式碼**快顯功能表。  
  
2.  將下列程式碼新增至按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]  
  
3.  在 C# 中，您必須將按鈕的事件處理常式新增至 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件。 如需建立事件處理常式的詳細資訊，請參閱[How to： 在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 您現在可以測試文件，請確定訊息**Hello World ！** 當您按一下按鈕時，會出現在文字方塊中。  
  
#### <a name="to-test-your-document"></a>測試文件  
  
1.  請按 F5 執行您的專案。  
  
2.  按一下按鈕。  
  
3.  確認**Hello World ！** 會出現在文字方塊中。  
  
## <a name="next-steps"></a>後續步驟  
 本逐步解說示範在 Word 文件上使用按鈕和文字方塊的基本概念。 接著可以執行下列一些工作：  
  
-   使用下拉式方塊變更格式。 如需詳細資訊，請參閱[逐步解說： 變更文件格式使用核取方塊控制項](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)。  
  
-   使用選項按鈕以選取圖表樣式。 如需詳細資訊，請參閱[逐步解說： 更新文件使用選項按鈕中的圖表](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)。  
  
## <a name="see-also"></a>請參閱  
 [Windows Form 控制項，在 Office 文件概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [逐步解說使用 Word](../vsto/walkthroughs-using-word.md)   
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)   
 [如何： 將 Windows Form 控制項加入 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
  