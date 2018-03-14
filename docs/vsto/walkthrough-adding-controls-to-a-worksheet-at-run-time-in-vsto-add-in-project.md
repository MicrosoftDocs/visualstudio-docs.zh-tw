---
title: "逐步解說： 將控制項加入工作表，在執行階段，在 VSTO 增益集專案 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
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
- add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: f32db4aa6b547f1555fbccc9cb03c00998169eaa
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project"></a>逐步解說：在執行階段於 VSTO 增益集專案中，將控制項加入工作表中
  您可以使用 Excel VSTO 增益集，將控制項加入任何開啟的工作表中。 本逐步解說將示範如何使用功能區，讓使用者將 <xref:Microsoft.Office.Tools.Excel.Controls.Button>、<xref:Microsoft.Office.Tools.Excel.NamedRange> 及 <xref:Microsoft.Office.Tools.Excel.ListObject> 加入工作表。 如需資訊，請參閱[將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
 **適用於：**本主題資訊適用於 Excel VSTO 增益集專案。 如需詳細資訊，請參閱[依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)。  
  
 這個逐步解說將說明下列工作：  
  
-   提供可將控制項加入工作表的使用者介面 (UI)。  
  
-   將控制項加入工作表。  
  
-   移除工作表的控制項。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## <a name="creating-a-new-excel-vsto-add-in-project"></a>建立新的 Excel VSTO 增益集專案  
 請從建立新的 Excel VSTO 增益集專案開始。  
  
#### <a name="to-create-a-new-excel-vsto-add-in-project"></a>若要建立新的 Excel VSTO 增益集專案  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，建立具有名稱的 Excel VSTO 增益集專案**為 ExcelDynamicControls**。 如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  將參考加入**Microsoft.Office.Tools.Excel.v4.0.Utilities.dll**組件。 本逐步解說稍後會需要用到此參考，以透過程式設計的方式將 Windows Form 控制項加入工作表。  
  
## <a name="providing-a-ui-to-add-controls-to-a-worksheet"></a>提供可將控制項加入工作表的 UI  
 將自訂索引標籤加入 Excel 功能區。 使用者可以選取索引標籤上的核取方塊，將控制項加入工作表。  
  
#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>若要提供可將控制項加入工作表的 UI  
  
1.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
2.  在**加入新項目**對話方塊中，選取**功能區 （視覺化設計工具）**，然後按一下 **新增**。  
  
     名為**Ribbon1.cs**或**Ribbon1.vb**會在功能區設計工具中開啟，並顯示預設索引標籤和群組。  
  
3.  從**Office 功能區控制項** 索引標籤**工具箱**，將核取方塊控制項拖曳至**group1**。  
  
4.  按一下 [CheckBox1]  予以選取。  
  
5.  在 [屬性]  視窗中變更下列屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**Button**|  
    |**Label**|**Button**|  
  
6.  將第二個核取方塊加入 [group1] ，然後變更下列屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**NamedRange**|  
    |**Label**|**NamedRange**|  
  
7.  將第三個核取方塊加入**group1**，然後變更下列屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**ListObject**|  
    |**Label**|**ListObject**|  
  
## <a name="adding-controls-to-the-worksheet"></a>將控制項加入工作表  
 您只能將 Managed 控制項加入做為容器的主項目。 因為 VSTO 增益集專案會使用任何開啟的工作表，所以 VSTO 增益集會將工作表轉換為主項目後，或取得現有主項目，再加入控制項。 將程式碼加入每個控制項的 Click 事件處理常式，以根據開啟的工作表，產生 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。 然後，將 <xref:Microsoft.Office.Tools.Excel.Controls.Button>、<xref:Microsoft.Office.Tools.Excel.NamedRange> 和 <xref:Microsoft.Office.Tools.Excel.ListObject> 加入工作表中目前選取的範圍。  
  
#### <a name="to-add-controls-to-a-worksheet"></a>若要將控制項加入工作表  
  
1.  在功能區設計工具中，按兩下**按鈕**。  
  
     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click>事件處理常式**按鈕**核取方塊會開啟程式碼編輯器中。  
  
2.  以下列程式碼取代 `Button_Click` 事件處理常式。  
  
     此程式碼會使用 `GetVstoObject` 方法來取得代表活頁簿中第一個工作表的主項目，然後將 <xref:Microsoft.Office.Tools.Excel.Controls.Button> 控制項加入目前選取的儲存格。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#2)]  
  
3.  在**方案總管 中**，選取 Ribbon1.cs 或 Ribbon1.vb。  
  
4.  在**檢視**功能表上，按一下 **設計師**。  
  
5.  在功能區設計工具中，按兩下**NamedRange**。  
  
6.  以下列程式碼取代 `NamedRange_Click` 事件處理常式。  
  
     此程式碼會使用 `GetVstoObject` 方法來取得代表活頁簿中第一個工作表的主項目，然後為目前選取的儲存格定義 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#3)]  
  
7.  在功能區設計工具中，按兩下**ListObject**。  
  
8.  以下列程式碼取代 `ListObject_Click` 事件處理常式。  
  
     此程式碼會使用 `GetVstoObject` 方法來取得代表活頁簿中第一個工作表的主項目，然後為目前選取的儲存格定義 <xref:Microsoft.Office.Tools.Excel.ListObject>。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#4)]  
  
9. 在功能區程式碼檔的頂端加入下列陳述式。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#1)]  
  
## <a name="removing-controls-from-the-worksheet"></a>移除工作表的控制項  
 當工作表儲存和關閉時，都不會保存控制項。 您應該在儲存工作表之前，以程式設計方式移除所有產生的 Windows Form 控制項，否則該活頁簿下次開啟時，只會顯示控制項的外框。 請將程式碼加入 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> 事件，以便從產生之主項目的控制項集合移除 Windows Form 控制項。 如需詳細資訊，請參閱 [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md)。  
  
#### <a name="to-remove-controls-from-the-worksheet"></a>若要移除工作表的控制項  
  
1.  在**方案總管 中**，選取 ThisAddIn.cs 或 ThisAddIn.vb。  
  
2.  在**檢視**功能表上，按一下 **程式碼**。  
  
3.  將下列方法加入 ThisAddin 類別。 此程式碼會取得活頁簿中的第一個工作表，然後使用 `HasVstoObject` 方法檢查工作表是否具有產生的工作表物件。 如果產生的工作表物件具有控制項，程式碼便會取得該工作表物件，並逐一查看控制項集合，同時移除控制項。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#6)]  
  
4.  在 C# 中，您必須建立 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> 事件的事件處理常式。 您可以將這個程式碼放入 `ThisAddIn_Startup` 方法中。 如需有關如何建立事件處理常式的詳細資訊，請參閱[How to： 在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。 以下列程式碼取代 `ThisAddIn_Startup` 方法。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#5)]  
  
## <a name="testing-the-solution"></a>測試方案  
 從功能區上的自訂索引標籤選取控制項，將此控制項加入工作表。 當您儲存工作表時，這些控制項將會被移除。  
  
#### <a name="to-test-the-solution"></a>若要測試方案  
  
1.  請按 F5 執行您的專案。  
  
2.  選取 Sheet1 中的任何儲存格。  
  
3.  按一下 [增益集]  索引標籤。  
  
4.  在**group1**群組中，按一下**按鈕**。  
  
     按鈕隨即出現在選取的儲存格中。  
  
5.  選取 Sheet1 中的其他儲存格。  
  
6.  在**group1**群組中，按一下**NamedRange**。  
  
     隨即定義選定儲存格的已命名範圍。  
  
7.  選取 Sheet1 中的一連串儲存格。  
  
8.  在**group1**群組中，按一下**ListObject**。  
  
     隨即加入選定儲存格的清單物件。  
  
9. 儲存工作表。  
  
     您加入 Sheet1 的控制項將不再出現。  
  
## <a name="next-steps"></a>後續步驟  
 您可以透過下列主題，進一步了解 Excel VSTO 增益集專案：  
  
-   若要深入了解如何將控制項儲存至工作表，請參閱 Excel VSTO 增益集動態控制項範例： [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)。  
  
## <a name="see-also"></a>請參閱  
 [Excel 方案](../vsto/excel-solutions.md)   
 [Windows Form 控制項，在 Office 文件概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [ListObject 控制項](../vsto/listobject-control.md)  
  
  