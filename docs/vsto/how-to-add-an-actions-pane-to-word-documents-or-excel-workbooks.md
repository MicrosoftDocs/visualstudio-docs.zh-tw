---
title: "如何： 執行窗格加入 Word 文件或 Excel 活頁簿 |Microsoft 文件"
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
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
ms.assetid: cea3c2b6-9364-4134-b812-50888ad8bd76
caps.latest.revision: "63"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ffdb997bbff96e99a456f7d4679a5da0e446ee4a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>如何：將執行窗格加入至 Word 文件或 Excel 活頁簿
  若要加入 Microsoft Office Word 文件或 Microsoft Excel 活頁簿的 [動作] 窗格，請先建立 Windows Form 使用者控制項。 然後，將使用者控制項加入<xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>屬性`ThisDocument.ActionsPane`欄位 (Word) 或`ThisWorkbook.ActionsPane`您的專案中的欄位 (Excel)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="creating-the-user-control"></a>建立使用者控制項  
 下列程序顯示如何建立使用者控制項，在 Word 或 Excel 專案。 它也會加入至被按下時，將文字寫入至文件或活頁簿的使用者控制項的按鈕。  
  
#### <a name="to-create-the-user-control"></a>若要建立使用者控制項  
  
1.  在 Visual Studio 中開啟 Word 或 Excel 文件層級專案。  
  
2.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
3.  在**加入新項目**對話方塊中，選取**執行窗格控制項**，其命名**HelloControl**，然後按一下**新增**。  
  
    > [!NOTE]  
    >  您可以另外加入**使用者控制項**至您的專案項目。 所產生的類別**執行窗格控制項**和**使用者控制項**項目在功能上相當。  
  
4.  從**Windows Form**  索引標籤**工具箱，**拖曳**按鈕**控制項拖曳至控制項。  
  
    > [!NOTE]  
    >  如果控制項未出現在設計工具中，按兩下 [ **HelloControl**中**方案總管] 中**。  
  
5.  將程式碼加入<xref:System.Windows.Forms.Control.Click>按鈕的事件處理常式。 下列範例會顯示 Microsoft Office Word 文件的程式碼。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]  
  
6.  在 C# 中，您必須加入用於按鈕 click 事件處理常式。 您可以將放在這段程式碼`HelloControl`建構函式的呼叫後方`IntializeComponent`。  
  
     如需如何建立事件處理常式資訊，請參閱[How to： 在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]  
  
## <a name="adding-the-user-control-to-the-actions-pane"></a>將使用者控制項加入至 [動作] 窗格  
 若要顯示 動作 窗格，將 使用者控制項加入<xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>屬性`ThisDocument.ActionsPane`欄位 (Word) 或`ThisWorkbook.ActionsPane`欄位 (Excel)。  
  
#### <a name="to-add-the-user-control-to-the-actions-pane"></a>若要加入使用者控制項加入執行窗格  
  
1.  將下列程式碼加入`ThisDocument`或`ThisWorkbook`類別層級宣告的類別 （並未新增此程式碼的方法）。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]  
  
2.  將下列程式碼加入`ThisDocument_Startup`事件處理常式`ThisDocument`類別或`ThisWorkbook_Startup`事件處理常式`ThisWorkbook`類別。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]  
  
## <a name="see-also"></a>另請參閱  
 [執行窗格概觀](../vsto/actions-pane-overview.md)   
 [逐步解說： 將文字插入文件中從 [動作] 窗格](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [如何： 管理執行窗格控制項配置](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [逐步解說：從執行窗格將文字插入文件](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  