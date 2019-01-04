---
title: 逐步解說：更新使用選項按鈕的文件中的圖表
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a16a9bffef76d904349f36e7cd2705ef89b13832
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53943232"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>逐步解說：更新使用選項按鈕的文件中的圖表
  本逐步解說示範如何在 Microsoft Office Word 的文件層級自訂中使用選項按鈕，讓使用者可以在文件上選取圖表樣式。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
- 在設計階段，將圖表加入至文件層級專案中的文件。  
  
- 透過將選項按鈕加入至使用者控制項來分組選項按鈕。  
  
- 當選取選項時變更圖表樣式。  
  
  若要查看完整的範例結果，請參閱 Word 控制項範例： [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## <a name="create-the-project"></a>建立專案  
 第一個步驟是建立 Windows 文件專案。  
  
### <a name="to-create-a-new-project"></a>建立新的專案  
  
1.  建立 Word 文件專案名稱**My Chart Options**。 在精靈中，選取**建立新的文件**。 如需詳細資訊，請參閱[＜How to：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 設計工具中開啟新的 Word 文件，並將**My Chart Options**專案加入**方案總管 中**。  
  
## <a name="add-a-chart-to-the-document"></a>將圖表加入至文件  
  
### <a name="to-add-a-chart"></a>加入圖表  
  
1.  在 Word 文件裝載於 Visual Studio 設計工具中，在功能區中，按一下**插入** 索引標籤。  
  
2.  在 **文字**群組中，按一下**插入物件**下拉式按鈕，然後按一下**物件**。  
  
     **物件**對話方塊隨即開啟。  
  
3.  在**物件類型**清單**建立新**索引標籤上，選取**Microsoft Graph 圖表**，然後按一下**確定**。  
  
     將圖表加入至文件的插入點，而**資料工作表** 視窗隨即出現一些預設的資料。  
  
4.  關閉**資料工作表**接受圖表中的預設值，並按一下 若要將焦點移開圖表文件內的視窗。  
  
5.  以滑鼠右鍵按一下圖表，然後按一下**格式化物件**。  
  
6.  上**版面配置**索引標籤**格式化物件**對話方塊中，選取**正方形**，按一下  **確定**。  
  
## <a name="add-a-user-control-to-the-project"></a>將使用者控制項新增至專案  
 文件上的選項按鈕預設並不會互斥。 若要讓選項按鈕正常運作，您可以將選項按鈕加入至使用者控制項，再撰寫程式碼以控制選取範圖。  
  
### <a name="to-add-a-user-control"></a>若要加入使用者控制項  
  
1.  選取 [ **My Chart Options**專案中**方案總管] 中**。  
  
2.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
3.  在**加入新項目** 對話方塊中，按一下**使用者控制項**，將控制項**ChartOptions，** 然後按一下**新增**。  
  
### <a name="to-add-windows-form-controls-to-the-user-control"></a>將 Windows Form 控制項加入至使用者控制項  
  
1.  如果設計工具中看不到 [使用者控制項，請按兩下**ChartOptions**中**方案總管] 中**。  
  
2.  從**通用控制項**索引標籤**工具箱**，將第一個**圓鈕**控制項至使用者控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**columnChart**|  
    |**Text**|**直條圖**|  
  
3.  新增第二**圓鈕**使用者控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**barChart**|  
    |**Text**|**橫條圖**|  
  
4.  新增第三個**圓鈕**使用者控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**lineChart**|  
    |**Text**|**折線圖**|  
  
5.  加入第四個**圓鈕**使用者控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**areaBlockChart**|  
    |**Text**|**區塊圖**|  
  
## <a name="add-references"></a>新增參考  
 若要在文件上的使用者控制項存取圖表，您必須參考`Microsoft.Office.Interop.Graph`專案中的組件。  
  
### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>加入 Microsoft.Office.Interop.Graph 組件的參考  
  
1.  在 [專案] 功能表上，按一下 [新增參考]。  
  
     [加入參考] 對話方塊隨即出現。  
  
2.  在  **.NET**索引標籤上，選取**Microsoft.Office.Interop.Graph** ，按一下 **確定**。 選取版本為 14.0.0.0 的組件。  
  
## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>選取選項按鈕時，變更圖表樣式  
 若要讓按鈕正常運作，請在使用者控制項上建立公用事件，加入屬性以設定選取類型，並為各個選項按鈕建立 `CheckedChanged` 事件的程序。  
  
### <a name="to-create-an-event-and-property-on-a-user-control"></a>在使用者控制項上建立事件和屬性  
  
1.  在 **方案總管**，以滑鼠右鍵按一下 使用者控制項，然後按一下 **檢視程式碼**。  
  
2.  將用於建立 `SelectionChanged` 事件和 `Selection` 屬性的程式碼加入至 `ChartOptions` 類別。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]  
  
### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>處理選項按鈕的 CheckedChange 事件  
  
1.  在 `CheckedChanged` 選項按鈕的 `areaBlockChart` 事件處理常式中設定圖表類型，然後再引發事件。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#10)]  
  
2.  在 `CheckedChanged` 選項按鈕的 `barChart` 事件處理常式中設定圖表類型。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#11)]  
  
3.  在 `CheckedChanged` 選項按鈕的 `columnChart` 事件處理常式中設定圖表類型。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#12)]  
  
4.  在 `CheckedChanged` 選項按鈕的 `lineChart` 事件處理常式中設定圖表類型。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#13)]  
  
5.  在 C# 中，您必須為選項按鈕加入事件處理常式。 您可以將程式碼加入至 `ChartOptions` 建構函式，放在 `InitializeComponent` 的呼叫下方。 如需建立事件處理常式的資訊，請參閱[How to:建立 Office 專案中的事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#14)]  
  
## <a name="add-the-user-control-to-the-document"></a>使用者控制項加入文件  
 當您建置方案時，新的使用者控制項會自動新增至**工具箱**。 然後，您可以將控制項從**工具箱**加入文件。  
  
### <a name="to-add-the-user-control-your-document"></a>將使用者控制項加入至您的文件  
  
1.  在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
     **ChartOptions**使用者控制項加入至**工具箱**。  
  
2.  在 [**方案總管] 中**，以滑鼠右鍵按一下**ThisDocument.vb**或**ThisDocument.cs**，然後按一下**檢視表設計工具**。  
  
3.  拖曳`ChartOptions`控制項從**工具箱**文件。  
  
     在 **屬性**視窗中，您只是將控制項加入文件的名稱`ChartOptions1`。  
  
## <a name="change-the-chart-type"></a>變更圖表類型  
 建立事件處理常式，以根據在使用者控制項中選取的選項來變更圖表類型。  
  
### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>變更顯示在文件中的圖表類型  
  
1.  將下列事件處理常式加入至 `ThisDocument` 類別。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]  
  
2.  在 C# 中，您必須將使用者控制項的事件處理常式加入至 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]  
  
## <a name="test-the-application"></a>測試應用程式  
 現在您可以測試文件，確定是否在選取選項按鈕時正確更新圖表樣式。  
  
### <a name="to-test-your-document"></a>測試文件  
  
1.  按下**F5**執行您的專案。  
  
2.  選取不同的選項按鈕。  
  
3.  確認圖表樣式的變更與所選的項目相符。  
  
## <a name="next-steps"></a>後續步驟  
 接著可以執行下列一些工作：  
  
-   使用按鈕填入文字方塊。 如需詳細資訊，請參閱[逐步解說：使用按鈕文件中的文字方塊中顯示的文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)。  
  
-   從下拉式方塊選取樣式，以變更格式。 如需詳細資訊，請參閱[逐步解說：使用 CheckBox 控制項變更文件格式](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)   
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)   
 [Office 文件上的 Windows Form 控制項的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
