---
title: "逐步解說： 使用功能區設計工具建立自訂索引標籤 |Microsoft 文件"
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
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
ms.assetid: 312865e6-950f-46ab-88de-fe7eb8036bfe
caps.latest.revision: "68"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 811e4eff77780bda2b348c26bb220a29d5fd1731
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer"></a>逐步解說：使用功能區設計工具建立自訂的索引標籤
  您可以使用功能區設計工具，建立自訂索引標籤，然後在其上加入和放置控制項。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   [建立執行窗格](#BKMK_CreateActionsPanes)。  
  
-   [建立自訂索引標籤](#BKMK_CreateCustomTab)。  
  
-   [隱藏和顯示執行窗格，請在 [自訂] 索引標籤上使用按鈕](#BKMK_HideShowActionsPane)。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="creating-an-excel-workbook-project"></a>建立 Excel 活頁簿專案  
 所有 Office 應用程式使用功能區設計工具的步驟大部分相同。 這個範例會使用 Excel 活頁簿。  
  
#### <a name="to-create-an-excel-workbook-project"></a>建立 Excel 活頁簿專案  
  
-   建立名稱的 Excel 活頁簿專案**MyExcelRibbon**。 如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 設計工具中開啟新的活頁簿，並將**MyExcelRibbon**專案加入**方案總管 中**。  
  
##  <a name="BKMK_CreateActionsPanes"></a>建立執行窗格  
 將兩個自訂的執行窗格加入至專案。 您稍後會將兩個用來顯示和隱藏這些執行窗格的按鈕加入至自訂索引標籤。  
  
#### <a name="to-create-actions-panes"></a>建立執行窗格  
  
1.  在 [ **專案** ] 功能表中，選擇 [ **加入新項目**]。  
  
2.  在**加入新項目**對話方塊中，選取**ActionsPaneControl**，然後選擇 **新增**。  
  
     **ActionsPaneControl1.cs**或**ActionsPaneControl1.vb**檔案隨即在設計工具中開啟。  
  
3.  從**通用控制項** 索引標籤**工具箱**，將標籤加入至設計工具介面。  
  
4.  在**屬性**視窗中，將**文字**屬性至 label1 **Actions Pane 1**。  
  
5.  重複步驟 1 到 5，建立第二個執行窗格和標籤。 設定**文字**屬性的第二個標籤**Actions Pane 2**。  
  
##  <a name="BKMK_CreateCustomTab"></a>建立自訂索引標籤  
 其中一個 Office 應用程式設計方針是使用者應一律具有 Office 應用程式 UI 的控制項。 若要為執行窗格加入這個功能，您可以加入顯示和隱藏功能區上自訂索引標籤的每個執行窗格的按鈕。 若要建立自訂索引標籤，加入**功能區 （視覺化設計工具）**項目加入專案。 設計工具可協助您加入及定位控制項、設定控制項屬性及處理控制項事件。  
  
#### <a name="to-create-a-custom-tab"></a>建立自訂索引標籤  
  
1.  在 [ **專案** ] 功能表中，選擇 [ **加入新項目**]。  
  
2.  選取 [ **加入新項目** ] 對話方塊中的 [ **功能區 (視覺化設計工具)**]。  
  
3.  變更至新的功能區的名稱**MyRibbon**，然後選擇 **新增**。  
  
     **MyRibbon.cs** 或 **MyRibbon.vb** 檔案會在功能區設計工具中開啟，並顯示預設索引標籤和群組。  
  
4.  在 [功能區設計工具] 中，選擇預設索引標籤。  
  
5.  在**屬性**視窗中，展開  **ControlId**屬性，並將其設定**ControlIdType**屬性**自訂**。  
  
6.  設定**標籤**屬性**我的自訂索引標籤**。  
  
7.  在功能區設計工具中，選擇  **group1**。  
  
8.  在**屬性**視窗中，將**標籤**至**Actions Pane Manager**。  
  
9. 從**Office 功能區控制項** 索引標籤**工具箱**，拖曳按鈕拖曳至**group1**。  
  
10. 選取**button1**。  
  
11. 在**屬性**視窗中，將**標籤**至**Show Actions Pane 1**。  
  
12. 新增第二個按鈕**group1**，並設定**標籤**屬性**Show Actions Pane 2**。  
  
13. 從**Office 功能區控制項** 索引標籤**工具箱**，拖曳**ToggleButton**控制項拖曳至**group1**。  
  
14. 設定**標籤**屬性**Hide Actions Pane**。  
  
##  <a name="BKMK_HideShowActionsPane"></a>隱藏和顯示執行窗格所使用的自訂索引標籤上的按鈕  
 最後一個步驟是加入回應使用者的程式碼。 針對兩個按鈕的 <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> 事件和切換按鈕的 <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> 事件加入事件處理常式。 將程式碼加入至這些事件處理常式以啟用隱藏和顯示執行窗格。  
  
#### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>使用自訂索引標籤中的按鈕隱藏和顯示執行窗格  
  
1.  在**方案總管 中**，開啟 MyRibbon.cs 或 MyRibbon.vb 的捷徑功能表，然後選擇**檢視程式碼**。  
  
2.  將下列程式碼加入至 `MyRibbon` 類別的頂端。 這個程式碼會建立兩個執行窗格物件。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]  
  
3.  以下列程式碼取代 `MyRibbon_Load` 方法。 這個程式碼會將執行窗格物件加入至 <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> 集合，並且隱藏物件不提供檢視。 Visual C# 程式碼也會將委派附加至數個功能區控制項事件。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]  
  
4.  將下列三個事件處理常式方法加入至 `MyRibbon` 類別。 這些方法會處理兩個按鈕的 <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> 事件及切換按鈕的 <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> 事件。 button1 和 button2 的事件處理常式會顯示交替的執行窗格。 toggleButton1 的事件處理常式則會顯示和隱藏作用中的執行窗格。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]  
  
## <a name="testing-the-custom-tab"></a>測試自訂索引標籤  
 當您執行專案時，Excel 會啟動，而**我的自訂索引標籤**索引標籤會出現在功能區上。 選擇按鈕上**我的自訂索引標籤**來顯示和隱藏執行窗格。  
  
#### <a name="to-test-the-custom-tab"></a>測試自訂索引標籤  
  
1.  請按 F5 執行您的專案。  
  
2.  選擇**我的自訂索引標籤** 索引標籤。  
  
3.  在**Custom Actions Pane Manager**群組中，選擇**Show Actions Pane 1**。  
  
     [動作] 窗格隨即出現，並顯示標籤**Actions Pane 1**。  
  
4.  選擇**Show Actions Pane 2**。  
  
     [動作] 窗格隨即出現，並顯示標籤**Actions Pane 2**。  
  
5.  選擇**隱藏 [動作] 窗格**。  
  
     執行窗格將不再顯示。  
  
## <a name="next-steps"></a>後續步驟  
 您可以透過下列主題，進一步了解自訂 Office UI 的方式：  
  
-   將內容為主的 UI 加入至任何文件層級的自訂。 如需詳細資訊，請參閱 [Actions Pane Overview](../vsto/actions-pane-overview.md)。  
  
-   展開標準或自訂的 Microsoft Office Outlook 表單。 如需詳細資訊，請參閱[逐步解說： 設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [功能區概觀](../vsto/ribbon-overview.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [自訂 Outlook 功能區](../vsto/customizing-a-ribbon-for-outlook.md)   
 [如何： 開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [如何： 變更功能區上的索引標籤的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [如何： 自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)   
 [如何： 將控制項加入 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [功能區物件模型概觀](../vsto/ribbon-object-model-overview.md)  
  
  