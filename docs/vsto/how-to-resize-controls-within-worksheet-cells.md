---
title: "如何： 調整工作表儲存格內的控制項的大小 |Microsoft 文件"
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
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
ms.assetid: 1439db4a-e64b-4381-a6e6-605ba94db3de
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 75759b501741329808198aafbc7dd39d0994cb98
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>如何：在工作表儲存格中調整控制項的大小
  當您調整資料行或工作表上的資料列時，會自動包含在資料格中任何主控制項調整大小，以高度或寬度調整過大小的儲存格。 Windows Form 控制項不調整大小會自動根據預設。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 如果您在設計階段加入控制項，您必須設定位置選項對每個控制項。  
  
 如果您以程式設計方式加入 Windows Form 控制項，並提供範圍引數，控制項會自動調整大小重新調整大小之範圍內的資料格。 如需詳細資訊，請參閱 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
## <a name="resizing-controls-at-design-time"></a>在設計階段調整控制項大小  
  
#### <a name="to-make-controls-resize-with-cells-at-design-time"></a>若要使控制項在設計階段調整大小與資料格  
  
1.  從**工具箱**，將 Windows Form 控制項拖曳至工作表。  
  
2.  以滑鼠右鍵按一下控制項，然後按一下**控制項格式**。  
  
3.  在**控制項格式**對話方塊中，按一下 [**屬性**] 索引標籤。  
  
4.  下**物件位置**，選取**位置和大小與資料格**選項，然後再按一下**確定**。  
  
     當您調整資料格包含控制項時，控制項調整大小以配合儲存格。  
  
## <a name="resizing-controls-at-run-time"></a>在執行階段調整控制項大小  
 如果您在執行階段加入 Windows Form 控制項，並傳入<xref:Microsoft.Office.Interop.Excel.Range>作為控制項的位置，控制項將自動調整大小重新調整大小的儲存格包含範圍。  
  
#### <a name="to-make-controls-resize-with-cells-at-run-time"></a>若要使控制項在執行階段調整大小與資料格  
  
1.  將控制項加入至範圍 A1。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]  
  
     當您調整資料格包含控制項時，控制項調整大小以配合儲存格。  
  
## <a name="resetting-control-placement"></a>重設控制項位置  
 您可以重設位置與設定控制項的調整大小`Placement`屬性，以下列其中一種<xref:Microsoft.Office.Interop.Excel.XlPlacement>值：  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>若要變更控制項的行為，使它不會調整大小或移動與儲存格  
  
1.  呼叫控制項的位置屬性，並將值設為<xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]  
  
## <a name="see-also"></a>請參閱  
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [如何： 將 Windows Form 控制項加入 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [如何： 列印時隱藏工作表上的控制項](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [在執行階段將控制項加入 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office 文件上的 Windows Forms 控制項限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  