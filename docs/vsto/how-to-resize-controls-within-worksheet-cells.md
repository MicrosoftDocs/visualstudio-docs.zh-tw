---
title: HOW TO：調整工作表儲存格內的控制項的大小
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 67ec290959263282c9a6f924ca9d6ba2c67b5930
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927346"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>HOW TO：調整工作表儲存格內的控制項的大小
  當您調整資料行或工作表上的資料列時，資料格內的任何主控制項自動調整大小的高度或寬度已調整大小之儲存格。 Windows Form 控制項不調整大小會自動預設。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 如果您在設計階段加入控制項，您必須設定位置的每個控制項的選項。  
  
 如果您以程式設計方式將 Windows Form 控制項，並提供範圍引數，控制項會自動調整大小的範圍內的儲存格重新調整大小時。 如需詳細資訊，請參閱 <<c0> [ 將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
## <a name="resize-controls-at-design-time"></a>在設計階段調整控制項的大小  
  
### <a name="to-make-controls-resize-with-cells-at-design-time"></a>若要使控制項在設計階段使用的儲存格調整大小  
  
1.  從**工具箱**，Windows Form 控制項拖曳到工作表。  
  
2.  以滑鼠右鍵按一下控制項，然後按一下**控制項格式**。  
  
3.  在 **控制項格式** 對話方塊中，按一下**屬性** 索引標籤。  
  
4.  底下**物件的定位**，選取**位置和大小與資料格**選項，然後再按一下 **[確定]**。  
  
     當您調整包含控制項的資料格時，控制項調整大小以配合儲存格。  
  
## <a name="resize-controls-at-runtime"></a>在執行階段的控制項重新調整大小  
 如果您在執行階段將 Windows Form 控制項，並傳入<xref:Microsoft.Office.Interop.Excel.Range>做為控制項的位置，控制項將自動調整大小的工作表資料格範圍，是調整大小時。  
  
### <a name="to-make-controls-resize-with-cells-at-run-time"></a>若要使控制項在執行階段使用的儲存格調整大小  
  
1.  您可以將控制項加入 A1 的範圍。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]  
  
     當您調整包含控制項的資料格時，控制項調整大小以配合儲存格。  
  
## <a name="reset-control-placement"></a>重設控制項的位置  
 您可以重設位置和設定控制項的調整大小`Placement`屬性，以下列其中一種<xref:Microsoft.Office.Interop.Excel.XlPlacement>值：  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>若要變更控制項的行為，使它不會調整大小或移動與儲存格  
  
1.  呼叫控制項的 [位置] 屬性，並將值設為<xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]  
  
## <a name="see-also"></a>另請參閱  
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [如何：將 Windows Form 控制項加入 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [如何：列印時隱藏工作表的控制項](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office 文件上的 Windows Form 控制項的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
