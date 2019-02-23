---
title: 逐步解說：針對 NamedRange 控制項的事件進行程式設計
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 44efc94f1bd9f0c2e962bf08bb663ada834f5b68
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633235"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>逐步解說：針對 NamedRange 控制項的事件進行程式設計
  本逐步解說示範如何新增<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項，Microsoft Office Excel 工作表並對其事件，藉由使用 Visual Studio 中 Office 開發工具的程式。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 在這個逐步解說期間，您將了解如何：

-   新增<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項加入工作表。

-   針對程式設計<xref:Microsoft.Office.Tools.Excel.NamedRange>控制事件。

-   測試您的專案。

> [!NOTE]
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

## <a name="create-the-project"></a>建立專案
 在此步驟中，您將建立使用 Visual Studio 的 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1.  建立 Excel 活頁簿專案同名**我的具名範圍事件**。 請確定**建立新的文件**已選取。 如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 設計工具中開啟新的 Excel 活頁簿，並將**My 名為範圍的事件**專案加入**方案總管 中**。

## <a name="add-text-and-named-ranges-to-the-worksheet"></a>加入文字和具名工作表範圍
 因為主控制項擴充 Office 物件，您可以將它們新增至相同的方式在文件中，您會將原生的物件。 比方說，您可以在其中加入 Excel<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項加入工作表，開啟**插入**功能表，指向**名稱**，然後選擇**定義**。 您也可以加入<xref:Microsoft.Office.Tools.Excel.NamedRange>藉由將它從控制項**工具箱**到工作表。

 在此步驟中，您會將兩個具名的範圍控制項新增至工作表使用**工具箱**，然後將文字加入工作表。

### <a name="to-add-a-range-to-your-worksheet"></a>將範圍新增到您的工作表

1.  確認*My 名為範圍 Events.xlsx*活頁簿是在 Visual Studio 設計工具中開啟與`Sheet1`顯示。

2.  從**Excel 控制項** 索引標籤的 工具箱 拖曳<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項加入儲存格**A1**在`Sheet1`。

     **加入 NamedRange 控制項** 對話方塊隨即出現。

3.  確認 **$A$ 1**會出現在可編輯的文字方塊中，且儲存格**A1**已選取。 如果沒有，請按一下資料格**A1**來選取它。

4.  按一下 [確定] 。

     儲存格**A1**成為名為範圍`namedRange1`。 沒有在工作表中的可見指示，但`namedRange1`會出現在**名稱**方塊 （位於工作表左邊的正上方） 當資料格**A1**已選取。

5.  新增另一個<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項加入儲存格**B3**。

6.  確認 **$B$ 3**會出現在可編輯的文字方塊中，且儲存格**B3**已選取。 如果沒有，請按一下資料格**B3**來選取它。

7.  按一下 [確定] 。

     儲存格**B3**成為名為範圍`namedRange2`。

### <a name="to-add-text-to-your-worksheet"></a>將文字加入工作表

1. 在資料格中**A1**，輸入下列文字：

    **這是 NamedRange 控制項的範例。**

2. 在資料格中**A3** (左邊的`namedRange2`)，輸入下列文字：

    **事件：**

   在下列章節中，您將撰寫程式碼，將文字插入`namedRange2`，並修改的屬性`namedRange2`控制項以回應<xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>， <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>，並<xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>事件`namedRange1`。

## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>加入程式碼以回應 BeforeDoubleClick 事件

### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>若要將文字插入 NamedRange2 根據 BeforeDoubleClick 事件

1.  在 **方案總管**，以滑鼠右鍵按一下**Sheet1.vb**或**Sheet1.cs** ，然後選取**檢視程式碼**。

2.  加入程式碼因此`namedRange1_BeforeDoubleClick`事件處理常式看起來如下：

     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]

3.  在 C# 中，您必須新增事件處理常式命名的範圍中所示<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>以下事件。 如需建立事件處理常式的詳細資訊，請參閱[How to:建立 Office 專案中的事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]

## <a name="add-code-to-respond-to-the-change-event"></a>加入程式碼以回應變更事件

### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>若要將文字插入 namedRange2 根據變更事件

1.  加入程式碼因此`NamedRange1_Change`事件處理常式看起來如下：

     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]

    > [!NOTE]
    >  按兩下 在 Excel 範圍中的儲存格進入編輯模式，因為<xref:Microsoft.Office.Tools.Excel.NamedRange.Change>即使不發生任何變更文字選取項目移超出範圍時，就會發生事件。

## <a name="add-code-to-respond-to-the-selectionchange-event"></a>新增程式碼來回應 SelectionChange 事件

### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>將文字插入 namedRange2 根據 SelectionChange 事件

1.  加入程式碼這麼**NamedRange1_SelectionChange**事件處理常式看起來如下：

     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]

    > [!NOTE]
    >  因為按兩下 Excel 範圍中的資料格選取範圍移動到範圍內，就會導致<xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>事件發生之前<xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>就會發生事件。

## <a name="test-the-application"></a>測試應用程式
 現在您可以測試您的活頁簿，以確認該文字描述的事件<xref:Microsoft.Office.Tools.Excel.NamedRange>引發事件時，將會插入至另一個已命名範圍的控制項。

### <a name="to-test-your-document"></a>測試文件

1.  按下**F5**執行您的專案。

2.  將游標置於`namedRange1`，並確認文字有關<xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>插入事件和註解插入至工作表。

3.  按兩下內`namedRange1`，並確認文字相關<xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>事件會插入使用中的紅色斜體文字`namedRange2`。

4.  按一下 外部`namedRange1`和附註的變更事件發生時結束編輯模式，即使未進行任何變更的文字。

5.  變更文字內`namedRange1`。

6.  外按一下`namedRange1`，並確認文字相關<xref:Microsoft.Office.Tools.Excel.NamedRange.Change>事件會插入具有藍色文字`namedRange2`。

## <a name="next-steps"></a>後續步驟
 此逐步解說將示範針對事件進行程式設計的基本概念<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項。 以下是可能來自於下一步的工作：

-   部署專案。 如需詳細資訊，請參閱 <<c0> [ 部署 Office 方案](../vsto/deploying-an-office-solution.md)。

## <a name="see-also"></a>另請參閱
- [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)
- [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [如何：調整 NamedRange 控制項的大小](../vsto/how-to-resize-namedrange-controls.md)
- [如何：將 NamedRange 控制項加入工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [如何：建立 Office 專案中的事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)
