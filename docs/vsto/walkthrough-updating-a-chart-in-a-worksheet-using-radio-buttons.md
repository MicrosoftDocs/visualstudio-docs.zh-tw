---
title: 使用選項按鈕更新工作表中的圖表
description: 瞭解在 Microsoft Excel 工作表上使用選項按鈕的基本概念，讓使用者能夠在選項之間快速切換。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4e375f394cd3d8be35ace8e3df07920fb824a07e
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526067"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>逐步解說：使用選項按鈕更新工作表中的圖表
  本逐步解說示範在 Microsoft Office Excel 工作表上使用選項按鈕的基本概念，讓使用者能夠在選項之間快速切換。 在此情況下，選項會變更圖表的樣式。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 若要以完整範例的形式查看結果，請參閱 [Office 開發範例和](../vsto/office-development-samples-and-walkthroughs.md)逐步解說中的 Excel 控制項範例。

 本逐步解說將說明下列工作：

- 在工作表中加入一組選項按鈕。

- 當選取選項時變更圖表樣式。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

## <a name="add-a-chart-to-a-worksheet"></a>將圖表加入至工作表
 您可以建立自訂現有活頁簿的 Excel 活頁簿專案。 在這個逐步解說中，您會將圖表加入至活頁簿，然後在新的 Excel 方案中使用此活頁簿。 本逐步解說中的資料來源是名為 **Chart 的資料** 工作表。

### <a name="to-add-the-data"></a>若要加入資料

1. 開啟 Microsoft Excel。

2. 以滑鼠右鍵按一下 [ **Sheet3** ] 索引標籤，然後按一下快捷方式功能表上的 [ **重新命名** ]。

3. 將工作表重新命名為 **圖表的資料**。

4. 將下列資料新增至 **圖表的資料** ，並將儲存格 A4 設為左上角，然後 E8 右下角。

   |區域/季|Q1|Q2|Q3|Q4|
   |-|--------|--------|--------|--------|
   |West|500|550|550|600|
   |東|600|625|675|700|
   |北|450|470|490|510|
   |南|800|750|775|790|

   接下來，將圖表加入至第一個工作表以顯示資料。

### <a name="to-add-a-chart-in-excel"></a>在 Excel 中加入圖表

1. 在 [ **插入** ] 索引標籤的 [ **圖表** ] 群組中，按一下 [資料 **行**]，然後按一下 [ **所有圖表類型**]。

2. 在 [ **插入圖表** ] 對話方塊中，按一下 **[確定]**。

3. 在 [ **設計** ] 索引標籤的 [ **資料** ] 群組中，按一下 [ **選取資料**]。

4. 在 [ **選取資料來源** ] 對話方塊中，按一下 [ **Chartdata 範圍** ] 方塊，並清除任何預設選項。

5. 在 [ **圖表的資料** ] 工作表中，選取包含數位的資料格區塊，其中包含要在右下角 E8 的左上角的 A4。

6. 在 [ **選取資料來源** ] 對話方塊中，按一下 **[確定]**。

7. 調整圖表的位置，讓右上角與儲存格 **E2** 對齊。

8. 將您的檔案儲存到 C 磁片磁碟機，並將它命名 **ExcelChart.xlsx**。

9. 結束 Excel。

## <a name="create-a-new-project"></a>建立新專案
 在這個步驟中，您將根據 **ExcelChart** 活頁簿建立 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 建立名為 **My Excel Chart** 的 Excel 活頁簿專案。 在嚮導中，選取 [ **複製現有檔**]。

     如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

2. 按一下 [ **流覽]** 按鈕，流覽至您稍早在本逐步解說中建立的活頁簿。

3. 按一下 [確定]。

     Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 [ **我的 Excel 圖表** ] 專案加入 **方案總管**。

## <a name="set-properties-of-the-chart"></a>設定圖表的屬性
 當您使用現有的活頁簿建立新的 Excel 活頁簿專案時，系統會自動為活頁簿中的所有命名範圍、清單物件和圖表建立主控制項。 您可以 <xref:Microsoft.Office.Tools.Excel.Chart> 使用 [ **屬性** ] 視窗來變更控制項的名稱。

### <a name="to-change-the-name-of-the-chart-control"></a>變更 Chart 控制項的名稱

1. <xref:Microsoft.Office.Tools.Excel.Chart>在設計工具中選取控制項，並在 [**屬性**] 視窗中變更下列屬性。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**dataChart**|
    |**HasLegend**|**false**|

## <a name="add-controls"></a>新增控制項
 此工作表使用選項按鈕，讓使用者有辦法快速變更圖表樣式。 不過，選項按鈕必須是互斥的，當選取一個按鈕時，就不能同時選取群組中的其他按鈕。 當您在工作表中加入數個選項按鈕時，預設不會發生這種行為。

 加入此行為的其中一種方式是將使用者控制項上的選項按鈕分組、在使用者控制項後方撰寫程式碼，然後將使用者控制項加入工作表。

### <a name="to-add-a-user-control"></a>若要加入使用者控制項

1. 在 **方案總管** 中選取 [**我的 Excel 圖表**] 專案。

2. 在 [專案] 功能表上，按一下 [加入新項目]。

3. 在 [ **加入新專案** ] 對話方塊中，按一下 [ **使用者控制項**]，將控制項命名為 **ChartOptions，** 然後按一下 [ **加入**]。

### <a name="to-add-radio-buttons-to-the-user-control"></a>將選項按鈕加入至使用者控制項

1. 如果在設計工具中看不到使用者控制項，請按兩下 **方案總管** 中的 [ **ChartOptions** ]。

2. 從 [**工具箱**] 的 [**通用控制項**] 索引標籤，將 **選項按鈕** 控制項拖曳至使用者控制項，並變更下列屬性。

   | 屬性 | 值 |
   |----------|------------------|
   | **名稱** | **columnChart** |
   | **Text** | **直條圖** |

3. 將第二個選項按鈕加入至使用者控制項，並變更下列屬性。

   | 屬性 | 值 |
   |----------|---------------|
   | **名稱** | **barChart** |
   | **Text** | **橫條圖** |

4. 將第三個選項按鈕加入至使用者控制項，並變更下列屬性。

   | 屬性 | 值 |
   |----------|----------------|
   | **名稱** | **lineChart** |
   | **Text** | **折線圖** |

5. 將第四個選項按鈕加入至使用者控制項，並變更下列屬性。

   |屬性|值|
   |--------------|-----------|
   |**名稱**|**areaBlockChart**|
   |**Text**|**區塊圖**|

   接下來，撰寫程式碼，以在按一下選項按鈕時更新圖表。

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>選取選項按鈕時變更圖表樣式
 現在您可以加入程式碼來變更圖表樣式。 若要這樣做，請在使用者控制項上建立公用事件、加入屬性來設定選取專案類型，以及為 `CheckedChanged` 每個選項按鈕的事件建立事件處理常式。

### <a name="to-create-an-event-and-property-on-a-user-control"></a>在使用者控制項上建立事件和屬性

1. 在 **方案總管** 中，以滑鼠右鍵按一下使用者控制項，然後按一下 [ **視圖程式碼**]。

2. 將程式碼加入至 `ChartOptions` 類別，以建立 `SelectionChanged` 事件和 `Selection` 屬性。

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>處理選項按鈕的 CheckedChanged 事件

1. 在 `CheckedChanged` 選項按鈕的 `areaBlockChart` 事件處理常式中設定圖表類型，然後再引發事件。

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]

2. 在 `CheckedChanged` 選項按鈕的 `barChart` 事件處理常式中設定圖表類型。

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]

3. 在 `CheckedChanged` 選項按鈕的 `columnChart` 事件處理常式中設定圖表類型。

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]

4. 在 `CheckedChanged` 選項按鈕的 `lineChart` 事件處理常式中設定圖表類型。

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]

5. 在 C# 中，您必須為選項按鈕加入事件處理常式。 您可以將程式碼加入至 `ChartOptions` 建構函式，放在 `InitializeComponent` 的呼叫下方。 如需如何建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]

## <a name="add-the-user-control-to-the-worksheet"></a>將使用者控制項新增至工作表
 當您建立方案時，會自動將新的使用者控制項新增至 [ **工具箱**]。 然後，您可以將控制項從 [ **工具箱** ] 拖曳至工作表。

### <a name="to-add-the-user-control-your-worksheet"></a>若要將使用者控制項加入工作表

1. 在 [建置] 功能表上，按一下 [建置方案]。

     **ChartOptions** 使用者控制項就會加入至 [**工具箱**]。

2. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **Sheet1** ] 或 [ **Sheet1.cs**]，然後按一下 [ **視圖設計** 工具]。

3. 將 **ChartOptions** 控制項從 [ **工具箱** ] 拖曳至工作表。

     系統會將名為的新控制項 `my_Excel_Chart_ChartOptions1` 加入至您的專案。

4. 將控制項的名稱變更為 **ChartOptions1**。

## <a name="change-the-chart-type"></a>變更圖表類型
 若要變更圖表類型，請建立事件處理常式，以根據使用者控制項中選取的選項設定樣式。

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>變更工作表中顯示的圖表類型

1. 將以下事件處理常式新增至 `Sheet1` 類別。

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]

2. 在 c # 中，您必須將使用者控制項的事件處理常式加入至 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件，如下所示。 如需如何建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]

## <a name="test-the-application"></a>測試應用程式
 您現在可以測試活頁簿，以確認當您選取選項按鈕時，圖表的樣式是否正確。

### <a name="to-test-your-workbook"></a>測試您的活頁簿

1. 按 **F5** 執行您的專案。

2. 選取不同的選項按鈕。

3. 確認圖表樣式的變更與所選的項目相符。

## <a name="next-steps"></a>後續步驟
 本逐步解說將示範如何在工作表上使用選項按鈕和圖表樣式的基本概念。 接著可以執行下列一些工作：

- 部署專案。 如需詳細資訊，請參閱 [部署 Office 方案](../vsto/deploying-an-office-solution.md)。

- 使用按鈕填入文字方塊。 如需詳細資訊，請參閱 [逐步解說：使用按鈕在工作表的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)。

- 使用核取方塊變更工作表上的格式。 如需詳細資訊，請參閱 [逐步解說：使用 CheckBox 控制項變更工作表格式](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)。

## <a name="see-also"></a>另請參閱
- [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)
