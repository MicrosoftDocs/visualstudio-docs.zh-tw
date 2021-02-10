---
title: 逐步解說：針對 NamedRange 控制項的事件進行程式設計
description: 瞭解如何使用 Visual Studio 中的 Office 開發工具，將 NamedRange 控制項新增至 Microsoft Excel 工作表，並針對其事件進行程式設計。
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b3305fdc8f4fbadb3dcdd9775c3a6fe3dac3a1fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937390"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>逐步解說：針對 NamedRange 控制項的事件進行程式設計
  本逐步解說將示範如何 <xref:Microsoft.Office.Tools.Excel.NamedRange> 使用 Visual Studio 中的 Office 開發工具，將控制項加入至 Microsoft Office Excel 工作表，並針對其事件進行程式設計。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 在這個逐步解說期間，您將了解如何：

- 將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項新增至工作表。

- 針對控制事件進行程式設計 <xref:Microsoft.Office.Tools.Excel.NamedRange> 。

- 測試您的專案。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

## <a name="create-the-project"></a>建立專案
 在這個步驟中，您將使用 Visual Studio 建立 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 使用「 **我的命名範圍事件**」名稱來建立 Excel 活頁簿專案。 確定已選取 [ **建立新檔** ]。 如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 [ **我的命名範圍事件** ] 專案加入 **方案總管**。

## <a name="add-text-and-named-ranges-to-the-worksheet"></a>將文字和命名範圍新增至工作表
 因為主控制項是擴充的 Office 物件，所以您可以用加入原生物件的相同方式，將它們加入至檔。 例如，您可以 <xref:Microsoft.Office.Tools.Excel.NamedRange> 開啟 [ **插入** ] 功能表，指向 [ **名稱**]，然後選擇 [ **定義**]，將 Excel 控制項加入工作表。 您也可以將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項從 [ **工具箱** ] 拖曳至工作表來加入控制項。

 在這個步驟中，您會使用 [ **工具箱**] 將兩個命名範圍控制項新增至工作表，然後將文字加入工作表。

### <a name="to-add-a-range-to-your-worksheet"></a>若要將範圍加入至工作表

1. 確認 [ *我的命名範圍 Events.xlsx* 活頁簿已在 Visual Studio 設計工具中開啟，並 `Sheet1` 顯示。

2. 從 [工具箱] 的 [ **Excel 控制項** ] 索引標籤中，將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項拖曳至中的儲存格 **A1** `Sheet1` 。

     [ **加入 NamedRange 控制項** ] 對話方塊隨即出現。

3. 確認 **$A $1** 出現在 [可編輯] 文字方塊中，並且已選取該儲存格 **A1** 。 如果不是，請按一下 [儲存格 **A1** ] 加以選取。

4. 按一下 [確定]  。

     儲存格 **A1** 會成為名為的範圍 `namedRange1` 。 工作表上沒有可見的指示，但 `namedRange1` 會出現在 [ **名稱** ] 方塊中 (位於左側工作表的上方，) 選取 [儲存格 **A1** ]。

5. 將另一個 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項新增至儲存格 **B3**。

6. 確認 **$B $3** 出現在 [可編輯] 文字方塊中，而且已選取 [ **B3** ] 儲存格。 如果不是，請按一下資料格 **B3** 加以選取。

7. 按一下 [確定]  。

     儲存格 **B3** 變成名為的範圍 `namedRange2` 。

### <a name="to-add-text-to-your-worksheet"></a>將文字加入工作表

1. 在 [儲存格 **A1**] 中，輸入下列文字：

    **這是 NamedRange 控制項的範例。**

2. 在) 左邊的儲存格 **A3** (中 `namedRange2` ，輸入下列文字：

    **事件：**

   在下列各節中，您將撰寫程式碼， `namedRange2` `namedRange2` 以回應的 <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> 、 <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> 和事件，在控制項中插入文字並修改控制項的屬性 <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> `namedRange1` 。

## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>新增程式碼以回應 BeforeDoubleClick 事件

### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>根據 BeforeDoubleClick 事件將文字插入至 NamedRange2

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **Sheet1** ] 或 [ **Sheet1.cs** ]，然後選取 [ **視圖程式碼**]。

2. 加入程式碼，讓 `namedRange1_BeforeDoubleClick` 事件處理常式看起來如下所示：

     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]

3. 在 c # 中，您必須加入命名範圍的事件處理常式，如 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 下列事件所示。 如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]

## <a name="add-code-to-respond-to-the-change-event"></a>加入程式碼以回應變更事件

### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>根據變更事件將文字插入至 namedRange2

1. 加入程式碼，讓 `NamedRange1_Change` 事件處理常式看起來如下所示：

     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]

    > [!NOTE]
    > 因為按兩下 Excel 範圍中的儲存格進入編輯模式， <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> 即使沒有對文字進行任何變更，當選取範圍移至範圍之外時，也會發生事件。

## <a name="add-code-to-respond-to-the-selectionchange-event"></a>新增程式碼以回應 SelectionChange 事件

### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>根據 SelectionChange 事件將文字插入至 namedRange2

1. 加入程式碼，讓 **NamedRange1_SelectionChange** 的事件處理常式看起來如下所示：

     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]

    > [!NOTE]
    > 因為按兩下 Excel 範圍中的資料格會使選取範圍移至範圍中，事件發生 <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> 之前就會發生事件 <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> 。

## <a name="test-the-application"></a>測試應用程式
 現在您可以測試活頁簿，以確認描述控制項事件的文字在 <xref:Microsoft.Office.Tools.Excel.NamedRange> 引發事件時，會插入另一個命名範圍中。

### <a name="to-test-your-document"></a>測試文件

1. 按 **F5** 執行您的專案。

2. 將游標放在中 `namedRange1` ，並確認已插入有關事件的文字， <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> 並將批註插入工作表中。

3. 按兩下 [內部] `namedRange1` ，並確認 <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> 已在中插入有關事件的文字，並以紅色斜體文字插入 `namedRange2` 。

4. 按一下 [外部 `namedRange1` ]，請注意，即使沒有對文字進行任何變更，結束編輯模式時也會發生變更事件。

5. 變更內的文字 `namedRange1` 。

6. 按一下 [外部] `namedRange1` ，並確認 [關於] <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> 事件的文字會插入藍色文字 `namedRange2` 。

## <a name="next-steps"></a>下一步
 本逐步解說將說明針對控制項事件進行程式設計的基本概念 <xref:Microsoft.Office.Tools.Excel.NamedRange> 。 以下是接下來可能會發生的工作：

- 部署專案。 如需詳細資訊，請參閱 [部署 Office 方案](../vsto/deploying-an-office-solution.md)。

## <a name="see-also"></a>另請參閱
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [如何：調整 NamedRange 控制項的大小](../vsto/how-to-resize-namedrange-controls.md)
- [如何：將 NamedRange 控制項加入至工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)
