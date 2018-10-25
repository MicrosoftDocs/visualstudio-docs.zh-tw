---
title: 逐步解說：使用選項按鈕更新工作表中的圖表
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5aff631d8c9b6bd65b8ae91c5d936d2669764791
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866437"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>逐步解說：使用選項按鈕更新工作表中的圖表
  本逐步解說會示範使用 Microsoft Office Excel 工作表上的選項按鈕，以讓使用者快速切換選項之間的基本概念。 在此情況下，選項會變更圖表的樣式。  

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  

 若要查看完整的範例結果，請參閱 Excel 控制項範例： [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)。  

 這個逐步解說將說明下列工作：  

-   您可以將選項按鈕群組加入工作表。  

-   當選取選項時變更圖表樣式。  

> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  

## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  

## <a name="add-a-chart-to-a-worksheet"></a>將圖表加入至工作表  
 您可以建立自訂現有的活頁簿的 Excel 活頁簿專案。 在本逐步解說中，您會將圖表加入至活頁簿，然後再使用新的 Excel 方案中的 此活頁簿。 本逐步解說中的資料來源是名為的工作表**圖表資料**。  

### <a name="to-add-the-data"></a>加入的資料  

1. 開啟 Microsoft Excel。  

2. 以滑鼠右鍵按一下**Sheet3**索引標籤，然後再按一下**重新命名**快顯功能表。  

3. 重新命名工作表以**圖表資料**。  

4. 新增下列資料以**圖表資料**使用 A4 的儲存格的左上角和 E8 右下角。  

   ||Q1|第 2 季|第 3 季|Q4|  
   |-|--------|--------|--------|--------|  
   |西部|500|550|550|600|  
   |東部|600|625|675|700|  
   |中北部|450|470|490|510|  
   |南部|800|750|775|790|  

   接下來，將圖表加入要顯示資料的第一個工作表。  

### <a name="to-add-a-chart-in-excel"></a>若要在 Excel 中加入圖表  

1.  在上**插入**索引標籤**圖表**群組中，按一下**資料行**，然後按一下**所有圖表類型**。  

2.  在 [**插入圖表**] 對話方塊中，按一下**確定**。  

3.  在 **設計**索引標籤中，於**資料**群組中，按一下**選取資料**。  

4.  在 **選取資料來源**對話方塊中，按一下**Chartdata 範圍**方塊，然後清除任何預設選取項目。  

5.  在 **圖表資料**工作表中，選取包含數字，其中包括 A4 左上角到 E8 右下角中的資料格區塊。  

6.  在 [**選取資料來源**] 對話方塊中，按一下**確定**。  

7.  調整圖表的位置，以便配合儲存格的右上角**E2**。  

8.  將檔案儲存到 C 磁碟機並將它命名**ExcelChart.xlsx**。  

9. 結束 Excel。  

## <a name="create-a-new-project"></a>建立新專案  
 在此步驟中，您將建立的 Excel 活頁簿專案，根據**ExcelChart**活頁簿。  

### <a name="to-create-a-new-project"></a>建立新的專案  

1.  建立 Excel 活頁簿專案同名**我的 Excel 圖表**。 在精靈中，選取**複製現有文件**。  

     如需詳細資訊，請參閱 <<c0> [ 如何： 在 Visual Studio 中的建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  

2.  按一下 **瀏覽**按鈕並瀏覽至您稍早在本逐步解說中建立的活頁簿。  

3.  按一下 [確定 **Deploying Office Solutions**]。  

     Visual Studio 設計工具中開啟新的 Excel 活頁簿，並將**我的 Excel 圖表**專案加入**方案總管 中**。  

## <a name="set-properties-of-the-chart"></a>設定屬性的圖表  
 當您建立新的 Excel 活頁簿專案，會使用現有的活頁簿時，主控制項會自動建立所有具名的範圍、 list 物件和活頁簿中的圖表。 您可以變更的名稱<xref:Microsoft.Office.Tools.Excel.Chart>使用的控制項**屬性**視窗。  

### <a name="to-change-the-name-of-the-chart-control"></a>若要變更圖表控制項的名稱  

1.  選取 <xref:Microsoft.Office.Tools.Excel.Chart>控制項設計工具中，並變更下列屬性中的**屬性**視窗。  

    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**dataChart**|  
    |**HasLegend**|**false**|  

## <a name="add-controls"></a>加入控制項  
 此工作表會使用選項按鈕，讓使用者快速變更圖表樣式的方式。 不過，必須是獨佔的選項按鈕 — 選取一個按鈕時，可以同時選取 沒有其他群組中的按鈕。 此行為不會根據預設，當您將數個選項按鈕新增至工作表。  

 加入此行為是將使用者控制項上的，選項按鈕的一種方法撰寫使用者控制項，背後的程式碼，然後將使用者控制項加入工作表。  

### <a name="to-add-a-user-control"></a>若要加入使用者控制項  

1.  選取 [**我的 Excel 圖表**專案中**方案總管] 中**。  

2.  在 [專案]  功能表中，按一下 [加入新項目] 。  

3.  在**加入新項目** 對話方塊中，按一下**使用者控制項**，將控制項**ChartOptions，** 然後按一下**新增**。  

### <a name="to-add-radio-buttons-to-the-user-control"></a>若要加入至使用者控制項的選項按鈕  

1. 如果設計工具中看不到 [使用者控制項，請按兩下**ChartOptions**中**方案總管] 中**。  

2. 從**通用控制項**索引標籤**工具箱**，拖曳**圓鈕**控制項至使用者控制項，並變更下列屬性。  


   | 屬性 | 值 |
   |----------|------------------|
   | **名稱** | **columnChart** |
   | **Text** | **直條圖** |


3. 將第二個按鈕加入至使用者控制項，並變更下列屬性。  


   | 屬性 | 值 |
   |----------|---------------|
   | **名稱** | **barChart** |
   | **Text** | **橫條圖** |


4. 將第三個選項按鈕加入至使用者控制項，並變更下列屬性。  


   | 屬性 | 值 |
   |----------|----------------|
   | **名稱** | **lineChart** |
   | **Text** | **折線圖** |


5. 第四個按鈕加入使用者控制項，並變更下列屬性。  

   |屬性|值|  
   |--------------|-----------|  
   |**名稱**|**areaBlockChart**|  
   |**Text**|**區塊圖**|  

   接下來，撰寫程式碼來更新圖表，按一下選項按鈕時。  

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>選取選項按鈕時，變更圖表樣式  
 現在您可以加入程式碼來變更圖表樣式。 若要這樣做，建立使用者控制項上的公用事件、 加入屬性以設定選取項目類型，以及建立事件處理常式`CheckedChanged`選項按鈕的每個事件。  

### <a name="to-create-an-event-and-property-on-a-user-control"></a>在使用者控制項上建立事件和屬性  

1.  在 **方案總管**，以滑鼠右鍵按一下 使用者控制項，然後按一下 **檢視程式碼**。  

2.  將程式碼加入`ChartOptions`類別來建立`SelectionChanged`事件和`Selection`屬性。  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]  

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>若要處理的選項按鈕 CheckedChanged 事件  

1.  在 `CheckedChanged` 選項按鈕的 `areaBlockChart` 事件處理常式中設定圖表類型，然後再引發事件。  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]  

2.  在 `CheckedChanged` 選項按鈕的 `barChart` 事件處理常式中設定圖表類型。  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]  

3.  在 `CheckedChanged` 選項按鈕的 `columnChart` 事件處理常式中設定圖表類型。  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]  

4.  在 `CheckedChanged` 選項按鈕的 `lineChart` 事件處理常式中設定圖表類型。  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]  

5.  在 C# 中，您必須為選項按鈕加入事件處理常式。 您可以將程式碼加入至 `ChartOptions` 建構函式，放在 `InitializeComponent` 的呼叫下方。 如需有關如何建立事件處理常式的資訊，請參閱 <<c0> [ 如何： 建立 Office 專案中的事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]  

## <a name="add-the-user-control-to-the-worksheet"></a>將使用者控制項加入工作表  
 當您建置方案時，新的使用者控制項會自動新增至**工具箱**。 然後，您可以將控制項從**工具箱**加入工作表。  

### <a name="to-add-the-user-control-your-worksheet"></a>若要將使用者控制項加入工作表  

1.  在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  

     **ChartOptions**使用者控制項加入至**工具箱**。  

2.  在 [**方案總管] 中**，以滑鼠右鍵按一下**Sheet1.vb**或**Sheet1.cs**，然後按一下**檢視表設計工具**。  

3.  拖曳**ChartOptions**控制從**工具箱**至工作表。  

     新的控制項，名為`my_Excel_Chart_ChartOptions1`加入至專案。  

4.  變更控制項的名稱**ChartOptions1**。  

## <a name="change-the-chart-type"></a>變更圖表類型  
 若要變更圖表類型，建立事件處理常式，以設定使用者控制項中選取的選項根據樣式。  

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>若要變更的工作表中顯示的圖表類型  

1.  將下列事件處理常式加入至 `Sheet1` 類別。  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]  

2.  在 C# 中，您必須將使用者控制項的事件處理常式<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>事件，如下所示。 如需有關如何建立事件處理常式的資訊，請參閱 <<c0> [ 如何： 建立 Office 專案中的事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]  

## <a name="test-the-application"></a>測試應用程式  
 您現在可以測試您的活頁簿，以確認當您選取的選項按鈕時，圖表會正確套用樣式。  

### <a name="to-test-your-workbook"></a>測試您的活頁簿  

1.  按下**F5**執行您的專案。  

2.  選取不同的選項按鈕。  

3.  確認圖表樣式的變更與所選的項目相符。  

## <a name="next-steps"></a>後續步驟  
 本逐步解說會示範在工作表上使用選項按鈕和圖表樣式的基本概念。 接著可以執行下列一些工作：  

-   部署專案。 如需詳細資訊，請參閱 <<c0> [ 部署 Office 方案](../vsto/deploying-an-office-solution.md)。  

-   使用按鈕填入文字方塊。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 使用按鈕在工作表中的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)。  

-   變更格式化工作表上使用核取方塊。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 使用 CheckBox 控制項格式變更工作表設定](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)。  

## <a name="see-also"></a>另請參閱  
 [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)  

