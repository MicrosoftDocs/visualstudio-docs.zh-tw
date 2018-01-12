---
title: "逐步解說： 自動化從自訂工作窗格應用程式 |Microsoft 文件"
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
- task panes [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio], custom task panes
- automating Office applications
- custom task panes [Office development in Visual Studio], automating applications
- custom task panes [Office development in Visual Studio], PowerPoint
- task panes [Office development in Visual Studio], automating applications
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 86f925cda43bf73354b94ecc966cdcae1a0c3ddd
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-automating-an-application-from-a-custom-task-pane"></a>逐步解說：運用自訂工作窗格自動化應用程式
  此逐步解說示範如何建立會自動化 PowerPoint 的自訂工作窗格。 自訂工作窗格會在使用者按一下自訂工作窗格上的 <xref:System.Windows.Forms.MonthCalendar> 控制項時，將日期插入投影片。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 雖然這個逐步解說特地使用 PowerPoint，但所示範的概念同樣適用以上所列的任何應用程式。  
  
 這個逐步解說將說明下列工作：  
  
-   設計自訂工作窗格的使用者介面。  
  
-   從自訂工作窗格自動化 PowerPoint。  
  
-   在 PowerPoint 中顯示自訂工作窗格。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft PowerPoint 2010 或 [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)]。  
  
## <a name="creating-the-add-in-project"></a>建立增益集專案  
 第一個步驟是建立 PowerPoint 的 VSTO 增益集專案。  
  
#### <a name="to-create-a-new-project"></a>建立新的專案  
  
1.  使用 [PowerPoint 增益集] 專案範本建立名為 **MyAddIn**的 PowerPoint VSTO 增益集專案。 如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會開啟 **ThisAddIn.cs** 或 **ThisAddIn.vb** 程式碼檔案，並將 **MyAddIn** 專案加入 [方案總管] 。  
  
## <a name="designing-the-user-interface-of-the-custom-task-pane"></a>設計自訂工作窗格的使用者介面  
 自訂工作窗格沒有視覺化的設計工具，但是您可以根據需要設計使用者控制項的版面配置。 稍後在本逐步解說中，您會在自訂工作窗格中加入使用者控制項。  
  
#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>設計自訂工作窗格的使用者介面  
  
1.  在 [專案]  功能表上，按一下 [加入使用者控制項] 。  
  
2.  在 [加入新項目]  對話方塊中，將使用者控制項的名稱變更為 **MyUserControl**，然後按一下 [加入] 。  
  
     使用者控制項隨即在設計工具中開啟。  
  
3.  從 [工具箱]  的 [通用控制項] 索引標籤，將 **MonthCalendar** 控制項拖曳至使用者控制項。  
  
     如果 **MonthCalendar** 控制項大於使用者控制項的設計介面，請配合 **MonthCalendar** 控制項調整使用者控制項的大小。  
  
## <a name="automating-powerpoint-from-the-custom-task-pane"></a>從自訂工作窗格自動化 PowerPoint  
 VSTO 增益集的用途是要在現用簡報的第一張投影片上放入選取的日期。 請使用控制項的 <xref:System.Windows.Forms.MonthCalendar.DateChanged> 事件，在選取的日期變更時加入該日期。  
  
#### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>若要從自訂工作窗格自動化 PowerPoint  
  
1.  在設計工具中，按兩下 <xref:System.Windows.Forms.MonthCalendar> 控制項。  
  
     **MyUserControl.cs** 或 **MyUserControl.vb** 檔案隨即開啟，而且系統也會建立 <xref:System.Windows.Forms.MonthCalendar.DateChanged> 事件的事件處理常式。  
  
2.  將下列程式碼加入檔案的頂端。 此程式碼會建立 <xref:Microsoft.Office.Core> 和 <xref:Microsoft.Office.Interop.PowerPoint> 命名空間的別名。  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#1)]  
  
3.  將下列程式碼加入 `MyUserControl` 類別。 此程式碼會將 <xref:Microsoft.Office.Interop.PowerPoint.Shape> 物件宣告為 `MyUserControl`的成員。 在下列步驟中，您會使用此 <xref:Microsoft.Office.Interop.PowerPoint.Shape> ，在現用簡報的投影片中加入文字方塊。  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#2)]  
  
4.  以下列程式碼取代 `monthCalendar1_DateChanged` 事件處理常式。 此程式碼會在現用簡報的第一張投影片中加入文字方塊，然後在文字方塊中加入目前選取的日期。 這段程式碼會使用 `Globals.ThisAddIn` 物件來存取 PowerPoint 的物件模型。  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#3)]  
  
5.  在 [方案總管] 中，以滑鼠右鍵按一下 **MyAddIn** 專案，然後按一下 [建置] 。 確認專案建置無誤。  
  
## <a name="displaying-the-custom-task-pane"></a>顯示自訂工作窗格  
 若要在 VSTO 增益集啟動時顯示自訂工作窗格，請在 VSTO 增益集的 <xref:Microsoft.Office.Tools.AddIn.Startup> 事件處理常式中，將使用者控制項加入工作窗格。  
  
#### <a name="to-display-the-custom-task-pane"></a>若要顯示自訂工作窗格  
  
1.  展開 [方案總管] 中的 [PowerPoint] 。  
  
2.  以滑鼠右鍵按一下 **ThisAddIn.cs** 或 **ThisAddIn.vb** ，然後按一下 [檢視程式碼] 。  
  
3.  將下列程式碼加入 `ThisAddIn` 類別。 此程式碼會將 `MyUserControl` 和 <xref:Microsoft.Office.Tools.CustomTaskPane> 的執行個體宣告為 `ThisAddIn` 類別的成員。  
  
     [!code-vb[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#4)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#4)]  
  
4.  以下列程式碼取代 `ThisAddIn_Startup` 事件處理常式。 此程式碼會建立新的 <xref:Microsoft.Office.Tools.CustomTaskPane> ，方法是將 `MyUserControl` 物件加入 `CustomTaskPanes` 集合。 程式碼也會顯示工作窗格。  
  
     [!code-vb[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#5)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#5)]  
  
## <a name="testing-the-add-in"></a>測試增益集  
 當您執行專案時，PowerPoint 會開啟且 VSTO 增益集會顯示自訂工作窗格。 請按一下 <xref:System.Windows.Forms.MonthCalendar> 控制項來測試程式碼。  
  
#### <a name="to-test-your-vsto-add-in"></a>測試 VSTO 增益集  
  
1.  請按 F5 執行您的專案。  
  
2.  確認自訂工作窗格已顯示。  
  
3.  在工作窗格上的 <xref:System.Windows.Forms.MonthCalendar> 控制項中，按一下日期。  
  
     現用簡報的第一張投影片中隨即會插入該日期。  
  
## <a name="next-steps"></a>後續步驟  
 您可以透過下列主題，進一步了解如何建立自訂工作窗格：  
  
-   在 VSTO 增益集中為不同應用程式建立自訂工作窗格。 如需支援自訂工作窗格之應用程式的詳細資訊，請參閱[自訂工作窗格](../vsto/custom-task-panes.md)。  
  
-   建立可用來隱藏或顯示自訂工作窗格的功能區按鈕。 如需詳細資訊，請參閱 [Walkthrough: Synchronizing a Custom Task Pane with a Ribbon Button](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)。  
  
-   針對在 Outlook 中開啟的每一封電子郵件建立自訂工作窗格。 如需詳細資訊，請參閱 [Walkthrough: Displaying Custom Task Panes with E-Mail Messages in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)。  
  
## <a name="see-also"></a>請參閱  
 [自訂工作窗格](../vsto/custom-task-panes.md)   
 [如何： 應用程式中加入自訂工作窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [逐步解說： 使用功能區按鈕同步處理自訂工作窗格](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [逐步解說：在 Outlook 中的電子郵件訊息顯示自訂工作窗格](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
  
  