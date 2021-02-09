---
title: 如何：調整工作表儲存格內的控制項大小
description: 瞭解如何在設計階段和執行時間，使用 Visual Studio 來調整 Microsoft Excel 工作表儲存格內控制項的大小。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7b62d3fed62b4d17b9f1918b76760593b38d83a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927817"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>如何：調整工作表儲存格內的控制項大小
  當您調整工作表上的資料行或資料列時，資料格內的任何主控制項都會自動調整大小，以調整大小的儲存格高度或寬度。 Windows Forms 控制項預設不會自動調整大小。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 如果您在設計階段加入控制項，則必須設定每個控制項的定位選項。

 如果您以程式設計方式加入 Windows Forms 控制項，並提供範圍引數，當調整範圍內的儲存格大小時，控制項會自動調整大小。 如需詳細資訊，請參閱 [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。

## <a name="resize-controls-at-design-time"></a>在設計階段調整控制項大小

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>在設計階段讓控制項調整資料格的大小

1. 將 Windows Forms 控制項從 [ **工具箱**] 拖曳至工作表。

2. 以滑鼠右鍵按一下控制項，然後按一下 [ **格式化控制項**]。

3. 在 [ **格式控制項** ] 對話方塊中，按一下 [ **屬性** ] 索引標籤。

4. 在 [ **物件定位**] 底下，選取 [ **使用儲存格移動和大小** ] 選項，然後按一下 **[確定]**。

     當您調整包含控制項的儲存格大小時，控制項會調整大小以符合儲存格。

## <a name="resize-controls-at-run-time"></a>在執行時間調整控制項的大小
 如果您在執行時間加入 Windows Forms 控制項，並傳入做為 <xref:Microsoft.Office.Interop.Excel.Range> 控制項的位置，則在重設包含該範圍之工作表資料格的大小時，控制項會自動調整大小。

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>讓控制項在執行時間使用儲存格調整大小

1. 將控制項新增至範圍 A1。

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]

     當您調整包含控制項的儲存格大小時，控制項會調整大小以符合儲存格。

## <a name="reset-control-placement"></a>重設控制項位置
 您可以將 `Placement` 屬性設定為下列其中一個值，以重設控制項的放置和調整大小 <xref:Microsoft.Office.Interop.Excel.XlPlacement> ：

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>變更控制項的行為，使其不會以儲存格調整大小或移動

1. 呼叫控制項的 [位置] 屬性，並將值設定為 <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating> 。

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]

## <a name="see-also"></a>另請參閱
- [Office 檔上的控制項](../vsto/controls-on-office-documents.md)
- [如何：將 Windows Forms 控制項新增至 Office 檔](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [如何：列印時隱藏工作表上的控制項](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [在執行時間將控制項新增至 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Office 檔上 Windows Forms 控制項的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
