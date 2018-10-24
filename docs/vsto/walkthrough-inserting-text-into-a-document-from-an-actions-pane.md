---
title: 逐步解說： 從 [動作] 窗格中的文件中插入文字
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: ad60aa15b3924bd562ed95c30ed9aaf4adef0133
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862186"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>逐步解說： 從 [動作] 窗格中的文件中插入文字
  本逐步解說示範如何建立 Microsoft Office Word 文件中的 [動作] 窗格。 [動作] 窗格包含兩個控制項收集輸入，然後將文字傳送到文件。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   使用在執行窗格控制項上的 Windows Form 控制項，以設計介面。  
  
-   [動作] 窗格開啟時顯示的應用程式。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## <a name="create-the-project"></a>建立專案  
 第一個步驟是建立 Windows 文件專案。  
  
### <a name="to-create-a-new-project"></a>建立新的專案  
  
1.  建立 Word 文件專案名稱**My 基本的 [動作] 窗格**。 在精靈中，選取**建立新的文件**。 如需詳細資訊，請參閱 <<c0> [ 如何： 在 Visual Studio 中的建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 設計工具中開啟新的 Word 文件，並將**My 基本的 動作 窗格**專案加入**方案總管 中**。  
  
## <a name="add-text-and-bookmarks-to-the-document"></a>加入文件中的文字和書籤  
 [動作] 窗格會將文字傳送至文件中的書籤。 若要設計文件，輸入一些文字，以建立基本表單。  
  
### <a name="to-add-text-to-your-document"></a>將文字加入文件  
  
1. 輸入下列文字插入 Word 文件：  
  
    **2008 年 3 月 21日日**  
  
    **名稱**  
  
    **地址**  
  
    **這是基本的動作 窗格，在 Word 中的範例。**  
  
   您可以加入<xref:Microsoft.Office.Tools.Word.Bookmark>藉由將它從您的文件的控制項**工具箱**在 Visual Studio 中或使用**書籤**在 Word 中的對話方塊。  
  
### <a name="to-add-a-bookmark-control-to-your-document"></a>若要加入書籤控制項加入文件  
  
1.  從**Word 控制項**索引標籤**工具箱**，拖曳<xref:Microsoft.Office.Tools.Word.Bookmark>控制項加入文件。  
  
     **加入書籤控制項** 對話方塊隨即出現。  
  
2.  選取的字詞**名稱**，而不選取段落標記，然後按一下**確定**。  
  
    > [!NOTE]  
    >  段落標記應該是外部書籤。 如果文件中看不到段落標記，按一下**工具**功能表上，指向**Microsoft Office Word Tools** ，然後按一下 **選項**。 按一下 [**檢視**索引標籤，然後選取**段落標記**中的核取方塊**格式化標記**一節**選項**] 對話方塊。  
  
3.  在 **屬性**視窗中，變更**名稱**屬性**Bookmark1**至**showName**。  
  
4.  選取的字詞**地址**，而不需選取的段落標記。  
  
5.  在上**插入**功能區 索引標籤中**連結**群組中，按一下**書籤**。  
  
6.  在 [**書籤**] 對話方塊中，輸入**showAddress**中**書籤名稱**方塊，然後按一下**新增**。  
  
## <a name="add-controls-to-the-actions-pane"></a>將控制項新增至 [動作] 窗格  
 若要設計執行窗格介面，將執行窗格控制項新增至專案，並再將 Windows Form 控制項加入執行窗格控制項。  
  
### <a name="to-add-an-actions-pane-control"></a>若要加入執行窗格控制項  
  
1.  選取 [ **My 基本的 [動作] 窗格**專案中**方案總管] 中**。  
  
2.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
3.  在 **加入新項目** 對話方塊中，按一下**執行窗格控制項**，將控制項**InsertTextControl，** ，按一下 **新增**。  
  
#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>將 Windows Form 控制項加入執行窗格控制項  
  
1.  如果執行窗格控制項不顯示在設計工具中，按兩下**InsertTextControl**。  
  
2.  從**通用控制項**索引標籤**工具箱**，拖曳**標籤**執行窗格控制項的控制項。  
  
3.  變更**文字**屬性的 Label 控制項，以**名稱**。  
  
4.  新增**Textbox**控制項加入執行窗格控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**GetName**|  
    |**Size**|**130, 20**|  
  
5.  新增第二**標籤**控制項加入執行窗格控制項，並變更**文字**屬性設**位址**。  
  
6.  新增第二**Textbox**控制項加入執行窗格控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**GetAddress**|  
    |**接受傳回**|**True**|  
    |**多行**|**True**|  
    |**Size**|**130, 40**|  
  
7.  新增** 按鈕**控制項加入執行窗格控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**addText**|  
    |**Text**|**插入**|  
  
## <a name="add-code-to-insert-text-into-the-document"></a>將程式碼加入文件中插入文字  
 在 [動作] 窗格中，撰寫程式碼中的插入文字的文字方塊內適當<xref:Microsoft.Office.Tools.Word.Bookmark>文件中的控制項。 您可以使用`Globals`類別來存取文件上的控制項從 [動作] 窗格上的控制項。 如需詳細資訊，請參閱 <<c0> [ 全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。  
  
### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>若要從書籤在文件中的 [動作] 窗格中插入文字  
  
1.  將下列程式碼加入<xref:System.Windows.Forms.Control.Click>事件處理常式**addText**  按鈕。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]  
  
2.  在 C# 中，您必須加入用於按鈕 click 事件處理常式。 您可以將此程式碼中的放`InsertTextControl`建構函式呼叫之後`IntializeComponent`。 如需建立事件處理常式的資訊，請參閱[如何： 建立 Office 專案中的事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]  
  
## <a name="add-code-to-show-the-actions-pane"></a>加入程式碼以顯示 [動作] 窗格  
 若要顯示 [動作] 窗格，請新增您所建立的控制項至控制項集合。  
  
### <a name="to-show-the-actions-pane"></a>若要顯示 [動作] 窗格  
  
1.  建立執行窗格控制項中的新執行個體`ThisDocument`類別。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]  
  
2.  將下列程式碼加入<xref:Microsoft.Office.Tools.Word.Document.Startup>事件處理常式`ThisDocument`。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]  
  
## <a name="test-the-application"></a>測試應用程式  
 測試您的文件，確認 [動作] 窗格隨即開啟，在開啟文件，並按一下按鈕時將文字方塊中輸入文字插入書籤。  
  
### <a name="to-test-your-document"></a>測試文件  
  
1.  按下**F5**執行您的專案。  
  
2.  確認 [動作] 窗格已顯示。  
  
3.  在 動作 窗格上的文字方塊中輸入您的名稱和地址，然後按一下 **插入**。  
  
## <a name="next-steps"></a>後續步驟  
 接著可以執行下列一些工作：  
  
-   在 Excel 中建立執行窗格。 如需詳細資訊，請參閱 <<c0> [ 如何： 執行窗格加入 Excel 活頁簿](http://msdn.microsoft.com/62abfce6-e44f-419d-85d8-26bf59f33872)。  
  
-   將資料繫結至執行窗格上的控制項。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 將資料繫結至 Word 執行窗格上的控制項](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)。  
  
## <a name="see-also"></a>另請參閱  
 [執行窗格概觀](../vsto/actions-pane-overview.md)   
 [如何： 加入執行窗格加入 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [如何： 執行窗格加入 Excel 活頁簿](http://msdn.microsoft.com/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [如何： 管理執行窗格控制項配置](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [書籤控制項](../vsto/bookmark-control.md)  
  
  