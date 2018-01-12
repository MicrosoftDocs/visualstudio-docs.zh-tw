---
title: "逐步解說： 將文字插入文件從執行窗格 |Microsoft 文件"
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 26d79087a4dbf7fc176ab3deb2c98cd5fdb5ba8a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-inserting-text-into-a-document-from-an-actions-pane"></a>逐步解說：從執行窗格將文字插入文件
  本逐步解說示範如何在 Microsoft Office Word 文件中建立執行窗格。 [動作] 窗格包含收集輸入，然後將文字傳送至文件的兩個控制項。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   使用執行窗格控制項上的 Windows Form 控制項，以設計介面。  
  
-   應用程式開啟時顯示 [動作] 窗格。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立 Windows 文件專案。  
  
#### <a name="to-create-a-new-project"></a>建立新的專案  
  
1.  建立 Word 文件專案名稱**我基本的 [動作] 窗格**。 在精靈中，選取**建立新的文件**。 如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 設計工具中開啟新的 Word 文件，並將**我基本的 動作 窗格**專案加入**方案總管 中**。  
  
## <a name="adding-text-and-bookmarks-to-the-document"></a>將文字和書籤加入至文件  
 [動作] 窗格會將文字傳送文件中的書籤。 若要設計文件，輸入一些文字，以建立基本表單。  
  
#### <a name="to-add-text-to-your-document"></a>將文字加入文件  
  
1.  輸入下列文字插入 Word 文件：  
  
     **2008 年 3 月 21日日**  
  
     **名稱**  
  
     **地址**  
  
     **這是基本的動作 窗格，在 Word 中的範例。**  
  
 您可以加入<xref:Microsoft.Office.Tools.Word.Bookmark>控制項加入文件拖曳從**工具箱**Visual Studio 中或使用**書籤**在 Word 中的對話方塊。  
  
#### <a name="to-add-a-bookmark-control-to-your-document"></a>若要加入書籤控制項加入文件  
  
1.  從**Word 控制項** 索引標籤**工具箱**，拖曳<xref:Microsoft.Office.Tools.Word.Bookmark>控制項加入文件。  
  
     **加入書籤控制項** 對話方塊隨即出現。  
  
2.  選取這個字**名稱**，而不選取段落標記，然後按一下**確定**。  
  
    > [!NOTE]  
    >  段落標記應該是外部書籤。 如果段落標記不顯示文件中，按一下 **工具**功能表上，指向**Microsoft Office Word Tools** ，然後按一下 **選項**。 按一下**檢視**索引標籤，然後選取**段落標記**中核取方塊**格式化標記**區段**選項** 對話方塊。  
  
3.  在**屬性**視窗中，變更**名稱**屬性**Bookmark1**至**showName**。  
  
4.  選取這個字**位址**，而不選取段落標記。  
  
5.  在**插入**功能區 索引標籤，請在**連結**群組中，按一下**書籤**。  
  
6.  在**書籤** 對話方塊中，輸入**showAddress**中**書籤名稱**方塊，然後按一下**新增**。  
  
## <a name="adding-controls-to-the-actions-pane"></a>將控制項加入至 [動作] 窗格  
 若要設計執行窗格介面，將執行窗格控制項加入專案，然後將 Windows Form 控制項加入執行窗格控制項。  
  
#### <a name="to-add-an-actions-pane-control"></a>若要加入執行窗格控制項  
  
1.  選取**我基本的 動作 窗格**專案中**方案總管 中**。  
  
2.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
3.  在**加入新項目**對話方塊中，按一下 **執行窗格控制項**，命名控制項**InsertTextControl，**按一下**新增**。  
  
#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>將 Windows Form 控制項加入執行窗格控制項  
  
1.  若執行窗格控制項不是顯示在設計工具中，按兩下**InsertTextControl**。  
  
2.  從**通用控制項** 索引標籤**工具箱**，拖曳**標籤**執行窗格控制項的控制項。  
  
3.  變更**文字**Label 控制項，以屬性**名稱**。  
  
4.  新增**文字方塊**控制項加入執行窗格控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**getName**|  
    |**Size**|**130, 20**|  
  
5.  新增第二個**標籤**控制項加入執行窗格控制項，並變更**文字**屬性**位址**。  
  
6.  新增第二個**文字方塊**控制項加入執行窗格控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**getAddress**|  
    |**接受傳回**|**True**|  
    |**多行**|**True**|  
    |**Size**|**130, 40**|  
  
7.  新增**按鈕**控制項加入執行窗格控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**addText**|  
    |**Text**|**插入**|  
  
## <a name="adding-code-to-insert-text-into-the-document"></a>加入程式碼，將文字插入文件  
 在 [動作] 窗格中，撰寫程式碼中的插入文字的文字方塊適當<xref:Microsoft.Office.Tools.Word.Bookmark>文件中的控制項。 您可以使用`Globals`類別來存取文件上的控制項從 [動作] 窗格中的控制項。 如需詳細資訊，請參閱[全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。  
  
#### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>若要從 [動作] 窗格，在文件中的書籤中插入文字  
  
1.  將下列程式碼加入<xref:System.Windows.Forms.Control.Click>事件處理常式**addText**  按鈕。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]  
  
2.  在 C# 中，您必須加入用於按鈕 click 事件處理常式。 您可以將放在這段程式碼`InsertTextControl`建構函式的呼叫後方`IntializeComponent`。 如需建立事件處理常式的詳細資訊，請參閱[How to： 在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]  
  
## <a name="adding-code-to-show-the-actions-pane"></a>加入程式碼，以顯示 [動作] 窗格  
 若要顯示 [動作] 窗格，將您所建立的控制項加入的控制項集合。  
  
#### <a name="to-show-the-actions-pane"></a>若要顯示 [動作] 窗格  
  
1.  建立執行窗格控制項中的新執行個體`ThisDocument`類別。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]  
  
2.  將下列程式碼加入<xref:Microsoft.Office.Tools.Word.Document.Startup>事件處理常式`ThisDocument`。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 測試文件，以確認動作 窗格中開啟文件開啟時並按下按鈕時，在文字方塊中輸入的文字插入書籤。  
  
#### <a name="to-test-your-document"></a>測試文件  
  
1.  請按 F5 執行您的專案。  
  
2.  確認 [動作] 窗格已顯示。  
  
3.  在 [動作] 窗格的文字方塊中輸入您的名稱和地址，然後按一下**插入**。  
  
## <a name="next-steps"></a>後續步驟  
 接著可以執行下列一些工作：  
  
-   在 Excel 中建立執行窗格。 如需詳細資訊，請參閱[How to: Excel 活頁簿中加入執行窗格](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872)。  
  
-   資料繫結至執行窗格上的控制項。 如需詳細資訊，請參閱[逐步解說： 將資料繫結至 Word 執行窗格上的控制項](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)。  
  
## <a name="see-also"></a>請參閱  
 [執行窗格概觀](../vsto/actions-pane-overview.md)   
 [如何： 執行窗格加入 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [如何： 將執行窗格加入至 Excel 活頁簿](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [如何： 管理執行窗格控制項配置](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [書籤控制項](../vsto/bookmark-control.md)  
  
  